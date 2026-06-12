---
title: "GRUB/MBR problems"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by fzf3 on 2006-09-02
Hi. My 1st post, so be gentle :)

My config:

drive 0 (master, ide0) has Windows XP Pro, drive C:
drive 0 (master, ide0) 2nd partition, D: under XP

recently added, so I could try Linux:

drive 1 (slave, ide0) Ubuntu installed

Everything is fine when I boot with this config. GRUB loads on startup and I can choose whether to boot Ubuntu or XP.

My problem is this:
Sometimes, I want to remove drive 1 and replace it with another hdd which I use to backup my drive 0 (XP) system and files. When I do this, GRUB fails to even come up with a menu and gives me an error, either 17 or 21. I even tried using my XP CD to rewrite the MBR on drive 0, but GRUB still comes up and fails. 

My biggest concern here is that even if I go back to the original config (in which case, GRUB loads normally and I can choose which system to boot), what happens if drive 1 fails? How do I boot XP from drive 0 when GRUB insists on loading and giving errors because drive 1 isn't there?

The whole point of me installing Ubuntu on a new and seperate drive was that I thought that if everything went horribly wrong, I'd just remove the 2nd drive and go back to XP on drve 0. Obviously, this isn't the case!

---

### Post by confused57 on 2006-09-02
Here's one way to set up a dualboot without installing grub to Windows mbr:

[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Also, you might be able to use a grub floppy:

[http://www.ubuntuforums.org/showthread.php?t=224345](http://www.ubuntuforums.org/showthread.php?t=224345)

A grub floppy could also be made at Ubuntu installation with the Dapper alternate CD.

---

### Post by fzf3 on 2006-09-02
Thanks, but having installed Ubuntu on drive 1 from the 'live CD', it seems to have already clobbered the MBR on drive 0. What I don't understand is, how to get the MBR restored on drive 0 so that I can remove drive 1 and boot drive 0 into XP as I did BEFORE I installed Ubuntu.

I'm keen to move away from XP to Linux but this is not encouraging. GRUB has obviously installed itself on my drive 0 MBR but won't allow me to boot XP unless drive 1 exists!   Not impressed :frown:

---

### Post by confused57 on 2006-09-02
Here's how to restore your Windows mbr(remove grub):
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Basically, you need to boot up with the Windows install cd(not a recovery cd) and press "r" for recovery mode, then enter **fixmbr** to repair the mbr.

You'll no longer be able to boot Ubuntu as your system is currently set up.
However, grub can be reinstalled with the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by fzf3 on 2006-09-02
I've already tried FIXMBR from XP's recovery console. Grub still loads.

Anyway, my point is: I don't really care which boot loader I use. Grub would be fine but surely, any decent boot loader would offer to boot partitions that ARE there, even when some are not?

Grub seems to rely upon drive 1 being present. When it isn't, it falls on its face. Crap. There must be a better way.

---

### Post by coffeecat on 2006-09-02
> **fzf3 said:**
> Grub seems to rely upon drive 1 being present. When it isn't, it falls on its face. Crap. There must be a better way.

Try to calm down and stop making comments like 'crap'. It is your lack of understanding that is impeding you. In your case you have (unknowingly) set up Grub stage 1 on the drive 0 mbr (WHERE IT BELONGS), and stage 2 on drive 1 (WHERE IT BELONGS, if you have your Linux root partition on drive 1). Removing drive 1 breaks Grub in this situation because you have taken half of it away. Would you function properly if I took half of you away? It's not Grub's fault - it wasn't designed to be mauled around like that. Neither is it your fault - you are new to this. But getting yourself in a tizwoz won't help. :wink:

Now - take a deep breath, decide exactly what you want to do and post back. There are plenty of people who will help you. :)

---

### Post by fzf3 on 2006-09-02
Thanks coffeecat. I'm perfectly calm  :) 

Please read my original post. I think that sets out quite clearly what I'm trying to do.

I thought I was playing safe by using the Live CD to install on Drive 1, leaving my drive 0 (XP) intact. I'm just very, very surprised that Grub won't work at all (ie. boot from drive 0) when drive 1 is removed - and I'm sure there must be a way around this without re-installing Ubuntu or XP.

I'm equally surprised that the FIXMBR from the recovery console hasn't worked but I guess that's a question for a non-Linux forum.

---

### Post by catlett on 2006-09-02
You are misunderstanding what is going on. Grub is installed in 2 places. It is on the mbr of your first drive (the one with XP) and it has the rest of it's files on your ubuntu partition on disk 2. You cannot remove either drive and have grub work.
You need to put your windows XP disk in and run fixmbr with that disk as master to return windows boot loader to that drive. You cannot put in any of your slave drives as master and run the command , it will only work on the drive with your XP installation.
The only way you would have been able to switch slave drives is if you had the windows drive as slave and the drive with ubuntu as master when you installed. Then grub would not have been "split" between the 2 drives. After installing like that, you could have switched the slave drives and just issued a command to mount the second slave drive after you booted into ubuntu.

---

### Post by Ahriman on 2006-09-02
As well as FIXMBR you could try FIXBOOT as well, usually when I have to use one I have to use both commands.

---

### Post by fzf3 on 2006-09-02
OK. Thanks for the replies & your patience!

Surely though, you must understand where I'm coming from...

Eventually I'd like to migrate to Linux and get rid of XP. In the meantime, I need to dual-boot. What if either of these HDDs fail? How do I boot either of them when one is missing? Surely, this is a fundamental issue.

I tried the link posted earlier to create a Grub rescue disk but that process didn't work, either.

---

### Post by catlett on 2006-09-02
Next time you install with 2 drives, do it like this [http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot) Installing with that process keeps the XP bootloader on the XP drive so you can put that drive in as master and boot to it. It also puts grub on the ubuntu drive so it can be master and boot ot ubuntu and with an edit to the grub menu, it can also boot XP. That way either drive is bootable alone and the ubuntu drive can boot both XP and ubuntu when it is master.

---

### Post by fzf3 on 2006-09-02
Thanks. That's what I was looking for (albeit too late, it seems!).

---

