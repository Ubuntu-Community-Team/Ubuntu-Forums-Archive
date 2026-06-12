---
title: "Gutsy boot problem with splash"
date: 2007-11-08
forum: Apple PPC Users
---

### Post by fuoco on 2007-11-08
I had this known problem with the gutsy livecd, which was both with the splash and the missing ide-core.
i could overcome this because the livecd has a nosplash kernel, but now that it's installed i don't have this kernel anymore, so it fails to boot because of the splash and hangs. Is there some way around it? (at least until this is fixed upstream) 
I can't disable the splash in yaboot because i cannot boot into the system...

---

### Post by AmericanYellow on 2007-11-16
I have the exact same problem. The way around this is to press Alt+F1 after the grub menu passes and you get the "Loading...." message. In doing this, you should see what is being loaded in a text-based form. You have to do this every time you boot up the computer. If you do not press Alt+F1 on time, the boot will freeze and you will have to restart and try again. (you have about 15 seconds to press Alt+F1)

Also, I had a problem were my booting would freeze during loading, especially at the Hardware section. If this happens, the likely cause is something connected to your PC. In my case, I used a USB Mouse on my laptop and if I boot with it connected my boot freezes. I just simply disconnect it while booting.

There are instructions to enable the splash here: [http://ubuntuforums.org/showthread.php?t=584205&highlight=missing+splash]("http://ubuntuforums.org/showthread.php?t=584205&highlight=missing+splash")

Hope this helps!

---

### Post by kugn on 2007-11-17
The solution can be found here
[http://ubuntuforums.org/showpost.php?p=3614279&postcount=58](http://ubuntuforums.org/showpost.php?p=3614279&postcount=58)

---

### Post by fuoco on 2007-11-17
I found another solution - i think to the real problem. After installation the config file /etc/usplash.conf was missing the resolution settings. Once I put in it:

xres=1024
yres=768

everything works as it should - no need for the ofonly video driver. can you try this and post your experience?

---

