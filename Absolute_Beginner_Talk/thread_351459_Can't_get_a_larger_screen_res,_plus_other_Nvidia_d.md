---
title: "Can't get a larger screen res, plus other Nvidia driver questions"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by DaveIsInTrouble on 2007-02-02
Okay, heres the deal.

I have a 7800 GTX, and I just installed Ubuntu. Now, my monitor is a 19" LCD, and I'd like the screen resolution to be bigger. I've used Automatix (recommended by a friend) to install the latest version of my drivers, but it still won't let me get my screen resolution to 1280 x 1024!

So I searched this forum and found a post like mine, and followed the instructions. [http://www.ubuntuforums.org/showthread.php?t=351237&highlight=desktop+resolution](http://www.ubuntuforums.org/showthread.php?t=351237&highlight=desktop+resolution)

It messed up Ubuntu, I didn't have any taskbars so I could move stuff around, and terminal would not work. So I reinstalled drivers via Automatix again. That made Ubuntu go back to normal, but I still can't get a larger screen resolution, and my Beryl doesn't want to work either!

Can anyone recommend anything?

---

### Post by Shatrat on 2007-02-02
If you run nvidia-settings what version do you have?
I dont use Automatix to install drivers so I dont know what it uses, but you need the new 9746 to do beryl.

Are you sure they are working at all?
If "glxinfo|grep rendering" returns yes, then you can assume you have at least some version of the nvidia drivers working.
You can manually add "1280x1024" to the /etc/X11/xorg.conf file in the Screen section near the bottom, at the beginning of each of the color depth modes.  Restart X and then 1280x1024 should be available.

---

### Post by DaveIsInTrouble on 2007-02-02
Okay, I've got the new 9746 version apparently, from the output of nvidia-settings and the output of the second command was Yes.

Okay, I'll do what you said for the second part. Maybe a reboot or two will do it (hopes to death Linux is like Windows)

---

### Post by DaveIsInTrouble on 2007-02-02
Okay, I just rebooted, and selected the BOTTOM 1280 x 1024 (the top one was messing up Ubuntu) and it WORKS thanks :)

But Beryl is still not working. Hmm. Should I head over to their forums for help?

---

### Post by shareMenaPeace on 2007-02-02
What happens when you type in beryl-manager ?

---

### Post by DaveIsInTrouble on 2007-02-02
I get a drop-down menu outlining the links to several of Beryl's managers...

Beryl is installed correctly, it just seems that the effects aren't happening...

Maybe it has something to do with my xorg.conf, cause I changed my nVidia driver AFTER beryl was installed, and that edits my xorg.conf...

Maybe a clean install of Beryl? I just haven't figured out how to remove it yet.

---

### Post by Shatrat on 2007-02-02
[http://ubuntuforums.org/showthread.php?t=349732](http://ubuntuforums.org/showthread.php?t=349732)
There is plenty of documentation on Beryl here and elsewhere.  
Even with all the advice in the world, you're gonna have to do some reading if you want to use beta software like that.

---

