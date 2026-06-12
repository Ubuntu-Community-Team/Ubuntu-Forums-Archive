---
title: "[SOLVED] Is this going to be stable?"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by Jive Turkey on 2007-10-06
I hosed my Feisty installation earlier today.  I compiled gnucash 2.2.1 from source and overwrote some config file or another resulting in an unbootable system.  Rather than researching how to fix it I just reinstalled and reformatted my "/" partition, leaving my "/home" folder intact.  From the LiveCD (7.04) I created the same user name with the same password and rebooted.

Miraculously, much of my customizations and settings are intact (I'm a recent winXP convert).  I would like some opinions on the soundness of this method before I get too far into running updates and reinstalling programs etc.  I was expecting to have to chroot my old home folder to back up/copy the files I wanted, but it appears that isn't necessary.

So, precisely, my questions are:

Is it generally a sound practice to reinstall around an existing /home directory?
What are likely problems with this?

If it is sound, do you have any tips on how to determine what could/should clean from my home folder?

Thanks

---

### Post by mivo on 2007-10-06
No problems with this method. Your settings are saved in /home, so unless there is an issue already with the settings (in which case you can delete the offending parts), this works absolutely fine. I have reinstalled Gutsy a couple of times, Feisty, and Kubuntu, and my /home always remained the same. That is the very advantage of having /home on its own partition. :) Unlike in Windows, you can easily re-install without having to reconfigure all your programs. You only have to reinstall the core system and re-download the applications you use (and the updates). This usually even works with different distros.

---

### Post by shad0w_walker on 2007-10-06
Agreed. This is pretty common practice in Linux circles, I use it myself (So much less hassle than backing up just for a clean install)

---

### Post by Jive Turkey on 2007-10-06
OMG Linux rocks!  Thanks guys!:guitar:

---

### Post by ronmarley1 on 2007-10-06
Just to add my two cents...  I always use a separate partition for /home.

---

