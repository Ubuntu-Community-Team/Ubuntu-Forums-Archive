---
title: "Frozen Apps, oh noes"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by showty on 2007-03-21
Hey all

I've got a problem where Ubuntu will hit a Windows like slump, and needs to be restarted to get anything working. I find I can no longer open any more applications (like Rhythmbox or even the System Monitor) they just appear in the task bar then disappear after the computer processes for 15 seconds or so.

Its been happening more and more often, and since I can't get to the System monitor, I can't see whats causing the problem, and only the apps that are open will work at all (at the moment it happened when i had the file browser open, open office writer, firefox and xchat). I had also just uninstalled a program I had installed with Wine (could wine be causing these 'hangs'?)

How can I fix this problem, its very reminiscent of Windows :(

Thanks

---

### Post by devnulljp on 2007-03-21
Are you just running out of RAM?

---

### Post by ziggykg on 2007-03-21
I suggest having a look at the log files (e.g. /var/log/messages) after an incident like this.  It may give clues as to what is causing the problem.  If you glance through it, can you see anything untoward?

---

### Post by showty on 2007-03-21
> **devnulljp said:**
> Are you just running out of RAM?

I have 2GB of DDR2 RAM and 2GB swap, I really hope that I'd be able to handle about 4 apps open at once.

ziggykg, I can't actually check right now, the only file browser I have open (I can't open additional ones because they will freeze) can show the file but obviously can't open it in my current system state.

---

### Post by showty on 2007-03-21
Please someone help, my system is unusable now and I don't want to touch Windows XP..

---

### Post by showty on 2007-03-21
Ok, I managed to get into the terminal (CTRL + ALT + F1) and entered dmesg, and I got all these lines of text like:

key pressed setkeycodes e001

stuff like that.. what does that mean?

---

### Post by showty on 2007-03-21
ok I checked and im getting setkeycodes e001 and e059..

---

### Post by Arby on 2007-03-21
It's probably going to be easier if you just post the messages you are seeing here for people to check. Something like ```
tail -n 20 /var/log/messages
``` would give you the last 20 lines of /var/log/messages. Post that lot here and see if anyone can spot anything unusual

---

### Post by showty on 2007-03-21
```
Mar 21 23:15:54 andrew-desktop kernel: [17180079.740000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Mar 21 23:19:46 andrew-desktop kernel: [17180311.336000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Mar 21 23:19:46 andrew-desktop kernel: [17180311.336000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Mar 21 23:20:19 andrew-desktop kernel: [17180344.956000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Mar 21 23:20:19 andrew-desktop kernel: [17180344.956000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Mar 21 23:21:05 andrew-desktop kernel: [17180390.384000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Mar 21 23:21:05 andrew-desktop kernel: [17180390.384000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Mar 21 23:47:52 andrew-desktop -- MARK --
Mar 22 00:02:02 andrew-desktop kernel: [17182847.396000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Mar 22 00:02:02 andrew-desktop kernel: [17182847.396000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Mar 22 00:02:02 andrew-desktop kernel: [17182847.612000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Mar 22 00:02:02 andrew-desktop kernel: [17182847.612000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Mar 22 00:02:48 andrew-desktop kernel: [17182894.044000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Mar 22 00:02:48 andrew-desktop kernel: [17182894.044000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Mar 22 00:03:02 andrew-desktop kernel: [17182907.144000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Mar 22 00:03:02 andrew-desktop kernel: [17182907.144000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Mar 22 00:04:47 andrew-desktop kernel: [17183012.884000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Mar 22 00:04:47 andrew-desktop kernel: [17183012.884000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Mar 22 00:04:47 andrew-desktop kernel: [17183012.972000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Mar 22 00:04:47 andrew-desktop kernel: [17183012.972000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Mar 22 00:13:27 andrew-desktop kernel: [17183532.740000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Mar 22 00:13:27 andrew-desktop kernel: [17183532.740000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Mar 22 00:13:33 andrew-desktop kernel: [17183538.836000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Mar 22 00:13:33 andrew-desktop kernel: [17183538.836000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.

```

And this was around the time the problem occured:
```
Mar 21 20:34:28 andrew-desktop gconfd (root-11251): SIGHUP received, reloading all databases
Mar 21 20:34:28 andrew-desktop gconfd (root-11251): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar 21 20:34:28 andrew-desktop gconfd (root-11251): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Mar 21 20:34:28 andrew-desktop gconfd (root-11251): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar 21 20:34:28 andrew-desktop gconfd (root-11251): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar 21 20:34:28 andrew-desktop gconfd (root-11251): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar 21 20:34:28 andrew-desktop gconfd (root-11251): GConf server is not in use, shutting down.
Mar 21 20:34:28 andrew-desktop gconfd (root-11251): Exiting
```

---

### Post by showty on 2007-03-21
Can't anyone help?

---

### Post by showty on 2007-03-21
Anyone? This is really important :(

---

### Post by Adramelech on 2007-03-21
get to a terminal Ctrl+alt+F1
try "top" to see if theres an appication using a lot of resources
ps -A to see all the process running

without knoing what can be the problem the only solution i can thin is reinstalling ubuntu-desktop maybe you tweaked some config file.

---

### Post by showty on 2007-03-22
I haven't touched any configuration files, other than resetting my xorg config after I installed the nvidia drivers (but it guided me through a wizard to replace it with a new one).

Just to clarify, everything works AT FIRST after boot, then after a while i start getting problems..

---

### Post by Rui Pais on 2007-03-22
Hi,
i wonder if that messages in yours logs are directly connected to the frozen of apps?... 

check your logs to see if that kind of message didn't appear on dates before the frozens started to happen. 

Not much a help here, but... check if the suggestion on [this blog]("http://ubuntu.wordpress.com/2006/02/10/unknown-key-pressed-error/") can help.

Good luck.

---

### Post by devnulljp on 2007-03-22
OK, I've just started seeing this too sometimes (in the last week or so). 
I wonder if there might be a bug in gconfd. 
Some info [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/)
For now, try 
sudo gconftool-2 --shutdown

There's a buglist here: [http://bugzilla.gnome.org/buglist.cgi?query=gconfd](http://bugzilla.gnome.org/buglist.cgi?query=gconfd)
I'm not sure if thsoe messages in syslog are normal or abnormal - I suspect it's just normal processing based on this: [http://www.gnome.org/projects/gconf/plans.html](http://www.gnome.org/projects/gconf/plans.html)
...anyone else got a better clue?

(I'm still trying to figure this out, but glad to see someone else with the same problem)

FWIW, you can redirect those messages to somewhere else

add a line like this to /etc/syslog.conf:

 user.* /var/log/someotherlog

Then
service syslog restart
 to reload the config file.

---

### Post by shane2peru on 2007-05-01
I'm having this same problem, and it is very much resembles Microsoft!  This scares me, and I thought it was just a problem on my machine!  Here is my logs, ```

May  1 21:05:14 shane-desktop kernel: [46444.879848] DMA free:2020kB min:88kB low:108kB high:132kB active:10204kB inactive:128kB present:16256kB pages_scanned:17636 all_unreclaimable? yes
May  1 21:05:14 shane-desktop kernel: [46444.879850] lowmem_reserve[]: 0 483 483
May  1 21:05:14 shane-desktop kernel: [46444.879856] Normal free:2752kB min:2764kB low:3452kB high:4144kB active:360260kB inactive:41912kB present:494792kB pages_scanned:861798 all_unreclaimable? yes
May  1 21:05:14 shane-desktop kernel: [46444.879859] lowmem_reserve[]: 0 0 0
May  1 21:05:14 shane-desktop kernel: [46444.879863] DMA: 1*4kB 2*8kB 1*16kB 2*32kB 0*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 2020kB
May  1 21:05:14 shane-desktop kernel: [46444.879873] Normal: 0*4kB 12*8kB 4*16kB 1*32kB 0*64kB 2*128kB 1*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 2752kB
May  1 21:05:14 shane-desktop kernel: [46444.879885] Swap cache: add 0, delete 0, find 0/0, race 0+0
May  1 21:05:14 shane-desktop kernel: [46444.879886] Free swap  = 0kB
May  1 21:05:14 shane-desktop kernel: [46444.879888] Total swap = 0kB
May  1 21:05:14 shane-desktop kernel: [46444.879889] Free swap:            0kB
May  1 21:05:14 shane-desktop kernel: [46444.881445] 128768 pages of RAM
May  1 21:05:14 shane-desktop kernel: [46444.881448] 0 pages of HIGHMEM
May  1 21:05:14 shane-desktop kernel: [46444.881450] 2462 reserved pages
May  1 21:05:14 shane-desktop kernel: [46444.881452] 15628 pages shared
May  1 21:05:14 shane-desktop kernel: [46444.881453] 0 pages swap cached
May  1 21:05:14 shane-desktop kernel: [46444.881455] 0 pages dirty
May  1 21:05:14 shane-desktop kernel: [46444.881456] 0 pages writeback
May  1 21:05:14 shane-desktop kernel: [46444.881458] 72 pages mapped
May  1 21:05:14 shane-desktop kernel: [46444.881460] 4143 pages slab
May  1 21:05:14 shane-desktop kernel: [46444.881461] 1361 pages pagetables

```
 
It appears as though my swap was out of space? or non-existent?  I checked an my swap was turned off.  Why?  This is odd.

Shane

---

