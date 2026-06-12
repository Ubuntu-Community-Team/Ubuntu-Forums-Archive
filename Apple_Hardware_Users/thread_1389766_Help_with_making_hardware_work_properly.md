---
title: "Help with making hardware work properly"
date: 2010-01-24
forum: Apple Hardware Users
---

### Post by breimer273 on 2010-01-24
Hello, I am a rejuvenated user of Ubuntu last time I used Ubuntu they were on Gusty Gibbon. But now I have a MacBook Pro and I am trying to install Ubuntu. I did the install properly using these instructions:
> [http://ubuntuforums.org/showthread.php?t=1192296](http://ubuntuforums.org/showthread.php?t=1192296)

Now here is where I am having problems:
First on step 3 of part two, getting access to the MAC HD user folder. It fails saying I do not have permission to access the directory. When I try to change the GID, mine is 20, it tells me that 20 is not a unique GID. Changing the User ID seems to work fine and then the last part actually changing the permissions does not work.

Second, The sound I followed all the instructions for the sound and I still got nothing at all.

Third, the keyboard brightness keys again I followed the instructions installed the package it told me to install and still does not control my screen or keyboard brightness. I don't know if the mic works because my speakers still don't work.

I am a fairly familiar with the Terminal but still a novice so please be clear with your instructions but I am an experienced computer user just not with Linux. Thanks for any help and I am so far glad to be back in the Linux world.

---

### Post by breimer273 on 2010-01-25
Also one other note, I just upgraded to version 9.10 I am still having the same problems as stated above but I thought I would add this so that all information is as current as possible.

---

### Post by Tycho59 on 2010-01-25
I myself am having issues setting up the Isight camera and still trying to figure out how to deal with adjusting the brightness of the screen.

What I CAN tell you is that to fix your issue with the mic and speakers is to install an app called gnome alsa mixer. To get the mic to work, make sure that both "rec" boxes are check and both captures are all the way up and you will be able to record audio.  As for playback of audio uncheck both of the mute buttons and you are all set.

---

### Post by adam814 on 2010-01-25
Well, I can tell you why you're getting that message while changing the GID.  On my system GID 20 is already in use by the dialout group.  My user is a member of the dialout group so I don't think changing your primary group id to 20 (or adding yourself to it as the case may be) would cause any real problems.

On my system there's no user with UID 20, so I think you're in the clear there.

Are you still getting permission denied errors reading from your Mac volume?

---

### Post by linuxopjemac on 2010-01-25
[http://mac.linux.be/content/how-access-files-osx-linux](http://mac.linux.be/content/how-access-files-osx-linux)

Tycho59: install pommed for brightness

breimer 273: what model MBP you have ? Brigtness: install pommed

---

### Post by breimer273 on 2010-01-25
> **Tycho59 said:**
> I myself am having issues setting up the Isight camera and still trying to figure out how to deal with adjusting the brightness of the screen.

What I CAN tell you is that to fix your issue with the mic and speakers is to install an app called gnome alsa mixer. To get the mic to work, make sure that both "rec" boxes are check and both captures are all the way up and you will be able to record audio.  As for playback of audio uncheck both of the mute buttons and you are all set.

I saw that on a different post and I made sure there are no mute boxes checked and all sliders are all the way up still nothing...

---

### Post by breimer273 on 2010-01-25
> **adam814 said:**
> Well, I can tell you why you're getting that message while changing the GID.  On my system GID 20 is already in use by the dialout group.  My user is a member of the dialout group so I don't think changing your primary group id to 20 (or adding yourself to it as the case may be) would cause any real problems.

On my system there's no user with UID 20, so I think you're in the clear there.

Are you still getting permission denied errors reading from your Mac volume?

Yes, I attempted to change the GID to 20 and the UID to 501. The UID was successfully changed but the GID had the not unique error. Then when I attempted to change permissions of the MAC HD volume it gives me the permission denied error. And if I try to open a document or something I am only able to open read-only.

---

### Post by breimer273 on 2010-01-25
> **linuxopjemac said:**
> [http://mac.linux.be/content/how-access-files-osx-linux](http://mac.linux.be/content/how-access-files-osx-linux)

Tycho59: install pommed for brightness

breimer 273: what model MBP you have ? Brigtness: install pommed

I have the 13" MBP the June 2009 release not sure the exact model number.

I have pommed installed according to Synaptic Package Manager. When I reboot in to OSX I will try the link you posted and see if that works.

---

### Post by linuxopjemac on 2010-01-25
This should work, tell us if it is not the case:
[https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Sound](https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Sound)

---

### Post by adam814 on 2010-01-25
Is your Mac volume owned by UID 501 and GID 20?  Can you mount it and then run "ls -l <mountpoint>" where mountpoint is where it is?

---

### Post by breimer273 on 2010-01-25
Alright so after everything so far I have gotten the sound to work. The problems I still have are the backlight on the keyboard does not light up and is not controlled by the F5 and F6 keys. I have installed pommed. Also, the backlight on the screen brightness is not controlled by the F1 and F2 keys.

---

### Post by breimer273 on 2010-01-25
OK I have another update I actually was able to get the backlight brightness thing working. BUT the keyboard backlight still DOES NOT WORK. So I need to figure that out.

---

