---
title: "How to edit /boot/grub/menu.lst"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by rdav@usa.com on 2006-02-09
I have been able to change the permissions for /boot/grub/menu.lst to -rwxrwxrwx.  Curiously, the filename (menu.lst) is in green.  What does the green color indicate?

I can now edit the file with Text Editor, but when I try to save it I get the error message:  "Could not save the file "/boot/grub/menu/lst"

This is driving me crazy.

Can anyone figure this out?

---

### Post by CookieOrc on 2006-02-09
what i do to edit the list is go into the terminal and type this
cd /
cd boot
cd grub
sudo gedit (for gnome) menu.lst
it will ask you for a password and open the program for you.

---

### Post by Kiwinote on 2006-02-09
try this
```
sudo gedit /boot/grub/menu.lst
```

Kiwinote

//EDIT Must have been typing this at the same time as CookieOrc, both ways do the same thing.

---

### Post by abhishekp on 2006-02-09
Hi rdav even i had the same problem before. Goto terminal window and type
sudo gedit /boot/grub/menu.lst and when you press enter you will be prompted for password, enter your current password and now you can edit and save the file.

---

### Post by abhishekp on 2006-02-09
wow what fast replies. Before I finished typing there were so many replies.

---

### Post by rdav@usa.com on 2006-02-09
Thanks!

That seems to have worked, because I was able to save the file and my change was still there after I ran the editor the second time.

There was a curious message, however:

  " (gedit:11947: GnomeUI-WARNING **: While connection to session manager:  Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."

What does that mean?

---

### Post by CookieOrc on 2006-02-09
[QUOTE=rdav@usa.com]
  " (gedit:11947: GnomeUI-WARNING **: While connection to session manager:  Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."
[/QUOTE]

Sounds like a password problem or do you have multiple desktop managers? Like gnome and KDE?

---

### Post by rdav@usa.com on 2006-02-09
HOORAY!

I not only edited menu.lst, but now my default boot is into Windows XP, which is exactly what I have been spending the last day trying to accomplish!

I have to say, however, that I find it has been an insidiously arcane and unforgiving process just to edit a file.  I don't even think a billion monkeys typing at random could do it in less than a trillion years.

Thanks to all the help I have recieved from this forum.  I was ready to give up.

I'm still curious about the implications of the message I received, however.  Does anyone know what it means?

tia

Robert
Mill Valley, California

---

### Post by christhemonkey on 2006-02-09
Did you run it from a root terminal perchance?
Because everything i run in a root terminal gives me these GnomeUI-Warnings.

---

### Post by rdav@usa.com on 2006-02-09
I am using the latest ubuntu, which seems to have a version of gnome.  I opened the terminal window, switched to su mode, changed to the grub directory, and used gedit to change menu.lst.  

When I saved the changed file, that's when I received the error message: 

" (gedit:11947: GnomeUI-WARNING **: While connection to session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."

If authentication failed, why was my change successful?

---

### Post by rdav@usa.com on 2006-02-09
Yes.  Apparently, we are both experiencing the same problem (assuming it is some kind of a problem).

Thanks.

---

### Post by Kiwinote on 2006-02-09
Try this rather than su, do you still get that message?
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Klaidas on 2006-02-09
Just a suggestion: make a backup of your menu.lst - you never know what might happen :)

---

### Post by lha on 2006-02-09
Hi [email]rdav@usa.com[/email],

You should make menu.lst writable only for root. When you made its permissions '-rwxrwxrwx', everybody on your system has read and write access to that file. Even if you are on a one-user system, it's good to have as little power to screw up your computer. Besides, menu.lst isn't a binary file or a script, so it shouldn't be executable. (That's the meaning of x in those permissions.) You can set menu.lst's permission to what they used to be with
```
sudo chmod 644 /boot/grub/menu.lst
```
and if you need to edit it again, use
```
sudo gedit /boot/grub/menu.lst
``` as mentioned in previous posts in this thread.

---

### Post by Michael Steinberg on 2006-02-09
[QUOTE=rdav@usa.com]Yes.  Apparently, we are both experiencing the same problem (assuming it is some kind of a problem).

[/QUOTE]

I don't think it's a problem, it's a reaction to using sudo to access a GNOME program rather than gksudo. But no harm ever seems to come of it; it's just GNOME being splenetic.

---

