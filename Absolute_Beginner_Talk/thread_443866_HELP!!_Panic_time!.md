---
title: "HELP!! Panic time!"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by femens on 2007-05-14
I've had troubles with all versions of Ubuntu 7.04 along with the latest Lnspire, Freespire, Kubuntu and Mepis on my compaq SR1550NX desktop system. 6.04 works like a charm.

My "Official" (not downloaded) version of 7.04 arrived in the mail today and I gave it a try. It seemed to be working OK when booted from the CD, so I thought I'd try an install. Everything went well until it came time to reboot. he installer had somehow messed up the version of grub bootloader it installed. The system would neither boot 7.04 or Windows (an essential for me)

I reinstalled Ubuntu 6.04 and it works well, but when I try to boot to Windows, I get the message that grub is loading, then an error 21 message. How can I get to the boot software installed on the main floppy and correct it so it'll load windows correctly?

---

### Post by Hobo Joe on 2007-05-14
I believe there is a way to re-install the bootloader from the terminal through the live CD, but sadly, i don't know the proper command(s).

I'm sure there is someone here who can help you though.

---

### Post by freebeer on 2007-05-14
Maybe you can do a search for "Error 21" on these forums?  I know I've seen a post or three about it.  Good Luck!

---

### Post by Dr Small on 2007-05-14
If you find a solution. This is the exact same problem my sister had when installing Ubuntu.
It messed up at the end, and wouldn't boot period.
We finally got to the menu to reinstall windoze with the partioned image, and we cleaned the other partioned out. She's afraid of linux now :P

Dr Small

---

### Post by ccesare on 2007-05-14
If you have a Windows recovery CD, you can have it reinstall the Windows bootloader over GRUB. Then, hopefully, you can go back and reinstall GRUB. But yeah, definitely do a search here and on Google for that error. I had a similar problem a month ago. Reinstalling my distro fixed it for me though.

Good luck, I know it's nerve-racking to not have access to your important data, but I also know that somewhere out there is a fix for you. Keep looking!

---

### Post by femens on 2007-05-14
Error 21 is "Non Existent Drive"  When the bootloader set up it had invalid drive IDs for both systems (I put Ubuntu on a separate USB HD and that works OK).

I have a Partition Magic disk around here somewhere. I hope it will allow me to regain access to Windows.

---

### Post by ccesare on 2007-05-14
What are you planning on doing with the partition magic disc?

---

### Post by femens on 2007-05-15
I was hoping that Partition Magic, which includes a boot system manager also, would let me re-do the messed up grub loader. No soap -- it only installs on a running Windows system. Now that I've recovered access to Windows, I may use it to set up a dual boot situation.

---

