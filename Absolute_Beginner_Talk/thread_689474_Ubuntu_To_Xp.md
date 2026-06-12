---
title: "Ubuntu To Xp"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by vstcroix on 2008-02-06
i RECENTLY BUILT MY PC AND DECIDED TO PUT UBUNTU 7.0 ON IT INSTEAD OF XP. I HAVE NEVER USED UBUNTU AND WOULD LIKE TO CHANGE BACK TO XP.
I HAVE AN XP CD AND TRIED BOOTING FROM CD TO INSTALL WINDOWS BUT IT KEEPS ON BYPASSING IT AND STARTING UP UBUNTU.
I TRIED GOING INTO THE BOOT SEQUENCE ´BY PRESSING ESC KEY´ BUT I ONLY HAVE 5 SECONDS TO CHANGE TO BOOT FROM CD ROM AND IT STILL BOOTS FROM HARD DRIVE.

---

### Post by agustin.g on 2008-02-06
Try hitting F2 to enter the motherboard's BIOS (some motherboards may have a different key for accessing it) and change the boot priority list by putting the CD drive before the HDD

---

### Post by tom66 on 2008-02-06
YOU SHOULD NOT TYPE IN CAPS. It is quite annoying. 

On the bootup phase of your computer, press DEL, INS, or the key which you use to enter your BIOS. Then reconfigure the drive order so that the CD drive is before the hard drive. With the XP CD inserted, restart your computer. 

Hope this helps.

---

### Post by Nythain on 2008-02-06
if you've got the xp cd in the cdrom drive, and it doesnt say
"press any key to load cd" or whatever when you're booting, before it even gets to grub... then either 
A. your cd isnt right
or
B. your bios boot order has hard drives above cdrom drive

the windows xp cd will give you the option to boot off the cd after the bios screen but before the grub loading part...

---

### Post by jken146 on 2008-02-06
Please don't shout.  You'll have to manage to time your pressing of the Escape key to within those 5 seconds, it seems, otherwise your PC will not boot from the CD.  Once you have done that, you can simply install Windows in the usual way, formatting the hard disk to remove Ubuntu.

---

### Post by MariusSilverwolf on 2008-02-06
If you're wanting to boot from CD, you're best off entering the BIOS and changing the boot order.

When you first turn on your computer, you should see a prompt along the lines off "Press <key> to enter Setup".  This key, depending on the motherboard manufacturer, could be F1, F2, F10, F12, or Del.

Press this key, and enter the BIOS configuration.  Using the commands listed along the bottom or the right side of the screen, navigate to Boot Options, and adjust the boot order so that the CD-Rom drive boots before the hard drive does.

Once that is changed, save and exit the BIOS configuration, and the system will reboot.  Place the Windows CD in the drive, and when it initializes, it will prompt for you to hit Enter to boot from CD.  Do so, and follow the setup directions from there.

---

### Post by mikewhatever on 2008-02-06
Sorry to send you of, but this forum is for discussing Ubuntu. You'd be better of consulting Microsoft resources on how to install its products. You are more then welcome to ask about Ubuntu. Here are a few helpful links;
[http://theeldergeek.com/xp_home_install_-_graphic.htm](http://theeldergeek.com/xp_home_install_-_graphic.htm)
[http://theeldergeek.com/xp_pro_install_-_graphic.htm](http://theeldergeek.com/xp_pro_install_-_graphic.htm)

---

### Post by MariusSilverwolf on 2008-02-06
> **mikewhatever said:**
> Sorry to send you of, but this forum is for discussing Ubuntu. You'd be better of consulting Microsoft resources on how to install its products. Here are a few helpful links;
[http://theeldergeek.com/xp_home_install_-_graphic.htm](http://theeldergeek.com/xp_home_install_-_graphic.htm)
[http://theeldergeek.com/xp_pro_install_-_graphic.htm](http://theeldergeek.com/xp_pro_install_-_graphic.htm)

From the way he described it, he wasn't having a problem with the Windows installation, but rather with getting his system to boot from CD.  He would have that problem if he was trying to boot from a LiveCD.  Seeking help with fixing that falls under the purview of this forum.

And, once he does get Windows installed again, he won't be back here asking for more Ubuntu help anyway, fulfilling that part of your suggestion.

Everybody wins.

---

### Post by fiddledd on 2008-02-06
> **MariusSilverwolf said:**
> From the way he described it, he wasn't having a problem with the Windows installation, but rather with getting his system to boot from CD.  He would have that problem if he was trying to boot from a LiveCD.  Seeking help with fixing that falls under the purview of this forum.

And, once he does get Windows installed again, he won't be back here asking for more Ubuntu help anyway, fulfilling that part of your suggestion.

Everybody wins.

And you never know, whatever didn't work for him in Gutsy might work in Hardy. Then he mught remember how helpful the Ubuntu Forums were and return here to help others in the future, :)

---

### Post by mikewhatever on 2008-02-06
> **MariusSilverwolf said:**
> From the way he described it, he wasn't having a problem with the Windows installation, but rather with getting his system to boot from CD.  He would have that problem if he was trying to boot from a LiveCD.  Seeking help with fixing that falls under the purview of this forum.

And, once he does get Windows installed again, he won't be back here asking for more Ubuntu help anyway, fulfilling that part of your suggestion.

Everybody wins.

I've installed Windows several times in the past, and every time I did, booting from the CD was the very first stage of the installation. If you object, check the links I posted above. Have you read the original post? It is clearly stated that Ubuntu was installed, so I feel safe to assume there was no problem with the Live CD, nor with the boot sequence. There seems to be a problem with the Windows installation CD, which has nothing whatsoever to do with Ubuntu, hence belongs on Windows support forum.

I do not understand the last part. Do you offer help so that the poster could get Windows installed and would not ask about Ubuntu? How is that a win?

> And you never know, whatever didn't work for him in Gutsy might work in Hardy. Then he mught remember how helpful the Ubuntu Forums were and return here to help others in the future, 

That's real funny. Let's become a Windows help and support forum then, and, hey, what about mac, they might think Ubuntu users are nice too.

---

### Post by MariusSilverwolf on 2008-02-06
> **mikewhatever said:**
> I've installed Windows several times in the past, and every time I did, booting from the CD was the very first stage of the installation. If you object, check the links I posted above. Have you read the original post? It is clearly stated that Ubuntu was installed, so I feel safe to assume there was no problem with the Live CD, nor with the boot sequence. There seems to be a problem with the Windows installation CD, which has nothing whatsoever to do with Ubuntu, hence belongs on Windows support forum.

He stated he built the PC, which would include a fresh, blank hard drive with nothing installed.  In such cases, even with the hard drive listed before the optical drive in the boot sequence, the Live CD would still boot after no file system was found on the hard drive.  We have to troubleshoot that portion of the problem FIRST before determining it's a problem with the Windows CD.

This forum is still dedicated to questions about computers in addition to Linux and Ubuntu, right?  Or did I misread that when I hopped in here?

---

