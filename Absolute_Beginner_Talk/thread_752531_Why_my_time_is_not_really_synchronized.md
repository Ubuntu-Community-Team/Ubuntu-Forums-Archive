---
title: "Why my time is not really synchronized?"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by incen on 2008-04-11
Hi, I keep having some problem synchronizing my Ubuntu clock. While in Windows, it seems fine (they are on the same PC). I doubted if it's the crystal problem.
I have NTP installed and I make it synchronized with some server. However, the clock is off after some days and I have to manually adjust it. What is the problem? Does anyone have the same situation? :confused:

---

### Post by Locutus_of_Borg on 2008-04-11
I had a problem with my clock that I eventually solved by resetting the hardware clock to match my system clock

```
sudo hwclock --systohc
```

make sure your system clock is correct first, of course.

---

### Post by incen on 2008-04-13
But how do I check my system clock?

---

### Post by forrestcupp on 2008-04-13
By 'system clock', they are talking about the clock you see in your panel.  Make sure it is set for the correct time, then run the command they gave you to set your hardware clock to be the same as what your clock says on your panel.  Evidently, that helps.

---

### Post by incen on 2008-04-14
Well, I tried to re-synchronize my clock now with the 'Manual' option. Obviously, it is 3 minutes late again. Last time I adjusted it is last Friday. What is the problem of my clock? It seems it's not really synchronized with the network. :(

---

### Post by wpshooter on 2008-04-14
> **incen said:**
> Well, I tried to re-synchronize my clock now with the 'Manual' option. Obviously, it is 3 minutes late again. Last time I adjusted it is last Friday. What is the problem of my clock? It seems it's not really synchronized with the network. :(

My "guess" is that you CMOS battery is getting weak !!!  Probably loosing time between being synchronized.

---

### Post by incen on 2008-04-15
Then, that's so bad... this PC is rather new. I just got it last Sep.

---

### Post by Tomosaur on 2008-04-17
> **incen said:**
> Then, that's so bad... this PC is rather new. I just got it last Sep.

Meh, it just happens sometimes. CMOS batteries are pretty cheap though, just buy one, pop the old one out, then stick the new one in. [Here's a guide](http://www.pctechbytes.com/computer/article-21.html) in case you don't know how to do it.

It's a bit weird that the Windows clock is fine though, so I'd check around to make 100% sure that it's not just a software problem.

---

### Post by incen on 2008-04-21
Hi, I'm not sure if now I'm the right track. The situation is really odd. Even with Manual mode, I tried to click on 'synchronize now'. A loading bar is running (seems looking info from the Internet); however, the time is not synchronized after it's done!!! It's still 40 minutes late! :(

Can someone explain this to me? I don't really know if this is my CMOS problem or there's something wrong with my Ubuntu. The latter case is what I worry about. :confused:

---

### Post by movrshakr on 2008-04-21
This is not focused yet on where the problem is.

The advice to get a good time in the system then write it to the HW clock with
sudo hwclock --systohc
is good.

You say you are running ntp.  Are you sure it is running?  
At a terminal, **ps -ef|grep ntp**
will show you if it is still an active process.
Be aware of this:  when ntp tries to start, if your "current clock" is more than 1000 seconds different from the time ntp gets from its server, ntp will hard fail and not start.

But ntp can be active yet not associating.  At a terminal, **ntpq -p**.  That will show you a list of the servers ntpd is trying to associate with (specified in ntp.conf).  The server currently associated is marked with a * asterisk in the leftmost column.  If you have a line with a * then your system time should be correct.

---

### Post by incen on 2008-04-21
I did this:
```
ps -ef|grep ntp
```
and the result is
```
cissi     7136  7119  0 16:43 pts/3    00:00:00 grep ntp
```

Then, this:
```
ntpq -p
```
and the result is
```
ntpq: read: Connection refused
```

So I guess my NTP didn't really start at least today since the time is already so off, right?

I did:
```
sudo hwclock --systohc
```
and then tried to synchronize manually again. However, nothing changed!!!

---

### Post by movrshakr on 2008-04-22
Indeed, that does indicate that ntp is not running...the 'grep ntp' line is because grep is running;  if ntp was running there would be a second line with ntpd in it.

You should NOT do the hwclock command when your system time is wrong;  that writes the incorrect time into the HW clock.  But you can manually do an ntpdate command (which will do a one-time clock update), THEN do the hwclock command to write a good time into your HW clock.  Then reboot and do the ps and ntpq commands previously stated to see if ntpd is running. Read **man ntpdate** to see the syntax for ntpdate.

BTW, **ntpq -p** won't show a star by the sync'ed server immediately;  it takes ntp a period of time and multiple server hits to test and calculate various things it uses internally. 

I suspect that ntp is not starting most likely because your HW clock is more than 16.67 minutes wrong from actual time.  After you do the ntpdate followed by hwclock steps above that should correct it.  There may be other problems to work out, but first we have to get your hwclock set right.

What ubuntu version are you running?

---

