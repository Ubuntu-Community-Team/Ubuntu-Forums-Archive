---
title: "New user here!"
date: 2011-02-21
forum: Apple Hardware Users
---

### Post by NooBuntu63 on 2011-02-21
Hey all!

I downloaded 10.10 yesterday and finally got it installed on a laptop, and...wow.
I knew about Ubuntu before, but never got around to exploring it, so I'm basically a newbie at it.

About me:
I'm an Apple guy. Have been, all my computing life. However, I'm feeling a little estranged, increasingly so, from Apple after all these years; perhaps Steve's illness is wreaking havoc on his brain chemistry, but Apple seems to be devolving more and more into v2.0 of an Evil Empire, albeit a much more stylish one than Gates envisioned. (Windows creeps me out; feels soulless, and just makes me very uncomfortable, so it's not even an option. I did my first-ever Windows install on this Acer the day before yesterday and felt unclean for the rest of the day. I wiped it.)
In any case, I'll still be using Apple, but now have a viable alternative. I am investigating moving all my mail and web-browsing activities to Ubuntu, leaving the creative stuff on Apple (for now, anyway).

What I do?
• Musician and audio engineer. Split between Digital Performer and Logic, with some ProFools looming on the horizon. Yes, I'll be looking into Ardour. :D

• Photographer. Commercial and modeling. I've just recently upped my Photoshop to CS4, and added Lightroom, so I'm pretty enamored with those for now. I don't expect to be able to shift that to Ubuntu anytime soon.

• I volunteer at a non-profit that refurbishes used computers, LCD monitors, and other electronic accessories, and gives them to the needy, under-employed, circumstance-victims (like last summer's fires outside of Boulder), etc. That's how I got the spark for Ubuntu lit under me again, as we let all out machines out the door with either LinuxMint or Ubuntu.

• I work part-time at an electronics parts supplier. Which has next to nothing to do with Ubuntu, just figured I'd round out my "do" list. :)

So, here I am, Ubuntu installed on a 2-3 year old Acer 4620, although I'm typing this on my MacBookPro as I haven't begun any transition yet. Which brings me to some noob questions.... and yes, I will be using the search functions a lot, but if you're a person who's reasonably skilled but not a code-geek, you'd have to agree that the language around here can be rather daunting, so coddle me a bit while I ask some probably searchable questions due to limited time and potential to be overwhelmed.

Thanks. :D

While this Acer's kinda neat, I'm not terribly interested in keeping it around as a main device. I'm a little spoiled/accustomed/hooked on Apple's hardware, admittedly. So my first question revolves around hardware. I have the following machines I could/might like to install Ubuntu on:

Early 2000's Powerbook G4 800Mhz 
Early 2000's Powerbook G3 (Pismo) 500Mhz
2004/5-ish Mac Mini 1.25Ghz PPC
2005/6-ish Macbook 1.83Ghz Intel
And out of four G5's - 2 quad-cores and 2 dual procs - I might be interested in running it on one of the dual procs or one of the quad-cores. Now the QCores need work (rebuild cooling system), and may not even work in the end, but whatever. All PPC.
I have plenty of RAM and a few spare hard drives for all of this, so I can configure to meet needs.

I smell potential headaches trying to figure this all out, especially when I try to read the forums looking for people who've put Ubuntu on similar machines. ANY pointers, direction, or shortcuts to the threads/forums I need for these machines will be greatly appreciated.

I also have a handful of Compaq nc6000's I'd like to install Ubuntu on, and one nx6125 that might get it, if I can prove the motherboard isn't dead.

So, yeah... I've got a handful. Any help is appreciated!

Dave

---

### Post by bapoumba on 2011-02-21
Welcome :)

I've moved your thread to the Apple Users section where I'm sure people will give you sound advices.

---

### Post by NooBuntu63 on 2011-02-21
:LOL: Right out the gate I get it wrong. Awesome!

---

### Post by bapoumba on 2011-02-21
> **NooBuntu63 said:**
> :LOL: Right out the gate I get it wrong. Awesome!
Nah, no worries. Even after I got to the Staff team I discovered some areas on UF ;)

---

### Post by NooBuntu63 on 2011-02-21
Okay... now I've got my first little frustration with this scenario....

I'm seeing the 10.4 is recommended for the older laptops, but if there's one thing that is NOT easy to find on Ubuntu.com, it's download links to earlier versions. Help?:confused:

---

### Post by realzippy on 2011-02-21
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by rg4w on 2011-02-21
The main download page has a popup menu where you can select 10.04 LTS:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

But note that for your G4 machines you'll need the PowerPC version, available here:
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

### Post by NooBuntu63 on 2011-02-21
I thought I saw, somewhere here, that someone had successfully run 10.04 on a PPC machine...

---

### Post by bdentremont on 2011-02-21
Welcome.  I've been a Ubuntu user for several years.  I like Apple hardware too and recently got a Macbook Pro.  I now dual boot with OS X, but mostly Ubuntu.  I can't address any of your hardware specifically, but here are some general thoughts:

1) There are separate wiki pages for Ubuntu on every version of Macbook/Macbook Pro ([https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)) which are invaluable and detail exactly what works by default and what needs tinkering and how to do it.  I suspect that you can find similar pages for the other hardware which will give you an idea exactly what would be involved on each machine.

2) If you're dual booting or sharing eternal hard drives the choice of filesystems for shared data is a bit tricky and worth thinking about before you partition.  The following guide is quite worth reading:
([http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems](http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems)).

3) I'm a mechanical engineer and would put myself in the "reasonably skilled but not a code-geek" category.  Learning a few bash commands (sudo, cp, mv, chmod, chown, man ...), finding a couple of text editors (nano, gedit), and learning to manage packages (apt-get, synaptic) will go a LONG way to making the forums more readable and making the command line a friend not an enemy.  The bash commands and nano are also available in the OS X terminal and may enable things your Mac friends never thought possible. :-)

Good luck.

---

### Post by Tu1J4kXk8NUhMz on 2011-02-22
> **bdentremont said:**
> 2) If you're dual booting or sharing eternal hard drives the choice of filesystems for shared data is a bit tricky and worth thinking about before you partition.  The following guide is quite worth reading:
([http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems](http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems)).

I want an eternal hard drive. :p I realize I'm being a smart-@$$ (and that it was a typo), but it sounds like an awesome piece of hardware...you know, if it existed.

> **NooBuntu63 said:**
> What I do?
&#8226; Musician and audio engineer. Split between Digital Performer and Logic, with some ProFools looming on the horizon. Yes, I'll be looking into Ardour. :D

&#8226; Photographer. Commercial and modeling. I've just recently upped my Photoshop to CS4, and added Lightroom, so I'm pretty enamored with those for now. I don't expect to be able to shift that to Ubuntu anytime soon.

&#8226; I volunteer at a non-profit that refurbishes used computers, LCD monitors, and other electronic accessories, and gives them to the needy, under-employed, circumstance-victims (like last summer's fires outside of Boulder), etc. That's how I got the spark for Ubuntu lit under me again, as we let all out machines out the door with either LinuxMint or Ubuntu.

&#8226; I work part-time at an electronics parts supplier. Which has next to nothing to do with Ubuntu, just figured I'd round out my "do" list. :)


Perhaps it's a bit late to point this out, but considering your "do" list (he he), you should check out Ubuntu Studio. It's a distro of Ubuntu which comes prepackaged with much of the software you'll probably be looking for anyway (if Ubuntu ever becomes your production OS, anyhow).

> Early 2000's Powerbook G4 800Mhz 
Early 2000's Powerbook G3 (Pismo) 500Mhz
2004/5-ish Mac Mini 1.25Ghz PPC
2005/6-ish Macbook 1.83Ghz Intel
And out of four G5's - 2 quad-cores and 2 dual procs - I might be interested in running it on one of the dual procs or one of the quad-cores. Now the QCores need work (rebuild cooling system), and may not even work in the end, but whatever. All PPC.
I have plenty of RAM and a few spare hard drives for all of this, so I can configure to meet needs.

I was under the impression that PPC hardware was no longer supported. Much in the same way as Apple is doing, PPC is going the way of the dodo, I'm afraid. However, it would seem that PPC is still community supported. In fact, I have an original stone PlayStation 3 with "Other OS" support and have installed Xubuntu PPC on it (quite a while ago). I haven't fussed with it too much since then, but there's a sticky at the top of the Apple community page explaining where to download PPC versions of Ubuntu.

Good luck with your transition. I have software I commonly use on Mac OS X and Windows (necessary evil...couldn't agree more with you), though I would like to soon move to an open source workflow which only uses Ubuntu. There are many users who have done so, and it's definitely an effective option.

One more piece of advice...bookmark UbuntuForums and visit frequently. The community is great at answering questions, so if it hasn't been asked and answered already, just ask it and it will be answered. Ubuntu is moving more towards a mainstream (and therefore intuitive) interface, but there's still a lot to get confused about.

---

