---
title: "instalation problems"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by lpaulstudio on 2008-02-21
OK, so originaly I had an old computer with a pentium II processor and I was trying to install ubuntu from the live CD. It worked but was so slow when I was trying to install it that it kept freezing (I had like 198mb of RAM). So yesterday I went out and bought a new motherboard and pentium 4 processor plus 2 1gb DDR2 RAM sticks. I bought new power supply as well and installed an extra fan I had laying around. I basically replaced everything except my floppy drive, CDROM drive, and a fairly new  hard drive that is blank. I spent $205 and got almost an entire system. I figured after that everything should run perfect. I was wrong. I have tried the standard 32-bit or whatever it is, the 32-bit alternate CD, and the 64-bit installer. NONE of them have worked. With the 32-bit normal install I either get error messages that say I need to reboot or my screen freaks out and gets all fuzzy. With the 32-bit alternate I get pretty far but eventually it stops at a blue screen with a silver bar at the bottom where you can enter commands. With the 64-bit either I get an error message that tells me to reboot or I get to a command prompt that tells you to enter help for a list of commands. I've tried a few of the commands but nothing helps. I have no idea what to do but have tried **very** hard to install ubuntu and I just can't get it to work. Someone please help!

---

### Post by Liet_Kynes on 2008-02-21
Can you give us the error message that is given before you have to reboot?

Also which version of ubuntu are you trying to install?

---

### Post by lpaulstudio on 2008-02-21
Yeah ok. It says: "Trying to fix but reboot is needed." And then sometimes it says: "Kernel panicked." and then something about killing. I'm not really sure. I've only got that one about twice. I'm trying to install version 7.10. the newest one.

---

### Post by uberlube on 2008-02-21
Try checking cd for defects at boot.

---

### Post by lpaulstudio on 2008-02-21
I have, and the CD's are all fine. I'm wondering if maybe some of my harware isn't compatible with linux. I don't know how to check but that's the only thing I can think of that could be going wrong.

---

### Post by Moop on 2008-02-21
It doesn't really sound like a hardware compatibility problem but more like a hardware problem. Have you tried running memtest from the live cd? 

Does the live cd boot and work ok?

---

### Post by Liet_Kynes on 2008-02-21
Run a chkdisk from windows to check for bad sectors on the harddrive.

---

### Post by lpaulstudio on 2008-02-22
well, the problem is, I don't have windows anymore.  Originaly I had windows 98 on my D drive that was 20gb. Then we got a virus and that drive locked up so we could neither save nor delete information from it or something like that (that's what the computer guy said). We got another drive (our C drive) that held 40gb. Later I got xp from a friend and installed it on the C drive. Somewhere during the process of upgrading/rebuilding my computer, the C drive was wiped out; at least I think it was cause I can't boot from it. I tried the old D drive and it started to work but then it said it was missing files. ??? So I have put those drives to the side and am just going to put ubuntu on a blank 160gb hard drive my uncle gave me. By the way, this computer that I am on is not the same computer that I am having trouble with. The one I'm rebuilding doesn't have internet access.

---

### Post by lpaulstudio on 2008-02-22
I think I have told my complete computer history by now, but does anyone know what could have gone wrong. I've heard that some hardware isn't compatible with linux. Could that be it?

---

### Post by Fafnir on 2008-02-22
When you get to the command prompt, are there any errors along the lines of "Failed to start X server"? At the prompt, try typing startx, hitting enter, and seeing what happens. Post the errors if, or more likely when, it fails.

Explanation: It sounds like part of the problem might be that something's going wrong with the drivers for your graphics card, so we can rule that out by trying to start the graphical part of the OS and seeing what happens. If that's the problem, it should be fixable but it might require a little tinkering... I doubt you'd ever get to a command prompt if there were serious incompatibilities with something key, like memory or the CPU, and if it's something like a sound card then the OS should boot regardless.

Just in case, though, what motherboard are you using? (A Pentium 4 should be fine for the CPU, so that won't be it.) You also might want to get hold of a program called memtest ([http://www.memtest.org/](http://www.memtest.org/)) - it's a freeware memory tester that works as a boot disk. I think there should be a copy on the LiveCD, but if you don't get the option to boot into it then download it on the computer that has Internet access, burn it, then stick it in the troublesome computer to see if there are problems with the memory.

---

### Post by kooolrock on 2008-02-22
I suggest that u visit [Ubuntu LoCo Team Forums]("http://ubuntuforums.org/forumdisplay.php?f=183"). take the LIVE help of a fellow Ubunt-ite. It'll be easier to solve ur problem. All the Best!

---

### Post by kooolrock on 2008-02-22
> **lpaulstudio said:**
> OK, so originaly I had an old computer with a pentium II processor and I was trying to install ubuntu from the live CD. It worked but was so slow when I was trying to install it that it kept freezing (I had like 198mb of RAM). So yesterday I went out and bought a new motherboard and pentium 4 processor plus 2 1gb DDR2 RAM sticks. I bought new power supply as well and installed an extra fan I had laying around. I basically replaced everything except my floppy drive, CDROM drive, and a fairly new  hard drive that is blank. I spent $205 and got almost an entire system. I figured after that everything should run perfect. I was wrong. I have tried the standard 32-bit or whatever it is, the 32-bit alternate CD, and the 64-bit installer. NONE of them have worked. With the 32-bit normal install I either get error messages that say I need to reboot or my screen freaks out and gets all fuzzy. With the 32-bit alternate I get pretty far but eventually it stops at a blue screen with a silver bar at the bottom where you can enter commands. With the 64-bit either I get an error message that tells me to reboot or I get to a command prompt that tells you to enter help for a list of commands. I've tried a few of the commands but nothing helps. I have no idea what to do but have tried **very** hard to install ubuntu and I just can't get it to work. Someone please help!
u deserve appreciation, just for the nice way in which u described the problem. Everyone needs to learn about this from YOU!:)

---

### Post by kooolrock on 2008-02-22
> **Moop said:**
> It doesn't really sound like a hardware compatibility problem but more like a hardware problem. Have you tried running memtest from the live cd? 

Does the live cd boot and work ok?
imp

---

### Post by lpaulstudio on 2008-02-22
ok, i'll try the memtest thing. I have winMd5Sum but it doesn't seem to work, it keeps freezing up.  So i'll use memtest. 

I've received **many** errors but I can't read them all because they go buy so fast. It's weird sometimes ubuntu starts to load and then just freeze up and other times it doesn't load, just gives me errors and all these wierd lines of numbers and mhat appears to be filenames and stuff. I try to make it out but it doesnt make any sense. I don't know anything about linux so this is all new to me. I don't remember seeing anything about failed to start server x but i'll give it a go, why not right? 

Right now I'm downloading an older version of ubuntu (version 6.10). I'm going to see if it works (I've heard of people that can only run older versions of ubuntu, not the new ones so i'm gonna try). If it doesn't work, I'll load the other CD's and see what I can find. Thanks for the help guys!

---

### Post by lpaulstudio on 2008-02-22
I looked at the memtest website, is that for recovering my old drives? I don't really care about them. All I had was Windows (ewww ... gross), photoshop cs2, and winzip 11 (both of which I took through a keygen and can get back the same way). I also had a bunch of music which I can reload with the CD's they came from. There wasn't really anything on there that I can't get back except for some music that I bought but that's alright.

Anyway, if that memtest thing is going to help me with ubuntu then i'll do it. But i'm not gonna download it and burn to cd if I don't have to. 

Ok. I have the latest "results". New post for this one.

---

### Post by lpaulstudio on 2008-02-22
So the 32-bit 6.10 version of ubuntu didn't work but let's face it, it didn't have much going for it anyway.

Now on to the 32-bit 7.10 version. This is where it gets interesting.

The first time I tried it, it didn't even get to the load screen, but instead gave me this exact error: "Kernel panic - not syncing: attempted to kill init!"
Instersting, I don't know what it means. Moving on:

The second time I tried the CD it just froze at the loading screen. This is the one with the Ubuntu logo and the loading bar beneath it with the pretty little orange bar going back and fourth. It imediately froze, the orange bar didn't go back and fourth at all.

The THIRD time it went to the loading screen and appeared to be working for a while and then gave me a BUNCH of text with numbers and codes and brackets and all that cryptic fun stuff. I copied down some of it:
"
**Bunch of numbers and stuff was above this**
Call Trace:
[<c01925eb>] d_alloc+0x1b/0x190
[<c0187afb>] cached_lookup+0x5b/0xa0
[<c018902f>] lookup_hash+0x7f/0xb0
[<c018ae08>] do_unlinkat+0x98/0x150
[<c0196cc4>] mntput_no_expire+0x24/0xa0
[<c017ea47>] filp_close+0x47/0x80
[<co1042527>] syscall_call+0x7/0xb
**Bunch of numbers for about three lines**
[ 220.266775] EIP:[<c017cc7c>] kmem_cache_alloc+0x4c/0x90 SS:ESP 0068:df9c5f04
_**curser is blinking but I cant enter anything**
"
Well wasn't it fun reading all that, it was even more fun copying it down.

Does anyone know what it means?

---

### Post by seventhc on 2008-02-23
I'm not really to sure, I'll see if I can find anything closely related, I searched a few of the errors, but the results of the search point to this thread lol.
Well first, have to double checked that everything is properly connected, and everything is properly seated.?
I don't think you got a new vid card, did you?
What vid card are you using?

---

### Post by lpaulstudio on 2008-02-23
no, not a new video card. I got one from my uncle but it's kinda old. It's a Geforce2 MX200 32 mb. Think that could be the problem? It doesn't seem to me like it would but you know way more than me. So I trust you.

---

### Post by seventhc on 2008-02-23
Well, it seems all of your new hardware should be fine and compatible,
and as long as you are certain that your CD Drive is functioning properly, I don't see what could be causing errors.
One thing you might want to try is to only use the hardware you need, so maybe take out nic card for now, internal modem if you have one.
You obviously need the vid card so leave that lol. But if there is a bad piece of hardware causing a problem which is possible, I'd want to take as much as possible out of the loop.
If I remember correctly you said this computer wouldn't go online, but did you still put in nic card/modem?
If it is the video card, do you possibly have a second one to test it with. Video cards aren't to cheap, so I wouldn't want to buy one unless I was certain it was needed.

---

### Post by lpaulstudio on 2008-02-23
I don't have anything plugged in besides the video card. My motherboard came with a ethernet port, audio jacks keyboard/mouse ports, 4 USB ports and the like. But I don't need anything except for the video card. I am at a complete loss for why I can't get ubuntu to work. So what about the 6.10 version of ubuntu? I think I almost got it to work. Are there any commands you think I should try at the command prompt?

---

### Post by seventhc on 2008-02-23
Have you tried booting the cd in safe graphics mode?
I know you've tried just about everything so it's hard to remember everything.
One thing to consider though. When I install ubuntu on my machine, although I don't get errors, there are times I have to reboot severl times. Like it boots up, but right when it's about to go to the desktop the screen locks up and the screen is all filled with lines...it's hard to describe it. But my point is, I have to reboot sometimes like 3 times.
**Edit**: [COLOR=DarkRed]thats when booting from the cd, not the installed version.[/COLOR]

---

### Post by lpaulstudio on 2008-02-23
Really??? That happens to me all the time. I know exactly what your talking about. Like the bar splits up and goes evrywhere. Yeah that happened a few times to me. So should I just keep trying it? Basically, one of three things happens. either it freezes at the loading screen, I get the lines, or I get to a black screen with white text that usually has a bunch of numbers and code and an error that says something like "trying to fix up but reboot is needed". maybe if I just keep trying it will work?

---

### Post by seventhc on 2008-02-23
it might, but I would still try choosing *safe graphics mode* from the menu.
It's either the second or third choice.

---

### Post by lpaulstudio on 2008-02-23
yeah, i've tried safe graphics mode. i'll try it again though. thanks man. You guys are so helpful here. You make new people feel welcomed and answer all my questions no matter how dumb or simple. I really like this forum, much better than all the rest. Thanks for everything. I guess i'll just try it over and over until it works. haha.:)

---

### Post by seventhc on 2008-02-23
Yeah, I like this forum too, it's great. While some problems are harder to solve than others, most get solved fairly quickly.
I wish I had a way to get your working, but I'm not to sure what else to try.
At this point I would even clean the CD dive. If you have a cleaner, just to make sure it's reading the disk correctly.

---

### Post by lpaulstudio on 2008-02-23
You know what's weird. is that ubuntu was working on my computer before I upgraded it. I only upgraded because it was SO slow that i couldn't even finish the installation. So I never got it onto my hard drive but i could boot from it off of the CD, and now I cant. That's kinda weird. I'm wondering if it has something to do with the new mother board or processor. 
See, when I went to go buy new hardware, I picked whatever was the cheapest cause I had around $270 that I could spend and I needed a lot of new stuff. So I got a motherboard/processor combo deal for $100. then I bought the RAM and new power supply. I'm wondering if I just bought a crappy motherboard? It was $60 by itself. That was really cheap compared to most of the other ones they had there. Maybe I should try to return it. Like I said before, i'm getting my guitar teacher's computer (eventually) and I don't know what he has inside there but if it's new enough, I might not need all this stuff I bought. I think if he has a pentium 4 or newer, i'll just return the stuff I bought and get a new motherboard. Plus, then I then I have the option for more RAM (not that I really need it). My motherboard only support 2gb of RAM. Just an idea.

---

### Post by lpaulstudio on 2008-02-23
A cleaner?  is it something I spray, like compressed air? I don't want to take it apart cause it's kinda hard to get back together (already done it once).

---

### Post by seventhc on 2008-02-23
Well, it should definitely work with a p4.
Do you know when your getting your teacher's computer?
Maybe if you return this stuff, you can just save your money, or put it into your teachers comp if you need anything for it.

---

### Post by seventhc on 2008-02-23
> **lpaulstudio said:**
> A cleaner?  is it something I spray, like compressed air? I don't want to take it apart cause it's kinda hard to get back together (already done it once).
no, they have a disk with a little brush attached to it, it takes a solution then you just play it. It basically cleans the lens. If you can see it when you open the tray you can probably use a q-tip and nail polish remover or rubbing alcohol.

---

### Post by lpaulstudio on 2008-02-23
I'm pretty sure i'm getting next thursday. He's old and worried about security. He wants me to erase everything on it, which I will, but doesn't seem to believe that it's so easy to do. Plus the computer won't even be connected to the internet, but he's still paranoid. So's he's been delaying giving it to me, but i'm not going to ask, that would be rude since he was nice enough to give it to me in the first place. 
He's got a pretty nice box and he's running xp (which would be nice to have). The problem is, if i don't like his motherboard and decide to use mine, his machine is old and he most likely has a IDE hard drive, not SATA. The problem is that, my motherboard has four SATA ports but one IDE port. Right now I have one 160gb hard drive and the CDROM plugged in, because their both IDE. But if i try to use his hard drive too, I wont have enough ports unless I can find a ribbon that has four connectors on it.

---

### Post by lpaulstudio on 2008-02-23
Yeah, ill probably just clean it manually with q-tip like you said. Thanks for all the help and info. I'm gonna go and try to get this thing workin. Thanx again!

---

### Post by seventhc on 2008-02-23
You're welcome,
although I do wish it worked.

Tell your teacher you can erase everything so that it's impossible to be recovered with a program called *secure-delete. *(would take a very long time)
I think the default setting overwrites data like 38 times..
But thats after ubuntu is already installed. ;)

---

### Post by lpaulstudio on 2008-02-23
Success! I have finally gotten ubuntu on my computer! I have so far only been able to get version 6.10 not 7.10 but that's alright. I very happy!

---

### Post by seventhc on 2008-02-24
I'm glad it finally installed.
Maybe 7.10 will goto your teachers computer easier when you get it.

---

### Post by lpaulstudio on 2008-02-24
hopefully. I haven't gotten 6.10 installed all the way on my hard drive. it said the installer crashed. But i'll get it to work. it's just annoying cause it takes a bunch of reboots to get it to work.

---

### Post by seventhc on 2008-02-24
> **lpaulstudio said:**
> hopefully. I haven't gotten 6.10 installed all the way on my hard drive. it said the installer crashed. But i'll get it to work. it's just annoying cause it takes a bunch of reboots to get it to work.
OH, I thought you got it installed.

---

### Post by tke1384 on 2008-02-24
I've tried a great deal many things installing both from the desktop CD and the alternate CD from a CD and from an image on a external USB drive.  I'm finding the problem seems to be related to formating my SATA HD that it recognizes as a SCSI do you find your problem and mine are related?

---

### Post by lpaulstudio on 2008-03-02
Maybe that's it! Although I don't have SATA hard drives. Mine are IDE. But maybe it's something like that.

---

