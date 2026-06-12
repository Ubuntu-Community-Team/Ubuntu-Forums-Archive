---
title: "Can I reinstall Fiesty without losing /home?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by samuraiCat on 2007-06-26
Good morning, everyone. Well, I have messed up Ubuntu to the point where I have to reinstall, which I confirmed here: [http://www.linuxdevcenter.com/pub/a/linux/2001/05/17/drivers_2-user.html](http://www.linuxdevcenter.com/pub/a/linux/2001/05/17/drivers_2-user.html)

> "You can't get the performance you desire from the current driver and want to try another one.

This is potentially the trickiest scenario to manage. Each of the available driver packages maintains a different presence in your system startup and filesystem. If your existing driver is modular you can simply remove it from /lib/modules/linux-version/sound; however, if the driver is hardcoded into the kernel you will to recompile the kernel for modular sound support. You must have a kernel set up for modular sound if you want to use the ALSA drivers (just don't select any specific driver when configuring the kernel). The 4Front package installation routine can be directed to uninstall any kernel sound modules (but not ALSA modules) before installing OSS/Linux; a reboot is not required."

I discovered that information, unfortunately, only after I installed the linux-oss drivers and totally hosed ALSA by attempting to uninstall it. Duh.

Anyway, what's the best way to restore everything but the /home directory to its original condition? (It's in a separte partition, BTW) Should I use the liveCD to recreate my partitions, only without checking the "format" box for /home? 

Sorry to ask, but I haven't found a comprehensive guide to doing this kind of reinstall. I know it's possible when upgrading to the next distro of Ubuntu, but I don't know if the procedure is the same for reinstalling a pristine version of your current distro.

Any step-by-step info would be great. 

Thanks!

---

### Post by Cypher on 2007-06-26
If you want to just get back all the files you had previously and are happy with the partitions as they exist right now, during the re-installation choose to format all partitions except "/home" as you suspect and you should be back in business..

---

### Post by samuraiCat on 2007-06-26
> **Cypher said:**
> If you want to just get back all the files you had previously and are happy with the partitions as they exist right now, during the re-installation choose to format all partitions except "/home" as you suspect and you should be back in business..

Thanks! So all the programs, drivers and settings will be just like a fresh install, but I'll keep my documents? Is this correct?

---

### Post by BlackMeTaL on 2007-06-26
> **samuraiCat said:**
> Thanks! So all the programs, drivers and settings will be just like a fresh install, but I'll keep my documents? Is this correct?

Yes, but only if /home is on a seperate partition. Also your personal settings for various programs are stored in your home folder so those settings won't be like a fresh install.

---

### Post by samuraiCat on 2007-06-26
> **BlackMeTaL said:**
> Yes, but only if /home is on a seperate partition. Also your personal settings for various programs are stored in your home folder so those settings won't be like a fresh install.

Edited to add: Yes, /home is a separate partition.

Okay, that makes me nervous. Which settings for which programs will be saved? How can I find out? I really want to wipe everything having to do with sound/multimedia and start from scratch. In fact, I wouldn't mind if every single setting, program, and driver went back to the fresh install version, as long as a couple of PDF's in my /home are not nuked. Thanks!

Edit #2: Maybe I should just save my PDFs and bookmarks and do a total reformat/reinstall. That would be slightly more time-consuming, and would require me to set up the users and desktop stuff again.

---

### Post by michaelzap on 2007-06-26
View hidden files in your home directory (ctrl+h in Nautilus) to see what programs have created settings folders in there, and rename or delete the ones that you don't want to use after the reinstall.

---

### Post by diskotek on 2007-06-26
be careful if you are using evolution. because evolution is keeping user data & emails in different location. i just want to warn because i had a pain like that....

[http://ubuntuforums.org/showthread.php?t=436178&highlight=evolution](http://ubuntuforums.org/showthread.php?t=436178&highlight=evolution)

---

### Post by kevdog on 2007-06-26
Just save the files you want to USB stick and be done with it!  Its far less risky.

---

### Post by Chris S. on 2007-06-26
Be wary if you are formatting everything but /home.  I did a reinstall without formatting my /home partition (to keep files and settings).  I went through a perfect install, but when I started up Ubuntu nothing worked.  I had used the same user name, so all my settings in the /home partition from before carried over and messed up my fresh install.  I reinstalled using the exact same procedure, but with a different username--no problems.

So, be careful.  Maybe you should pick a new user name so it doesn't use those old settings, or move your entire user directory to somewhere else on /home partition and let Ubuntu make a new, clean user.  Then copy over the files you need and go from there.

---

### Post by samuraiCat on 2007-06-26
> **kevdog said:**
> Just save the files you want to USB stick and be done with it!  Its far less risky.

Yeah, that sounds like a better idea. I'll just have recreate the users anyway, I suppose.

---

### Post by samuraiCat on 2007-06-26
> **Chris S. said:**
> Be wary if you are formatting everything but /home.  I did a reinstall without formatting my /home partition (to keep files and settings).  I went through a perfect install, but when I started up Ubuntu nothing worked.  I had used the same user name, so all my settings in the /home partition from before carried over and messed up my fresh install.  I reinstalled using the exact same procedure, but with a different username--no problems.

So, be careful.  Maybe you should pick a new user name so it doesn't use those old settings, or move your entire user directory to somewhere else on /home partition and let Ubuntu make a new, clean user.  Then copy over the files you need and go from there.

Ugh. Forget it. I'll just save my bookmarks and files on a USB. 

Okay, so why is reinstalling so difficult, but upgrading to Gutsy Gibbon or Hemorraging Hippo is not?

---

### Post by samuraiCat on 2007-06-26
> **michaelzap said:**
> View hidden files in your home directory (ctrl+h in Nautilus) to see what programs have created settings folders in there, and rename or delete the ones that you don't want to use after the reinstall.

That's the kind of thing that got me in trouble in the first place! I just started deleting and installing stuff, and screwed up everything having to do with my audio. I don't know enough about Linux to start doing that yet. I've bought some books, though, so one of these days I'll get to mess around with it.

By the way, why aren't there any tutorials or how-tos regarding reinstallation?

---

### Post by forestpixie on 2007-06-26
I did a reinstall few days ago - I had a deal of trouble originally getting monitor and tv out setup properly - so before I did my reinstall I copied xorg.conf - then when I'd reinstalled and got drivers etc.  copied it back. 

Just a thought:)

And I forgot Evolution - d'oh!

---

### Post by samuraiCat on 2007-06-26
> **forestpixie said:**
> I did a reinstall few days ago - I had a deal of trouble originally getting monitor and tv out setup properly - so before I did my reinstall I copied xorg.conf - then when I'd reinstalled and got drivers etc.  copied it back. 

Just a thought:)

And I forgot Evolution - d'oh!

Thanks, FP. Actually, my video settings were screwed up...by me...as well, so I need a new xorg.conf anyway. I tried to install the nvidia-glx drivers, not realizing that I needed the nvidia-glx-legacy drivers, and then I didn't supply a range for my horiz/vert...it was total blue screen of death time. Forget it. I'll reinstall.

---

