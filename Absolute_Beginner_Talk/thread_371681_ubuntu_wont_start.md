---
title: "ubuntu wont start"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by kristiansuhl on 2007-02-27
Hi everyone!

I don't know anything about Gnu+Linux but I managed to install Ubuntu a few days ago on my laptop and the installation worked out fine! After the installation the program wanted me to reboot and start into the new system without the CD. This first reboot also worked fine, I got into the system and everything seemed to work out.

My problem is that when I have installed it, rebooted into system first time - everything works fine - but when I for some reason boot the third time or turn of computer and then turn it on again - nothing works.

The graphical environment does not work and I get a message about it not being configured correctly and that it cannot find the screen. The message said that there was a log file of the problem in /var/log/Xorg.0.log but when I looked at this file it was a very big one with pages of text.

How do I begin to solve this huge problem? Is it possible to solve this at all? :-(

---

### Post by taurus on 2007-02-27
Boot into recovery mode from GRUB menu and at the prompt, reconfigure your X again.

```
dpkg-reconfigure xserver-xorg
```
If you are not sure about a question, just use the default answer and use **vesa** as a driver for your graphic card.  And what kind of graphic card do you have anyway?

When done, reboot and see what happens.

```
shutdown -r now
```

---

### Post by kristiansuhl on 2007-02-27
Cool! That actually worked (I think)! Thank you!

Now there is a new problem and this time it is with my keyboard. WIth that help on reconfiguring I managed to get to the graphical version of the login page but now I cannot use my keyboard except for the swedish letters åäö. They are the only letters working when I want to enter my login name and password in graphical ubuntu.

In the settings program you gave me advice about I tried changing from `us` to `se` and changing from `pc 101` to the other types like `pc 104` and so on. Nothing seem to work.

I have a swedish computer with swedish keyboard. Its a HP Pavilion dv1263ea.

Does anybody know a good way of getting that keyboard working?

---

### Post by kristiansuhl on 2007-02-27
Oh, maybe I should add that the keyboard works fine when using Live CD (with english letters though). The touch pad also works with live CD.

---

### Post by kristiansuhl on 2007-02-27
could the problem be with the drivers for the keyboard or the settings?

---

