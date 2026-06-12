---
title: "Keyboard volume control for USB Audio?"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Lokanna on 2007-07-29
I just purchased a Turtle Beach Audio Advantage Micro USB sound card due to Creative sucking sweaty globes which reside on the under carriage of Rhinoceros' and I'm having a difficult time with one (to me) very important ability.

With my onboard audio, I was able to setup my keyboard to adjust volume no matter what program I was in.  I have audio coming through the USB right now and I'm able to adjust it; but the keyboard commands won't work.  

I first went to System > Preferences > Sound and changed the playbacks to "USB Audio".  However, the bottom category lists Default Mixer Tracks as C-Media USB Audio (ALSA), so I selected that.  

In my keyboard shortcuts, I ensured the volume knobs were configured. 

I then fired up both Rhythmbox and XMMS to play music.  I tried to adjust the volume and GNOME pops up the little graphical window which displays the sound going up and down, however, the volume isn't changing.  Rhythmbox is pretty limited in the options department so I fired up XMMS to see if I could configure IT to allow GNOME to adjust it's volume.  No matter what options I tried, I was unable to accomplish the task.  

I googled this problem and didn't uncover to many posts/articles.  The few I did turn up mainly dealt with users not getting sound the moment they plugged the USB dongle into their port.  I knew enough to figure that out, just can't get these keyboard controls.  

Is this something that is just a limitation of the OS, or can this be accomplished?  My keyboard is a Microsoft Reclusa (however it's configured as a generic 105).  I'd appreciate any help, it's pretty frustration as I really need to be able to adjust this on the fly (god forbid I 'accidently' don't hear my wife ;D) 

](*,)

---

### Post by sad_iq on 2007-07-29
Try selecting pcm from System->Preferences->sound and see if it works.

---

### Post by Lokanna on 2007-07-29
> **sad_iq said:**
> Try selecting pcm from System->Preferences->sound and see if it works.

PCM is the only available option for the Mixer and is selected.  I re-selected it per the suggestion and it's still not controlling my volume.  

Any other suggestions?

---

### Post by sad_iq on 2007-07-30
Open volume control then Edit->Preferences and select witch sliders you can have in that box!!! Then with all of them opened see witch slider goes up and down when pressing the keyboard buttons and replace pcm with that...see if it works!!!

---

### Post by mcduck on 2007-07-30
Go to System/Preferences/Sound and you can select there the sound interface & channels to be controlled by your keyboard. If you don't see all channels then go to mixer, set that to use your USB sound card and then enable all available channels in Preferences.

---

