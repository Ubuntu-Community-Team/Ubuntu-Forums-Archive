---
title: "After install of Karmic-Alt, getting root prompt on reboot"
date: 2010-02-12
forum: Apple Hardware Users
---

### Post by DougieFresh4U on 2010-02-12
Unfortunetly, I only have an old iMac G3 (blue & white). So wanting to use Ubuntu I downloaded the Karmic alternate as it was just under 700MB, downloading the PowerPC version. The install went good, so I thought. When it kicked out the cd and ask to be rebooted, I was presented with the 'white' Ubuntu logo for a bit then blank screen and back to logo and ended up with a root prompt. I proceeded to "sudo nano..." to get the X11 'empty' file and put in all the required info I had found in another thread. When trying to save it, I am getting error about 'Read only file system".
I am happy I made it this far. I am using my room mates computer to access forum.
Any one who can assist helping me, I would really be happy. I did read through about 11 pages of this 'Forum section' and really didn't understand it all.
Thanks

EDIT: upon reboot, the promt is:
root:ubuntu

---

### Post by linuxopjemac on 2010-02-13
are you sure you boot from the HD after installation ? In the live environment you cannot edit the /etc/X11/Xorg.conf file, unless you chroot into the system:

[http://mac.linux.be/content/chroot-system-livecd](http://mac.linux.be/content/chroot-system-livecd)

then you are in your installed system and you can edit your conf files. then a reboot and it should work (boot from HD).

---

### Post by DougieFresh4U on 2010-02-13
> **linuxopjemac said:**
> are you sure you boot from the HD after installation ? In the live environment you cannot edit the /etc/X11/Xorg.conf file, unless you chroot into the system:

[http://mac.linux.be/content/chroot-system-livecd](http://mac.linux.be/content/chroot-system-livecd)

then you are in your installed system and you can edit your conf files. then a reboot and it should work (boot from HD).
Thanks for your response. 
I do believe it's booting from hard drive as the cd is out when I reboot, unless it's running from the RAM which I doubt.  iIwill give it another try in the next few days as I have already reinstalled  Mac 10.3.

---

