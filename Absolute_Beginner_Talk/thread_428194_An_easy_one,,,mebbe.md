---
title: "An easy one,,,mebbe"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-04-30
I just loaded around 8-900 Midis from XP and they won't play. Kmid and Rhythmbox say they can't open [dev/sequencer] as it may be in use or not installed. I looked through everything in Synaptic and could find it not.

Any idea as to where I can find/enable this dev thing?

Thanks tons,

Jon

---

### Post by blackened on 2007-04-30
I'm by no means an audio expert, so take of this what you will. It sounds like both programs are looking for an external (hardware) midi sequencer. In Linux, devices, both internal and external, are treated as files, hence the /dev directory.

You should be able to go into preferences in each program and change to a software sequencer such as rosegarden or jazz++ or something. Like I said though, I'm no audio expert.

---

### Post by girishv on 2007-04-30
If you simply want to replay the midi's you copied, you can use timidity
Install it if you have not already
sudo apt-get install timidity

Girish

---

### Post by koconnor100 on 2007-04-30
> **Romin-1 said:**
> I just loaded around 8-900 Midis from XP and they won't play. Kmid and Rhythmbox say they can't open [dev/sequencer] as it may be in use or not installed. I looked through everything in Synaptic and could find it not.

Any idea as to where I can find/enable this dev thing?

Thanks tons,

Jon

go to google
search for easyubuntu
install it
Reboot computer
Run it (from the menu's) 

EasyUbuntu contains the most common patches for ubuntu that most users want. Straight off the Live CD the music player and dvd player arn't actually much good, along with a host of other odds and ends. Just start her up , click on the updates you want (don't install nvidea drivers if you don't have an nvidia card ...in fact if your video is working you may wanna skip all video options entirely) and off she goes. 

Oh , and if the list falls off the bottom of the screen ,which it useally does .... 
click on an item in the list
Tab once, you're now in the password field
enter your password
tab once , you're now on the ok button
press enter. 

Watch the pretty lights and bars ....

---

### Post by Romin-1 on 2007-04-30
Thanks for your help fellas.

I installed Timidity with Synaptic and now I can't find the danged thang. Looked everywhere with no joy. Where is it hiding and how do I get it out where I can use it? Same thing happened with Wine. I download and install stuff and they go missing on me.

Frustratedly,

Jon

PS: Aint' got much hair left,,,

---

### Post by Terl on 2007-04-30
> **Romin-1 said:**
> Thanks for your help fellas.

I installed Timidity with Synaptic and now I can't find the danged thang. Looked everywhere with no joy. Where is it hiding and how do I get it out where I can use it? Same thing happened with Wine. I download and install stuff and they go missing on me.

Frustratedly,

Jon

PS: Aint' got much hair left,,,

For Wine -->  type winefile at the prompt in a terminal.  It will create folders and add it to your menu.  Type winecfg to configure.

try typing timidity at the command prompt.  Maybe that will open it.

---

### Post by Romin-1 on 2007-04-30
Thanks heaps, that found Wine but timidity only brings up the EULA, drat!

Thanks again,

Jon

---

