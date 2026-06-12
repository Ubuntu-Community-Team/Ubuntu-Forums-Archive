---
title: "Install Problem"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by RED WIND on 2006-12-23
I am something I get it on the live CD boot, and right after I install with the alternative CD. I dont know what it means.

Exactly what it says
```

Starting up...
[17179571.408000] Kernel panic - not syncing: I0-APIC + timer dosen't work! Boot with apic=debug and send a report. Then try booting with the 'noapic' option [17179571.408000]

```

Someone HELP!!!       ](*,) ](*,) ](*,) ](*,)

---

### Post by Titus A Duxass on 2006-12-23
As it states in the message try boot with noapic, that means adding noapic to the end of the boot line.
Start the install process, tab down to the selection you want (i.e. Install in text mode) then press F6, you should see a line of text appear, simply add noapic to the end and then press enter to start booting with noapic.

---

### Post by RED WIND on 2006-12-23
so I should reinstall

---

### Post by Titus A Duxass on 2006-12-23
Do you have a working install?

If yes then ignore my post and do the following:

In a terminal enter;
sudo nano /boot/grub/menu.lst
and add noapic to the end of the line with your kernel details in.

If you do not have a working installation then you have to reinstall.

---

### Post by RED WIND on 2006-12-23
I have a question

I put that at the end. Is it going to look different or is gonna be no sign

---

### Post by Titus A Duxass on 2006-12-23
> I put that at the end. Is it going to look different or is gonna be no sign - sorry but you'll have to be a bit clearer.  What is going to look different?

---

### Post by RED WIND on 2006-12-23
I realy dont know but when I hit enter it loads and looks just like it did before

---

### Post by RED WIND on 2006-12-23
it works thanks

---

### Post by RED WIND on 2006-12-23
now that I have it installed the resolution is very low so I go to change it and it is saying there is only one choice for the resolution

---

### Post by houstonbofh on 2006-12-23
This is X configuration.  I would recommend starting a new thread.  In it, tell us what kind of video card you have.  We need to know the exact model.

---

