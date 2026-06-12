---
title: "lockups - how I might identify them or fix the problem"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Algus on 2008-02-05
I've had two lockups so far, once yesterday when I was running 7.04.  I was running Firefox and Pidgin and had a couple browser windows open.  The system hard locked on me and I had to shut down completely.  

Later, after I had updated to 7.10 and got all the relevant patches, my system slowed to a crawl when I was running Pidgin and Firefox.  I could still move my mouse cursor but basically nothing worked, the system was completely unresponsive so I ended up having to power down.  

If I were in XP or whatever, I'd try to pull up the Task Manager to see if I could force unresponsive programs to terminate or some such, or at least be able to monitor my CPU activity.  In both cases when this happened my cooling fans were running so if I could say anything happened, I'd say the CPU got clogged up (yeah, I dunno that much about hardware so if this sounds dumb then...well it's because I'm a noob in a lot of respects) 

Is there anything comparable I can try in Ubuntu? Or at least anyway I can figure out what might have happened after I reboot?  Both times this happened I'd say I had my machine on for less then an hour whereas just now before making this thread I spent about an hour and a half using OpenOffice to type up an assignment for one of my classes tommorow and everything worked perfectly.  

My specs: 

Sony VAIO PCG-K23 
Pentium 4 2.80 ghz
512 MB RAM (PC2100) 
60 GB HDD (4200 RPM) 
ATI Radeon 345 IGP 

I was speculating that Ubuntu might not be able to manage my fans as well as Windows does.  It's a notebook and thanks to that Pentium 4 it gets pretty hot (the earlier models in the K series were well known for overheating).  Is this a likely issue? I'd hate to have to stop using Ubuntu on this machine but if it can't manage my hardware properly...

---

### Post by Joeb454 on 2008-02-05
Do you have the Compiz effects enabled? This may be the cause of some of the lock-ups?

It should be in System>Preferences>Appearance and then make sure "None" is the option that is checked :)

---

### Post by kpkeerthi on 2008-02-05
I'm just guessing here. Are you running ATi binary driver? May be switch to "vesa" driver and see if that improves anything else.

---

### Post by jan quark on 2008-02-05
I have encountered lock ups--- but this is a wild guess--- using xchat and the touch pad

since I  switch the IRC client and plugged in an usb mouse it seems the system is stable

just another food for thought

---

### Post by Algus on 2008-02-05
I do not have the Compiz effect on.  I will see about getting that driver you mentioned kpkeerthi 

jan quark - I CAN use a USB mouse when I'm at home (I have a few extras) but not being able to use the touchpad would be...unfortunate...when I'm in class.

---

### Post by bomanizer on 2008-02-05
try dmesg, or look at var/log/messages for recent entrys after a lockup.

My 2cent.

---

### Post by mrthundercleese4 on 2008-02-05
I had the same problem and attributed it to gnash which is open source flash (horrible)

in the terminal 
"sudo aptitude purge gnash"

then to install adobe flash type
"sudo apt-get install ubuntu-restricted-extras"

there are other messenger programs also, pidgin does seem like it likes to lock up quite a bit.

---

### Post by kpkeerthi on 2008-02-05
Locate a section that looks like
```

Section "Device"
   Identifier "Generic Video Card" 
   Driver "fglrx"
   BusID "PCI:1:0:0"

```
in /etc/X11/xorg.conf and change the line ```
   Driver "fglrx"
``` to ```
   Driver "vesa"
```

Save and Exit and Reboot.

---

### Post by Algus on 2008-02-05
I wouldn't mind if it was just Pidgin that locked up.  The trouble is it got my whole system :P I really don't care what messenger program I use, I only bother with an AIM account anyway since that's what all my friends use.  

Anyway, I switched my video driver.  Screen's displaying properly so far.  I suppose I should run Pidgin right now and see if it locks on me.  It seems like both times this happened I had both Firefox and Pidgin running.

---

### Post by jan quark on 2008-02-05
also you can try a light weighed web browser like 
kazehakase

it can be found via synaptic and I use it and can recommend 
I switched from firefox :)

---

### Post by emarkd on 2008-02-05
> **mrthundercleese4 said:**
> I had the same problem and attributed it to gnash which is open source flash (horrible)

in the terminal 
"sudo aptitude purge gnash"

then to install adobe flash type
"sudo apt-get install ubuntu-restricted-extras"


I second this statement.  Firefox with Gnash is very unstable, but Firefox with Flash is much better behaved.

If it happens again and you're about to have to reboot, try to get to one of your virtual text terminals by pressing <ctrl><alt>F1, <ctrl><alt>F2, etc.  There you can log in and run
```
top
```
to see what's taking up your processes.  You can run that from the Terminal, too, if you just want to see how it works.  The left-most column is the PID (program ID) for the process.  If you find that a process is taking 100% CPU or RAM, you can hit 'q' to quit top, then run

```
kill whateverPID
```

Then run top again and see if it's gone.  If it's not, you have to tell Linux to get serious about it and really kill that process, which you do by running

```
kill -9 whateverPID
```

Then, if things look good in top, you can try and get back to your GUI by pressing <ctrl><alt>F7

Hope this helps.

---

### Post by Algus on 2008-02-05
ubuntu is literally the first Linux OS I've ever used so I'm a pretty big n00b.  I'm still a little uncomfortable with the terminal (the closest I've used is MS-DOS...for playing old computer games ;p) 

Anyway, I did what mrthundercleese4 suggested.  I wouldn't be opposed to switching from Firefox but there are a few websites I visit that I have custom extensions for and I really couldn't live without them.  Though I suppose if I had to in order to run Ubuntu...actually I'd probably just end up spending most of my time browsing in XP if that were the case.  

kpkeerthi - this is what I have in that section

Section "Device"
	Identifier	"ATI Technologies Inc Radeon IGP 330M/340M/350M"
	Driver		"ati"
	BusID		"PCI:1:5:0"

It won't actually let me change anything in that file.  Pardon my, erm, ignorance but is this something that I need to do from the terminal with root access? 

Anyway, thanks to everyone for offering advice so far.  Especially the top command emarkd, that's exactly what I was looking for how to do.  I appreciate it.

---

### Post by emarkd on 2008-02-05
You're welcome.  If Firefox was your problem, it was probably related to gnash and maybe you've solved it.  And yes, editing xorg.conf must be done using sudo or gksu, but DON"T DO IT unless you really have to. If you do decide to muck around in there MAKE A BACKUP!

---

### Post by Algus on 2008-02-05
Humm.  It just happened to me again.  I was running perfectly for a good hour and a half with both Pidgin and Firefox open.  Firefox ended up crashing and when I reloaded it the font was messed up.  I think the default font changed, but I can't be sure...it just looks different.  

Anyway, I rebooted the system and not five minutes after I'd opened Firefox back up everything slowed to a crawl and the menus were very unresponsive.

---

### Post by Algus on 2008-02-05
Alright, I have some more time to play now.  I am almost 100% sure that if the problem isn't with Firefox then it's with hardware, but again I'm not sure.  Next time my system locks or crashes I'll see if I can use top to deal with it.  I was just using <ctrl> <alt> and getting a feel for the terminals.  

To follow up on my last post my Firefox did crash on me and then after I rebooted it locked up on me almost right away.  Haven't been on the computer since then.  I used just very briefly a few minutes ago and it was working.  I have downloaded kazehakese and am currently on the forums using it.  I'll try to use it as sort of a "control" element to confirm whether or not it is Firefox or just another problem.  I suppose as a last resort I can try that edit that you suggested kpkeerthi 

As I said earlier, I wouldn't be opposed to switching to a different messenger client, as long as it has AIM support.  Does anyone have a suggestion on that front?

---

