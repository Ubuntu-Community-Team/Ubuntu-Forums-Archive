---
title: "Gutsy is ssssllllooooowwww"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by josborne31 on 2008-01-14
I recently setup a dual boot for Windows XP Pro and Gutsy. Windows continues to work normally, but anytime I boot into Gutsy I have issues. The problem is that Gutsy gets progressively slower the longer I am logged on. I don't typically do all that much in Gutsy, mainly web browsing (using FireFox) or attempting to use its default mail manager (can't recall its name). If I do much more than that, Gutsy tends to slow down to the point that I can click on a link and wait almost 10 to 15 seconds before it will actually click. 

What is going on, or better information might be how do I start diagnosing and troubleshooting this issue? I am new to the whole Linux thing, and don't know the tools and commands that would help. If this were going on in Windows, I am a lot more versed in troubleshooting.

TIA

---

### Post by asmiller-ke6seh on 2008-01-14
What kinds of things, do you think, in Windows might cause this? You might want to try a different browser, and see if you have the same problem? How much RAM does your system have? Do you use Firefox in Windows?

Firefox can really eat RAM, and if you have limited RAM, you might be experiencing RAM cram, resulting in the need to cache to SWAP. If your SWAP drive is not set up properly, you could be having problems.

---

### Post by josborne31 on 2008-01-14
I have had issues with Firefox (older versions) leaking RAM in the past, but the upgrade to 2.0 (and later) fixed those issues. I don't think that Firefox is the sole cause of the issue, as browsing my HDD in Ubuntu can cause the same problem. 

I should have plenty of hardware to support the linux distro: 
AMD Athlon 64 X2 +3800
2 GB of RAM
74 GB HDD (10k rpm)

I do use the same version of Firefox in Windows, and it doesn't have this issue. Causes that would contribute to this in Windows would include an application that stopped responding, temporary internet files too excessive, multiple background processes running, spy/ad-ware, hardware driver errors, IRQ conflicts, and occasionally if you haven't updated your anti virus software it takes a while to update and scan. Those are all items in Windows I know how to check and correct.

---

### Post by asmiller-ke6seh on 2008-01-14
<scratches head> sounds like you have plenty of RAM.

Next person; next suggestion.

---

### Post by Samhain13 on 2008-01-14
Run "top" and see what's eating the most resources. If it happens to be something called "tracker", you can go to Preferences > Sessions and uncheck it so that it doesn't start automatically at session start. Just a suggestion, though. :)

If it's something else, post the results here so someone else can take a look at it and offer another suggestion.

---

### Post by josborne31 on 2008-01-14
I wonder if this has something to do with Compiz? I haven't used Linux much, but I started using it more once I enabled the 'cube desktop' feature. I don't know for sure, but maybe the slowness started <i>after</i> i enabled this feature. 

I don't want to get rid of the cube desktop, as that was (sad to say) one of the main reasons I started checking out Linux to begin with. 

Anyone had experience with Compiz causing slowness? 

I just saw the 'tracker' post. I will check that this evening and let you know the results.

---

### Post by asmiller-ke6seh on 2008-01-14
> **josborne31 said:**
> The problem is that Gutsy gets progressively slower the longer I am logged on.
This sounds like a memory leak as one possible problem.
> **josborne31 said:**
> I don't typically do all that much in Gutsy, mainly web browsing (using FireFox) or attempting to use its default mail manager (can't recall its name). If I do much more than that, Gutsy tends to slow down to the point that I can click on a link and wait almost 10 to 15 seconds before it will actually click. 

This sounds like RAM cram as one possible problem.

In either case, 2 GB of RAM is a lot, and I would not expect to see these symptoms with such relatively light use. Therefore, it must be something else.

Are you running the 64-bit version for AMD, or the 32-bit version? Ubuntu, Kubuntu, or other? Since you mentioned Compiz, what kind of video card do you have, and how much memory does it have -- onboard or shared RAM? What driver are you using? If nvidia are you using the Free- or Non-free driver?

---

### Post by wolfen69 on 2008-01-14
try diabling ipv6 in firefox. [http://en.opensuse.org/Disable_IPv6_for_Firefox](http://en.opensuse.org/Disable_IPv6_for_Firefox)

---

### Post by asmiller-ke6seh on 2008-01-14
> **wolfen69 said:**
> try diabling ipv6 in firefox. [http://en.opensuse.org/Disable_IPv6_for_Firefox](http://en.opensuse.org/Disable_IPv6_for_Firefox)

I'm curious as to why you think this would solve josborne31's problem?

I have a 1GB system, and I haven't disabled IPv6 in Firefox, and I have none of the problems that josborne31 is experiencing.

---

### Post by wolfen69 on 2008-01-14
for some, it may work. if it doesnt work, it can be easily reversed. that's all.

---

### Post by asmiller-ke6seh on 2008-01-14
> **wolfen69 said:**
> for some, it may work. if it doesnt work, it can be easily reversed. that's all.
The speed gains in a browser for disabling IPv6 are so small - - and what josborne31 is describing is so very different than (and probably totally unrelated to) IPv6 in FireFox.

He stated:
> The problem is that Gutsy gets progressively slower the longer I am logged on. 

That is not an IPv6 browser "slowdown" problem.

---

### Post by josborne31 on 2008-01-29
Sorry for the long delay in answering the post's suggestions. 

I am still experiencing the issue. To clarify, the entire computer gets slower the longer I am logged in whether I use Firefox or not. This leads me to believe it is not Firefox.

If it were related to Firefox, I would assume that closing all running Firefox windows would resolve the issue. This is not the case either. 

I ran the command Top, and to be honest I am not sure what is considered the biggest hog of resources. 

Its either Gnome-terminal, XGL or its init. How do I tell which is the resource hog? Those three processes were showing the highest numbers under the heading RES. 

Respectively, the numbers they show are 26m 84m and 1964. 

Does that help?

---

### Post by prostar on 2008-01-30
Would you say that you get about 100seconds of useful time before it slows down?  I would assume that it's the "tracker" search tool indexing your files the same way windows "file indexer" does.  I used to curse at win98 until I learned what was happening.  You can tweak the settings in System -> Preferances -> Indexing preferences.  Throttle it down to the slower end.  _OR just let it finish for once_.  I am guessing you always end up rebooting before it finishes.  It won't have to do that again unless you delete it's database or something.  

Another tip.  Right click on your top "panel"->add to panel, and add the system monitor.  Then right click on the monitor and set what things you want to watch.  CPU, Network, and disk will give you a good overview.  Now anytime you want to see what's happening you can just left click the system monitor and get a windows style task manager.

Good luck.

P.S. One last tip: if you're not familiar with top, do your self a favour and get "htop"

---

### Post by josborne31 on 2008-01-30
File Indexer huh? I guess I hadn't really thought about that. Last night, I let it just sit while I went and fixed dinner before I worked on it. It did seem to be faster after dinner than it was before, so the indexing might have been the issue. 

And thank you for the tip on adding the system monitor. I am anxious to figure out all I need to know in order to be more proficient with Ubuntu. The "Windows style" system monitor would be very handy!

---

### Post by prostar on 2008-01-30
Since you seem to be new to Linux, and also I have time to kill at work, I'll throw you some more bones....

[LIST]
[*]The ipV6 disable is worthy.  It can cause firefox to sit there looking for an ipv6 DNS server when there is none.
[*]Whether it's Winblows or Linux get the "fasterfox" extension, or search the forum on Firefox speedup.
[*][www.gnome-look.org](www.gnome-look.org)
[*]While you're adding things to the panel, add weather and some launchers for you favorite apps.
[*]You can use evolution(email) to read your gmail.
[/LIST]

Cheers.

---

### Post by budlatte on 2008-01-30
i have a similar problem, but it my computer is slow no matter how long the computer is running for, (tracker isn't even on on the top readout) and i suspect xgl/compiz-fusion is to blame since it is always at or very near the top.  The cube desktop works fine until there is a window open on any one of the virtual desktops, then it is slow as sin, and none of the visual effects like wobbly windows and the like work correctly.

I have a sinlge core AMD 64 3500+ processor, but was told that gusty shouldn't hog so much of the CPU.  I really don't want to reinstall gusty, i am thinking i will remove xserver-xgl, and try to reinstall it along with comp-fusion.  I am almost ready to buy a 64 X2 3600 dual core, but before i do that is there something quicker or easier is should do that, or go through reinstalling xgl?

any help would be great

---

### Post by LowSky on 2008-01-30
why buy a X2 3600+, your gains wont be that much.
I have an much older Athlon 2500+ running on 256 MB RAM and it is running just fine. My 3700+ with 2 GB of RAM is  a champ and can run anything I throw at it

 The best thing to do is turn off tracker (as it is still running even without the icon on the top panel. Also turn off Advanced Desktop features, and see if the system speeds up.

Make sure you have the newest driver for your video card. ATI video card are problematic so I would start there. No need replacing your processor when it works Just fine.

---

### Post by josborne31 on 2008-01-30
I did the ipv6 disable last night before dinner. I need to read up further on what it does and why it doesn't effect Windows boxes like it does Linux. 
The fasterfox extension doesn't do much that I haven't already done without the extension, so i probably won't bother with it. 
Good link, will have to look into it more this evening and over the weekend.

I plan on really playing around with Gutsy this weekend. I want things working better then they have been, and to do that I need to not only know what is working properly but what is not.

---

### Post by budlatte on 2008-01-30
the only reason i was looking at the X2 3600 is because its the only dual core i can find for the socket 939 mobo i have, and it's 50 bucks from tigerdirect.com

i do have an ATI X700 pro video card that i have had a lot of problems with when i used edgy, but gusty and the ati restricted drivers seemed to fix it.  I am pretty sure the drivers are the latest ones, but i will double check tonight.

are the Advanced Desktop features you mentioned separate from what compiz-fusion is running? I don't think i have ever touched the Advanced Desktop features, but again, i will check tonight.

Thanks for the advice

---

### Post by budlatte on 2008-01-30
i changed some settings in compiz-fusion and installed fasterfox and things have improved greatly.  i may still upgrade processors depending on how it recacts to programs like thoggen.  or possibly an overclock.  on a side note--i can only find the X2 3600 for the 939, do you know of places i could get a faster processor for the 939 mobo?

Thanks for the help.

---

### Post by josborne31 on 2008-01-30
Newegg.com has a couple of Opteron procs that are socket 939. 

The X2 3600+ is 2.0GHz, 64KB L1 (x2), dual core. L2 cache is 2x 256KB.
The Opteron 185 is 2.6GHz, 128KB L1 (x2), dual core. L2 cache is 2x 1MB. 
And its 4 times more expensive....so you decide which you prefer. 

There are other Opterons for the 969 socket on Newegg's site, so don't think you have to stay with that 185. Hope that helps.

---

### Post by prostar on 2008-01-31
budlatte:

  Your problem seems more like compiz/xgl isn't using your video cards acceleration.  Try using it without the desktop effects.  If you have a decent video card it should work the same with/without effects.  If it's not, look into how to get your graphics card working properly.  Search for gears and restricted drivers for more info.

Good luck.

---

