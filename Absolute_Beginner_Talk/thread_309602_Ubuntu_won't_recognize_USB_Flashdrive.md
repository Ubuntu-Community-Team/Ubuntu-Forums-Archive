---
title: "Ubuntu won't recognize USB Flashdrive"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by xopodox on 2006-11-29
Everything else seems to be working properly, except for the fact that ubuntu will no longer recognize my flash drive...

Here is the chain of events:
1. Flash Drive works with Live CD booted
2. Flash Drive works with OS installed
3. Flash Drive left in computer, computer is restarted and will not boot (trying to boot from Flash Drive?).  Flash Drive removed, computer restarted and things work again.
But...
4. There are 6 USB ports on my computer, 2 in front and 4 in back.  2 of the ports in the back are occupied by a printer and a modem, which continue to function properly.  
5. Flash drive was originally plugged into one on the front.  Computer now will not recognize it at that location.  When plugged into a port on the back it worked again.
6. Flash Drive ejected from desktop, then removed.
7. Now will not recognize at any ports.

Is there a way to make the computer search for the flash drive? Refreshing the "Computer location" doesn't work.

Also, drive is of somewhat questionable quality, but it was working earlier and has worked with windows computers I've used it with.

Any ideas on how I should try to fix this?  Thank you for your help.

---

### Post by lhtown on 2006-11-29
Welcome to Ubuntu. We hope you enjoy it.

I seem to recall having a similar problem when I was running the Dapper Drake version. I think there was a file that didn't get deleted for some reason (I think it had permissions set so that only root could delete it.)

Take the usb drive out and reboot and check to see if there is a folder under the /media folder (or directory if you prefer to call it that) that appears to be your USB drive. If there is, you might try deleting it.

If you can't delete it because you don't have permission, you can open up a terminal and type 'sudo nautilus' and then press enter and then enter your password and press enter again. After that, Nautilus, the file manager will open up and you will have permission to delete anything on your computer and destroy your system if you aren't careful! You should be able to delete the offending file with no problem.

As I recall, I only had the problem once.  I don't know what caused it. I think I did reformat my usb drive, but I don't know if that helped or not.

Happy Ubuntuing

---

