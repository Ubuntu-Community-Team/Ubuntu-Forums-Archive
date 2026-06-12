---
title: "Screen Corruption/Crashing -- Computer Unusable"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Unicow on 2007-12-13
I'm having some pretty extreme errors with my computer. I'm not sure if it's ubuntu's fault with something that I've done or if it's a hardware failure (I'm beginning to suspect it's the latter, due to what I'll explain later), but things have gotten to the point where my desktop computer is virtually unusable. I'm new to linux -- I've been using it for about three months now, so I'm not completely uninformed, though this problem greatly passes the scope of my abilities --, so I ask, please, that you bear with me if I have problems relaying what needs to be known.I'm using a Dell XPS that I purchased about a year ago that was pretty high-end for the time, and ran me about 1K$.

My problem is with screen corruptions and errors -- even things that, to me, a graphics card failure wouldn't effect, though my knowledge in this is limited. Sometimes my screen will go either mostly off-white or, conversely, extremely colorful, usually with corrupted images of what was just happening on-screen. Other times, it won't eve get past the log-in screen. It automatically does this every time I restart the X server from the log-in screen, too.

Things DO NOT freeze up if I switch to a console window (alt-f2, for example) and work from there, but, of course, working without my KDE GUI is very limiting. There are STILL glitches that occur when I'm in this console-only mode, though. Random letters will display in random colours, and sometimes I'll type, say, 'x' on the screen and it will show up as another random letter.

...I guess it is starting to sound like my graphics card. I guess it can't be kubuntu, given that I've a slew of other problems, like how before kubuntu is booted to, my screen is dotted with random pixel colours (usually red, blue or green), even at the first screen where there's the big DELL logo. For the past four or five weeks, too, when I was able to actually log in and get things working, the tops and bottoms of my scroll bars would be glitchy, and display black with random colors dotted in. I've got no idea what could be making some characters show up as something erroneous, though.

For example of that last bit, I've got my computer set up to boot first from floppy, then check the hard drive. I'm always greeted with an error that says nothing is found in the floppy drive and to go ahead and press F1 to continue.

I'm looking at it now. It /should/ be displaying this:

Floppy diskette seek failure
 Strike the F1 key to continue, F2 to run the setup utility.

What it is displaying is:

FlOppy diskette s%ek failure
 Strike the F1 key to continue, F2 to run the setup utility.

...so, am I going to have to buy a new graphics cards? :(

---

### Post by innuendosoft on 2007-12-13
According to your statements, I would say there's a video card issue here. But if I were you I would try some other things before throwing the card to the bin.
- Reset BIOS options to default settings
- Remove floppy drive from boot sequence (at least to get rid of that msg!)
- Try another monitor if available
- Try a OS fresh install (consider running Ubuntu live from cd)
- Try another graphics card if available

Best of lucks!

---

### Post by deadgobby on 2007-12-13
What version of the XPS?
See these links
[https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1210?highlight=%28dell%29](https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1210?highlight=%28dell%29)
[https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1330?highlight=%28dell%29](https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1330?highlight=%28dell%29)
[https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1710?highlight=%28dell%29](https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1710?highlight=%28dell%29)
[https://wiki.ubuntu.com/LaptopTestingTeam/DellXpsGen2?highlight=%28dell%29](https://wiki.ubuntu.com/LaptopTestingTeam/DellXpsGen2?highlight=%28dell%29)
 Gobby

---

### Post by kevinatkins on 2007-12-13
Hi,

This does look like a problem at the hardware level, as opposed to the operating system.

It could be any number of things, so I think you're going to need to do some testing.

The first thing I'd do is run a memory test. If you grab an Ubuntu installation CD and boot from that, you'll see an option for 'Memtest86' - select that and allow it to do a full run. It might take some time, but if there are problems with your memory, it should reveal them.

Next, even if memory test goes through OK, I'd still be inclined to try a different stick of memory in the machine - I have had one case where memtest86 passed OK, but the memory was still faulty.... Do make sure that you observe anti-static precautions when handling memory, or any other internal part, and handle by edges only.

If memory proves OK, it might be worth disconnecting / removing as much as you can from the motherboard, for instance any non-essential PCI cards, unused drives, etc then try booting again to see if the problems go away.

I think it will come down to a process of elimination, starting with the cheapest / easiest things first...

---

### Post by Unicow on 2007-12-15
Hello, this is unicow again. I tried the suggested things, though nothing of note happened to change the situation. Then I thought to open it up to take a look, and I noticed that my graphics card was caked with dust. I blew off a lot off it, and used my finger to clean up some more where I thought I wouldn't be at a shock rist, and lo and behold, when I booted back up, conditions were much better. I'm no longer seeing so many stray pixels though there are a few.

I'm going to figure out a safer way of cleaning it up (static electronic damages computers, I know that much) and see if this elimnates the problem entirely.

thank you for advice. it was right in thinking it was a hardware problem.

---

### Post by Unicow on 2007-12-15
I forgot, I wanted to ask: can anyone reccomend any techniques to cleaning up a dusty system in a safe manner?

---

### Post by tekwerx on 2007-12-15
> **Unicow said:**
> I forgot, I wanted to ask: can anyone reccomend any techniques to cleaning up a dusty system in a safe manner?

Go to your local computer store and get some canned air.  Feel free to use those puppies till theyre empty - just be warned: you WILL make a mess by blowing all of that out of there.  Oh, and dont shake when you spray.  The can will tend to spray liquid instead of a vapor.  :(

---

### Post by Unicow on 2007-12-15
Thank you very much! I will go buy my local Best Buy and see if they can get me what I need.

Who would of thought that something like dust could have such an effect? :???:

---

### Post by tekwerx on 2007-12-15
> **Unicow said:**
> Thank you very much! I will go buy my local Best Buy and see if they can get me what I need.

Who would of thought that something like dust could have such an effect? :???:

Dust is the enemy of your machine.  Ive had this happen to me before and I knew right away you'd open it up and find that.  This will sound silly, but use a vacuum cleaner with a soft brush extension on it to suck away some of the dust as well - that will cut down on some of the mess.  Also, its usually good practice to make sure you clean it out every three or four months.

---

