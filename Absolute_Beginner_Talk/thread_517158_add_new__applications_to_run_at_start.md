---
title: "add new  applications to run at start"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by dizzy_spells on 2007-08-04
Hi,

How do you get applications to run during start up e.g. Firestarter Firewall and Kiba dock? In windows i used to drag the apps into a startup folder but i can't find the equivalent in Ubuntu

Thanks

---

### Post by xopher_mc on 2007-08-04
System> Prefrences >session

---

### Post by Jored on 2007-08-04
How do you find the command to start up an application (eg Firestarter)?

---

### Post by carloslosgrande on 2007-08-04
[FONT="Comic Sans MS"]Firestarter is just the gui for your firewall. Your firewall is always running (sort of). Firestarter is so you can make changes if you need to. You don't need to have it running all the time, some would say its better not to have it running unless you need to make a change. There are quite a lot of threads about this, in a lot more detail than I can give.
I don't know what 'kiba dock' is but generally if you go to >system>preferences>sessions>startup programs
you can add it in there.[/FONT]

---

### Post by coolen on 2007-08-04
kiba-dock is a super-fun-happy dock with funky physics.
Just add a new start-up application, set the command as kiba-dock (I assume), then make sure it's checked.

---

### Post by benx009 on 2007-08-04
> **Jored said:**
> How do you find the command to start up an application (eg Firestarter)?

most of the time, the command for an app is its name (for example, to run firestarter, type in firestarter in a terminal)

---

### Post by AlexenderReez on 2007-08-04
> **Jored said:**
> How do you find the command to start up an application (eg Firestarter)?

> **benx009 said:**
> most of the time, the command for an app is its name (for example, to run firestarter, type in firestarter in a terminal)

find it in terminal example -->

> :~$ **which** swiftweasel
/usr/local/bin/swiftweasel


---

### Post by dizzy_spells on 2007-08-05
All,
thanks for the advice. I have been able to get Kiba-dock to autostart but when i added Firestarter, it wouldn't start as it's a system tool and requires a password (fair enough i guess). 

carloslosgrande, you say my firewall is always running and that firestarter is just the gui. How do i know the firewall is running? I can't see anything obvious to prove this

---

### Post by godd4242 on 2007-08-05
> **dizzy_spells said:**
> All,
thanks for the advice. I have been able to get Kiba-dock to autostart but when i added Firestarter, it wouldn't start as it's a system tool and requires a password (fair enough i guess). 

carloslosgrande, you say my firewall is always running and that firestarter is just the gui. How do i know the firewall is running? I can't see anything obvious to prove this

Perhaps typing "top" in your terminal will show you it.
Just a guess mind you, but it'll show all your running processes.

---

### Post by dizzy_spells on 2007-08-05
just tried it and got this. what am i looking for?

worryingly i have 2 users, 1 zombie. What do these mean?

top - 18:03:33 up 22 min,  2 users,  load average: 0.33, 0.54, 0.60
Tasks:  98 total,   2 running,  95 sleeping,   0 stopped,   1 zombie
Cpu(s):  5.6%us,  2.6%sy,  0.0%ni, 71.5%id, 19.2%wa,  1.0%hi,  0.0%si,  0.0%st
Mem:    255964k total,   227440k used,    28524k free,     3172k buffers
Swap:   449780k total,   110024k used,   339756k free,    72928k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4486 root      15   0  144m  36m 4752 R  6.6 14.4   3:32.18 Xorg               
 6086 rj        15   0 54556  15m  10m S  0.7  6.2   0:00.71 gnome-terminal     
 5242 rj        15   0 46932 4796 3596 S  0.3  1.9   0:07.14 compiz.real        
 5309 rj        15   0 16280 1540 1276 S  0.3  0.6   0:01.85 gnome-screensav    
 6112 rj        15   0  2316 1148  880 R  0.3  0.4   0:00.19 top                
    1 root      15   0  2908  520  468 S  0.0  0.2   0:01.90 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 events/0           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper            
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
   30 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kblockd/0          
   31 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   32 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  137 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod            
  156 root      15   0     0    0    0 S  0.0  0.0   0:00.04 pdflush 
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 events/0           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper            
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
   30 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kblockd/0          
   31 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   32 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  137 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod            
  156 root      15   0     0    0    0 S  0.0  0.0   0:00.04 pdflush

---

### Post by philinux on 2007-08-05
> **Jored said:**
> How do you find the command to start up an application (eg Firestarter)?

One way I was told is to right click on the app and add to panel. Then right click on panel launcher and look under properties for the command. you can always delete the shortcut from panel after. It's a bit clunky but it works.

---

### Post by oldos2er on 2007-08-05
>How do i know the firewall is running?

 It's compiled into the kernel.

---

### Post by dizzy_spells on 2007-08-05
"It's compiled into the kernel." i assume then that it is all part and parcel of Ubuntu and i shouldn't need to worry?

What about this zombie and 2nd user i can see in Terminal?

Sorry to be paranoid but up until last wednesday, i was a windows user (i say that as i haven't looked at XP since)

---

### Post by carloslosgrande on 2007-08-05
[FONT="Comic Sans MS"]Sorry to take so long, your firewall is IPtables and firestarter is the gui to make changes to this, so its always there. I'm a total novice in this area so have a look at this;[http://ubuntuforums.org/showthread.php?p=3088372](http://ubuntuforums.org/showthread.php?p=3088372)
and relax.[/FONT]

---

