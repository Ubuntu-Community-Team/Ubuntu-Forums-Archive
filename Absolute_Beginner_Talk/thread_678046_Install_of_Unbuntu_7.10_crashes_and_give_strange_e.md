---
title: "Install of Unbuntu 7.10 crashes and give strange error messages"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by utklasad on 2008-01-25
Greetings!
I've just got my laptop, and I got tierd of Vista, so I decided to try Ubuntu 7.10.

I'm planning to keep Windows, I've 2 hdds in the computer, one 150gb for Windows and one 150 gb thats empty..
I want to install Ubuntu on the empty disk, so I can switch between the OS.

Fujitsu Siemens Computer (FSC) Amilo Xa 2528
([www.fujitsu-siemens.com/Resources/175/1543626421.pdf](www.fujitsu-siemens.com/Resources/175/1543626421.pdf)).

I've tried to install Unbuntu 7.10 with both alternitve CD and the Dekstop CD, none of them work. I cant even boot with the desktop CD, with the alternitve CD I get trough the keyboard langunge selection, and it crashes when its going to read my CD rom.  I just get this error message, on both verisions:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu4) Built-in shell (ash)
Enter "help" for a list of built-in dommands.

/bin/sh: can't access tty; job control turnd off
(initramfs)

[ 0.206515] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0

37.588000 hda: drive not ready for command
37.588000 hda: drive not ready for command
37.588000 hda: drive not ready for command
37.588000 hda: drive not ready for command
37.588000 hda: drive not ready for command
37.588000 hda: drive not ready for command
37.588000 hda: drive not ready for command
37.620000 hda: drive not ready for command
37.620000 hda: drive not ready for command

Then its freezez and stays there, I've been waiting up to 1 hour, nonthing happend.

I've tried to burn the CD in diffrent speeds, also lent my friends CD that worked, nonthing help.

Ive tried to solve this for some hours now, so some help would be very nice!

Kind Regards,
Blixmo

---

### Post by Ryadt on 2008-01-25
check your cd for any defects..

---

### Post by Cypher on 2008-01-25
Hmm..at the prompt type "dmesg | grep -e hd" and show us what you see. HDA should be your hard drive and HDB should the CD. Looks like the hard drive is having some issues..

---

### Post by utklasad on 2008-01-25
Ok ok. I will try this Cypher, brb ^^

---

### Post by utklasad on 2008-01-25
Nonthing happend, but this time I got another error, or, actully the same:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu4) Built-in shell (ash)
Enter "help" for a list of built-in dommands.

/bin/sh: can't access tty; job control turnd off
(initramfs)

37.588000 hda: drive not ready for command
37.588000 hda: drive not ready for command
37.588000 hda: drive not ready for command
37.588000 hda: drive not ready for command
37.588000 hda: drive not ready for command
37.588000 hda: drive not ready for command
37.588000 hda: drive not ready for command
37.620000 hda: drive not ready for command
37.620000 hda: drive not ready for command

Ive also got a friend whos got exactly the same problem with his Amilo Xa 2528, he dont get it to work either, he even tried at Fujitsu Siemens forums.

---

### Post by utklasad on 2008-01-25
I also got another error, direct after the start screen, I could not read it before, but now I got it:

[ 0.206515] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0

---

### Post by markyb86 on 2008-01-25
You sure your not booting a patched Mac OS X 10.4.8 cd?

All jokes aside do you know what manufacturer the sata controller is made by?

---

### Post by utklasad on 2008-01-25
Ehrm, what do you mean? I have downloaded Ubuntu from ubuntus homepage, nonthing else.. I've tried both the desktop and alternitve verions.. (incase if you didnt was joking)

I've also made a little search about this, seems like alot of peapols have this problem, with Amilo XA 2528, but their must be a fix?

Heh, well, I dont know what manafacturer sata controller is made by, how do I check that? :p

---

### Post by markyb86 on 2008-01-25
I was just joking about the Mac OS part, but it seems as it might be nvidia which is supported, but the errors you are getting are acting as if that particular sata controller isnt supported

---

### Post by utklasad on 2008-01-25
So there is nonthing I can do? I've searched like hell on other forums, I've found alot of threads about this, but not anything to solve it..

---

### Post by markyb86 on 2008-01-25
Keep windows and try to install ubuntu with [Wubi.]("http://wubi-installer.org/")

---

### Post by utklasad on 2008-01-25
I was already planning to keep Windows, I've 2 hdds in the computer.. One 150gb for Windows and one 150 gb thats empty..      
                                                                                                                                                                                      I wanted to install Ubuntu on the empty disk, well.. Maybe I have to wait, but I will check this Wubi..

---

### Post by rosegarden78 on 2008-01-25
Would installing it to the 1st disk and mounting the 2nd disk in Ubuntu be unacceptable?  I think only one disk is like the boot disk anyway. If Windows in on the 1st disk you can split (partition) it in Step 4 just choose Custom.  I use a 20/80 split for XP/Ubuntu but use whatever you feel is best.  You need at least a '/' and a 'swap' partition and only use primary partitions.  I use a setup as described [here]("http://ubuntuforums.org/showthread.php?t=677959") and [here]("http://ubuntuforums.org/showthread.php?t=385981").

---

### Post by limac on 2008-01-25
did you try the alternate cd yet? if not try it first. tho it comes with a text installer...

regards,
limac

---

### Post by limac on 2008-01-25
oopsey, please disregard my post. I didin't read your post completely! 

regards,
limac

---

### Post by utklasad on 2008-01-25
Ive just fixed it. I just installinux.com and made a private boot CD, and it worked.. thanks for all the replies.

---

### Post by Vitz on 2008-01-28
I too have the 2528, and have been looking for a fix for ages now. I'll try that Instalinux thing right now. Let's hope I manage to do this. If not, I hope you can help me out a bit.

---

### Post by patko on 2008-01-28
hello, I've just installed ubuntu32 on an amilo xa 2528, it wasn't without pain, like you have experienced.

 The kernel doesn't have the driver for the cdrom, that's why it couldn't detect it.

solution: network install

once aptitude is installed, I've installed manually with the command

sudo aptitude install ubuntu-desktop 

and once it's finished

startx

there you go ;)

you might have to had acpi=off to /boot/grub/menu.lst

I've completely removed vista because it takes too much place on RAM and HD and because I don't want to use/see anymore this ugly and innefficient Operating System.

Also I went to this forum to find out a clean solution for adding the good CDROM driver to the kernel, apparently we have to recompile...

---

### Post by Vitz on 2008-01-28
Heh multiple fixes all of the sudden :)

That Instalinux thing worked perfectly. Thanks!

---

