---
title: "booting to Linuxdesktop"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by jloveless on 2008-02-05
I have Ubuntu 7.10 and it was working well until I started to screw with it (duh). I installed KDE 4 through Synaptic and then decided to remove it. It seemed to remove ok but now when I boot I end up at a Linux desktop rather than Gutsy.

My system is a well endowed HP with Vista Ultimate. I used Easy BCD to create a dual boot option. The first boot menu offers Windows Vista or Ubuntu 7.10. Then the (grub, I think) menu shows Ubuntu 7.10, Ubuntu Recovery and Memory test. If I select Ubuntu 7.10 the opening Ubuntu logo shows but then it ends up with a login to the Linux desktop - not graphical. 

Everything else seems to be ok and I don't believe I lost or disrupted anything too major, so I need to know now if there is a way to invoke the original (Gnome) desktop from the text Linux desktop and then how to repair the boot instructions to get me bac to the normal boot..

I am a newby, certainly, and I am thankful for help like I can get here.

Jon
[email]jaloveless@gmail.com[/email]

---

### Post by %hMa@?b&lt;C on 2008-02-05
when you get to console try 
sudo dpkg-reconfigure xserver-xorg 
follow the prompts

---

### Post by jloveless on 2008-02-05
Thanks. I did try that. It warned me that I had a customized xorg and that it had saved a backup. I rebooted and got the same results - at the console. Is there a console command to launch the G desktop??

Thanks.

---

### Post by %hMa@?b&lt;C on 2008-02-05
try "startx"

---

### Post by jloveless on 2008-02-05
Well, startx worked to get me back into the Ubuntu desktop, but when I reboot, I get the same thing - when I select Ubuntu 7.10 I end up at the Linuxdesktop login. When I run startx my gra[hical desktop comes up but the permissions are now different. I can't run anything, such as Synaptics and it says I don't have authority. Also, when I go to reboot I don't get Reboot as an option. Woe is me. Is there any additional info I can get you that will help analyze this issue?

Thanks again for your help.

---

### Post by Nythain on 2008-02-05
```

sudo aptitude install gdm

```
sounds like removing kde4 also quite possibly kill kdm, wich was possibly installed and replaced gdm when you installed kde4... dont know how or why that would happen, but meh, worth a shot... since startx is starting your desktop, you dont have any xorg errors or problems, so its gotta be your display manager

---

