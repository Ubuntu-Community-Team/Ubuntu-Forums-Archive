---
title: "Dual Boot OS Choices Order"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by Bruhthakuga on 2006-08-01
Ubuntu Friends,
     I installed Ubuntu with XP and what to know if I can change the order of the list to choose which OS I want to boot uo to.  When I boot up Ubuntu is first and is pre-selected to boot up after a few seconds if no choice is made.  As I am in the first stage of the migration from Windows I still want Xp to be first.k

---

### Post by Jagot on 2006-08-01
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by teasum on 2006-08-01
I think part of Bruhthakuga's question is how to change the order of the OS list displayed in GRUB.  Changing the default number in GRUB's menu.lst file will make XP boot automatically... but is there a way to change the display order of the GRUB menu (i.e. putting the 'other OS' section on top)?

---

### Post by Tomosaur on 2006-08-01
It is possible to change the order your OS' are listed by editing the /boot/grub/menu.lst file. Towards the end is the actual menu. You'll need to swap around the different listings to get the order you want to achieve. It is much easier to just set the default to whatever you want it to be. [I wrote a script for this very purpose.](http://www.ubuntuforums.org/showthread.php?t=226857).

It won't change the menu order, but it will set whichever menu item you want to be the default.

---

### Post by confused57 on 2006-08-01
Another method would be to move the Windows entry to just above the line ###BEGIN AUTOMAGIC KERNELS LIST in your /boot/grub/menu.lst.
Have the default OS to boot set to 0, and Windows will always boot first even if a new kernel is installed.

This thread describes dualbooting, but editing your menu.lst would be the same(just substitute your current Windows grub entry):

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by dpds68 on 2006-08-01
> **Jagot said:**
> [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

Thank you just what I was looking for :D

---

### Post by Bruhthakuga on 2006-08-02
I got a problem, I was trying to follow the instructions from the link

[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

When I entered:

   sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

into the terminal and hit enter I got a prompt asking for a password, However, no text could be entered.  I closed the terminal and reopened another and entered:

    sudo gedit /boot/grub/menu.lst

and the same thing happened. It was late so I logged off and went to bed, I don't know of any bad results as of yet as I have not yet logged on to Ubuntu today.  What did I do and can I recover and continue?

---

### Post by confused57 on 2006-08-02
> **Bruhthakuga said:**
> I got a problem, I was trying to follow the instructions from the link

[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

When I entered:

   sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

into the terminal and hit enter I got a prompt asking for a password, However, no text could be entered.  I closed the terminal and reopened another and entered:

    sudo gedit /boot/grub/menu.lst

and the same thing happened. It was late so I logged off and went to bed, I don't know of any bad results as of yet as I have not yet logged on to Ubuntu today.  What did I do and can I recover and continue?

You won't see any text being entered for your password, for security reasons.  Just type your password & press enter...no harm was done with what you did.

---

### Post by Bruhthakuga on 2006-08-03
Jagot, as I stated I had a problem and the results was that now when I log on I get the first two choices doubled, anyway, I when I open the Grub Menu List  document I see the duplicate list.  My first thought was to just delete the duplicate list.  But my second thought was to get more instruction, so here I am.  Find below a direct copy of the part of the Grub Menu List that is in question:
[COLOR="Black"][/COLOR]
     ## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-amd64-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
boot[B][COLOR="Blue"]

title		Ubuntu, kernel 2.6.15-23-amd64-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
boot[/COLOR][/B]

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


I was thinking that I should delete the the bold blue hightlighted text above?  What should I do?  I also want to know if I change the name of windows XP Home whould it also display what I changed it to?

---

### Post by Bruhthakuga on 2006-08-03
Sorry double post

---

### Post by Tomosaur on 2006-08-03
It's not duplicated, it's just listing different kernels. Look at the numbering of each one, they're slightly different. Grub is set by default to list all of the kernels available to you. You can edit this by looking for the line where it says this

[/CODE]
#howmany=all
[/CODE]

Change all to '1' if you only want to list the first kernel grub comes across. Do not remove the '#'.

---

