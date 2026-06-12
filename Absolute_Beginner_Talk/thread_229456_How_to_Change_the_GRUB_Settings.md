---
title: "How to Change the GRUB Settings"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by deepank on 2006-08-04
I have a dual boot system with ubuntu as the primary option by default. The GRUB Bootloader has a timeout of about 10 seconds. I want to ask how can I change the timeout settings in the GRUB. Can I also change the default option. Also is there any theme or color scheme available for GRUB so as to make it look a bit better?

---

### Post by ciscosurfer on 2006-08-04
First copy your orginal /boot/grub/menu.lst file so you can revert to it if something goes wrong. Copy and paste into a terminal these instructions:```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
``` Then edit your menu.lst file```
sudo gedit /boot/grub/menu.lst
```To change the default boot option (and they refer to how they are ordered in your file, simply change the line that says **default 0** to **default 4** perhaps if that's where another kernel or OS is located.

Likewise, you can change the timeout to any other number including 0 for no timeout.   So to change the timeout to 20 seconds, you would change the line that reads **timeout 10** to **timeout 20**.

You can change the colors of your menu by altering the line that says color.  First, uncomment the line that begins **#color cyan/blue white/blue** by *removing* the pound sign in front of it.  You can experiment with these colors, keeping in mind there are a limited set of color options that GRUB will accept.  Do a search on the web for 'changing grub color'.
Hope this helps.

---

### Post by Tomosaur on 2006-08-04
Check the link in my sig. :)

</self promotion> :P

---

### Post by ciscosurfer on 2006-08-04
@Tomosaur

Very nice script.  If only someone could write a safe reboot straight to OS function...

---

### Post by Tomosaur on 2006-08-04
Indeed. I'm looking into it myself - it can definately be done but it's just finding the best way to do it. I fear that implementing it would mean re-writing some of the other functions to accomodate it - something which I want to try and avoid (because I'm lazy :P )

---

