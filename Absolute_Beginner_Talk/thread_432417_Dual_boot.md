---
title: "Dual boot"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Ephilei on 2007-05-04
Normally I'd just go and try this, but it's someone else's computer and I have limited time with it. (Yes, everything's backed up, but restoring would be a big pain.) The computer already has Windows installed with an empty partition where I'm going to install Ubuntu. I want to double check that 

[LIST]
[*]I want to install Grub
[*]The OS can be chosen from a boot screen
[*]Grub can be set to boot Windows automatically (might seem silly, but's important to the person I'm installing for)
[/LIST]

And can Grub be uninstalled later?

---

### Post by Billy McCann on 2007-05-04
Yes to all.

It's very easy to get GRUB to boot directly into Windows by default.

You can't uninstall GRUB if you want your computer to boot.  :)

---

### Post by bobplano on 2007-05-04
yep everything you want to do is pretty easy. you just have to do a little editing to the grub files (not too hard) and then you (or your friend) should be set. as for uninstalling grub you also have to restore the windows mbr using the cd or downloading the mbr. 
to Billy: the reason i uninstalled grub was im using an externa; hd and i installed grub to the insternal one so it wouldnt boot at all without the external hd in, which was impractical, because other people are using the computer and don't want to have to plug it in everytime

---

### Post by teddybairs1 on 2007-05-04
To my knowledge:

1. GRUB is installed by default when you install Ubuntu.
2. That's the purpose of GRUB, so yes, you can choose which OS you want at bootup. You have ten seconds to choose.
3. To my knowledge Ubuntu doesn't give you the choice as to which OS you want as default. It always defaults to Ubuntu.
4. I'm sure someone else will correct me on this and come up with a great command line way of removing GRUB, but for the average user, no. You can't remove GRUB unless you overwrite the Master Boot Record with something else (for example, a MS Windows install; Windows trashes your MBR and assumes it's the only kid on the block, new or otherwise; that's why you never want to install Linux first and then windows: windows doesn't know how to play nice with others).

---

### Post by Billy McCann on 2007-05-04
> **bobplano said:**
> to Billy: the reason i uninstalled grub was im using an externa; hd and i installed grub to the insternal one so it wouldnt boot at all without the external hd in, which was impractical, because other people are using the computer and don't want to have to plug it in everytime
Neat trick.  I'll have to remember that.  :)

---

### Post by rsambuca on 2007-05-04
> **teddybairs1 said:**
> To my knowledge:

1. GRUB is installed by default when you install Ubuntu.
2. That's the purpose of GRUB, so yes, you can choose which OS you want at bootup. You have ten seconds to choose.
3. To my knowledge Ubuntu doesn't give you the choice as to which OS you want as default. It always defaults to Ubuntu.
4. I'm sure someone else will correct me on this and come up with a great command line way of removing GRUB, but for the average user, no. You can't remove GRUB unless you overwrite the Master Boot Record with something else (for example, a MS Windows install; Windows trashes your MBR and assumes it's the only kid on the block, new or otherwise; that's why you never want to install Linux first and then windows: windows doesn't know how to play nice with others).
1.  Yes, but you can direct where to install it.  ie.  hd0 for the mbr, or wherever else you wish to install it if you don't want to overwrite the MBR.  There are a number of 'stages' of grub.  Only stage 1 is written to the MBR (or your chosen location).  The stage 1 instructions then point the loader to the stage 2 location (which is usually in your /boot/grub/ directory.

2.  You have 10 seconds to press an arrow key.  After that you can take as long as you wish to choose.  Also, you can change the time available to as little or as much as you want.

3.  The default is ubuntu, but again you can change the default to XP, or whatever OS you want.

4. Basically correct.  For all intents you really have to overwrite the MBR to change it.

---

### Post by teddybairs1 on 2007-05-04
thanks for the correction rsambuca. how is it that you change which is the default os to boot from in GRUB?

---

### Post by rsambuca on 2007-05-04
> **teddybairs1 said:**
> thanks for the correction rsambuca. how is it that you change which is the default os to boot from in GRUB?

If you run ```
gksudo gedit /boot/grub/menu.lst
``` you will wee the grub menu.  About 10 lines down or so, there is a line that says "default     '#'"

Just change the # to whatever OS you want to be the default.  Just keep in mind that the numbering starts at zero, not one.  Also, it basically counts every 'title' as an OS, so the line that says "title     Other operating systems:" will be counted by grub.

To keep it simple for others in my household, I have set XP as the default :(  and changed the "timeout" line to 2 seconds so that if anyone else just turns on the computer, it will boot into XP after a small 2 second delay.  I can easily press an arrow key in that time and then select whichever OS I want (I currently have six on my rig!)

---

### Post by useLinux, on 2007-05-04
> **rsambuca said:**
> If you run ```
gksudo gedit /boot/grub/menu.lst
``` you will wee the grub menu.  About 10 lines down or so, there is a line that says "default     '#'"

Just change the # to whatever OS you want to be the default.  Just keep in mind that the numbering starts at zero, not one.  Also, it basically counts every 'title' as an OS, so the line that says "title     Other operating systems:" will be counted by grub.

To keep it simple for others in my household, I have set XP as the default :(  and changed the "timeout" line to 2 seconds so that if anyone else just turns on the computer, it will boot into XP after a small 2 second delay.  I can easily press an arrow key in that time and then select whichever OS I want (I currently have six on my rig!)

Very Very clever :P I have a "dedicated" computer, but my mum etc uses mine cos its faster than the other 1 :| So i think ill 'borrow' your technique xD

---

### Post by teddybairs1 on 2007-05-04
Good to know. Think I'll keep my laptop the way it is for now. I'm a little slow on the trigger some times and 10 seconds is just about right, but it's good to know I can change it if I need to.

---

