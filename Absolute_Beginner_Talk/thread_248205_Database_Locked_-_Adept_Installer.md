---
title: "Database Locked - Adept Installer"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Network Nurd on 2006-08-31
First I'd like to apologize for the simple question.  I'm sure it's come up somewhere in the forums before but I cannot seem to find it anywhere (a solution that works for me that is.)

I'm using Kubuntu 6.06 - while trying to run the add/remove programs application I get a Database Locked - Adept Installer window.  Apparently I have another program open that is using this resource.

I've gone through my process table and cannot find any apt-get, adept, aptitude or any other program that I can see that is running that might cause this (of course most of the processes running look Greek to me.

What can I do to resolve this?

Thanks!

---

### Post by BatteryCell on 2006-08-31
Close any apps that you know you have opened (like adept) then just run this:
```
dpkg --configure -a
```
in the terminal.

Adept commonly crashes and then the Database is locked...

---

### Post by Network Nurd on 2006-08-31
Unfortunately that does not work.  I think I've read that in another post and tried it w/o success.

---

### Post by SkyNet2029 on 2006-09-01
You could try running 'top' in a terminal/Konsole and checking to see if the 'update-notifier' is running. That would cause a 'process locked' error too, although it's not listed as adept it still uses the same process as adept/apt-get/aptitude.
Conversely you could always just run 
```
$sudo killall update-notifier adept aptitude 
```
in Konsole/terminal just to make certain the process is indeed not running, then try the add/remove.
It was my understanding that the 'dpkg --configure -a' was just to continue a sub/process that was terminated prematurely, as it should just barf up the same error output (sub-process dpkg locked by another process)as before, since you would just be attempting to access a locked database by way of another application.

---

### Post by Network Nurd on 2006-09-03
Hi Sky, thanks for the info.  This is what I get 

```
dan@dan-desktop:~$ sudo killall update-notifier adpet aptitude
Password:
update-notifier: no process killed
adpet: no process killed
aptitude: no process killed
dan@dan-desktop:~$
dan@dan-desktop:~$

```

I've rebooted the machine and it still won't allow me to download anything from the package manager.  I assumed it was because of automatic updates but I killed that process in the "task bar" and told it not to run at startup.  I'm at a loss here.

---

### Post by luv2craftca on 2006-09-03
I don't know how to fix your problem, but noticed a type-o in your post of your terminal output....  It says 'adpet' instead of 'adept' so is it possible that adept may be running still?

---

### Post by Network Nurd on 2006-09-03
> **luv2craftca said:**
> I don't know how to fix your problem, but noticed a type-o in your post of your terminal output....  It says 'adpet' instead of 'adept' so is it possible that adept may be running still?

Ahh good eye!!  I fixed it and still nothing.  It's becoming quite frustrating! :(

---

### Post by xpod on 2006-09-03
I too had the exact same prob as you last night on our Kubunto machine.
Even whan i rebooted i got the same stuff.

If i tried to just start adept i got a box telling me it was in "read only mode" and i would not be allowed to change or modify any packages with
adept,aptitude or indeed apt-get..

Mine began when removing unused games and other apps.I`d remove 3 at a time then after two lots the 3rd lot just stuck on 90ish%.

I ended up killing it and trying again to remove the apps in question but thats when all the hassle began....

I had done ...$sudo killall update-notifier adept aptitude  many times all to no avail....
And i tried a lot of other stuff i seen out there but still no joy...

In the end........reinstalled cause it was bloody easier PLUS i wanted to try something anyway so it was`nt a prob really..

Good luck though..

---

### Post by SkyNet2029 on 2006-09-03
O.k... what about the output of:

```
$sudo ps -e
```

from konsole? This should list every running process, although it is kind of strange that you would need to do things this way after a reboot.
maybe even posting the output of that or previous from 'top' would help.

---

### Post by leefw on 2006-09-04
> **BatteryCell said:**
> Close any apps that you know you have opened (like adept) then just run this:
```
dpkg --configure -a
```
in the terminal.

Adept commonly crashes and then the Database is locked...

I was having the exact same problem. This worked for me... however, notice two dashes before configure. Didn't see that at first... ](*,) 

I ran the command, some process started (I thought this was the update at first), then after that I started adept - no trouble! Problem solved.

---

### Post by pyman on 2006-09-22
Thanks!
I was just about to re-install Ubuntu when I found this.
dpkg --configure -a
You saved another NOOB...:D

---

### Post by ososxe on 2006-09-25
Thanks! it worked for me also!! In my case, it was the installation of the flashplugin that crashed it, i forgot i had to cancel it (is on a machine i don't use much) so it seems that when i cancelled it it did not freed the process, even after many reboots.
Again, thanks a lot!!

---

### Post by Mithrilhall on 2006-10-16
Thanks....

> 
dpkg --configure -a



This worked perfectly for me.

---

### Post by Petrol-ORD on 2007-09-06
> **Network Nurd said:**
> Unfortunately that does not work.  I think I've read that in another post and tried it w/o success.
In the event any other users are encountering this same problem, this worked for me, but as a newb, I had to try a few times.  If you're as new to the command line as I am, here's how it worked for me.

Open 'Konsole'
type: *sudo dpkg --configure -a*
 This will generate a password prompt which will allow the execution of the command.  If you just tried '*dpkg --configure -a*' without the '*sudo*' preceding it, you'll see no change since you're not logged in as Root (super-user).

Thanks all for the help (nevermind the help is a year old)

cheers,
petrol

---

