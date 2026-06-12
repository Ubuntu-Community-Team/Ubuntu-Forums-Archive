---
title: "Grub error 18 - Grub fails to boot."
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by bwallum on 2008-02-18
Hello

I have just installed 7.10 on a friends Windows machine. All went well, I downloaded the 100+ updates, they were installed and the system requested a re boot.

At this time my friend wanted to see if he had any email so we restarted in Windows. That done we went to restart in Ubuntu. Made it through POST as usual but then got the "Grub loading'''" message shortly followed by "error 18".

Friend now thinks my coputer knowledge is 'alternative' at best.

How can I get grub to boot please?

Regards
Bob

---

### Post by dje on 2008-02-18
From the GNU GRUB manual:
> Error 18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 

Have you tried googling?
> ubuntu <computer make/model>
> grub error 18

Sorry i can't be more helpful

dje

---

### Post by Forrest Gumpp on 2008-02-18
This looks as if it may be a limitation of the BIOS in your friend's computer.

Would a workaround be to install an additional HDD (it could be an older relatively small capacity one) and then re-install Ubuntu manually, this time creating a / partition for Ubuntu on the newly-installed HDD?

This way the GRUB would not be outside the limit of what the BIOS can handle, if I understand things correctly.

It goes without saying that the additional HDD would need to be big enough for Ubuntu and any envisaged additional programs.  A separate Ubuntu home partition could reside upon the HDD containing your friend's Windows.

---

### Post by bwallum on 2008-02-19
Thanks for the responses.

I think the BIOS setting is ok. I put a second hard drive in the machine and Windows saw it ok. The second hard drive had been used at the time of Installing Ubuntu. I therefor went for a Ubuntu partition based on the "largest continous space" option at set up. It could be installed anywhere I guess, I don't know until I access the machine again (tonight around 19:30 GMT). 

I have cut a 'super grub' disk and will attempt to use it on the machine. I am a little unsure of which command to use. My current thinking is to go for resetting MBR at Linux root. I need to keep the machine dual boot. Any comments?

Regards
Bob

---

### Post by bwallum on 2008-02-23
I have removed Ubuntu and reinstalled Windows. Very painful. Can I put in a request for an easy to understand grub editor please.

---

### Post by bwallum on 2008-02-26
Update.

The machine is back up and running. The problem was trying to install a Master Boot Record (mbr) at the beginning of a partition which was not at the beginning of the drive.

The machine has two physical drives called C and D.

Before installing Ubuntu Windows XP was on drive C and drive D was used to backup important data.

I then defragged the D drive and set up an Ubuntu partition(s) on the last half of the D drive.

Within one or two iterations of starting and closing down each os the system refused to boot any os and posted the 'Grub 18 error'

The limitation in where the mbr is placed is a BIOS limitation. The machine is not that old, runs a socket A cpu at 266 MHz and is otherwise ok. The BIOS will accept multiple mbrs but these must be at the very beginning of the physical harddrive.

Solution was to render unto Windows what belongs to Windows, moving all D drive backups to the C drive. I then set up Ubuntu on the whole of drive D. Then I copied the backup files into Ubuntu.

A point to note is that Ubuntu can see all the Windows files but Windows cannot see the Ubuntu files. That's about right I think and a healthy barrier. Also some BIOS chips can be upgraded to allow mbrs at the beginning of partitions which are not at the start of the drive.

The Grub Manual is at [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

