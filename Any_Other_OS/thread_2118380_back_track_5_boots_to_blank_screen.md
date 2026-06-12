---
title: "back track 5 boots to blank screen"
date: 2013-02-21
forum: Any Other OS
---

### Post by yanvolking on 2013-02-21
Hello community,

I have just installed black track 5 (Based on Ubuntu 10.04) on a separate 500GB HDD and when I run it on my Acer Aspire One D270 it boots to a blank screen.  The partition on the 500GB hdd is encrypted.  When I run backtrack on other computers it boots normally.

With the acer aspire one d270 everything starts ok : it prompts me for the partition password, then the splash screen passes by for a while then the screen goes blank.  The WLAN indicator light does not even light up so the boot process has stalled.

BUT: when I boot up the system with the acer aspire one d270 connected to an external monitor, the system boots completely and successfully, even activating the acer's own monitor.  

Can anybody tell me if there is a way of booting correctly without having to connect an external monitor first?  

I know the acer aspire one d270 has an issue with linux systems due to its cedarview graphics card, but if that were the case the problem would persist with the external monitor as well, I suppose.

---

### Post by varunendra on 2013-02-21
*Thread moved to **Other OS/Distro Talk**.*

---------------------

Have you tried 'nomodeset' option at kernel boot line?

I'm assuming it uses same grub2 menu as default Ubuntu. If so, you may try 'failsafeX' mode in Recovery menu, or add it to kernel boot line (by pressing 'e' at grub menu > adding 'nomodeset' at the end of boot line) for temporary testing, or permanently set nomodeset option in /etc/default/grub file > then do 'update-grub'.

Let me know if you need help with this, although I'm not sure if it'll help.

---

### Post by yanvolking on 2013-02-21
Hi there Varunendra,

with thias system I dont have a kernal boot line.  In BIOS i hit F12 to select the boot volume, highlight the usb connected HDD and hit enter.  This leads straight to the splash screen.  The splash process is briefly interrupted to ask for the encrypted volume password and then carries on until the screen blacks out and the whole process stalls. 

Should I then use the external screen to execute the full boot process and then go edit a boot file as you suggest?

---

### Post by varunendra on 2013-02-21
> **yanvolking said:**
> Should I then use the external screen to execute the full boot process and then go edit a boot file as you suggest?
You can do that but that will make it permanent, while I think we should first try it temporarily.

The boot process you described is same in Ubuntu if it is the only OS on the drive. You should be able to get the Grub menu by press & holding 'Shift' key during the splash screen. Not sure whether before or after the encryption password stage though.

Once there, press 'e' to edit the default boot line.

To be honest, I'm suggesting all this by guess, assuming that since the boot menu is presented by Grub, the process should be the same.

---

### Post by yanvolking on 2013-02-21
Hello [[COLOR=#C61919]**varunendra**[/COLOR]]("http://ubuntuforums.org/member.php?u=1043629"),

I did what you told me: I rebooted pressing the shift key.  It got me the grub menu.  But adding the "nomodeset" caption at the end of the kernel boot line did not solve the problem.  The next time round I went into recovery mode, then from the menu screen there booted normally.  I noticed then that the fonts of the splash screen were suddenly much smaller, and this time the boot process went right the way through to the X screen.  Not sure why that happened but the important thing is thaqt the problem is solved.

Thanks for the help.

---

### Post by varunendra on 2013-02-21
Glad it worked 'somehow'! ;)

> **yanvolking said:**
> I noticed then that the **fonts of the splash screen were suddenly much smaller**,..
Means higher resolution - further means the X somehow got configured correctly. That's better than nomodeset, because nomodeset lets you login in basic graphics mode - to circumvent graphics related issues.

As a side note, although not guaranteed, the nomodeset option almost always helps whenever there is 'graphics-only' problem. So am wondering if you added it correctly, or if there was some other issue as well.

To be precise, it has to be added without quotes *[COLOR="DarkSlateGray"](and in /etc/default/grub file, it has to be added 'between' the quotes in "GRUB_CMDLINE_LINUX_DEFAULT=" line. For example - **GRUB_CMDLINE_LINUX_DEFAULT="quiet [COLOR="Red"]nomodeset[/COLOR] splash"**)[/COLOR]*

Not that it matters now, but just in case you need it again. :)

---

### Post by rxattila on 2013-02-25
i havent reade any of the other ppls thingers.. but

backtrack5 allways boots to a blank screen

you must   type    startx        to start  BT5  GUI

---

