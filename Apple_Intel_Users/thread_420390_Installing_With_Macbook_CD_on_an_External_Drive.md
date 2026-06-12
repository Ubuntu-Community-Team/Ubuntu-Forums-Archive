---
title: "Installing With Macbook CD on an External Drive"
date: 2007-04-23
forum: Apple Intel Users
---

### Post by Luigi239 on 2007-04-23
Hello, I am trying to install Fiesty on my External USB HDD. The partitian scheme is shown in this picture...

[IMG]http://img67.imageshack.us/img67/354/screenshotinstalltp5.png[/IMG]
(The first Drive is the internal, as the second one is external. There is one HFS+, and One Fat32.)

How Can I partitan this so that I can boot directly from the external drive, without touching my systems drive? I dont care if I lose all the data on my external.

Thanks. :)

---

### Post by hajk on 2007-04-25
Mmm... interesting problem. I have exactly the reverse setup: Linux on the internal HD (with an old-fashioned MBR based partitioning) and Mac OS X on the external Firewire/USB drive (with GPT based partitioning). EFI (successor to BIOS) always preferentially boots a from a GPT drive if there is one, and otherwise looks for a boot loader (like GRUB) on an MBR drive.

Now, in your case, you would have to hold the Alt/Option key to boot Linux from the external drive (it will show as a "Windows" drive). 

Now to your question: you could let the Feisty partitioner use the whole /dev/sdb with a default partitioning scheme, which will then probably look like /dev/sdb1 for the root partition and /dev/sdb5 for swap. Or you can make separate partitions for /home, /var, /usr and so on. You might also reserve part of the drive for a possible second OS. Now, having said this, you should realize that the partitioner is notoriously buggy if you want to do anything but the default scheme.

---

### Post by sklarsky on 2007-04-25
I've been trying to accomplish the same on my CDiMac- my internal HD failed verification and so bootcamp would not allow me to repartition the internal drive.  I had formatted my 200gb firewire drive with GPT (since intel macs can only boot externals if they are gpt i believe) in Disk Utility with about 20gb reserved for ubuntu and the rest was partitioned as HFS+.  in the ubuntu installer i manually edited the partiiton table to create /boot, / , and /swap ...

the tricky part is at the end when it reviews all the settings you chose for installation there is a button for advanced options where it asks which hard drive to install the boot loader on.  by default it will have (hd0) which is the internal drive.  i've tried changing that to (hd1) which is my external, but when i went to choose to the external as the boot device in apple's boot loader, grub says it has a HD error.  if i try to use refit to boot i get an error saying apple's firmware is not good with externals

i haven't thought about using my external of osx and the internal for ubuntu...

-j

---

### Post by hajk on 2007-04-25
You can't use Grub on a GPT HD, as far as I know, so no wonder that route failed. I believe "elilo" can be used for that, even without REFIT, although when I last tried that (in October 2006) it didn't quite work yet.
There's a MacBook page on the Debian wiki that has more info on booting Linux from a GPT-formatted drive without BootCamp and/or REFIT.

---

### Post by xGuse on 2007-04-25
Holy crap!!  This is exactly what I have been bbeating my skull bloody over for the past month!  God I hope that your questions get answered!  It seems that the issue is getting Grub placed in the right location.  I have gotten a successful install with no errors but using the command line trick in the macbook howTo ([https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)) but it never boot correctly.  I have read somewhere that the macbooks dont boot from USB.  Can anyone confirm or deny this with more certainty? 

Thanks all and poster!

Gus

---

### Post by ronocdh on 2007-04-25
> **xGuse said:**
> Holy crap!!  This is exactly what I have been bbeating my skull bloody over for the past month!  God I hope that your questions get answered!  It seems that the issue is getting Grub placed in the right location.  I have gotten a successful install with no errors but using the command line trick in the macbook howTo ([https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)) but it never boot correctly.  I have read somewhere that the macbooks dont boot from USB.  Can anyone confirm or deny this with more certainty? 

Thanks all and poster!

Gus
You are correct in that the Macs are set up not to boot from USB; however, I have seen tricks about creating a Linux USB installation, then booting to a Linux live CD, burning a special CD, and booting to THAT with the USB drive inserted. Apparently that boot CD ordered the system to flip to a USB boot; it's something Apple has tried to disable.

I'm sorry, I just Advanced Search the forums for 5 minutes and couldn't find the post I wanted. I was pretty sure the gentleman was kind enough to post here in Apple Intel... anyone remember?

---

### Post by hajk on 2007-04-26
> **xGuse said:**
>   I have read somewhere that the macbooks dont boot from USB.  Can anyone confirm or deny this with more certainty?Well, I boot OS X off an external LaCie HD with both a FireWire 400 and a USB 2.0 interface; either way works. I don't know whether this holds for a USB stick as well (my guess is it does).

---

### Post by xGuse on 2007-04-26
I want to use USB HD not a flashdrive anyway.

---

