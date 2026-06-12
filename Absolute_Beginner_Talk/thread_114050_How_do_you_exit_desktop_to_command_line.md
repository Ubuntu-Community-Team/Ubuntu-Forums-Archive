---
title: "How do you exit desktop to command line"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by Jubal on 2006-01-07
I know it is probably something very basic and easy, but after wasting the last 45min trying to find the answer I still have no idea.

---

### Post by Zelut on 2006-01-07
Are you looking for the Terminal?  Applications > Accessories > Terminal ? (gnome)  This is where you'd run your command-line stuff..

---

### Post by Jubal on 2006-01-07
I am trying to update a driver here is the error message I get

Please be sure you have exited X
         before attempting to upgrade your driver.  If you have exited X, know
         that your kernel supports module unloading, and still receive this
         message, then an error may have occured that has corrupted the NVIDIA
         kernel module's usage count; the simplest remedy is to reboot your
         computer.

So I need to exit X and run command

---

### Post by bluevoodoo1 on 2006-01-07
try ctrl+alt+f2 (that works for me... ) 

also see [http://ubuntuforums.org/showthread.php?t=108303](http://ubuntuforums.org/showthread.php?t=108303)

(EDIT= added link)

---

### Post by sjh on 2006-01-07
[QUOTE=bluevoodoo1]try ctrl+alt+f2[/QUOTE]

If I remember correctly, this will stop Gnome but you need to sign in from here and

```
sudo /etc/init.d/gdm stop
```

to stop the X server.

Hope this helps
SJH

---

### Post by GreyFox503 on 2006-01-07
And to get back to your graphical desktop, press Ctrl + Alt + F7.  If the screen looks black and nothing shows up, then go back the the terminal and run 'startx'.

---

### Post by Jubal on 2006-01-07
Yes that worked thank you

---

