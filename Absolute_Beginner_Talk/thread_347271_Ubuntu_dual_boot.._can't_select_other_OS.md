---
title: "Ubuntu dual boot.. can't select other OS"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Kenaf on 2007-01-27
I just installed Ubuntu, and I have a Windows XP Pro partition installed as well.  When I boot up my computer, the dual boot menu comes up and counts down from 10 to 0, and says if I want to choose a different one, to use the Up and Down arrows.

Hitting the arrows or any other button does absolutely nothing, so I'm stuck booting in Ubuntu everytime.  As fun as getting acquainted to Linux is, I still have a lot of files over on Windows I would like to get to. 

I use a USB keyboard, I had considered that it may be the reason I can't change the options.  Also, something to note.. when I put the Ubuntu CD in and booted from it for the first time, a menu popped up there asking what I want to do as well, and I remember my keyboard wouldn't respond then, either.

However, I do know my keyboard does work in DOS, because I can hit DEL to get to my CMOS with no problem.

Any help is appreciated.

---

### Post by taurus on 2007-01-27
Do you see the options to boot others (like recovery mode and memtest) in the menu at all or is it just a count down?  What happens if you hit the Esc key?  Maybe you need to add an entry in /boot/grub/menu.lst for your XP.

---

### Post by Kenaf on 2007-01-27
Woops, guess I should have mentioned that.  Yes, there are three options for Ubuntu (including the ones you mentioned) and I can see the Microsoft Windows XP Professional, I just can't move the selector using the arrows to get to it.

---

### Post by taurus on 2007-01-27
So the down arrow from your USB keyboard doesn't function at all with GRUB?

---

### Post by Kenaf on 2007-01-27
That seems to be the case.  I can't select anything, I just have to wait for the counter to go down and run Ubuntu by default.

---

### Post by cuculus on 2007-01-30
Me too!  The really bad news is that I jumped into the deep end of the pool and installed Ubunto on my work computer...so now I cannot do any work at work until I can get to my XP Pro OS.

Did you ever get this problem resolved?  And if so, can you share the solution?

Thanks

Greg

---

### Post by Crakie on 2007-01-30
Sometimes you need to enable USB-keyboards in the BIOS. Browse through the options or check your motherboard's manual on how to do that; it should be quite easy.

---

### Post by Malac on 2007-01-30
**CAUTION: **this could trash your system do it at your own risk and/or make a backup.
It will allow you to boot ubuntu from the Windows XP boot menu.[LIST=1]
[*]Login and get to a root terminal
[*] Use df to see which filesystem device holds /boot (e.g. [COLOR=Blue]/dev/hda2[/COLOR])
If you installed GRUB to the MBR run grub-install /dev/hd[COLOR=Blue]x0[COLOR=Black] where  [COLOR=Blue]x [COLOR=Black]is your drive and [/COLOR]0[COLOR=Black] is the partiton number of your Ubuntu Install (1 is first partition)[/COLOR][/COLOR][/COLOR][/COLOR]
[*] Insert a DOS floppy disk and enter:
      mount -t msdos /dev/fd0 /mnt/floppy
[*] Substituting your /boot device, enter:
      dd if=[COLOR=Blue]/dev/hda2[/COLOR] of=/mnt/floppy/UBUNTU.BIN bs=512 count=1
[*] Remove the floppy and reboot to Windows CD run Recovery Console.
[*]Run commands fixmbr and fixboot
[*]Type Exit. The system should reboot to Windows now.
[*]Login to Windows
[*] Insert the DOS floppy disk
[*] Copy the LINUX.BIN file from A:\ to C:\
[*] Open the System Properties window
[*] Click the Advanced tab
[*] Under *Startup and Recovery*, click Settings
[*] Click Edit to open the boot.ini file in Notepad
[*] Add this line to the end of the file and save:
      C:\UBUNTU.BIN="UBUNTU"
[*] Close the Startup and Recovery settings, open it again, and Linux should now appear in the *Default operating system* drop-down menu.
[*] Reboot and test it out[/LIST]Hope this helps.

EDIT: This of course assumes your keyboard works at the XP boot menu screen. :)

---

