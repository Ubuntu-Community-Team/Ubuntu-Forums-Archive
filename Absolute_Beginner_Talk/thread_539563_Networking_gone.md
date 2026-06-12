---
title: "Networking gone"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by owenb@theofficenet.com on 2007-08-31
While making several attempts to get the dialup on my Tecra 8000 working I did something that screwed up the Networking process.
This is what now happens.  I start with the System icon, then choose "Adminstration" then "Networking".
the bottom menu bar then shows, "Starting  Adminstrative Application.  Then the screen reverts to a empty desktop.
  How do I get the graphical menu  for "Networking" back again.  I still need to get my dialup figured/installed.
Thanks, 
             Owen

---

### Post by schorsch on 2007-08-31
Are you still member of the "admin" group? Please open e terminal window, type "id" in it and post the output here.

---

### Post by owenb@theofficenet.com on 2007-09-01
> **schorsch said:**
> Are you still member of the "admin" group? Please open e terminal window, type "id" in it and post the output here.

uid=1000 (owenb)  gid=1000 (owenb)  groups=4 (adm) ,28 (dialout) , 24 (cdrom) ,25(floppy) ,29(audio) , 30(dip) ,44(vidio) ,46(plugdev) , 106(lpadmin) ,110(scanner) ,112(admin) ,1000 (owenb)
owenb@(none) :-$

This is what I think appears on the screen.  The very last line was questionable.
I don't think I am a member of the "admin" group. If I am, it is the result of more of my bumbling.
Owen

---

### Post by schorsch on 2007-09-01
O.K. you are a member of the admin group (112). As probably being the person who installed the OS you are member of the admin group per default but sometimes users kick themselves out of this group which can cause any kind of trouble.
Please type in terminal window
```
gksudo network-admin
```
and post the output here ... if there is any output in the terminal ...

---

### Post by owenb@theofficenet.com on 2007-09-01
> **schorsch said:**
> O.K. you are a member of the admin group (112). As probably being the person who installed the OS you are member of the admin group per default but sometimes users kick themselves out of this group which can cause any kind of trouble.
Please type in terminal window
```
gksudo network-admin
```
and post the output here ... if there is any output in the terminal ...

sudo:  unable to lookup  (none) via gethostbyname()

---

### Post by schorsch on 2007-09-01
Well, you have to assign a hostname to your computer first. You can do this by typing
```
sudo hostname *owenb*
```
in a terminal. Substitute *owenb* with a hostname of your choice. After that try again with
```
gksudo network-admin
``` and if that works please give this name again on the "General" Tab as you have only set the hostname for the moment.

---

### Post by owenb@theofficenet.com on 2007-09-01
I did change from "owenb" to 'beriault"
In a terminal I entered "gksudo (network-admin)"

which responded with:
"sudo: unable to lookup (none)  via gethost by name ()"

---

### Post by schorsch on 2007-09-01
Another idea:
```
gksudo gedit /etc/hostname
```
enter "beriault" without the quotes and save. Make no new line after the name!
```
gksudo gedit /etc/hosts
```
and check if there is a line starting with 127.0.0.1. It should look like this in your case:
```
127.0.0.1 beriault localhost
``` Change it if it does not look like this.
Try again with
```
gksudo network-admin
```

---

### Post by owenb@theofficenet.com on 2007-09-01
I tried both code lines and got the same response, ""sudo: unable to lookup (none) via gethost by name ()

Maybe I am going about accessing the terminal wrong.   I proceed  with "Applications >Accessories>Terminal.  This brings up a menu with a title bar of "owenb@(none):~".
The curser is preceeded with :
owenb@(none):~$.

Did I mess up so badly that I should reinstall?
I feel bad about using so much of your time trying to help me straighten out my screw up.
Owen

---

### Post by schorsch on 2007-09-01
If you have edited both files as I suggested you should reboot ... sorry, I forgot to mention. There won't be a reinstall necessary, this is not Wi......
After the reboot open up a terminal window again and the line at front should look like:
```
owenb@beriault:~$
```
Then try again with
```
gksudo network-admin
```

The trick is to get the error messages from graphical apps. When they are started via a menu or an icon the error messages are hidden somewhere whereas when started via a terminal they will be shown in the terminal window.

... and do not feel bad ... We were all beginners once upon a time and I learned a lot about Ubuntu with this forum .... perhaps in a few months when you got used to it you will help others, too! That's community ... :-)

---

### Post by owenb@theofficenet.com on 2007-09-01
I have tired suggestions in your last post.  Sadly nothing worked.  The respose to the commands have been the same as previously.  Such as"

owenb@(none):~$ gksudo   network-admin
sudo:  unable to lookup  (none) via get host by name()

I question the inclusion of (none) in my name.  My sign on for my dialup provieder is [email]owenb@xxxxxxxxxxx.com[/email]
I have no idea where the (none) comes from.  I know in earlier setups the command line merely had the owenb .  Could the (none) be causing the problem?
Owen

---

### Post by schorsch on 2007-09-02
Instead of "(none)" there should be the name of your computer. Your sign in at your provider does not matter at the moment. Please post the output of
```
cat /etc/hostname
cat /etc/hosts
```
Have you alreadyrebooted as I wrote in my last post?

---

