---
title: "Sound / Graphics - ALSA  // Almost there, just need a little push"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by blackrob on 2007-02-03
Hello!
                 I have recently installed Ubuntu and I must say this is one of the best distros out right now. I am comming from Slackware on my laptop. I had read a post reguarding Ubuntu and getting Wirless to work was petty easy so I made the switch :).

                  Anyway on to my question. I'm using this on a lap top, Gateway ( don't remeber the type lol). I have gotten my sound to ' almost ' work out of the box. By most meaning that I can hear the starting up sound and loggin off sound. I got those two to work by messing with the ALSA mixer and its ' Switches '. However I cannot hear .ogg files or my belovid .mp3 files.

                               My sound card is a intergrated intel chip : Intel 82801DB-ICH4

I have noticed one or two things that concern me.
I don't see any module.conf or any other known conf file except for alsa.conf.


As for my graphics issue, when I; glxinfo |grep direct

I get this OUPUT:libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes

When I run glxgears it runs but I get declibGL warning: 3D driver claims to not support visual 0x4
and my fps is normal.

~~ My xorg config file seems to have placed my intel graphics chip under the i810 driver, which from what I have read works well.

~~ My question reguarding graphics is simply is there anyway I can get openGL to work? ( Thats what I'm thinking is not working )

---

### Post by blackrob on 2007-02-03
pushing....

---

### Post by r4ik on 2007-02-03
Try,

[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=intel+Audio](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=intel+Audio)

If you didn't already.

Good luck !

---

