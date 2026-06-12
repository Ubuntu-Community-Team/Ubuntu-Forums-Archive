---
title: "How do I edit my GRUB menu.lst ?"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by brjoon1021 on 2006-10-04
Hi,

I am running the latest Ubuntu release with all updates, I think that makes it 6.06.1 ?  Anyway, I am multibooting Linux, using the GRUB of PCLinuxOS. I want to edit the GRUB of Ubuntu down to just the ubuntu entries. I think that is safe, right? I also want to set the timer to "0" so that I don't see Ubuntu's GRUB screen, but just start booting into it.

I can't figure out how to edit GRUB in Ubuntu, though. I do it in PCLinuxOS every couple of days because I am a distro whore and have installed about 14 on this computer now - just because I want to. Is there a "control Center"-like area or administration area for this? Or, I know how to get to the GRUB menu.lst but any changes I make can't be saved. I don't really understand the No root user / sudo Ubuntu policy because I use PCLinuxOS, DreamLinux or SUSE most of the time. That is definitely going to change now that I discovered Automatix and Ubuntu is a terrific multimedia OS - just where it gave in to the others prior to using Automatix. Anyway, PCLinuxOS prompts for a root password  If it needs root privileges for something that I want to do. Ubuntu just tells me that I can't save the changes I just tried to make on the GRUB menu.lst, and that is that.

So, How can I do it?


Please help.

B.

---

### Post by henriquemaia on 2006-10-04
Try this:

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by h2gofast on 2006-10-04
holy shit dude, back it up first.
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

so when you screw it up
sudo cp /boot/grub/menu.lst.backup /boot/grub/menu.lst

gets you back to where you started.

---

### Post by tonyr1988 on 2006-10-04
That will work, but I've always used gksudo instead of sudo for graphical applications like gedit. Not sure if it makes much of a difference, but that's what I've been told to do. :)

---

### Post by brjoon1021 on 2006-10-04
Thanks for your help but I am still not out of the woods...

when I entered "sudo cp /boot/grub/menu.lst /boot/grub/menu.lst" the command that you told me to enter, I get this message back:

cp: `/boot/grub/menu.lst' and `/boot/grub/menu.lst' are the same file
user@ubuntu:~$"

what am I doing wrong?

---

### Post by h2gofast on 2006-10-04
umm,
> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

ok, cp is the copy command, it makes a copy of a file and names it what(and where) you want to name it.

type in "man cp" for some info
press q when you're finished reading.

your command copied the same file, mine copies to a file named menu.lst.backup
;)

---

### Post by henriquemaia on 2006-10-05
> **brjoon1021 said:**
> Thanks for your help but I am still not out of the woods...

when I entered "sudo cp /boot/grub/menu.lst /boot/grub/menu.lst" the command that you told me to enter, I get this message back:

cp: `/boot/grub/menu.lst' and `/boot/grub/menu.lst' are the same file
user@ubuntu:~$"

what am I doing wrong?

The second path must be where to put the new file (and filename).

My suggestion:

```
cp /boot/grub/menu.lst ~/Desktop/menu.lst.backup
```

This will make a copy of your menu.lst in your 
Desktop. No need to be sudo, as you're keeping the file in your desktop as a normal user (where you can archive it where you find appropriate).

---

