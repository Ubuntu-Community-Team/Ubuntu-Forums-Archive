---
title: "Boot change needed"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2006-03-27
Hi all! I have 2HDD the Master has Win XP and Ubuntu (breezy)as dual boot.On the second drive (Slave drive) I have another linux OS (Mepis) installed. What I would like is to have the choice of booting into any of the 3 systems placed into Grub on the Primary(Master) drive. If this is possible could someone walk me through the procedure. I naively thought that Grub on the Master drive would recognise and display the slave drive. How wrong I was.
Thanks

---

### Post by Sbarton on 2006-03-27
I tried making an entry in menu list but it was no good (probably my fault). Anyone have an idea how I could achieve this. Maybe a third party boot manager?
Thanks

---

### Post by AndrewCaul on 2006-03-27
What is the output of
```
fdisk -l
```

---

### Post by aysiu on 2006-03-27
Generally, Linux distributions are pretty good at detecting Windows--they're not always good at detecting other Linux distributions.

What you need to do is mount the Mepis drive and copy the Mepis entry in /boot/grub/menu.lst to the Ubuntu /boot/grub/menu.lst

For the sake of this example, let's say Mepis is /dev/hdb1 (you should do a *sudo fdisk -l* to be sure, though). ```
sudo mkdir /tmp/mepis
sudo mount -t ext3 /dev/hdb1 /tmp/mepis
sudo nano /tmp/mepis/boot/grub/menu.lst
``` Find the relevant Grub entry and copy and paste it to a text file. Then Control-X and Enter.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo nano /boot/grub/menu.lst
``` Paste in the Mepis entry--make it sure it follows the same format as the Ubuntu entries. I think Ubuntu includes the path (hd1,0) on a separate line from the kernel and initrd, and Mepis includes the path on both. Then save (control-x), confirm (y), and exit (Enter).

---

### Post by Sbarton on 2006-03-27
Thanks for your replies I will attempt the instructions. Wish me luck!
sbarton

---

### Post by Sbarton on 2006-03-28
H

---

### Post by Sbarton on 2006-03-28
Ignore post no attachments added.

---

### Post by belikralj on 2006-03-28
In addition to configuring menu.lst in /boot/grub you need to copy these files from Memps (did i spell it right?) boot: System.map, vmlinuz and initrd.img each has the Kernel number of that system as a suffix.

That is how I made a dual boot Ubuntu and Red Hat which both use grub. I'm not certain about it but I think it should work for any other distro of Linux as well using the same method.

good luck

---

### Post by aysiu on 2006-03-28
[QUOTE=belikralj]In addition to configuring menu.lst in /boot/grub you need to copy these files from Memps (did i spell it right?) boot: System.map, vmlinuz and initrd.img each has the Kernel number of that system as a suffix.[/QUOTE] I've set up numerous dual-boot with Mepis and have never had to copy a file. I'm not sure if maybe Red Hat requires you to copy files.

---

### Post by Sbarton on 2006-03-30
[QUOTE=aysiu]Generally, Linux distributions are pretty good at detecting Windows--they're not always good at detecting other Linux distributions.

What you need to do is mount the Mepis drive and copy the Mepis entry in /boot/grub/menu.lst to the Ubuntu /boot/grub/menu.lst

For the sake of this example, let's say Mepis is /dev/hdb1 (you should do a *sudo fdisk -l* to be sure, though). ```
sudo mkdir /tmp/mepis
sudo mount -t ext3 /dev/hdb1 /tmp/mepis
sudo nano /tmp/mepis/boot/grub/menu.lst
``` Find the relevant Grub entry and copy and paste it to a text file. Then Control-X and Enter.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo nano /boot/grub/menu.lst
``` Paste in the Mepis entry--make it sure it follows the same format as the Ubuntu entries. I think Ubuntu includes the path (hd1,0) on a separate line from the kernel and initrd, and Mepis includes the path on both. Then save (control-x), confirm (y), and exit (Enter).[/QUOTE]

Hi all! I have made sure that Mepis is /dev/hdb1. My next step was to complete the next instruction in a terminal creating the tmp mepis menulist. When this is on screen I have highlighted and copied what I think is the relevant entry, (title MEPIS at hda1, kernel 2.6.15-1-586tsc
kernel /boot/vmlinuz-2.6.15-1-586tsc root=/dev/hda1 nomce quiet vga=791), and saved it in OO as a text file.Now the next instruction (Then Control-X and Enter) is where I think one of the steps I am going wrong. I assumed this to be Keyboard entries, but are these to be entered into the mepis menulist which is still showing, and where?
On following the next instruction, I opened another terminal to backup and bring up the ubuntu menulist. Where would I paste the mepis 2 lines in the menu list and what should the format look like? The last part to save (control-x), confirm (y), and exit(Enter) again is probably another place I am going wrong.
I am trying to take this all on board and have attempted the procedure how I have interpreted it, obviously this a bad interpretation on my part as I have failed every attempt. Your advice would be most helpful.
Thanks

---

### Post by meborc on 2006-03-30
instead of **sudo nano **do **sudo gedit **... it will open a better text editor (in a sence of point'click)... then highlight the text you need and copy it somewhere... then close the file etc etc

nano is a bit hard for the beginners...

---

### Post by Sbarton on 2006-04-02
After trying to copy/paste etc and messing up big time, I used the Mepis cd details to try again. I managed to get grub on the PC but then only had Win XP and Mepis which is not what I wanted. Since then I have restored XP mbr and my second drive has a bootable mepis. However, I cannot get into Ubuntu at boot time. I know the partitions are still there but not at boot up.](*,) I don't want to re install Ubuntu if I can avoid it.If someone has a step by step solution I would be grateful.
Thanks

---

### Post by belikralj on 2006-04-02
I think I posted this on your other thread. But heres where I got the information about copying those files and how to make multiple Linux distro's dual boot with each other as well as XP

Here's the first link for all the tutorials: 
[http://librenix.com/?page=Dual-boot](http://librenix.com/?page=Dual-boot)

Here's the multiple Linuxes dual booting link:
[http://os.newsforge.com/os/04/12/21/1852209.shtml](http://os.newsforge.com/os/04/12/21/1852209.shtml)

again, good luck! Hope I helped.

Also any of you other guys tell me if I was wrong to copy those files cause I just followed the instructions in the link. I understand the code writing a lot better than the file dependencies.

---

### Post by Sbarton on 2006-04-02
[QUOTE=belikralj]I think I posted this on your other thread. But heres where I got the information about copying those files and how to make multiple Linux distro's dual boot with each other as well as XP

Here's the first link for all the tutorials: 
[http://librenix.com/?page=Dual-boot](http://librenix.com/?page=Dual-boot)

Here's the multiple Linuxes dual booting link:
[http://os.newsforge.com/os/04/12/21/1852209.shtml](http://os.newsforge.com/os/04/12/21/1852209.shtml)

again, good luck! Hope I helped.

Also any of you other guys tell me if I was wrong to copy those files cause I just followed the instructions in the link. I understand the code writing a lot better than the file dependencies.[/QUOTE]

Thanks a lot I will look at those. I know time is valuable, so thanks!

---

### Post by ferebee on 2006-04-02
[QUOTE=Sbarton]After trying to copy/paste etc and messing up big time, I used the Mepis cd details to try again. I managed to get grub on the PC but then only had Win XP and Mepis which is not what I wanted. Since then I have restored XP mbr and my second drive has a bootable mepis. However, I cannot get into Ubuntu at boot time. I know the partitions are still there but not at boot up.](*,) I don't want to re install Ubuntu if I can avoid it.If someone has a step by step solution I would be grateful.
Thanks[/QUOTE]

If you have Mepis' grub on your MBR and can boot into Mepis, then you can fix this.

With Mepis Grub in the MBR boot into Mepis and go to 
System>Filestystem>Mount Partitions
and mount the partition where you have Ubuntu installed.

Then open Konqueror file browser.
Navigate to your /mnt folder and open 
the Hd folder that contains your Ubuntu installation.
Open the Boot folder, then the Grub folder. Your Ubuntu menu.lst
file should be here. Right click it and go down to Open With- you can chose
a text editor here, let's go with Kwite. It will open your
menu.lst in read only mode, but that's okay here.

The entries you are looking for will look something like this, though your hdd locations and kernels might be different.

```

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda9 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda9 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,8)
kernel		/boot/memtest86+.bin  
boot
```

Copy the first two entries, not the memtest one. I believe Mepis Grub has memtest, and you probably won't need it twice. Paste it into a **new **text file and keep this at the ready.

Now close Kwrite and go back to Konqueror, and navigate back to your
Mepis root folder. '/' in the location bar will take you right to it.
Open your Mepis Boot folder and then the Grub folder.
Right Click to copy this menu.lst file, and put it somewhere you can find it easily,say your desktop or home folder as a backup.

Back in Konqueror you'll right click the original menu.lst and this time instead of chosing Open with go down to Actions>Edit as root
Kwrite will open your Mepis menu.lst. Mine looks like this:
```

timeout 15
color cyan/blue white/blue
foreground ffffff
background 0639a1

gfxmenu /boot/grub/message

title  MEPIS at hda6, kernel 2.6.15-1-586tsc
root   (hd0,5)
kernel /boot/vmlinuz-2.6.15-1-586tsc root=/dev/hda6 nomce quiet vga=791
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda9 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title Puppy Linux (on /dev/hdb3)
root   (hd1,2)
kernel /boot/vmlinuz root=/dev/hdb3 ro vga=790
savedefault
boot

title Windows at hda1
rootnoverify (hd0,0)
chainloader +1

title MEMTEST
kernel /boot/memtest86.bin
```

As you can see I've already pasted my Ubuntu and Puppy Linux
grub menu listings here. You could go to the text file you made earlier
with your Ubuntu info and copy and paste your Ubuntu entries underneath
the Mepis ones. Save and close the file.

If all is well with your Ubuntu install and your Mepis grub, then hopefully, this may work.

---

### Post by Sbarton on 2006-04-10
Success at last!:D After  a reinstall (due to my own errors) and having a broadband upgrade problem I am very happy to state I have succeeded in putting mepis on the boot menu. I must thank all those of you who have helped me along this path, also for your patience and tolerance, and of course your experience.=D> =D>

---

