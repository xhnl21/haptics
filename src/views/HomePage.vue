<template>
  <ion-page>
    <ion-content :fullscreen="true">
      <div id="container">
        <ion-button @click="triggerHapticFeedback">Trigger Haptic Feedback</ion-button>
        <ion-button @click="hapticsImpactMedium">hapticsImpactMedium</ion-button>
        <ion-button @click="hapticsImpactLight">hapticsImpactLight</ion-button>
        <ion-button @click="hapticsVibrate">hapticsVibrate</ion-button>
        <ion-button @click="hapticsSelectionStart">hapticsSelectionStart</ion-button>
        <ion-button @click="hapticsSelectionChanged">hapticsSelectionChanged</ion-button>
        <ion-button @click="hapticsSelectionEnd">hapticsSelectionEnd</ion-button>
      </div>
    </ion-content>
  </ion-page>
</template>

<script>
import { Haptics, ImpactStyle } from '@capacitor/haptics';
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'HapticsExample',
  setup() {
    const triggerHapticFeedback = async () => {
      try {
        await Haptics.impact({ style: 'heavy' });
      } catch (err) {
        console.error('Error triggering haptic feedback:', err);
      }
    };

    const hapticsImpactMedium = async () => {
      await Haptics.impact({ style: ImpactStyle.Medium });
    };

    const hapticsImpactLight = async () => {
      await Haptics.impact({ style: ImpactStyle.Light });
    };

    const hapticsVibrate = async () => {
      await Haptics.vibrate();
    };

    const hapticsSelectionStart = async () => {
      await Haptics.selectionStart();
    };

    const hapticsSelectionChanged = async () => {
      await Haptics.selectionChanged();
    };

    const hapticsSelectionEnd = async () => {
      await Haptics.selectionEnd();
    };
    return { triggerHapticFeedback, hapticsImpactMedium, hapticsImpactLight, hapticsVibrate, hapticsSelectionStart, hapticsSelectionChanged, hapticsSelectionEnd};
  },
});
</script>

<style scoped>
#container {
  text-align: center;
  
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  
  color: #8c8c8c;
  
  margin: 0;
}

#container a {
  text-decoration: none;
}
</style>
