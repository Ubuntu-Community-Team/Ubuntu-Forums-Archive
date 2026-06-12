---
title: "Keyboard problem with ubuntu installation"
date: 2008-05-09
forum: Apple Hardware Users
---

### Post by Niila on 2008-05-09
I have intel 1.83ghz mac mini with leopard, and i would like to try new ubuntu beside it. I have already created new partition for it. But as soon as my mac boots from the hardy heron cd, and the language selection comes up, my logitech keyboard doesnt work at all, so i cant continiue. 

Just to make sure, desktop amd64 image is the right one for me?

Cheers!

---

### Post by cyberdork33 on 2008-05-09
> **Niila said:**
> Just to make sure, desktop amd64 image is the right one for me?If you have a Core2 Duo processor, then you can use 32bit or 64bit. If you have a Core Duo then you can only use the 32bit version.This shouldn't have anything to do with your keyboard working though.

Make sure that you have all your system updates under OSX as a firmware update fixed a non-responding keyboard issue that used to effect us much the same way you describe. The other cause could be that you keyboard just won't work without some extra configuration, which means you need to get a hold of some other keyboard to do the install.

---

### Post by Niila on 2008-05-15
I bought apples new wired keyboard but it still doesnt work at all. Am i really the only one having this problem?

I always get stuck at the language selection menu.. :confused:

---

### Post by Niila on 2008-06-30
This case still remains unsolved... ;)

---

### Post by gamood on 2008-07-02
Did you try connecting both the mouse and the keyboard into separate usb plug (as you have more than one i think)
then try a non vga keyboard only installation and test your mouse after you have it boot and go the the graphical friendly desktop
I think not enough drivers are loaded during the install to properly recognise modern keyboard you mentioned
And tell us about succes or failure

---

### Post by cyberdork33 on 2008-07-02
I think I have heard of a bug in the Apple EFI firmware that does this on the newer keyboards. I don't know the remedy off hand, but it has been discussed in the forum before.

---

### Post by umbrAtrorum on 2008-07-03
i had the exact same issue yesterday.

1. do NOT hold the "C" button needed to boot from the cd longer than until you hear the cd spinning. if i hold it until the screen goes black, i have the same issue.

after that it worked for me until entering the actual setup, my keyboard hung again at the language selection.

2. what i did to solve that, was to push enter a couple of times while the setup program was being loaded.

i hope this works for you too. good luck!

jaspeR

---

### Post by umbrAtrorum on 2008-07-03
now that my operating systems have failed me again and i had to reinstall linux again, i found the correct workaround that worked yesterday as well:

1. is still valid, don't hold the "C" button for too long

2. in the appearing menu where you choose to install ubuntu, enter keymap with F3, choose usa intl. here. that worked for me. i also made sure that no usb devices were plugged in (having my regular mouse plugged to the usb produced the problem as well).

that should work better than the mere enter-hitting on kernel-loading.

jaspeR

---

