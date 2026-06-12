---
title: "[SOLVED] Ubuntu running EXTREMELY slow"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by bidget on 2008-04-09
When I try to switch desktops, it takes around 10 or 11 seconds for it to switch to the other desktop. Although, if I hit super+e to bring up the expo thing (I enabled it in the compiz graphics options) I can switch desktops quickly with no problems. It seems that it only freezes for that 10 or 11 seconds when I try to click on the desktop in the bottom right corner. Any ideas?

Oh and also, I can't get the 3d cube to work! :(

---

### Post by Crafty Kisses on 2008-04-09
> **bidget said:**
> When I try to switch desktops, it takes around 10 or 11 seconds for it to switch to the other desktop. Although, if I hit super+e to bring up the expo thing (I enabled it in the compiz graphics options) I can switch desktops quickly with no problems. It seems that it only freezes for that 10 or 11 seconds when I try to click on the desktop in the bottom right corner. Any ideas?

Oh and also, I can't get the 3d cube to work! :(

Hmmm, post the following output:
```
top
```

---

### Post by bidget on 2008-04-09
top - 00:48:26 up 25 min,  2 users,  load average: 0.19, 0.27, 0.29
Tasks: 121 total,   2 running, 119 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.3%us,  0.3%sy,  0.0%ni, 98.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2063624k total,  1085348k used,   978276k free,    75124k buffers
Swap:  1951856k total,        0k used,  1951856k free,   647772k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5697 root      15   0  394m  37m 9100 S    3  1.9   1:21.44 Xorg               
 6095 dan       15   0  266m  43m  22m S    0  2.2   0:07.77 compiz.real        
 6317 dan       15   0  246m  24m  12m R    0  1.2   0:00.77 gnome-terminal     
    1 root      15   0  5112 1964  572 S    0  0.1   0:01.28 init               
    2 root      11  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   30 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0          
   31 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1          
   32 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid

---

### Post by Crafty Kisses on 2008-04-09
Also, what are your system specs?

---

### Post by bidget on 2008-04-09
Gigabyte GA-M57SLI-S4 Rev. 2
AMD Athlon64 X2 5000+ Black Edition
2GB OCZ XTC Platinum PC2-6400
e-GeForce 8800GT

---

### Post by Crafty Kisses on 2008-04-09
> **bidget said:**
> Gigabyte GA-M57SLI-S4 Rev. 2
AMD Athlon64 X2 5000+ Black Edition
2GB OCZ XTC Platinum PC2-6400
e-GeForce 8800GT

Do you have anything else running when you do this? Possibly like Firefox or something.

---

### Post by bidget on 2008-04-09
Well yeah... What would be the point in switching between empty desktops...?

---

### Post by Crafty Kisses on 2008-04-09
> **bidget said:**
> Well yeah... What would be the point in switching between empty desktops...?

Yeah, I was just asking. You might want to post your Xorg logs.

---

### Post by SunnyRabbiera on 2008-04-09
11 seconds is far from "extremely slow" to me, if it took 30 seconds then that would boarder and a full minute is about right there...
It could be going a lot slower then 11 seconds.

---

### Post by Crafty Kisses on 2008-04-09
> **SunnyRabbiera said:**
> 11 seconds is far from "extremely slow" to me, if it took 30 seconds then that would boarder and a full minute is about right there...
It could be going a lot slower then 11 seconds.

Yeah, really.

---

### Post by bidget on 2008-04-09
So... It's supposed to be slow?

Also, where are these logs? I can post them if I know where to find them haha :D

---

### Post by njparton on 2008-04-09
No it's not supposed to be that slow.
 
Are you using the nvidia restricted drivers?
 
You may also be experiencing problems with compiz, you could try removing it and all the associated stuff that comes with it and reverting to metacity as your gnome window manager.

---

### Post by Crafty Kisses on 2008-04-09
You may want to try the official nVidia drivers, see if it makes a difference.

---

### Post by bidget on 2008-04-09
Hmm well I downloaded a program called envy and used that to install my nvidia drivers. Should I be using different drivers maybe?

---

### Post by Crafty Kisses on 2008-04-09
> **bidget said:**
> Hmm well I downloaded a program called envy and used that to install my nvidia drivers. Should I be using different drivers maybe?

Not sure, I'd go through the Restricted Drivers Manager, but that's just me.

---

### Post by njparton on 2008-04-09
Envy is the best way to install the nvidia drivers IMHO. It tends to offer more up to date drivers than the inbuilt restricted drivers manager in ubuntu.
 
Try removing compiz and using metacity instead.
 
Changing between desktops should be instantaneous, especially with your system specs.

---

### Post by bidget on 2008-04-09
> **njparton said:**
> 
Changing between desktops should be instantaneous, especially with your system specs.

That's what I was thinking :(

Is metacity as nice looking as compiz fusion? I really like all the effects, but if this is the only way to get it working then I'll give it a try.

Also, with the Restricted Drivers Manager, when I open it all it says is "Your hardware does not need any restricted drivers," hence the reason I used envy :D

---

### Post by Crafty Kisses on 2008-04-09
> **bidget said:**
> That's what I was thinking :(

Is metacity as nice looking as compiz fusion? I really like all the effects, but if this is the only way to get it working then I'll give it a try.

Also, with the Restricted Drivers Manager, when I open it all it says is "Your hardware does not need any restricted drivers," hence the reason I used envy :D

Hmmm, weird, and did it say that before you installed your drivers through Envy?

---

### Post by bidget on 2008-04-09
Yep. I tried using the Restricted Drivers Manager first but then it wouldn't work so I came here and someone directed me to Envy, which worked perfectly. On a side-note here, is there software like daemontools or some equivalent for linux?

Oh umm... How do I remove compiz??? It's not in the add/remove menu

---

### Post by SunnyRabbiera on 2008-04-09
the add/remove applet is a very basic tool, a better application is under system>administration called synaptic.
Synaptic is like a more advanced version of add/remove although its been around a bit longer.
you can use synaptic to search for compiz and remove it, synaptic has a real basic interface so it should not be hard to figure out.

---

### Post by bidget on 2008-04-09
Well actually, I've gotten my desktop cube to work so I won't worry about removing compiz. The problem with it freezing if I click on one of the other desktops in the bottom right still happens, but any other method of changing workspaces works fine so I guess I'll just leave it the way it is. Thanks for the help though :)

---

### Post by Crafty Kisses on 2008-04-09
> **bidget said:**
> Well actually, I've gotten my desktop cube to work so I won't worry about removing compiz. The problem with it freezing if I click on one of the other desktops in the bottom right still happens, but any other method of changing workspaces works fine so I guess I'll just leave it the way it is. Thanks for the help though :)

No problem man, hopefully you can get that fixed, but like people have said you really shouldn't have issues with your specs.

---

### Post by erginemr on 2008-04-09
> **bidget said:**
> Well actually, I've gotten my desktop cube to work so I won't worry about removing compiz. The problem with it freezing if I click on one of the other desktops in the bottom right still happens, but any other method of changing workspaces works fine so I guess I'll just leave it the way it is. Thanks for the help though :)

Hold on! You are wrong in your assumption above. If you remove compiz, all effects, including desktop cube will be gone! I'll explain in a minute...

---

### Post by erginemr on 2008-04-09
If you want, you can temporarily disable Compiz and fall back to Metacity with:
```
Alt+F2 -> metacity --replace
```
and reactivate Compiz with:
```
Alt+F2 -> compiz --replace
```
Try reverting to Metacity and using the bottom right applet (which is called "Workspace Switcher") now. Does it change between the desktops fast in this mode?

Second question: How is the speed when you chenge desktops with:
```
Ctrl+Alt+Keyboard Right/Left Arrow
```

Third question: When Compiz is active, can you switch between the desktops fast by rotating the cube (by using "Ctrl+Alt+mouse left click and drag" or by "Mouse middle click and drag"?

If your answer to all these questions is yes, then as you now have other means to switch desktops, maybe all you need to do is give up on using the "Workspace Switcher" applet. You can right click on it and select "Remove from Panel".

---

### Post by Arthur Archnix on 2008-04-09
You can change how long it takes to switch desktops when using the mouse and pointing at the corner. Using compiz config go into the rotate cube settings. Make the speed lower. Mines 38.

---

### Post by bidget on 2008-04-09
Speed when using ctrl+alt+left/right is great, same with ctrl+alt+mouse1. It only seems to be the workspace switcher that is slow, I've removed it from the panel and am just going to use the desktop cube from now on. One thing I noticed when I temporarily switched to metacity was that if I opened like 5 or 6 windows on one workspace, then switched over to another one, I could still see a little preview in the workspace switcher showing where the windows were. When I had compiz enabled, I couldn't see the other ones. So I guess something is a little funky with the workspace switcher, but as I'm using the desktop cube now it doesn't really matter. Thanks for the help everyone :)

---

### Post by erginemr on 2008-04-10
You are most welcome. :D You can keep an eye on the workspace switcher, as it may start working correctly when you upgrade to Hardy. On a side note, you can also try to start a new instance of workspace switcher now to check if there is any difference by right clicking on the panel and selecting "Add to Panel...".

On a final note:
**To close a thread **-> Select **"mark this thread as solved"** from the thread tools menu. 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

