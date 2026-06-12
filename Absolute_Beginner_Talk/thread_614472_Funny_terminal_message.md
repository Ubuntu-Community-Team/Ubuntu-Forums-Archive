---
title: "Funny terminal message"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by scrimple101 on 2007-11-16
After synchronism of the time in the gnomebar on the desktop when i try to now install some thing knew i get this: 

robert@robert-desktop:~$ sudo apt-get install banshee
sudo: timestamp too far in the future: Nov 17 00:37:48 2007
robert@robert-desktop:~$ 

Does anyone know what's going on? And/or fix this?

Regards, Rob

---

### Post by matthewcraig on 2007-11-16
Set your time, or try another source.  Most likely it will work later.  You're out of sync with the server.

---

### Post by zabien1970 on 2007-11-16
Today is Nov. 16

---

### Post by scrimple101 on 2007-11-16
Thanks for your replys, i have Friday, November 16 2007 on the gnomebar but in the terminal it has  this readout:
robert@robert-desktop:~$ sudo apt-get install banshee
sudo: timestamp too far in the future: Nov 17 00:37:48 2007
robert@robert-desktop:~$ 

do i need to restart to reset the time i changed servers but thins didn't change anything

Regards, Rob

---

### Post by jordanmthomas on 2007-11-16
The time on your computer has changed.  This has nothing to do with certain servers.  Does
```
date
``` give you a time BEFORE the one sudo is complaining about?

If so, you have two options:  wait until Nov 17 00:37:48 2007
or
set your time to be later than that.

---

### Post by scrimple101 on 2007-11-16
This is the read out for the date code:

robert@robert-desktop:~$ date
Fri Nov 16 17:32:15 EST 2007
robert@robert-desktop:~$ sudo apt-get install banshee
sudo: timestamp too far in the future: Nov 17 00:37:48 2007
robert@robert-desktop:~$ 

 How did this happen? it was working fine before i sychronised the time.
how do i set the time in the terminal?
Regards, Rob

---

### Post by yabbadabbadont on 2007-11-16
```
man sudo
```
I don't have sudo on my system currently, or I would find the name of the file for you.  There is a timestamp file associated with your user somewhere (I think in your home directory) that you can delete in order to correct this issue.

Edit: In the terminal window, what is the output when your run ```
ls -la
```

---

### Post by jordanmthomas on 2007-11-16
What happened is this:  at some point in time your computer thought it was Nov. 17, and you used sudo during this time.  Now, for security reasons, sudo keeps track of when it is used.  Now you've fixed the time and sudo is like, "hey, how can he be trying to use me in the PAST??" and it will not let you use sudo.

The only way I know to fix it is to set your time aside from waiting is this:
1.  set the time to the future using the clock in your panel
2.  run this in a terminal to clear sudo's timestamp
```
 sudo -k
```
3.  set time back to what it is supposed to be.

---

### Post by jordanmthomas on 2007-11-16
> **yabbadabbadont said:**
> ```
man sudo
```
I don't have sudo on my system currently, or I would find the name of the file for you.  There is a timestamp file associated with your user somewhere (I think in your home directory) that you can delete in order to correct this issue.

This file is /var/run/yourusername

Unfortunately, you can't really remove it without root access or a working sudo.  :)

---

### Post by yabbadabbadont on 2007-11-16
> **jordanmthomas said:**
> This file is /var/run/yourusername

Unfortunately, you can't really remove it without root access or a working sudo.  :)

Reboot.  Take the failsafe option.  Run "sudo -k".  Reboot.  All done.  :D

---

### Post by jordanmthomas on 2007-11-16
Oh yeah, I forgot that Ubuntu will let you log on as root like that.
(IMHO a bad idea, but whatever)

However, would sudo -k as root not just clear root's sudo file?

So, scrimple, now you have a couple of choices...that essentially do the same thing.

---

### Post by yabbadabbadont on 2007-11-16
> **jordanmthomas said:**
> However, would sudo -k as root not just clear root's sudo file?

Then he can cd into /var/run and find the file and rm it manually.  ;)

(By the way, no box is secure if someone has physical access to it... :D)

---

### Post by jordanmthomas on 2007-11-16
> **yabbadabbadont said:**
> 
(By the way, no box is secure if someone has physical access to it... :D)

I know, but why make it easier?  

And yeah, using rm should work too.

edit :  sorry for going off topic.  :)

---

### Post by scrimple101 on 2007-11-16
Thanks for all your help everything is rosy tea now thank again 
Regards, Rob

---

