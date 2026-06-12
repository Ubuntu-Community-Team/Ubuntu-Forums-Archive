---
title: "Computer troubles."
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by Jimmey on 2005-12-02
I recently got a second hand PC - Which I didn't pay for, as the previous owners where unable to fix what to me sounded like a strictly Windows problem - Windows itself failed to load. I thought that if it was a Windows problem, then a quick re-format with the Ubuntu install CD would clear it up right away. But, as I had a copy of the liveCD, I thought that I might aswell give it a try. 

So, I inserted the liveCD, and it loaded the bootscreen. But, after that, nothing. I can't press enter to proceed with the default settings. The computer just freezes. The same is the case with the install CD (Both of which I know aren't corrupted ).

Entering special boot parameters wont work, because the computer stops responding. 

I initially thought that the problem would be lack of RAM - I've only 64MB. But I've been told that the ubuntu server version should run on 64MB, and that therefore the install CD should work anyways ( I may have mis-intepreted this ).

I've thought about using the 64bit .iso instead - Could that be the problem?

Basically - is it worth keeping this computer, or has is floated it's way up to hardware heaven?

Thanks

Jimmey

---

### Post by teaker1s on 2005-12-02
try running a memory test-should be an option in bios- normally it's disabled for a faster boot

---

### Post by Jimmey on 2005-12-02
I will do - But as I am away from the computer right now, ( I am in college ), what sort of results should I expect from this test?

---

### Post by xmastree on 2005-12-02
Yeah, run memtest. A friend of mine who makes a living fixing PCs says **Always re-seat the RAM** that is enough to fix 50% of the problems.
I'm not sure 64MB is enough to run the live CD though. Ok for the install, but the live needs more RAM since it can't write to the disks.
> I've thought about using the 64bit .iso instead - Could that be the problem?Unless it's an AMD64, don't use the 64 bit ISO, and if it only has 64MB, I guess it's not.
Who would build a 64 bit PC and cripple it with only 64MB or RAM?

---

### Post by teaker1s on 2005-12-02
if it refuses to complete to the max install memory then you have bad memory, also I've had a dodgy modem(suspected power surge) stop it booting if it has one remove it while installing-possibly no effect but worth a try

---

### Post by xmastree on 2005-12-02
[QUOTE=Jimmey]I will do - But as I am away from the computer right now, ( I am in college ), what sort of results should I expect from this test?[/QUOTE]Erm, a pass? :rolleyes: 

Ok, it's fairly self-explanatory. You select it at boot time and it will display something like
**running test 1** 1...2...3..4... etc. up to 100%, then another, and so on. It will tell you if it passes or fails.

It'll be obvious once you see it.

**teaker1s** also has a point about the modem. If there are any other expansion cards in there, LAN, sound, whatever, remove them. Strip it to the bare minimum (cpu, RAM, video) and run it like that.

---

### Post by Brunellus on 2005-12-02
64 MB RAM is not a lot.  It will run a 'server' install, but be aware that if you do that, you get the bare minimum:  the ubuntu base system, the bash shell....and....um, that's it.  No fancy-schmancy graphical user interfaces.  In fact, no graphical user interfaces at all (unless you count ncurses applications).

I agree with the other posters--make sure your problem isn't bad RAM.  You can then go ahead and install, but you'd need to go for a "server" install then install a very minimal system.

---

### Post by Jimmey on 2005-12-02
Would that be suitable to use as a place to store files on the network?
So, if I used that computer as storeage space, almost, then I could connect it to the network, store files from my laptop on there, and download/upload as I like? That's all I'd use it for.

---

### Post by xmastree on 2005-12-02
Sure, that would be ok. Once you have it configured, tell it not to load x at startup. You won't even need a keyboard or monitor after that. You can install webmin to administer it remotely. I have one like that. It has more than 64MB though, 192 IIRC. It's a PIII/500

---

### Post by Brunellus on 2005-12-02
[QUOTE=xmastree]Sure, that would be ok. Once you have it configured, tell it not to load x at startup. You won't even need a keyboard or monitor after that. You can install webmin to administer it remotely. I have one like that. It has more than 64MB though, 192 IIRC. It's a PIII/500[/QUOTE]
it doesn't even need to install the x server, if he opts for a "server" install.

---

