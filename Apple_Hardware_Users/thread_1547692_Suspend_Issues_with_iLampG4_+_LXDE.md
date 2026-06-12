---
title: "Suspend Issues with iLampG4 + LXDE"
date: 2010-08-07
forum: Apple Hardware Users
---

### Post by Doobie9 on 2010-08-07
Ok, so I've got Debian Lenny (not Ubuntu, I know, but close enough) running on an iMac G4 (The ones with monitors on little arms). When I first installed suspend-to-ram worked perfectly fine; it would switch over to some blank tty, then suspend, and when it awoke it moved back to  the desktop. 

Then, for apparently no reason, the computer would just freeze when suspend was initiated; the screen would garble up with weird, colorful distortions and I would be unable to change to a tty. I had to hard reset. 

To 'fix' this problem I've written a script that takes my current tty as a variable, then changes to a blank tty, and then initiates the pm-suspend command; then returning me to the previous tty. 

Now, I need to figure out how to make the 'suspend' button in LXDE run my script instead of whatever it does by default. Or, perhaps I could find some way to change the default behavior of the suspend button? I've figured out how to do something similar to this on an Intel machine; but there is no /etc/defaults/acpi-support on this machine. I'm tired of hard-resetting this thing trying to figure this out.

I'd really like to fix this problem. It's frustrating to know that successful suspend/resume is possible but having no elegant way to initiate it. Any help is appreciated.

---

### Post by linuxopjemac on 2010-08-07
I also use Debian Lenny on my PowerBook G3 Pismo. What I did to have a working sleep/suspend is to switch to a different kernel.

```
jeroen@debian ~ $ uname -r
2.6.32-bpo.2-powerpc
```

You can have this kernel by activating the backports repository and to then select this kernel with synaptics package manager. This kernel solved my issues.

Success

---

### Post by Doobie9 on 2010-08-08
> **linuxopjemac said:**
> I also use Debian Lenny on my PowerBook G3 Pismo. What I did to have a working sleep/suspend is to switch to a different kernel.

```
jeroen@debian ~ $ uname -r
2.6.32-bpo.2-powerpc
```

You can have this kernel by activating the backports repository and to then select this kernel with synaptics package manager. This kernel solved my issues.

Success

I have since installed Debian Squeeze on this machine, and have encountered the same issue. Suspend may work only once, and then fail with each subsequent attempt.

I have written down the name of that kernel, and will investigate it. My problem, however, may not be on the device-driver level. Whenever I change over to tty1, log in as root, and run pm-suspend, the computer will suspend just fine with no issue; it is when I am running something in X that I have the system-wide freeze/garble. What I'm trying to do here to just wrap the normal sleep functionality in tty-switching so that it's not dealing with X.

So, to clarify: suspend actually works, but only with my hacky little script. What I'm really looking for is an *elegant* solution so that someone less-knowledgeable in the ways of Linux can simply select 'Suspend' from a neat little menu without being punished with an awful crash. This computer isn't just for my own use. 

[ For the sake of full disclosure: I've actually got two iLamp G4s that are practically identical machines; one is just for myself and the other is for someone else. I treat them like one machine because what works for one will work for another and vice-versa. Now both of them are running Debian Squeeze with LXDE and identical xorg.confs, etc. Whenever I work on one I am, indirectly, working on the other, because any fix to one can be applied to another quite easily. ]

---

### Post by linuxopjemac on 2010-08-08
I see...You have to start looking into suspend and sleep hooks. I am not entirely sure whether this works for Ubuntu/PPC too, but you could try to make a hook in /etc/pm/sleep.d with the name 20_gdm and put the following in:

```
#!/bin/sh  
gdm stop
```

chmod +x to make this file executable (all as root of course)

You do the same for /etc/pm/power.d/10_gdm

```
#!/bin/sh  
gdm start
```

Hope that works

---

### Post by Doobie9 on 2010-08-19
> **linuxopjemac said:**
> I see...You have to start looking into suspend and sleep hooks. I am not entirely sure whether this works for Ubuntu/PPC too, but you could try to make a hook in /etc/pm/sleep.d with the name 20_gdm and put the following in:

```
#!/bin/sh  
gdm stop
```

chmod +x to make this file executable (all as root of course)

You do the same for /etc/pm/power.d/10_gdm

```
#!/bin/sh  
gdm start
```

Hope that works

My script uses the "fgconsole" command to grab the current console (almost always 7 for GUI stuff) and stores it as a variable called CURRENT_CONSOLE; then it uses the chvt command to change to virtual console 63 "chvt 63" (I saw that in one of the 'suspend' scripts, and it works just fine).

In the center of the script is the pm-suspend command, which works fine if I'm not in an x-running console. 

Then it runs, upon completion of pm-suspend (after waking): "chvt $CURRENT_CONSOLE"

This restored the current working state with the desktop and whatever programs were running. If I'm not mistaken, won't "gdm stop" kill all that's currently going on in the x-session? 

The next time I'm on the machine, I'll look for the /etc/pm/power.d folder and try to make some 'hooks' that do the same thing as my scripts. Does the pm-suspend command use the hooks? I don't want to put anything in the hooks that use pm-suspend if it, itself, uses hooks; that seems like a never-ending nightmare of recursion.

If I can't do that, then I'll try stopping GDM. While slightly less elegant than I'd prefer, if it makes things work then that's progress.

---

