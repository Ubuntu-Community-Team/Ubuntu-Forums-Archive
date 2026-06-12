---
title: "Dual-booting questions (Dell Latitude D810)"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by mathmo3 on 2007-01-02
Hi,

I'd like to install Ubuntu on my Dell Latitude D810 laptop, dual-booting with Windows XP (keeping Windows running is important though).  I've already resized my Windows partition to make some space but there are a couple of questions I'm not sure about, being new to Linux.

Firstly, do you think it's safe to install Edgy on my laptop, given the bug reported at [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/43745](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/43745) ?  I haven't seen any reports specific to this model of Dell but similar ones have suffered.  I do currently have backups but it would be an incredible pain if my computer failed in a week or two's time.

Secondly, what are the advantages and disadvantages of using the Windows boot loader over GRUB on the MBR?  I've seen descriptions [here]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3") and [here]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/") of how to use Windows' boot loader over GRUB - are these reasonable guides?

Thanks for your help.

---

### Post by Sef on 2007-01-03
> Firstly, do you think it's safe to install Edgy on my laptop

Yes, but **back up** your files first.  There are no 100% guarantees.

> Secondly, what are the advantages and disadvantages of using the Windows boot loader over GRUB on the MBR?

Windows Advantages: You enjoy doing a lot more work to get something running.

GRUB Advantages: It just works out of the box.

To dual boot:

Read [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing") (for installing from the Live CD.)

Read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/") (for installing from the alternate cd.)

---

### Post by mathmo3 on 2007-01-03
Thanks for your message.  I went ahead with the install (I already had backups) and everything seems to be working fine, as far as I can tell.  I have one question, though - I've made a shared FAT32 partition but I didn't think to change the mount point in the installer, so it's still at /media/sda5.  Is it best to mount it somewhere else, like /share, or does it not really matter (as I won't be using it a huge amount)?

---

