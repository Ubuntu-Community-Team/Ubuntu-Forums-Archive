---
title: "Can not login after change"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Hnurre on 2008-01-22
Succesfully installed 7.10 on Dell D600 and was very happy! :)
For some reason I wanted to try dual screens. So I did something in administration>screens and then logged off. Now the screen is distorted and I can't log back on.:(
How do I revert to last working setup from recovery? (I am at the terminal prompt.)
Thnks in advance!

---

### Post by user1397 on 2008-01-22
what do you see at the prompt? do you see your **username@your computer's name**?  or do you see a **root**? or what?

---

### Post by Hnurre on 2008-01-22
root@dell-d600

[and that is my comps name]

---

### Post by user1397 on 2008-01-22
> **Hnurre said:**
> root@dell-d600

[and that is my comps name]then its pretty simple, just type ```
reboot
``` and it'll reboot and hopefully you'll be taken to your login screen; if not, just post here again

---

### Post by Hnurre on 2008-01-22
It rebooted ok - but I am back to a screen that is unreadable.
The screen is black with some letters scattered here and there - absolutely no login screen.
As I said, I changed something in the admin/screens setup and then was prompted to log off for the changes to take effect. It was then it started! No proper login screen etc.
I guess that I need to find the Ubuntu equivalent of "last working profile" or something?
I have found out how to boot into recovery - but then?

---

### Post by philinux on 2008-01-22
Go into recovery mode and use this 

[FONT="Times New Roman"]ls -l /etc/X11[/FONT]
This will list the contents of the X11 directory and show the date time etc.

Make sure of the capital X

Look for files xorg.conf and xorg.conf~

the one with the ~ could be the backup. Check the date/time stamp.

If it is then

cp /etc/X11/xorg.conf~ /etcX11/xorg.conf

This will restore the graphics/other config file.

---

### Post by Hnurre on 2008-01-22
I have 4 xorg:

xorg.conf
xorg.conf.1
xorg.conf.failsafe
xorg.conf.failsafe.bak

I don't know how to check the date/time stamp though. It doesn't show. I guess I should delete or change name of one of them?

---

### Post by Hnurre on 2008-01-22
sorry!
messed up the "1" and "l" I now see the time stamp. Should I change name of one of them?

---

### Post by philinux on 2008-01-22
xorg.conf is the latest which one is next the ls -l gives the time stamp.

All you have to do then is use the cp (copy) command i showed you above with the correct file.

---

### Post by Hnurre on 2008-01-22
Thanks to you guys I found the conf file and copied the backup xorg.conf.1 over the new one that I had messed up.
Thanks again! :)

---

### Post by philinux on 2008-01-22
Glad that was sorted.

---

