---
title: "Clean Installation, but will not boot from 2nd drive"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Cold-Gin on 2007-06-28
Hi. I have a second hard drive that I have installed Ubuntu 7.04 on. I was able to complete the installation, but when I reboot, I get the GRUB menu that allows me to choose Ubuntu or Windows, but Ubuntu will not boot from the second drive. I just get a black screen and that's as far as it goes.

I also noticed similar behavior when I was trying to reboot the machine. When I clicked the "Restart computer" button after the installation, Ubuntu closed out the gui, but it will not physically shut off the computer. It just goes to a black screen, and hangs there.

Has anybody encountered a similar problem in a two-drive scenario?

P.S - I also brought Ubuntu up in recovery mode, and I can execute:

shutdown -P now

from a prompt, and then it will then turn off the computer.

Thank you.

---

### Post by Cold-Gin on 2007-07-01
Someone showed me that I can get my PC to boot into Linux by performing the following steps from the grub (boot loader) menu:

1.) At the grub menu, select 'e' to edit the Ubuntu start up commands
2.) I then remove the quiet command
3.) I press 'b' to boot
4.) The screen then goes black and just hangs
5.) At this black screen, I can press <ctrl> + <alt> + <F1>

This allows the gui to come up, and I can log in normally. Everything else functions fine from this point. I am also able to shutdown using the 'quit' menu option then the 'shutdown' icon. This physically shuts down my machine.

I also notice that when the machine hangs on the black screen, the power button does not respond when trying to power off manually. I literally have to cut the power on the power strip to kill my machine. 

How can I get my machine to boot into Ubuntu cleanly? Also, I noticed in the Ubuntu device manager that there is a section for "Power Button". Should something be adjusted here to configure the power button properly?

My PC:

Gateway 300X
Celeron 1.8GHz processor
768MB ram

Thanks!

---

### Post by Cold-Gin on 2007-07-02
Got the solution from a kind responder @ linuxquestions.org. Check this link:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Here's exactly what I did:

1.) Backed up /boot/grub/menu.lst
2.) Added vga=771 noapic nolapic to the end of the # kopt line like the directions describe
3.) Tried multiple shutdowns and restarts and it reboots consistently using the grub menu!

I also get the Ubuntu status bar as I am booting. That's where I was getting the black screen that just froze prior to adding these new boot options to menu.lst

:D

---

### Post by Cold-Gin on 2007-07-03
Sorry... I left out a step:

2a.) Ran sudo update-grub

---

