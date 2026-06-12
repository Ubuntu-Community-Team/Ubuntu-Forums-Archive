---
title: "Trying to get TV tuner to work"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by schnarkle on 2006-04-29
Following these instructions [http://ivtvdriver.org/index.php/Howto:Debian](http://ivtvdriver.org/index.php/Howto:Debian)
when i type in apt-get install ivtv0.4-utils ivtv0.4-source module-assistant
I get this message:
--------------------------------------------------
apt-get install ivtv0.4-utils ivtv0.4-source module-assistant
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ivtv0.4-utils: Depends: libgcc1 (>= 1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
  Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
------------------------------------------------------------

Any ideas on how I can get past this step?

thanks!

---

### Post by Christmas on 2006-04-29
What TV-Tunner do you have? I have Leadtek TV2000 XP and it detected it without any need to install drivers. I use TVtime to watch TV and works perfectly. Try this:
```
sudo apt-get install tvtime
```
Enter your user password and go under Applications -> Sound & Video -> TVtime. Then scan for channels using the TV Standard for your zone (mine is PAL), modify the volume boost to "full" and there you go!

---

### Post by schnarkle on 2006-04-29
I have a Hauppauge WinTV-PVR350 that was recommended for use with MythTV and Linux.

I do have TVTime installed but on Input Configuration inside the program i get "Format unsupported by OV511 USB Camera. Cannot open capture device /dev/video0.

hmm I think that USB Camera is my webcam....  not sure how to change that?

---

### Post by Christmas on 2006-04-29
Well this is more than my knowledge. I was hoping that your card was already detected... Hope somebody else can try helping you with installing the proper driver.

---

