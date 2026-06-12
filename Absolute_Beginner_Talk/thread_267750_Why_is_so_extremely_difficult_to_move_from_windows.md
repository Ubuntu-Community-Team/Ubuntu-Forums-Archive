---
title: "Why is so extremely difficult to move from windows to linux?"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by sc0undrel on 2006-09-29
Every single time I try to switch to Linux, I get completely stuck on some kind of a problem/problems that is/are so difficult to solve that I just give up. Take for example my [Refresh rate](http://ubuntuforums.org/showthread.php?t=266556) which I'm unable to fix.

In WinXP installing the monitor's drivers took about 20 seconds, all I had to do was some mouse clicks and voila! It worked perfectly.

Now with Ubuntu (and every other distro, I suppose), I have to manually install the graphics card the drivers using the command shell (because Easy Ubuntu doesn't work), then edit some configuration files and finally the graphical interface doesn't even start, I don't know how to get back into X, replacing the xorg.conf file with the backup verson has no effect, since drivers are all messed up somehow. And the only solution for me is to reformat+reinstall everything all over again.

I'd really like to learn a bit more about Linux, but how am I supposed to do that if my eyes are bleeding, and solving such a simple problem like changing the monitor's refreshrate takes days  and all I have at the end are just a lot of headaches. =\

---

### Post by hyper_ch on 2006-09-29
My videocard was recognized with no problems... and I just installed the nVidia drivers yesterday... that was not a big issue either as there is a nice copy'n'paste howto...

---

### Post by scottbraun4571 on 2006-09-29
Hey scoundrel,

Ive had the same problem with my video card (its an ATI 9600 pro) and resolution switching. I agree that it is super frustrating when Windows lets you do something easily and Unbuntu wont. I just ran mine at 60 Hz, but evidently thats a problem for you, which is cool. 

If you goto the Ubuntu guide (ubuntuguide.org) there are instructions on how to install your specific video card. For the ATI card I have, I used the ATI wiki. For an nvidia card on another computer, i just used the simpler instructions from the guide.

Also, if you are having problems with Ubuntu, you could try out another distro, or just stick with XP. Ive found trying other distros that Ubuntu was the first one that actually recongnized my hardware, so i gave it a shot. But for you, obviously its different. If you need more help on the video card thing, reply!

---

### Post by petri on 2006-09-29
Is this your graphics card: Club3D X1900XTX 512MB?
Then, have you tried this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide?](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide?)


BTW you do know that you can copy with your left mousebutton and paste with clicking your scrollwheel?

And why it is so extremely difficult to move from windows to linux? Partly because of the vendors doesn't make any or too little drivers for their products for linux. The community has to make their own and that of course takes time. Next time you buy hardware ask specifically for products which has drivers to linux. When we all do that then in a couple of years there will be drivers for linux. :-D

---

### Post by Atomic Dog on 2006-09-29
> **petri said:**
> 
BTW you do know that you can copy with your left mousebutton and paste with clicking your scrollwheel?

And why it is so extremely difficult to move from windows to linux? Partly because of the vendors doesn't make any or too little drivers for their products for linux. The community has to make their own and that of course takes time. Next time you buy hardware ask specifically for products which has drivers to linux. When we all do that then in a couple of years there will be drivers for linux. :-D

I seriously didn't know about clicking the scroll wheel.  Holy crap that's a nice little tip!

I had a lot of trouble when I first installed Ubuntu on a desktop machine for work.  But I learned a lot.  I built a second Ubuntu box for work and it went much faster.  I then installed Ubuntu on my laptop (Toshiba M55) after a few quirks were ironed out it works great.

My point is that familiarity with an OS makes switching hard to do.  Once you use a linux distro for a while it gets easier.  I'm not about to say that it's easier than Windows, but the security issue alone is worth it for me.  Now if I need a Windows app I fire up my Windows VM and go to town.  I like trmnl svr client better, vpn works well, some apps I like for Win.

But I have to say that the more I used Ubuntu the less I used Windows...till one day I realized I never boot into Windows any longer.  Stay with it.  The experience alone is worth it.  One day you will deal with a linux box.  Especially in IT.

---

### Post by tommcd on 2006-09-29
I think the source of your problems (as others have alluded to) is your ATI video card. It is much easier to get nvidia cards up and running. Just get the drivers in synaptic, and you are good to go. This is because nvidia supports linux. ATI does not.

---

### Post by Javier_Electrico on 2006-09-29
Why is so difficult?? guess is because we're used to use A, and when we finally begin to use B, our brain asumes that we're in A.
It IS difficult for me to use Ubuntu, but I keep working, and I've and I'm learning a lot.
And about your video card trouble, i know that there's a ATI and NVIDIA packages.
Why don't you try $sudo apt-cache search your_video_card
grettings.

---

### Post by gn2 on 2006-09-29
> **sc0undrel said:**
> (and every other distro, I suppose), =\

Have you actually tried another Distro?

Give PCLinuxOS a go, it might work better, I have found it's much easier to set up than Ubuntu.
[http://www.pclinuxos.com/page.php?7](http://www.pclinuxos.com/page.php?7)

Won't beat around the bush here, the problem is almost certainly your graphics card. ATI have a long history of dreadful driver support for all operating systems, not just Linux.

---

### Post by petri on 2006-09-29
Oh my gosh! I have to be a Sherlock Holmes to be able to help you! 
And I'm just Homer Simpson :rolleyes: 

You are using 64-bits Ubuntu, right? Just follow my link above and use **Method 2**.


EDIT: And 64-bits Ubuntu is **not** for newbies! There is a dedicated forum for it,search here [http://ubuntuforums.org/index.php](http://ubuntuforums.org/index.php)

---

### Post by hyper7 on 2006-09-29
I find learning to be part of the charm of any *nix based OS.

You have to break a few eggs before you completely scramble your brain.

I do, because I can, twice as much as I would sitting around with windows warez.  Something about having a need and meeting it?

Go figure.

---

### Post by Atomic Dog on 2006-09-29
> **hyper7 said:**
> I find learning to be part of the charm of any *nix based OS.

You have to break a few eggs before you completely scramble your brain.

I do, because I can, twice as much as I would sitting around with windows warez.  Something about having a need and meeting it?

Go figure.

Once you start to learn a few things, learn some terminal commands, understand the file structure, and get familiar with your developer environment (Gnome, kde, ...), you find linux to be not so bad.  Plus there is a gaggle of software out there to suit most of your needs.

He's right, you do tend to scramble your brains at first, but it ends up as a beautiful and tasty omellette.:-D

---

### Post by BLTicklemonster on 2006-09-29
How lond did it take you to become proficient at windows? A week? Usually not, so however long it took you, you are now proficient at windows, and are looking at ubuntu, and are like me and everyone else out there. You don't want to take more than a day to master it. 

Take your time. Freedom comes with a price, but pricey things never come freely. wtf, where did that come from? anyway, stick with it, it's worth the trip.

---

### Post by BLTicklemonster on 2006-10-01
Bloody hell, I killed another thread.

---

### Post by sbergman27 on 2006-10-01
> **BLTicklemonster said:**
> Bloody hell, I killed another thread.

For what it's worth, I sometimes feel that way, too.
I think it's just a sort of statistical likelihood thing combined with our own selective memories.

I don't think they *really* all hate us. ;-)

---

### Post by white on 2006-10-01
[quote=gn2]ATI have a long history of dreadful driver support for all operating systems, not just Linux.[/quote]

That may be true now (Catalyst bloatware on windows, poor support for Linux/Mac) but it wasn't always that way. I remember when I looked forward to new Catalysts coming out. Hopefully with AMD+ATi now, we'll see true Linux support. :)

---

### Post by Josh1 on 2006-10-01
I found switching to Ubuntu so easy, but then again I know quite alot about computers in general so lol.

> **white said:**
> That may be true now (Catalyst bloatware on windows, poor support for Linux/Mac) but it wasn't always that way. I remember when I looked forward to new Catalysts coming out. Hopefully with AMD+ATi now, we'll see true Linux support. :)

Go and get an nVidia card, it'll run better then that pile of scrap metal they call ATI ;).
- Josh

---

### Post by white on 2006-10-01
[quote=Josh]Go and get an nVidia card, it'll run better then that pile of scrap metal they call ATI .[/quote]

ATi and nVidia have always had bouts for supremacy, the 9700/9800pro completely owned all the nVidia FX series, the 6800 and the x800 series were basically split down the middle, and the 7800/7900 series have taken the cake for now but as I said, with AMD+ATi we'll see much better offerings now. Better processes and AMD's fabs at ready, I know we'll see better offerings.

---

### Post by Cruz on 2006-10-01
(pay attention the the title)

Before, everything was so nice, efficient and free. And now...well, the hardware recognition worked really great and I set up my screen in half a minute, but now here I am flooded by viruses before I even set a desktop background. And I just can't find where the virus protection is enabled. In fact, I can't find ANY software here at all, I even had to download firefox and there I thought it comes with the OS. There isn't even an FTP client to copy my files from my old machine am I too stupid to find it or is it getting ridculous? Before I had a great community which answered to all my problems in less than 5 minutes. Now nobody seems to be able to help. I tried calling this hotline for a few dollars a minute and the guy on the other said I need to buy and install additional sofware. Starting from $150 for an office suite he babbled, but he couldn't tell me what's the shortcut to switch to another X-Server. I'm getting really frustrated. I tried to set the access permissions to my files but I can't handle this command line thing. I read the man pages to all commands in less than 5 minutes (there really aren't many) but couldn't find any helpful command to help me automate larger tasks in the future. Guess I gonna have to klick my way through this file explorer thing ALL THE TIME. And then I discovered there is no permissions, everybody has access to my stuff. I think I give up and go back to linux. These cutting edge technologies are always there for the smarter kind to use.

---

### Post by BLTicklemonster on 2006-10-03
:) good post, cruz

---

### Post by gn2 on 2006-10-03
> **Cruz said:**
> (pay attention the the title)

Before, everything was so nice, efficient and free. And now...well, the hardware recognition worked really great and I set up my screen in half a minute, but now here I am flooded by viruses before I even set a desktop background. And I just can't find where the virus protection is enabled. In fact, I can't find ANY software here at all, I even had to download firefox and there I thought it comes with the OS. There isn't even an FTP client to copy my files from my old machine am I too stupid to find it or is it getting ridculous? Before I had a great community which answered to all my problems in less than 5 minutes. Now nobody seems to be able to help. I tried calling this hotline for a few dollars a minute and the guy on the other said I need to buy and install additional sofware. Starting from $150 for an office suite he babbled, but he couldn't tell me what's the shortcut to switch to another X-Server. I'm getting really frustrated. I tried to set the access permissions to my files but I can't handle this command line thing. I read the man pages to all commands in less than 5 minutes (there really aren't many) but couldn't find any helpful command to help me automate larger tasks in the future. Guess I gonna have to klick my way through this file explorer thing ALL THE TIME. And then I discovered there is no permissions, everybody has access to my stuff. I think I give up and go back to linux. These cutting edge technologies are always there for the smarter kind to use.


Moderators, I know Aysiu has covered this in his "Zero Reply Posts" thread, but can we please have a separate sticky thread about people making posts in one great long continuous paragraph that just goes on and on, with no line breaks, or gaps between, because I find it can become difficult to understand also it's tiring on the eyes when you have to concentrate hard on where you are in the text and it's hard to refer back to something earlier in the text because it's not spaced out and I just find it hard to find if you know what I mean. I'm sure I'm not the only one who finds it a struggle to read posts like this where there aren't even gaps between the paragraphs. Don't want to come over as a bit of a grammar or language bore, it's just easier for folks to read if it's laid out better? Also it's more likely that people will take time to read through the post if it's laid out in a more user friendly format? Or is it just me, what do you think?

---

### Post by BLTicklemonster on 2006-10-04
??? That's just plain rude.

---

### Post by Hairyred on 2006-10-04
> **BLTicklemonster said:**
> ??? That's just plain rude.
He's got a point. though.

---

### Post by _Dan on 2006-10-04
> Why is so extremely difficult to move from windows to linux?

In my case because I can't get [VPN](http://ubuntuforums.org/showthread.php?t=268793) to work.

---

### Post by got_nix on 2006-10-04
um.. i'ld say a steeper learning curve and the general laziness of man.. some dont like to read some dont have determination and descipline. I fully switched only run ubuntu (dapper) on my notebook and the onlything i haven't solved yet is syncing my qtek with my notebook and i found a solution but just haven't tried it as yet. linux is pretty easy.

---

