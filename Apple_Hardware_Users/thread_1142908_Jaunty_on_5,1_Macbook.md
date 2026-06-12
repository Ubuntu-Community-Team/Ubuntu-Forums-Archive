---
title: "Jaunty on 5,1 Macbook"
date: 2009-04-29
forum: Apple Hardware Users
---

### Post by CodeSamurai on 2009-04-29
Hello all! I'm on my Unibody Macbook with Jaunty installed.  Everything seems to be working well except battery life!  I've gone through the wiki and attempted to blacklist the eth0 which is responsible for 75% of my wakeups according to powertop.  Even after blacklisting, it continues to be an issue.  I think I did the blacklisting correctly...
> gksudo gedit /etc/modprobe.d/blacklist
followed by 
> blacklist forcedeth

I've never heard of forcedeth...but I was just following the wiki...

but it didn't seem to work.  Any ideas?  I'm sure this would improve battery life.  Also, I seemed to have gotten both internal speakers working...I'm trying to figure out how I did this because it wasn't my intention.  I was actually trying to configure conky...such is life.  If I figure it out, I'll let you know.  

Other than that, any ideas for getting better battery life?  This has always been my one issue with Ubuntu.  I'm doing laptop mode, lower brightness, disabled bluetooth, trying to disable eth0, etc...any ideas?  Let me know and take care!

Trent out

---

### Post by cyberdork33 on 2009-04-29
where you have 'forcedeth' you should have the name of the linux module that is the driver for your hardware.

---

### Post by gotgenes on 2009-04-30
> **cyberdork33 said:**
> where you have 'forcedeth' you should have the name of the linux module that is the driver for your hardware.
On my MacBook 5.1, lsmod definitely shows a module called "foredeth", even though I have what the OP used in my /etc/modprobe.d/blacklist.conf. I also tried moving it to the deprecated /etc/modprobe.d/blacklist, to no avail--that module still loads. When I do a
```
sudo rmmod forcedeth
```
eth0 goes away.

---

### Post by alexmurray on 2009-04-30
After updating the blacklist ([FONT="Courier New"]/etc/modprobe.d/blacklist.conf[/FONT]), you need to regenerate the initramfs - run the following from a terminal:

```
sudo depmod -ae
sudo update-initramfs -u
```

---

### Post by Yashiro on 2009-05-01
*forcedeth* is the module name (driver) for nvidia nforce based ethernet. 
It does indeed perform a stupid number of wakeups to work around some old bug that no one seems able to fix.

---

### Post by mbs348 on 2009-05-02
I too am on a Macbook 5,1 and am seeing insane amount of wakeups from eth0....would also be interested in a fix.

-m

---

### Post by alexmurray on 2009-05-02
This is not trivial to fix, but there have been a few attempts, with the most recent one being this patch:

[http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-09/msg03314.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-09/msg03314.html)

I've been thinking of trying to get a more generic solution done for a while, something more along the lines of Andrew Morton's suggestion:

> How do we fix this? Perhaps disable the timer by default, then wait
for the first tx timeout and then enable the timer at that stage, while
printing a message saying "add module option <foo> to prevent this
once-off timeout from happening"?

or perhaps this from Robert Hancock

> Enabling by default and disabling after a TX done interrupt was received would likely be a better approach (or one of the more creative approaches that others have mentioned).

combined with something like Alan Cox's suggestion:

> Surely you only need the timer running when transmits are active and
sufficient transmits to make it worth recovering the queued memory ?

But I havent really had the time lately to look into it..

---

### Post by gotgenes on 2009-05-09
Interesting. Thanks for the background, Alex.

---

