---
title: "Booting without a CD?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by stereoguy823 on 2007-04-20
Hi All. Very cool forum and community. I am very impressed with this whole new 'world' here.

I wonder if you can help me. I have spent the best part of 2-3 days searching and googling for an answer and i don't yet think I've found it yet.

I have a JVC XP3210 mini-note laptop with 256MB ram and a 10GB HDD. It is divided into 3 partitions. One is the C Drive, one is the D drive named 'data' and the third is hidden with the windoze XP recovery in it.

What I'd like to do is keep the XP partition intact for a restore in the future may be. Then utilise the rest for an ubuntu install. i do not want to 'dual boot' this machine. 
However, as there is no built-in CD Rom drive or floppy I can't just run the Ubuntu CD. I can of course run it across the network, but that isn't available from the Bios. I think the PCMCIA slot is available but cannot find a drive that will boot *for certain* for less than £140 and I would rather not spend that kind of money to do this.

Does anyone have a solution? I have this machine networked with two other XP machines. Both of which will have Ubuntu at some stage, I'm sure.

I have read some solutions creating partitions using partition magic, but I don't have a copy and the others I have researched require a Live CD. Help!

---

### Post by Cypher on 2007-04-20
Without access to a floppy or CD-ROM. The only other thing I can think of is using a USB flash drive with the Live CD on there and then using that to install Ubuntu.

But, depending on how old your laptop is and what version of BIOS there is, it might not support booting from USB. If you can possibly find an update to the BIOS, this might be the path you want to head.

These [instructions](http://www.debuntu.org/book/export/html/160) will tell you how to transfer the LiveCD to the USB flash drive.

Regards

---

### Post by az on 2007-04-20
What do you mean about not wanting to dual-boot.  If you want to install Ubuntu and keep XP, that's dual-booting.

Your most viable option is to remove the hard drive and place it in another computer and install ubuntu from there.  Swap the drive back when you are done.

The only think you should need to reconfigure is the graphical system.  The first time you boot (once the HD is back home in your laptop) is to boot into recovery mode and run

dpkg-reconfigure -phigh xserver-xorg

and then

init 2

---

### Post by stereoguy823 on 2007-04-20
Thanks for the replies.

I checked the bios, not USB booting unfortunately. I may have to go down the HDD removal route. Hadn't thought of that.

I don't want or need dual boot. But the XP recovery partion used to restore the machine would be helpful to keep. I don't know of a way to copy it at the moment. Still getting my head around other stuff :-) Bit *too* used to windows!

What about transferring the contents of the Ubuntu CD to the 'data' partition of the laptop. Is there anyway to invoke the file that would be used to start the cd from DOS?

I can get to the DOS prompt from the bios. Any other ideas?

---

### Post by Cypher on 2007-04-20
Don't worry about the dual-boot stuff..during Ubuntu install you'd just leave the restore partition alone and play with the other partitions. Now, of course, since you don't have a CD or Floppy, not sure how you would indeed restore XP if you ever wanted to..but that's an entirely different story.

Back in the day people used to use a DOS floppy with loadlin to boot into the installer. But all of that requires a bit more knowledge of Linux in general. Your best bet is to take your HDD to another machine and do a proper install there and then return it to the laptop.

Regards

---

### Post by phidia on 2007-04-20
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Check out the above link "Installation without a CD"

---

### Post by stereoguy823 on 2007-04-20
Thanks for all the suggestions.

Looks like I'll be removing the HDD..........

---

