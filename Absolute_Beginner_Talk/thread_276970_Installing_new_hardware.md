---
title: "Installing new hardware"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by keheikev on 2006-10-13
My current video card an ATI radeon agp 4x 64 MB  I think is going because it does not display the boot up menu (I dual boot win xp home, and Dapper)and the start up screen where Ubuntu boots is displayed only for a short time as well as the shutdown screen where each of the devices as they are shut down a reverse progress bar does not show up only on the dvi interface and only with my new viewsonic monitor. It works fine with my wifes dvi screen and this screen does work fine on her Sony Viao...

whew to make a long story short I bought a new agp pro ATI 4x-8x card with 256 MB memory. Do I need to do anything in advance of installing the new card or should ubuntu change the conf file for me ie detect new hardware?
Kiheikev
Aloha!
TIA

---

### Post by chuckyp on 2006-10-13
Well dunno if ati cards use drivers that are all the same.  But if they do it should work with out issue.  If it doesn't and you boot up and x fails.  You can change /etc/X11/xorg.conf to vesa instead of whatever driver is there.  That should get you back into X so you can fix stuff.

---

### Post by catlett on 2006-10-13
Put the card in and boot. If it gets detected, you will boot without an issue. If it doesn't work you will know right away.
You will be greeted by an x server failed screen. Then you will be sent to the ubuntu text login. Lgin in with your user name and then your user password. Now you are basically in a terminal. Enter this command to reconfigur x. You will be able to correct the settings for your new video card.
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by keheikev on 2006-10-14
More to the point I should ask Is Ubuntu a plug and play operating system? Does the user get some popups that new hardware is detected? I would think so. This isnt some just out yesterday top of the line card just your basic older style with both dvi and analog inputs. BTW way I do get all the boot menus (grub and the progress bar)on analog so it is kind of a wierd failure for a an ati card.
Kiheikev:cool:

---

