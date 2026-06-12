---
title: "lost my video"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by dsperry101 on 2007-06-30
help!!!

  I was trying to correct a problem with a program I was running (limewire). Originally it ran ok   but then for some reason it ran in a window that was blank . I thought it might be a video 
problem with the restricted driver for the video (nvidia) of my laptop. I thought disabling the driver might get me to a mode where the program would be visible and I could get the video of the program back.
   I disabled the restricted driver but when I did that the whole screen went blank, Its like all the programs are there under a cream colored blank screen . The system boots up ok but the  screen goes blank.
   I have some things I don't want to loose so I dont want to reinstall and repartition the drive . 
   Is there some way to recover??

---

### Post by avik on 2007-06-30
After you boot up, try pressing Control-Alt-F1.  This should get you to the command line (assuming your computer is responding at all to the keyboard).  Log in and re-enable the NVIDIA driver:

```
sudo nvidia-glx-config enable
```

I don't know about the Limewire issue.

---

### Post by dsperry101 on 2007-06-30
Commandline command not found ??

---

### Post by avik on 2007-07-01
How did you install the NVIDIA drivers in the first place?

---

### Post by dsperry101 on 2007-07-01
I installed ubuntu from cdrom they sent and drivers were on the cd i guess i didn't have to provide any drivers during  the install

---

### Post by avik on 2007-07-01
And how did you disable the driver?  Through the Restricted Drivers Manager, right?  If that's the case, you'll have to wait for someone else.  I'm not sure about the mechanism regarding that.  Sorry.

EDIT: Oh, I almost forgot. Try:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by dsperry101 on 2007-07-05
Avik ,
   The last  command string you gave worked!! I was able to select a lower resolution and different driver . Got video back and selected right settings .  Thanks for your help !!!!!

---

### Post by Raineer on 2007-07-06
Since you might be back.... Limewire has LOTS of issues with Java versions.  The only versions I've seen work is the latest level of 1.4 (very old...), and usually the very latest release, JRE Version 6 **release 1**. That last part is important because it was just recently updated. 

I am not sure that Synaptic is updated with that version, you may need to follow the manual instructions on java.com to get it. I can confirm Limewire can show up with a blank screen with some (most) Java versions. It is *not* a display problem and not a computer problem so don't feel like you need to tinker too much, good luck!

---

