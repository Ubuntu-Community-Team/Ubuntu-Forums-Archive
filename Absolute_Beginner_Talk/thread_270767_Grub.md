---
title: "Grub"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by Troglodite on 2006-10-03
Hi,

I had linux installed, and then installed windows. After that i recovered my grub with a super recovery cd. The thing is, that grub doesnt recognise windows xp. I just recognises many ubuntus (all the same).

---

### Post by sonny on 2006-10-03
Now that windows is installed I suggest you to re-install Ubuntu, remember that Windows likes to be alone in the system, so install it alone, and them install Ubuntu.

---

### Post by PPAAUULL on 2006-10-03
you could do that or you could just re install grub and let it detect the OS's again. A lot less work then reinstalling the whole system again.

---

### Post by sonny on 2006-10-03
> **PPAAUULL said:**
> you could do that or you could just re install grub and let it detect the OS's again. A lot less work then reinstalling the whole system again.
He already did that, and didn't result as desire.

---

### Post by justin whitaker on 2006-10-03
> **Troglodite said:**
> Hi,

I had linux installed, and then installed windows. After that i recovered my grub with a super recovery cd. The thing is, that grub doesnt recognise windows xp. I just recognises many ubuntus (all the same).

This is where you get your Linux hacker stripes. Each of the Ubuntus are different kernel versions, or permissions. It's one install. 

The anwser you seek at at the bottom of this page:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Look at "Configuring the Grub Menu".

The command is:

> sudo nano /boot/grub/menu.lst 

Then edit grub so that the Windows XP entry looks something like:

> title  Microsoft Windows XP Home #An entry for a Windows installation
#If you're reading this guide, you probably want this
root   (hd0,0)
makeactive
chainloader +1

The root you change to the designation of your XP partition.

Save, reboot.

Cross Fingers.

YMMV. ;)

---

### Post by Troglodite on 2006-10-03
thats strange, in /boot i dont have any grub directory. In fact, i have my windows stuff there.

---

### Post by PPAAUULL on 2006-10-03
sonny, if he did then he did not state it. he said he recovered it not reinstalled it. If he did then I am sorry but I did not have that information.

---

### Post by sonny on 2006-10-03
> **PPAAUULL said:**
> sonny, if he did then he did not state it. he said he recovered it not reinstalled it. If he did then I am sorry but I did not have that information.
Mmmmm... I re-read the posts and he didn't said... Troglodite, how exactly did you recover grub?.

---

### Post by Troglodite on 2006-10-03
I used super grub disk

[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

---

