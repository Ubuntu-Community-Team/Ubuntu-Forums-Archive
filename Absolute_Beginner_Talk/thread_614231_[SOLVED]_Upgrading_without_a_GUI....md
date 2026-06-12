---
title: "[SOLVED] Upgrading without a GUI..."
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by AndrewS on 2007-11-15
Hi

This may well be a stupid question, but is it possible to upgrade a "broken" 7.04 installation (that's "broken" as in I managed to destroy the GUI by some inept tinkering, and i can't get it back...) to 7.10, using text mode (I can get a text console )?

TIA

Andrew:confused:

---

### Post by PmDematagoda on 2007-11-15
You can follow the text instructions on upgrading using the terminal here:-

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by mike555 on 2007-11-15
I think it would be better to do a clean install , of course back up your stuff in your /home folder to a thumbdrive or external drive first then , get the version you want, burn it to a CD as a .iso slowly , then install........... if this is the only computer you have you should be able to get and burn the CD from the ¨live" older CD (if you still have it)

---

### Post by AndrewS on 2007-11-15
Thanks for the replies.  I think what I want to do is to boot the PC which has the broken 7.04 release installed, but on which I get no graphical interface, then to switch to text mode with Ctrl+Alt+F1.  If I log in there, can I issue the upgrade command?

Thanks again

Andrew

---

### Post by AndrewS on 2007-11-15
Thanks for the replies.  I think what I want to do is to boot the PC which has the broken 7.04 release installed, but on which I get no graphical interface, then to switch to text mode with Ctrl+Alt+F1.  If I log in there, can I issue the upgrade command?

Thanks again

Andrew

---

### Post by PmDematagoda on 2007-11-16
You can upgrade your system using that, or you can use Recovery Mode as well without facing any problems.

---

### Post by newlinux on 2007-11-16
I second the clean install. You can upgrade a broken installation, but depending on how you broke it you might be waisting your time, as your upgrade may be broken too.

---

### Post by PmDematagoda on 2007-11-16
While the clean install is cleaner and more reliable, it does not harm to try upgrading the PC, AFTER backing up your data of course. And the upgrade could also solve your problem by replacing the corrupted X-server with a new working one which can be gotten to work simply by using "sudo dpkg-reconfigure xserver-xorg".

---

### Post by newlinux on 2007-11-16
It can harm your time, which was my point. But that may or may not be a concern.

---

### Post by zvacet on 2007-11-16
Try in terminal

```
sudo aptitude -f install
```

That maybe correct your broken packages.

---

### Post by AndrewS on 2007-11-17
Not an issue any more, I managed to fix the gui (with help from this Forum).

Thanks for the suggestions anyway.

Andrew

---

