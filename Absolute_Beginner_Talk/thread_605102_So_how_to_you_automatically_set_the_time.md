---
title: "So how to you automatically set the time?"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by jgrant on 2007-11-06
This is insane!

How do you set the time with Ubuntu 7.10 automatically???  I have read many questions about this and nobody has a straight answer that works!  I have tried several of the suggestions out but every time I click on Adjust Date & Time and select Keep Synchronized with Internet Servers, the Synchronize Now button is grayed out...

What gives?  The timezone is correctly set and I have selected several of the time servers, yet it does not work.  What is the trick to make this work??

Thanks for any help...

joe

---

### Post by yogo on 2007-11-06
tzconfig

---

### Post by jgrant on 2007-11-06
Interesting.

I tried tzconfig and no dice.  Got an error massage stating "command not found".  I stated on my first post that I am using Ubuntu 7.10; from what I read, tzconfig is not part of it, yes?

What gives?  An OS that cannot sync it's clock?

joe

---

### Post by Dr Small on 2007-11-06
I thought you could sycronize your clock by right clicking on the time and selecting "Adjust Date & Time"...

---

### Post by philinux on 2007-11-06
+1 Dr thats what I thought too.

Just set you time zone under prefs too,

---

### Post by poudin on 2007-11-06
[http://www.cyberciti.biz/faq/set-date-time-network-time-protocol-ntp/](http://www.cyberciti.biz/faq/set-date-time-network-time-protocol-ntp/)

this should work...schedule the ntpdate script with cron hourly..and that should keep the system up to date.

---

### Post by jgrant on 2007-11-06
> **Dr Small said:**
> I thought you could sycronize your clock by right clicking on the time and selecting "Adjust Date & Time"...

That is what I thought too!!  BUT, in my case I can click on the time zone and set it up all I want but the button that says "Synchronize now" always stays grayed out.  This is what makes this so frustrating.  

I'll see about setting the cron job to do the work.

Thank you all.

joe

---

### Post by Bigbird999 on 2007-11-06
Dual boot with win 2k and I have the same greyed out button, plus it is always fighting with windows.  Both are out by 1 hr every time I fix one it borks the other.

BB

---

### Post by bluepowder7 on 2007-11-06
haha!  i got irritated by that too, but then figured it out.

switch to MANUAL, and THEN you can synchronize.  it's weird and counterintuitive, but that's how it seems to work.  once synched, you can revert back to "keep synched with internet servers"

---

### Post by jgrant on 2007-11-06
> **bluepowder7 said:**
> haha!  i got irritated by that too, but then figured it out.

switch to MANUAL, and THEN you can synchronize.  it's weird and counterintuitive, but that's how it seems to work.  once synched, you can revert back to "keep synched with internet servers"

Oooookay!   Let me give that a try...  

Thanks all!

joe

---

### Post by Duck2006 on 2007-11-06
> **Bigbird999 said:**
> Dual boot with win 2k and I have the same greyed out button, plus it is always fighting with windows.  Both are out by 1 hr every time I fix one it borks the other.

BB

Have you gone in to your BOIS on your system and ajusted there, sounlds like your time is not set write there.

---

### Post by nhandler on 2007-11-06
I think this is the way it is meant to be. Think about it...

If it is set to keep synchronized, it syncs automatically. There would be no need to Sync it yourself. In manual, you might want to sync it every now and then to keep the clock set acurately.

---

### Post by bluepowder7 on 2007-11-06
ya, but when it's set to synch to internet servers, it should realize that it's out of whack and synch itself up within a matter of seconds.

only reason i found that trick is because i got fed up with having my PC clock synched with central Europe or wherever (it was off by 10 hours or so), so i flipped to manual and whoa!  i can now synch with a network computer.

---

### Post by crav on 2007-11-07
Image attached shows what the problem is.

---

### Post by asmiller-ke6seh on 2007-11-20
Ubuntu automatically sets the clock each time the network interface is restarted (see the script at [FONT="Courier New"]/etc/network/of-up.d/ntupdate[/FONT]) - Ubuntu looks to see if the file [FONT="Courier New"]/etc/default/ntupdate[/FONT] exists. This file contains a single line: the name of the NTP time server. Unless you created this file, Ubuntu will fall back to use [FONT="Courier New"]ntp.ubuntu.com[/FONT]. If your system cannot reach that NTP server, then your clock will not be set at boot time, and will drift. If you don't reboot your system for a long time, your clock can drift. You can add a Cron job to run it - weekly is often enough -

> sudo crontab -e

then add this line to run [FONT="Courier New"]ntpupdate[/FONT] every Sunday at 5 minutes after midnight (you can choose another time that works best for you)

> 5 0 * * 0 /etc/network/if-up.d/ntupdate

Hope that you find this helpful. This is just one way ... of course in Linux there are many ways that will work, but this works for me.

---

### Post by asmiller-ke6seh on 2007-11-20
> **crav said:**
> Image attached shows what the problem is.

Please remember:

> Linux is not Windows

Among other things, this means that you should not expect that Windows logic is Ubuntu logic ... things work DIFFERENTLY, but they DO WORK.

This is a perfect example.

See my post, above.

---

