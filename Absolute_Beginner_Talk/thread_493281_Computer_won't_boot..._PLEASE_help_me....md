---
title: "Computer won't boot... PLEASE help me..."
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Volsfan91 on 2007-07-05
I'm working on my 7.04 Live CD.

My computer has Ubuntu 7.04 installed as well as XP Home.

Today, I was trying to use Partition Magic (we'll call this **mistake number one**) to create a swap partition, something I had failed to do before.

I resized my Windows partition to 1 gig less than it was before to create a new swap part. I also set it to become a swap part using Partition Magic.

I hit Apply, and rebooted. Everything went smoothly until "step 3". It gave me a file system error, and said "failed". I hit a button to reboot... and was greeted with **Grub Error 17**. 

The PC won't do anything past that.

The good news is that I can view and browse both partitions and all of my files are safe.

Help me PLEASE. I've got like an hour at most to get this fixed.

---

### Post by Cypher on 2007-07-05
Follow [these instructions]("http://ubuntuforums.org/showthread.php?t=24113") and re-install grub and see if that fixes your problem..

---

### Post by Volsfan91 on 2007-07-05
Thank you for the quick response. /dev/hda6 is my Linux partition. I change the mount point to just "/" right?

---

### Post by Cypher on 2007-07-05
I would follow the instructions in post #2, from inside Grub..

---

### Post by sab0403 on 2007-07-05
> **Volsfan91 said:**
> Thank you for the quick response. /dev/hda6 is my Linux partition. I change the mount point to just "/" right?

Yes.

---

### Post by Volsfan91 on 2007-07-05
[quote=Instructions]8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu[/quote]

Mine doesn't give me the option to continue, only to press okay and go back and tick the format box. :\

---

### Post by Cypher on 2007-07-05
Please follow the instructions in[ Post #2]("http://ubuntuforums.org/showpost.php?p=117829&postcount=2") which uses the safer "Grub" way as opposed to the potentially harmful (if not properly done) "Disk Partition" way..

---

### Post by Volsfan91 on 2007-07-05
Okay, I'm looking at that, but to be honest, it's over my head.

[quote=Instructions]4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.[/quote]

This part kind of confuses me with the numbers and such. Would you tell me a little more about it?

I really appreciate your help.

---

