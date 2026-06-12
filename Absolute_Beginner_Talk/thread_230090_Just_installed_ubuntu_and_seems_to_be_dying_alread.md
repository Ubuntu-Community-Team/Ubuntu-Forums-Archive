---
title: "Just installed ubuntu and seems to be dying already!"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by woodlandjustin on 2006-08-05
I installed ubuntu this morning. Already it seems wierd. I hibernated it, turned it on, worked more, shut down, on again, more work, and hibernated again. Few hours break, Now on again, but as it was turning on there were some worrying looking graphics, like messed up looking, all wierd, but after some moments it booted up fine. Firefox was open but the tabs were closed. I THINK I left it with a few tabs open. Anyway, I am following some help on another problem on the forums so I had to open a terminal, but:

When I try to open a terminal via "applicatoins", a box appears on the bar at the bottom of the screen saying "starting terminal", it waits a while, then that box disappears. No terminal appears.

Why is this? Is my hard disc sick? I wiped SUSE and Windows 2000 as SUSEs password mysteriously changed upon turning on from a force turn off (shut down didn't work) and also windows couldn't shut down or hibernate or anything without me holding down the power button too. Is this all connected? Now I have ONLY Ubuntu, and I beleive it erased the hard disc completely, so I thought all would be well.
Thank you
Justin

---

### Post by woodlandjustin on 2006-08-05
As I was typing away on an email, the 3 terminals just popped up! So that took about, 10  minutes?
Justin

And, what's with this window I'm typing into now? It went wierd. It's been doing that since I installed Ubuntu. Sometimes suddenly it just goes wierd like I am typing in the middle, and then the cursor goes to the left but the typed words go on on the right, or the words go onto a new line but in the midle of the page it all looks really wierd!!! But I just keep on going, and when I preview my post, it looks totaly normal. But it is rather offputting. Is there a way to make it behave normally? 

Also maybe a seperate thing, many times now I have been typing and suddenly everthing is deleted!! As if I have done a select all and then typed over it or something. Luckily I just do control z. But it is pretty frustrating. What is it doing that for and how do I make it stop?

Thanks!
Justin

---

### Post by Third Thoughts on 2006-08-05
It does sound like there's something wrong with your hardware. The best way to figure out if its the hard drive is to run a LiveCD and see if you have any problems. If not, then its probably your hard drive, and if so, then the problem might be in your mobo or something like that. The fact that all 3 OS's haven't been happy though is very disturbing. I'd suggest giving a couple different LiveCDs a try. Start with the Ubuntu Install CD, and then download Knoppix, dyne:bolic, Damn Small Linux... there are thousands of choices.

~Andrew S.

---

### Post by woodlandjustin on 2006-08-05
I was using DSL before ubuntu and it worked fine. Then when I got ubuntu I was first using the live CD. It was tortourously slow. And very ofen when I use the internet I will have 10 or more tabs open (for example now I have 7). That was not possible with the live CD. Kind of made it crash, or maybe I just had to wait, but I wasn't going to wait over 5 minutes just to be able to close the window! I couldn't do anything at all!

Anyway with the live CD I wouldn't be able to test hibernating, right? And, it DOES shut down and hibernate. The other 2 OSs were running for several years, and just in the end went funny. 
And since I wrote the above post, I have NOT shut down or restarted, I have ONLY hibernated for the night, and now turned back on, and, although those worrying graphics did occur during the coming-out-of-hibernation process (but is that normal? Like for example, a box maybe 2/3 the sixe of the full screen, red with lines down it. Then, the same box but with what looked like messed up obliterated script along the top section of it.
Anyway, now the terminal opens up fine, without any problem. Still, it seems to be a sign that SOMETHING is wrong. Is there any diagnostic test I can run? Running a live CD I would guess would just look normal and probably not indicate any problem.

Thanks
Justin

---

### Post by mjpatey on 2006-08-05
woodlandjustin-

The Live CD will show you whether the problem is likely your hard drive.  As Third Thoughts mentioned, the ability to run without these problems from the Live CD would point to the HD as a strong possibility, since the HD is the main component that's not used during a Live CD session.

I also couldn't help but notice you mentioned your hardware began to break down only after "several years"... you didn't mention exactly how many years, but a lot of stuff will start acting funky at 3, 4 or 5 years of age.

Live CD's your best bet.  And thankfully, hard drives are cheap!

-Mark

---

### Post by woodlandjustin on 2006-08-06
> **mjpatey said:**
> woodlandjustin-

The Live CD will show you whether the problem is likely your hard drive.  As Third Thoughts mentioned, the ability to run without these problems from the Live CD would point to the HD as a strong possibility, since the HD is the main component that's not used during a Live CD session.
[...]
-Mark

But I already said that the problems are not so simple as that, for ewxample, the terminal thing - now it works fine. So if it worked fine also on a live CD, that doesn't tell me anything.And like I said, I already used DSL and Ubuntu live. And, the problem with hibernating etc, like I said, wouldn't be diagnosed with a Lve CD, would it?
I do appreciate your response though. Any more suggestions also gratefully accepted. Especially if anyone knows how to successfully diagnose what the problem is.
Justin

---

### Post by TheWizzard on 2006-08-06
hi justin,

your problem sounds like hardware troubles. please check your ram and hdd! 
- for testing your ram you can use the Memtest86+ that is in the ubuntu startup menu and in the menu of the installation cd.
- for testing your hdd use e2fsck. it is on the rescue-cd, which you can download from [http://rescuecd.sourceforge.net/](http://rescuecd.sourceforge.net/) .  to test your first hdd, type "e2fsck -c -c  /dev/hda"

further, i would recommand to shutdown and not hibernate when you go to sleep. the linux kernel is very stable and can run for months or years non-stop, but the gui and software may leave junk in ram and runaway processes. 

good luck.

---

