---
title: "Ok, Now What!"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Don1500 on 2007-05-03
I've got Ubuntu loaded in my USB drive, it works with my laptop and my desktop, EXCEPT!!!!

If I remove my USB drive and try to boot back to windows the BIOS locks up with the message:

GRUB
ERROR 21

I have set my BIOS to not even look for the USB drive at boot. I need to have this puter boot into windows without the USB drive connected. How do I get rid of GRUB?

---

### Post by Churnd on 2007-05-03
Your BIOS is not looking for the USB drive, but Grub is.  You can either rewrite the MBR using the Windows recovery console or you can edit grub manually via a live CD.  Since you said you want to get rid of grub:

1.  Boot to the XP CD
2.  Select R for Recovery Console
3.  Select your Windows Installation (usually 1)
4.  Type fixmbr
5.  Reboot

---

### Post by Don1500 on 2007-05-03
Thanks, That's good, but I don't have access to the Windows CD. How can I edit GRUB to shut itself down and do a normal windows boot if the USB is not present.

---

### Post by MRiGnS on 2007-05-03
Errr how can you have windows without any kind of CD?

---

### Post by Don1500 on 2007-05-03
I have the CD but not at this location. I was under the impression this install would be invisable to the receiving machine. That I would be able to load from the USB drive without any impact on the receiver.

---

### Post by Churnd on 2007-05-03
There might be a better way that I"m not aware of, but you can comment out the USB line from grub and it will work:

1.  Boot to your USB Key (Ubuntu?)
2.  Open a terminal and type "gksudo gedit /boot/grub/menu.lst"
3.  Comment out all entries except Windows
4.  Save and reboot

By comment out, I mean put a # in front of each line.  Say this is one entry:

```
#Debian Etch
title		Debian GNU/Linux Etch, kernel 2.6.18-4-686 (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.18-4-686 root=/dev/hdb1 ro 
initrd		/boot/initrd.img-2.6.18-4-686
savedefault
boot
```

You would make it:

```
#Debian Etch
#title		Debian GNU/Linux Etch, kernel 2.6.18-4-686 (on /dev/hdb1)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.18-4-686 root=/dev/hdb1 ro 
#initrd		/boot/initrd.img-2.6.18-4-686
#savedefault
#boot
```

To solve the problem entirely, you can reinstall Ubuntu on your USB Key:  [http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/](http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/)

---

### Post by Don1500 on 2007-05-03
THANKS!
Although that didn't do exactly what I wanted, it did show me haw to get things done in that section of the boot. I have learned more in that short piece then I have in the past week. Now it's time to learn some linux code! I will rewrite that section to:
1. Check if the USB is there
2. If Yes then boot directly from it
3. If NO then boot to windows.
and all this will be invisable to the user. All I need now is a linux code book.

THANKS again, you've been a real help. Now I know what can be done.

---

### Post by Don1500 on 2007-05-03
Now we're cookin'!

Got Windows to be the first (default) option, hid the menu (esc to get back) now I need to modify the other files to make sure Grub doesn't crash if the USB isn't there. I'm learning!

---

### Post by lazyart on 2007-05-03
Soon you'll have to update your sig!

---

### Post by Don1500 on 2007-05-03
That may be the case.

Hummmm...... The Incomplete Novice?

---

### Post by mikewhatever on 2007-05-03
I think the problem is that Grub is in the MBR of you internal HDD. Do you remember whether it was installed to hda0 at the end of Ubuntu installation? If you put grub to the mbr of the external HDD, it would completely isolate the two OSs. If the usb disk is present, grub will load and you'll have a choice to boot Ubuntu or Windows, if not, the PC will boot straight into Windows.

Of cause you'll need to reinstall grub to the right location, so check with GParted what your usb drive's called. Use this page to reinstall grub [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

Also, you'd need to recover Windows boot loader. Since you do not have Windows CD, use one of these [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
MbrFix.exe or Super Grub Disk should work for you.

Good luck.

---

### Post by Don1500 on 2007-05-03
WOW! More then I could ask for! Thanks. Let me know if you need a ride or anything.

---

### Post by mikewhatever on 2007-05-03
You are welcome, hope it does work out.
One more thing, you might want to backup the present grub menu.lst file for the sake of its Windows entry, because when you rewrite it, that entry would be gone, and you'll need to add it manually.

---

### Post by Don1500 on 2007-05-03
since this was a new install I just re-installed it. This time when asked I said to put the boot in the right place. Now all I have left is to fix the Mbr file in windows.
(And you know, I  KNEW it was my fault all along!)
Thanks again

---

### Post by mikewhatever on 2007-05-03
Good choice, I didn't think of reinstalling. I hope you'll like the new set up.:)

---

