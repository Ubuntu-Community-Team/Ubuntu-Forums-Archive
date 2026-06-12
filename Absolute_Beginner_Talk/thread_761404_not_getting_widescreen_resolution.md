---
title: "not getting widescreen resolution"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by rajaram_s on 2008-04-21
I am using a dell inspiron 640m series laptop, which runs on an Intel 945GM chipset. I was really happy since there was not a single driver that I had to install, nor was there a single compatibility issue. Compiz fusion works just great on it.... The resolution was working. Once I was playing this game "lego racers " on ubuntu using tha latest version of wine and someway, the application stopped resonding and I had to kill the process, using terminal. The game normally changes the resolution to 800*600 before start and at end automatically changes it bak to 1280*800 (my native resolution). From the time I killed the process, even after many reboots and upgrades, the native and the only resoltion available is 800*600. How do I solve it?

---

### Post by kpkeerthi on 2008-04-21
From GRUB, boot into recovery mode and run this command at the prompt
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

If it prompts for resolution, choose the one(s) your monitor supports. 

Type **reboot** and boot normally.

---

### Post by christianxxx on 2008-04-21
First of all, have a look in **/etc/X11/xorg.conf** to see whether to desired resolution is listed. You should see this undes "Section: Screen" and the different "SubSection: Display".
I think it should be ok to add new sections here, but if not:

```
sudo dpkg-reconfigure xserver-xorg
```
to reset the drivers, and take it from there?

Hope this helps.

---

### Post by Penguin Power on 2008-04-21
Both of those commands above will work, however the -phigh flag will remove any questions that xserver does not deem important.

The two questions you want to look out for are drivers, near the beginning, and the option to add extra resolutions, near the end.

---

### Post by rajaram_s on 2008-04-21
Thank you so much... I am not on my laptop right now... I'll try them and get back to you if they work....

---

### Post by bartcramer on 2008-04-21
I have the same chipset & resolution (Acer 5610), and never had problems on Gutsy... most important setting might not be in Xorg 7.3 (which now mostly relies on 'detecting' instead of 'setting'), but in the driver you are using (in the "Screens & Graphics" dialog, if I am not mistaken). Try to set that to VESA, and then back to intel-experimental. Should solve the issue, and if not: try searching in launchpad... 

Good luck!

---

### Post by rajaram_s on 2008-04-23
Thanks.... resettin xorg workes... I got my widescreen resolution back again............

---

