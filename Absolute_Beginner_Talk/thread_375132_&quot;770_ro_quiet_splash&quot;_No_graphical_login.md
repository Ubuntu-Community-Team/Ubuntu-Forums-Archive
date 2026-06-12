---
title: "&quot;770 ro quiet splash&quot;? No graphical login? Commande line only?"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by atselby on 2007-03-03
I recently upgraded to Ubuntu Edgy and all was fine after a few slight problems that I easily fixed using a guide on debianadmin.com. However now after I've fixed a problem with my sources.list, something happened during upgrade to it, it all appeared fine and since it was working I installed newer updates for apps and downloaded a few new ones that I'd been trying to get using Synaptic. It all worked fine and all. However after I had turned it off for the night, since evidently hibernate doesn't like to work anymore, I tried to login again this morning and get this error message at the end  when it's all done moving around and loading stuff.

```
 "Booting 'Ubuntu, kernel 2.6.17-11-386'

root  (hd0,4)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.17-11-486 root=UUID=a19a0f73-a024-45a1-994a-bd7a2c783
770 ro quiet splash
   [LINUX-bzImage, setup=0x1c00, size=0x17e746]
initrd /boot/initrd.img-2.6.17-11-386
   [Linux-initrd @ 0x1f91c000, 0x6d367f bytes]
savedefault
boot

Ubuntu 6.10 adam tty1

adam login:
```

And I can login but after that I get

```
Last Login: Fri Mar 2 16:31:35 2007 on tty1
Linux adam 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686

The programs included with the Ubuntu system are free software; the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to th extent permitted by applicable law.
1 failure since last login.
Last was Fri 02 Mar 2007 4:31:53 PM CST on tty1.
```

And then a prompt for a command.
If I login is there some way to swith back to the graphical login and get me into GNOME? I think that's the problem is that it can't get to GNOME or something. I'm not very savvy when it comes to Linux so full command lines with intructions or at least an order would help me alot.

Thanks,

Adam

---

### Post by atselby on 2007-03-03
Please if anyone could even offer suggestions as to what this may be so I can better search for a solution I would appreciate it greatly.
I'm open to any ideas. Thanks again,

Adam

---

### Post by Tomosaur on 2007-03-03
That's not an error message - it's the standard logon message when you're not using the GUI. Just log in at the prompt, and type the following:

```

sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure xserver-xorg

```

Both of these commands will ask you a few questions. Once you're finished, reboot the machine, and your GUI should display properly again.

---

### Post by atselby on 2007-03-03
Ah. Alright. Let me try this real quick. I figured it was something along the lines of GNOMe wasn't working but apparently I was incorrect.

To "sudo dpkg-reconfigure gdm" I get,

"/usr/sbin/dpkg-reconfigure: gdm is broken or not fully installed"

Any help there?

Adam

---

### Post by Tomosaur on 2007-03-03
Try this then:
```

sudo aptitude install gdm

```

---

### Post by atselby on 2007-03-03
Alright. I didn't think it was possible to do an install of anything without a internet connection but apparently it has one before I get to gnome now. Installing...

Apparently part of this is caused by vmware player since I've gotten a few prompts about overwritting files that it's got or something. It goes by a bit fast for me to get some of it... I think I'll be removing that soon then. Could this be a real problem for it?

It worked. Thanks a great deal.

Adam

---

