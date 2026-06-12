---
title: "Can't see 2nd hard drive"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by ngiovas on 2006-05-24
Now that I have Ubuntu loaded on my machine, I am trying to do some fine tuning.  One of the first things I noticed is that it doesn't show the second drive that is in the machine.  I use this drive for data storage on my network - not necessarily for direct access by this machine.  will I not be able to do this any more?

The drive is formated as NTFS (which may be the problem).  Is there a way that I can leave it in this computer and access it via the network, or am I stuck unless I reformat it?

By the way - the other machines on the network are all still Win XP.

NG

---

### Post by Porta on 2006-05-24
If you go to the ubuntu-wiki there is something about NTFS-drives, how to read and write to them and such.Look for NTFSreadwrite in the searchbox.

Porta

---

### Post by ProjectGod on 2006-05-24
you can mount the NTFS drive so that ubuntu can see it. and READ data from it. but WRITING to NTFS from LINUX is a no no. i think they'll eventually release a linux kernel that will be able to READ and WRITE to NTFS... eventually... but not at the moment. 

just before you try mounting an NTFS partition / disk... check if ubuntu linux recognises the physical disk attached to the computer by using this command at the console / terminal:

sudo lshw -C disk

you'll have to supply YOUR user password when prompted to enter password...

below are links to mounting an NTFS partition / disk.

[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

have fun!

---

### Post by ngiovas on 2006-05-24
Sorry, I need some clarification.  I understand that I will not be able write to the NTFS drive from my linux machine.  What I don't understand is, if I am accessing the NTFS drive, that resides on the linux machine, from an XP machine - will I be able to write to it?  Is the read/write controled by the operating system of the machine that houses the drive?

---

### Post by Mustard on 2006-05-24
[QUOTE=ngiovas]Sorry, I need some clarification.  I understand that I will not be able write to the NTFS drive from my linux machine.  What I don't understand is, if I am accessing the NTFS drive, that resides on the linux machine, from an XP machine - will I be able to write to it?  Is the read/write controled by the operating system of the machine that houses the drive?[/QUOTE]

Hmm..interesting question.  I would suspect it is controlled by the machine that hosts the drive.  For example, over a network, linux could write to an NTFS drive on a windows machine, because windows is doing the writing.  From this I would surmise that the opposite is true as well.  I don't have any evidence for this though. :)

---

### Post by nanotube on 2006-05-24
mustard's suspicion is correct - the actual writing to the drive is being done by the host os.
if you want to read/write ntfs, look into "captive" ntfs driver.

---

