---
title: "No trackpad after wakeup from suspend"
date: 2008-12-09
forum: Apple Hardware Users
---

### Post by anando on 2008-12-09
Hi

I would be grateful for your advice regarding my macbook pro (1,1) running Intrepid Ibex and open source radeon driver (not fglrx).

It suspends and wakes up fine - but after it does, I can't use my trackpad anymore. 

- Anando.

---

### Post by Dareajoe on 2008-12-10
How do I set different mouse and trackpad speeds on Windows 2000 or XP laptop?I just got a wireless mouse for my laptop, and it is more sensitive than my trackpad. I went in to the Control Panel to lower the mouse pointer speed for the wireless mouse. This affected the trackpad, and now it is not sensitive enough. How can I configure these speeds separately?Thanks.

---

### Post by cyberdork33 on 2008-12-11
> **anando said:**
> It suspends and wakes up fine - but after it does, I can't use my trackpad anymore.
after you resume and it is not working, run 
```
sudo modprobe -r appletouch
```
then
```
sudo modprobe appletouch
``` and see if it works.

---

### Post by anando on 2008-12-11
Many thanks cyberdork - is there a way to make it happen automagically ? Perhaps a script or similar which gets executed after wake up from suspend ... just thinking aloud.

Cheers,
Anando.

> **cyberdork33 said:**
> after you resume and it is not working, run 
```
sudo modprobe -r appletouch
```
then
```
sudo modprobe appletouch
``` and see if it works.

---

### Post by anando on 2008-12-11
I poked around a bit and added 

```

modprobe -r appletouch
modprobe appletouch

```to /etc/acpi/resume.d/99-macbook-fix.sh

But that does not work for me. I'd be grateful for any advice.

Incidentally, after resume, my USB mouse works for me.

Cheers,
Anand.

> **anando said:**
> Many thanks cyberdork - is there a way to make it happen automagically ? Perhaps a script or similar which gets executed after wake up from suspend ... just thinking aloud.

Cheers,
Anando.

---

### Post by cyberdork33 on 2008-12-12
So I assume reloading the module worked?

You should be able to add modules that you want unloaded on suspend and reloaded on resume in /etc/default/acpi-support

---

### Post by anando on 2008-12-12
Hi cyberdork

> **cyberdork33 said:**
> So I assume reloading the module worked?

You should be able to add modules that you want unloaded on suspend and reloaded on resume in /etc/default/acpi-support

Yes, reloading the module worked like a charm. Sorry I should have mentioned it earlier.

So, if I add appletouch to STOP_SERVICES, it would work. Do I understand you correctly ?

Cheers,
Anando.

---

### Post by cyberdork33 on 2008-12-12
> **anando said:**
> So, if I add appletouch to STOP_SERVICES, it would work. Do I understand you correctly ?
It isn't a service, so no that wouldn't work.

I was referring to the "MODULES=" section, but from reading the top section of this file, it is depreciated now. I am not sure where to configure it.

---

### Post by ilsamos on 2008-12-15
I have the same problem, no solution yet?
Thanks

Andrea

---

### Post by anando on 2008-12-15
Andrea, 

Yeah - I am awaiting a tip from our more experienced friends as well ...

A temporary solution is: after you wake up from suspend, and presented with your desktop with no trackpad working, do the following:

* Press **[FONT=Courier New][COLOR=Purple]Alt+F2[/COLOR][/FONT]** - this will open the 'Run Application' dialogue box
* Type [COLOR=Purple]**[FONT=Courier New]xterm[/FONT]**[/COLOR] and press enter - this will open a terminal for you
* In the terminal, type (in succession): 
[B][FONT=Courier New][COLOR=Purple]   sudo modprobe -r appletouch 
   sudo modprobe appletouch[/COLOR][/FONT][/B]

[COLOR=Black]Now you should have your trackpad working again. 

This is a minor inconvenience - but one nevertheless. I wish there was an automatic way of modprobing appletouch upon wakeup - anyone ?

Cheers,
Anando.

 
[/COLOR]

---

### Post by cyberdork33 on 2008-12-15
> **anando said:**
> Andrea, 

Yeah - I am awaiting a tip from our more experienced friends as well ...

A temporary solution is: after you wake up from suspend, and presented with your desktop with no trackpad working, do the following:

* Press **[FONT=Courier New][COLOR=Purple]Alt+F2[/COLOR][/FONT]** - this will open the 'Run Application' dialogue box
* Type [COLOR=Purple]**[FONT=Courier New]xterm[/FONT]**[/COLOR] and press enter - this will open a terminal for you
* In the terminal, type (in succession): 
[B][FONT=Courier New][COLOR=Purple]   sudo modprobe -r appletouch 
   sudo modprobe appletouch[/COLOR][/FONT][/B]

[COLOR=Black]Now you should have your trackpad working again. 

This is a minor inconvenience - but one nevertheless. I wish there was an automatic way of modprobing appletouch upon wakeup - anyone ?

Cheers,
Anando.

 
[/COLOR]

Well, you should be able to add those commands to a script similar to what you tried before, but those scripts don't seems to be executed.

According to the acpi-support file, it sounds like gnome-power-manager should be handling this now, I would start looking for its documentation.

---

### Post by ilsamos on 2008-12-17
I think I have solved this problem! :guitar:

Maybe it's not exactly a smart solution but it works on my Macbook Santa Rosa 4,1 !

Just try to follow theese steps:

open the file /etc/default/acpi-support with your preferred editor:

**sudo gvim /etc/default/acpi-support**

find the line: 

*SUSPEND_METHODS="dbus-pm dbus-hal pm-utils"*

and replace with:

*SUSPEND_METHODS="pm-utils"*

save, then type:

[B]touch /etc/pm/sleep.d/99-macbook_fix
sudo chmod +x /etc/pm/sleep.d/99-macbook_fix
sudo gvim /etc/pm/sleep.d/99-macbook_fix[/B]

and write in it:

[I]#!/bin/sh

modprobe -r appletouch
modprobe appletouch[/I]

save, reboot (I don't know if it is really needed but I did) and try to hibernate and wake up your mac!

I must thank the author of this webpage who inspired me the solution:

[http://handyfloss.net/2008.11/hibernating-my-macbook-under-ubuntu-intrepid-ibex/](http://handyfloss.net/2008.11/hibernating-my-macbook-under-ubuntu-intrepid-ibex/)

Let me know if it works for you too!

Bye
Andrea :p

---

### Post by ilsamos on 2008-12-17
I suggest you to read the webpage I linked before, there's something strange (a bug) with acpi which may shorten hard drives lifetime..

Please excuse me for my bad English. :-?

---

### Post by anando on 2008-12-17
Hey Andrea - Awesome - I got this to work in 2 out of two suspend/wakeups so far. I will wait for a few more times before I mark this thread as SOLVED.

- Anand.





> **ilsamos said:**
> I think I have solved this problem! :guitar:
.....

Let me know if it works for you too!

Bye
Andrea :p

---

### Post by cyberdork33 on 2008-12-19
> **ilsamos said:**
> I suggest you to read the webpage I linked before, there's something strange (a bug) with acpi which may shorten hard drives lifetime..

Please excuse me for my bad English. :-?
This problem has been around for awhile and the function is disabled in Ubuntu by default because of it.

---

### Post by david_edmundson on 2008-12-25
I just rebuilt my kernel having replaced drivers/input/mouse/ appletouch.c with the file from the latest 2.6.28 kernel. It's had a load of changes. So far I've the mouse has restored from suspend perfectly every time.

---

### Post by cyberdork33 on 2008-12-28
> **david_edmundson said:**
> I just rebuilt my kernel having replaced drivers/input/mouse/ appletouch.c with the file from the latest 2.6.28 kernel. It's had a load of changes. So far I've the mouse has restored from suspend perfectly every time.

awesome, thanks!

---

### Post by tealio on 2009-01-23
The modprobe solution worked for me, but it doesn't seem to be reading xorg.conf when the trackpad comes back... so every time i suspend i end up with the default trackpad settings.

does anyone know how to make xorg.conf be reread without restarting X?

is there a way to make this happen via modprobe?

[COLOR="Red"]EDIT[/COLOR]: OK so this problem only happens when i run the commands from a terminal... when i suspend, for some reason it restores the mouse settings...

---

