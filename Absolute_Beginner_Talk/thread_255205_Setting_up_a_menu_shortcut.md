---
title: "Setting up a menu shortcut"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by ron999 on 2006-09-11
Hi
I've installed Epson printer utilities programs mtink and mtink-doc.
I run mtink from the terminal by entering sudo mtink then entering my password.
It's an executable file in usr>bin folder.
If I set up a shortcut in my Applications>System Tools menu then mtink will open up but will not allow me to use it - message says "Error No access to printer device file".
I suppose that I'm not being given access without the password.
Is there a simple way for me to make a menu shortcut for mtink? - one that works.

PS I'm using Ubuntu 6.06 Dapper Drake

---

### Post by BoneKracker on 2006-09-11
In the menu item you created, try putting "gksu" at the beginning of the command.  This is like saying "sudo" in the terminal.  When you run the menu item, you will be asked for your password.

---

### Post by ron999 on 2006-09-11
Hi boneKracker
No, it doesn't work.
It says:- Could not launch menu item. Details:Failed to execute child process "gksu/usr/bin/mtlink"(No such directory)

---

### Post by Najand on 2006-09-11
> Hi boneKracker
No, it doesn't work.
It says:- Could not launch menu item. Details:Failed to execute child process "[COLOR="Red"]gksu/usr/bin/mtlink[/COLOR]"(No such directory)
Reply With Quote
You have forgotten the space between gksudo and /usr/bin/mtlink
```
gksudo /usr/bin/mtlink
```

---

### Post by ron999 on 2006-09-11
No Najand, when I use that command in the shortcut it doesn't open up at all, nothing happens.

---

### Post by Najand on 2006-09-11
check the command in terminal and write down the error messages.
```
gksudo /usr/bin/mtlink
```

---

### Post by ron999 on 2006-09-11
Najand
I don't get any error messages at all when I have gksudo /usr/bin/mtink
as the command in the shortcut.
Sometimes it asks me for my password and then it does nothing.
(btw it's mtink, not mtlink)

---

### Post by ron999 on 2006-09-12
Hi
Has anybody got a method for this shortcut please?

---

### Post by Najand on 2006-09-12
> **ron999 said:**
> Hi
Has anybody got a method for this shortcut please?

hmm, when you execute mtink in terminal, do you use sudo or you just execute it there?

---

### Post by crossedout on 2006-09-12
Does mtink work properly when you use it from terminal?  It sounds like its some sort of syntax issue with the shortcut rather than a problem with the software.  If it does work properly from terminal, what exactly are you typing at the prompt?

-Xout

---

### Post by danellisuk on 2007-01-27
I have the same problem (on edgy eft).  Mtink starts okay from the command line (when using sudo).  I have managed to get it to start from the menu but only by using "sudo mtink" (without the quotes) and checking "Run the command in a terminal".  Which is not perfect but will do for me.

Using "gksu mtink" as the command does not work.  There is no error, nothing.

When running "gksu mtink" or "gksudo mtink" from the command line it returns the following error after prompting for your password:-

***************************************************
daniel@edgy-desktop:~$ gksudo mtink
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: Can't open display: :0.0
***************************************************

I have a feeling that this is due to the way mtink works.  But I really dont know much about this yet.

Regards,
Dan.

---

