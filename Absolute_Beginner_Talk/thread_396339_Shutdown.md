---
title: "Shutdown"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by alfix on 2007-03-29
Pc with Windows XP shutdown well, but with Edgy don't shutdown.

I have added the line apm power_off=1 at /etc/modules 
I have added acpi=force to the /boot/grub/menu.lst.

But Pc don`t shutdown.

¿Whats wong?

---

### Post by tatimmer on 2007-03-29
Try this from a terminal:
<shutdown -h now> shuts down and turns off
<shutdown -r now> shuts down and reboots

---

### Post by alfix on 2007-03-30
<shutdown -h now> dont'work
<shutdown -r now>  works well

The problem is with  power-off.

---

### Post by greatwolf on 2007-03-30
I'm having the same problem with this as well. My specs are:

Shuttle - AN35 ultra using nforce2 chipset
1 gig DDR PC3200 KingMax ram
ATi Radeon 9800 SE
120gb WD hd
200gb Maxtor hd

For me when during shutdown, I get to the ubuntu splash screen with the orange loadbar and I hear a slight click from my case, probably coming from the hd, like it's about to turn off but it never does. The thing just stays on.

I tried the Knoppix livecd distro as well and that one doesn't have this problem of shutting down btw. 

Any suggestions on how to start diagnosing this problem is appreciated.

Edit: oh forgot to add, I was doing this with Ubuntu 7.04 beta Fiesty.

Thanks

---

### Post by openix on 2007-03-30
If you want to power a machine off at the console try this,

shutdown -hP now

Remember you have to have root privileges to do this. Read up further on this by issuing the following at the console,

man shutdown

Hope that helps

---

### Post by Sunflower1970 on 2007-03-30
My old Compaq does this. Everything shuts down after the Ubuntu splash screen comes up, except the power supply. I just hit the power button and manually turn it off. Slightly annoying, but I can live with it :)

---

### Post by alfix on 2007-03-30
I also can live with it, but it is sad that Windows can and Ubuntu no

---

### Post by alfix on 2007-03-30
updated bios and it works :)

---

