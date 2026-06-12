---
title: "freezes at loading kernel"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by pearlson on 2006-07-08
when i tried installing from the liveCD my notebook was stalling at the line, "unpacking linux. ok, loading kernel". 


someone told me to enter "boot acpi=off" in the extra options. That worked and got me past the freeze and i was able to install ubuntu from the Ubuntu desktop. 

now when grub loads and i select ubuntu to run it freezes at the same point and i have to do a hard shutdown. i tried entering the acpi=off command by editing the command line and two things happen.

First; if i enter into the Ubuntu boot code it hangs up in the same place, "unpacking linux. okay, loading the kernel." 

Second; if i enter the code in the diagnostic mode it it makes a small difference but it just hangs up somewhere else after a lot of code flashes by the screen.

any ideas how to append the boot command from grub to make ubuntu load?

also, my sound card isn't picked up when i was running the liveCD.

 i have an ASUS S1300N machne.

thanks! MP

---

### Post by pearlson on 2006-07-09
so i fixed the problem, finally!

the acpi=off command needed to be added again to the boot command in grub. so for a while i would manually put the line in after each restart. then i found a website explaining how to edit the menu.lst -- here is the fix.

(i used Vim, but any text editor will work as long as you are su -)
FIRST: copy the menu.lst file incase you make a mistake.

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-original

SECOND: edit the menu.lst file. you'll need super user priv since its a read-only file by default.

sudo vim /boot/grub/menu.lst

the code is pretty simple for the file: # are comments and ignored by the booting shell, the rest is code that is either displayed or executed. scroll down to where there aren't any more commented sections and append the Ubuntu command as follows:

title Ubuntu, kernel 2.6.15-25-386
root (hd0,2)
kernel /boot/vmlinuz-2.6.15-25-386 root=/dev/hda3 ro quiet splash acpi=off
initrd /boot/initrd.img-2.6.15-25-386
savedefault
boot


you can add the acpi=off to the recoery mode also if you want.


cheers,
MP
pearlson is online now   	Edit/Delete Message

---

### Post by SirHC_Fantastic on 2008-03-29
I have the same problem and forgive my naivety but exactly how did you enter boot acpi=off?
Did you just add that verbatim after the "--" that comes up when you open extra options?

---

