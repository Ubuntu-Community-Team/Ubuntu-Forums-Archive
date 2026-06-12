---
title: "Flash on 64bit (not Gnash)"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2008-02-08
So gnash doesnt support flash 9, and I am having lots of issues because of that. Is there any way to make the non-free flash player work on a 64bit Ubuntu 7.10? Thanks!

---

### Post by jan quark on 2008-02-08
try this
```

sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```

---

### Post by tuxsheadache on 2008-02-08
I did this, but i am having a lack of sound. Any idea why?

---

### Post by nynoah on 2008-02-08
Try Jans solution first.  But if that does not work try what is written on this thread.  
[http://ubuntuforums.org/showthread.php?t=476924&highlight=64bit+flash]("http://ubuntuforums.org/showthread.php?t=476924&highlight=64bit+flash")

Noah

---

### Post by kevindubrow on 2008-02-08
Okthe first way didnt work...I had audio but no video. I'll try the second way.

Edit:The second way worked perfectly! Thank you so much!

---

### Post by nynoah on 2008-02-08
also check the thread that is a few below you about 64bit flash and ndiswrapper.  Seems to be some ideas there.

---

### Post by nynoah on 2008-02-08
be sure to thank those that helped you and mark the thread as solved.  

Glad to hear it worked out for you.

Noah

---

### Post by tuxsheadache on 2008-02-08
> **nynoah said:**
> Try Jans solution first.  But if that does not work try what is written on this thread.  
[http://ubuntuforums.org/showthread.php?t=476924&highlight=64bit+flash]("http://ubuntuforums.org/showthread.php?t=476924&highlight=64bit+flash")

Noah

The top recommended link does not work.
Any ideas?
(jans got me video, but no sound)

---

### Post by nynoah on 2008-02-08
ok just wondering when you download the file that is needed for the install of the older version of Flash.  Is it on your desktop or did you move it to you home folder.  It needs to be in your home folder in order for the rest of the instructions to work.   It can not install if that file is on your desktop.  

Does that help?

---

### Post by tuxsheadache on 2008-02-08
I installed it in the home folder, but still no sound. I hope this may help:

ls -al /usr/lib/mozilla//plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-02-08 23:04 .
drwxr-xr-x 3 root root 4096 2008-02-06 08:22 ..
lrwxrwxrwx 1 root root   37 2008-02-08 23:04 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root   36 2008-02-06 08:22 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root   37 2008-02-06 08:22 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root   34 2008-02-06 08:22 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   35 2008-02-06 08:22 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root   36 2008-02-06 08:22 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   37 2008-02-06 08:22 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root   42 2008-02-06 08:22 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root   43 2008-02-06 08:22 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt

ls -al /usr/lib/firefox/plugins/
total 20
drwxr-xr-x 2 root root  4096 2008-02-08 23:04 .
drwxr-xr-x 5 root root  4096 2008-02-08 16:12 ..
lrwxrwxrwx 1 root root    37 2008-02-08 23:04 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root    36 2008-02-06 08:22 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2008-02-06 08:22 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2008-02-06 08:22 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2008-02-06 08:22 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2008-02-06 08:22 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2008-02-06 08:22 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2008-02-06 08:22 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2008-02-06 08:22 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 11456 2008-02-07 11:07 libunixprintplugin.so

---

### Post by nynoah on 2008-02-08
I personally do not use the totem plugins.  I use the *Gxine*,  try installing Gxine and see if that fixes your problem.

---

### Post by tuxsheadache on 2008-02-08
I have installed Gxine using software manager, how do i make it the default for sound for flash?

---

### Post by nynoah on 2008-02-08
so I am to take it that, that did not fix the sound problem?

---

### Post by tuxsheadache on 2008-02-08
The totem plugins are still associated with most of the audio/visual files.
Any easy way of changing it to Gxine?

---

### Post by SIXAXIS on 2008-02-08
I had the same problem. I think the easiest way to install Flash and other plugins is to download Firefox (32-bit) and then install the 32-bit plugins.

---

### Post by nynoah on 2008-02-08
Really for me when I was having flash problems, I installed the older version using the Ndiswrapper and the instructions from the 64bit flash sticky thread.  Did you try the older version there and did it install correctly?

---

### Post by tuxsheadache on 2008-02-08
The old version link does not work anymore.

---

### Post by nynoah on 2008-02-08
the old link version downloaded just fine for me just now.  Are you saving the file or just opening it.  You need to save it.  Then move it from your desktop to your home folder and then do the rest of the stuff with Ndis.

---

### Post by tuxsheadache on 2008-02-08
I installed it all and followed instructions and it did not work :(

---

### Post by nynoah on 2008-02-08
Well I am stumped.  I am far from an expert.  I was just trying to impart my little bit of knowledge that I do have.  Just wondering do you have Gnash installed?  Because you might have conflicts between 2 flash systems.

---

### Post by tuxsheadache on 2008-02-08
Gnash is uninstalled as well.
I will have a good relook at things in a while when i feel more awake =)
Thanks for your help so far though

---

### Post by nynoah on 2008-02-08
No problem......sometimes you need to take break and come back refreshed.  

I have had the same problem as you before.  But someone helped me.  When you learn more, help others in return if you can.

---

### Post by tuxsheadache on 2008-02-11
Got it working now, I was still starting up the 64 bit Firefox, not the 32 bit, that's why I didn't notice the change. Terrible mistake, but 32 bit does work =)

---

