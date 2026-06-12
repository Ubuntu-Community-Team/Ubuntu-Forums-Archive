---
title: "Laptop - Screen on when I close Lid"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by ost on 2007-01-18
As the the title says when I put the screen down on my dell Inspiron 5150 the screen stays on. I have it set in preferences to suspend but still no luck. By the way I am running dapper.

Thanks
Jonathan

---

### Post by jordanmthomas on 2007-01-19
Could you post your xorg.conf
```
cat /etc/X11/xorg.conf
```
I just want to make sure you have DPMS enabled

If it is trying to suspend and can't you may have troubles with your acpi stuff and any errors should show in /var/log/acpid

Shut your lid and then open it back up and see what's at the end of:
```
cat /var/log/acpid
```

---

### Post by andrew.46 on 2007-01-19
Hi Jonathon,

 I am not sure that I can help you with your problem:

> **ost said:**
> As the the title says when I put the screen down on my dell Inspiron 5150 the screen stays on. I have it set in preferences to suspend but still no luck. By the way I am running dapper.

Thanks
Jonathan

 But you may be able to help me with mine: I suspect that when I close the fridge door the light does not go out: any ideas?

                    Andrew :)

---

### Post by jordanmthomas on 2007-01-19
Aww, come on andrew.46.  It is really annoying because my laptop did the same thing at one point and fixing it was a pain.  Also, it's annoying because it was the only light in my room because I don't have windows in my room.  I'm sure it's annoying to ost too or else he wouldn't post.

to solve your fridge problem, try locating a switch that your door would hit when shutting.  Manually depress the switch and see if your light goes out.  If it doesn't could you please post what brand you have and how many watts your light is?  :)

---

### Post by andrew.46 on 2007-01-19
Hi Jordanmthomas,

 Thanks for your suggestion:

> **jordanmthomas said:**
> 

to solve your fridge problem, try locating a switch that your door would hit when shutting.  Manually depress the switch and see if your light goes out.  If it doesn't could you please post what brand you have and how many watts your light is?  :)

 Actually I attempted to solve the problem by climbing into the fridge and shutting the door from the inside. Sure enough the light did go out but unfortunately I am now locked in. Fortunately I took my laptop with me and a longish length of network cable attaching it to my ADSL modem so I can still download porn for about 2 hours until the laptop battery dies.

 Hmmmm.... I knew it was going to be a bad day ....

         Andrew :twisted:

---

### Post by ost on 2007-01-19
Thanks for the replies. The computer will suspend after being idle for a while so I kinow that works. 

"Shut your lid and then open it back up and see what's at the end of:
Code:

cat /var/log/acpid"

This is what I got:

[Tue Jan 16 17:00:47 2007] starting up
[Tue Jan 16 17:00:47 2007] 54 rules loaded
[Tue Jan 16 17:00:54 2007] client connected from 4587[108:108]
[Tue Jan 16 17:00:54 2007] 1 client rule loaded
[Tue Jan 16 15:08:17 2007] exiting
[Tue Jan 16 15:09:24 2007] starting up
[Tue Jan 16 15:09:24 2007] 54 rules loaded
[Tue Jan 16 15:09:26 2007] client connected from 4120[108:108]
[Tue Jan 16 15:09:26 2007] 1 client rule loaded
[Tue Jan 16 23:19:35 2007] exiting
[Wed Jan 17 06:44:54 2007] starting up
[Wed Jan 17 06:44:54 2007] 54 rules loaded
[Wed Jan 17 06:44:56 2007] client connected from 4120[108:108]
[Wed Jan 17 06:44:56 2007] 1 client rule loaded


in other words it didn't do anything when I closed it. It finally suspends after the idle time is reached. 

Any more suggestions?

Thanks.

ps The light in the fridge never goes off.:rolleyes:

---

### Post by bootslap on 2007-01-19
Hey ... sorry .... just popped to say, I also have the same problem...

---

### Post by petersjm on 2007-01-19
> **ost said:**
> ps The light in the fridge never goes off.:rolleyes:

Oh, but it does! There's a tiny little man inside fridges that flicks a switch when you open and close the door. I've seen him. He's very shy, mind, but I befriended him by offering him a tiny little woman to keep him company. I'm still searching for one... :p 

As for the *real* problem, I'm afraid I don't have a clue... :(

---

### Post by LarryGB on 2007-01-21
Actually, I think this is what is to be expected. This is with battery operation [ no ac adapter ] and a lid closing and opening. Maybe your ACPI is not loaded or enabled.

```
[Sun Jan 21 19:23:37 2007] action exited with status 0
[Sun Jan 21 19:23:37 2007] completed event "battery BAT1 00000080 00000001"
[Sun Jan 21 19:35:34 2007] received event "button/lid LID 00000080 00000001"
[Sun Jan 21 19:35:34 2007] notifying client 4130[108:108]
[Sun Jan 21 19:35:34 2007] executing action "/etc/acpi/lid.sh"
[Sun Jan 21 19:35:34 2007] BEGIN HANDLER MESSAGES
[Sun Jan 21 19:35:34 2007] END HANDLER MESSAGES
[Sun Jan 21 19:35:34 2007] action exited with status 0
[Sun Jan 21 19:35:34 2007] completed event "button/lid LID 00000080 00000001"
[Sun Jan 21 19:35:35 2007] received event "button/lid LID 00000080 00000002"
[Sun Jan 21 19:35:35 2007] notifying client 4130[108:108]
[Sun Jan 21 19:35:35 2007] executing action "/etc/acpi/lid.sh"
[Sun Jan 21 19:35:35 2007] BEGIN HANDLER MESSAGES
[Sun Jan 21 19:35:35 2007] END HANDLER MESSAGES
[Sun Jan 21 19:35:35 2007] action exited with status 0
[Sun Jan 21 19:35:35 2007] completed event "button/lid LID 00000080 00000002"

```

cat /proc/sys/vm/laptop_mode
0


Anyone comment on the ACPI mode?

---

### Post by jordanmthomas on 2007-01-21
It seems as if ost does not have acpid running
```
sudo /etc/init.d/acpid stop
sudo /etc/init.d/acpid start
```
See what happens after that.

The output that LarryGB posted is the sort of stuff you should get...what you had before makes it seem as though your computer is not recognizing that the lid is being closed and it is just suspending because it has been idle.

I'm not sure what to do from here, but here is a quick and dirty solution to at least turn off the screen:
```
  xset -display :0 dpms force off
```
This may be a helpful read to you (you should be able to ignore the parts about building your kernel)
[http://gentoo-wiki.com/HOWTO_Software_Suspend_v2](http://gentoo-wiki.com/HOWTO_Software_Suspend_v2)

---

### Post by soliac on 2007-04-06
I have the exact same problem on an Inspiron 5160. I also get the same output from cat /var/log/acpid as ost got. Would love a solution which would autoturn the screen off/on.
p.s. running Edgy.

---

### Post by gamma on 2007-04-25
I believe something is borked with ACPI and the Inspiron 5150. I have the latest BIOS version on the laptop and my lid switch doesn't work either. I remember reading somewhere that this laptop only issues one ACPI event at the beginning then it doesn't send any other events to the OS. Also notice in Gnome it takes some time for the battery status to be updated. If the laptop was working properly soon as you pull the plug it should say battery where now it takes 20 seconds to change the status (because it's manually polling the state).

There was a command you could enter in grub that disabled something, I can't remember the command, but upon entering it everything worked, but CD burning no longer worked. So I decided to keep CD burning working and not use the command. If I can find what it was again I'll post it here. I'd recommend searching the Dell Support Forums, this topic has been discussed before.

---

### Post by gamma on 2007-04-25
[http://bugzilla.kernel.org/show_bug.cgi?id=1752](http://bugzilla.kernel.org/show_bug.cgi?id=1752) is the bug report in the kernel. The solution is to add irqpoll to the grub parameters.

I've heard from people that this limits performance, but things don't seem slower for me. I tried this on Dapper way back when and couldn't burn CDs, I have yet to try in Feisty though.

---

