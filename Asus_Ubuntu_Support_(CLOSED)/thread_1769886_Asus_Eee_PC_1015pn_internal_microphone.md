---
title: "Asus Eee PC 1015pn internal microphone"
date: 2011-05-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Jinseru on 2011-05-28
Ok, so I've searched, and it just doesn't make sense. Initially I had an issue with the sound from the internal speakers, but PulseAudio and Alsa fixed this problem right up for me, but now I cant get Ubuntu 11.04 to recognise the internal microphone that comes with my internal webcam. The camera works, but when I look at the settings for input it doesn't recognise any input devices. I'm kinda stuck at this point, and I have to believe that there is a fix for this, but I can't figure it out.

---

### Post by The Bird Man of Alcatraz on 2011-05-29
I have the same netbook, and had the same problem at some point.  May be from a different cause, though. 

Two things to check; first, that the Sound Preferences aren't stuck on the HDMI audio hardware, and second, that in the drop down menu on the Hardware tab Settings for the Selected Device, the Duplex option is selected.

---

### Post by Deevad on 2011-06-01
Same here, with another model but in the same serie ; my wife laptop ( 1005HA eeepc ) internal microphone doesn't work anymore (it worked good weeks ago). Something dealing with last updates for sure ( Maverick Meerkat ). 

I suscribe to this thread if a power user can answer and help to repare. The workaround is a mini-jack microphone for the moment, and it works fine.

---

### Post by antoiner_roquentin on 2011-06-08
I am stuck with a similar problem. I have an ASUS Eee PC and run Ubuntu, for some reason when I try to make phone calls inside of Gmail I can hear people but they can not hear me speaking. I know that my microphone works because I have loaded the sound recorder and successfully used it. I checked the options under hardware and made sure it was set to the "Duplex" option; I am really at a loss as to why this will not work.

Super users, please help!

---

### Post by lidex on 2011-06-18
> **antoiner_roquentin said:**
> I am stuck with a similar problem. I have an ASUS Eee PC and run Ubuntu, for some reason when I try to make phone calls inside of Gmail I can hear people but they can not hear me speaking. I know that my microphone works because I have loaded the sound recorder and successfully used it. I checked the options under hardware and made sure it was set to the "Duplex" option; I am really at a loss as to why this will not work.

Super users, please help!

If your mic works, then its something else. Do you have google talk plugin installed?
[http://www.ubuntuupdates.org/ppas/47](http://www.ubuntuupdates.org/ppas/47)

---

### Post by SeijiSensei on 2011-07-20
I found a solution to the microphone problem with Skype on a 1201n.  I'd suspect the problem is the same across many EeePC's.

1)  Run "sudo apt-get install pavucontrol" which is the volume control applet for PulseAudio.

2)  Make sure that your PulseAudio settings are correct.  I'm using Kubuntu 10.10 where they are controlled via System Settings > Multimedia > Phonon.  Make the NVIDIA microphone device the default.

3)  Now start Skype and choose Options > Audio.  Uncheck the box that tells Skype to manage your microphone.

4)  Open the pavucontrol applet; I did this by running it in a terminal.  Now choose the Input Devices tab, and click the icon to unlock the two volume sliders.  Put one slider at 100% and the other at 0%.

5)  Try making a test call to the Echo123 service at Skype.  Your microphone should function correctly.

---

### Post by Deevad on 2011-07-25
**@SeijiSensei : ** Many thanks ! It worked here for a 1005Ha ( even if I don't have Nvidia ). Only this steps was suffisent to me :

1) Open pavucontrol from a terminal ( was installed on the default edition )
2) Now choose the Input Devices tab, and click the icon to unlock the two volume sliders. Put one slider at 100% and the other at 0%.

I still get a noisy sound, maybe worst than it was before from the echo123 test. I guess this bad recognition as stereo microphone is the root of the problem, and this trick help to use it but is not well optimised to take part of the full quality of the microphone. Too bad I don't know to who repport the problem ; if someone have an idea, go for it !
Many thanks again.

---

### Post by r_mano on 2011-11-30
I opened a bug report at [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/898081](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/898081), please follow that and "affects me" if it's the case...

---

### Post by r_mano on 2011-11-30
I tried the solution posted in the bug, following instructions from [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS) 

It works!

---

