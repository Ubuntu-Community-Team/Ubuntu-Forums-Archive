---
title: "No booting at all"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by jaseerabubakar on 2007-10-08
Hi,
I installed Ubuntu as dual boot (along with Win XP) and after that the Grub screen comes up and the system reboots automatically.. 

I installed Ubuntu after Linux only

Any help ???

Thanks,
Jaseer

---

### Post by jfinkels on 2007-10-09
I can't understand what your problem is. Are you trying to say that although GRUB boots normally, Ubuntu fails to load?

---

### Post by HW_Hack on 2007-10-09
Well it sounds like your MBR (Master Boot Record) is hosed up --- however typically Grub just sort of fails and then stops ---- and leaves some text on the screen ..... forcing you to do a ctl+alt+del  to restart.  

If I understand correctly the system does not start to boot linux - but just boots and re-cycles as the grub menu comes up.  Something got fouled up when Ubuntu tried to write to your MBR - best bet is to boot using your XP CDROM (any XP CDROM) and choose to do a repair ----- prior to doing that - use another computer to google   "XP MBR Repair"  and print out the instructions (its very easy). 
Do this because when you choose repair - you will be dumped into a XP command line and will need to enter a few commands.   

You will have to re-install Linux ---

---

### Post by alienexplorers on 2007-10-09
Boot your XP disk into recovery mode and enter:
> fixmbr
Then reboot and put you Ubuntu Live-CD in and let it load.  Once loaded you can enter the following commands:
> sudo grub
find /boot/grub/stage1
root (hd#,#)
setup (hd#)
For complete directions see the link in my sig on how to reload grub.

---

### Post by jaseerabubakar on 2007-10-09
Hey.. thanks. That fixed the problem.
I am happy man now... :)

---

