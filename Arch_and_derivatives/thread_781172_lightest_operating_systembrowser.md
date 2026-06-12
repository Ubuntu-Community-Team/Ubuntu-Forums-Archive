---
title: "lightest operating system/browser?"
date: 2008-05-04
forum: Arch and derivatives
---

### Post by savagenator on 2008-05-04
Hello all

at the moment i'm streaming internet radio using flash. I'm also using about 40% to 50% of the CPU on this computer. Its a 2001 laptop with a 600mhz Pentium 3. Also running Arch with xfce4. 

My question is: What do i need to do so that not so much CPU is used? Like use fluxbox or openbox? or something else? Also something else other than firefox (swiftweasel has no difference in CPU usage, optimized for pentium 3)

I used e17 for a while before, but realized than the pengiuns in the backround are also eating CPU power (still usable though, shows how great enlightenment is)

---

### Post by NightwishFan on 2008-05-04
Perhaps try Puppy Linux or dsl. For a window manager, try icewm or jwm. The lightest web browser I can think of is lynx for command line.

---

### Post by kerry_s on 2008-05-04
that's normal cpu usage for flash. mine runs about 65 when i'm listening to pandora.com or watching youtube on my 450mhz 256mb ram. mines a custom debian build up from the base. built specifically to work within the 256mb ram, using low resource programs. my startup ram use is less than 15mb.

---

### Post by atomkarinca on 2008-05-04
For a lightweight browser you can try webkit based browsers, like Epiphany-webkit or Midori. But I don't think they support flash now. You can try Opera 9.50b2, it's faster than Firefox and it handles flash better.

---

### Post by agim on 2008-05-04
Kerrys, you say your startup ram use is less than 15mb? Two questions... what is the startup time and can you give me some pointers? I am trying to build my own low resource machine.

---

### Post by kerry_s on 2008-05-04
> **agim said:**
> Kerrys, you say your startup ram use is less than 15mb? Two questions... what is the startup time and can you give me some pointers? I am trying to build my own low resource machine.

rebooted just for you, pic->

---

### Post by savagenator on 2008-05-04
thank you for your responses. Unfortunatly flash is a must, but getting a lighter de is a good idea. I tried using an openbox wm with xfce4  but i did not notice a speed difference

actually the bottleneck is the CPU, since it constantly goes up to 100% usage when opening anything (programs or webpages)

---

### Post by NightwishFan on 2008-05-04
Puppy uses jwm and has flash by default, try it out. I triple boot Kubuntu Vista Puppy.

---

### Post by finferflu on 2008-05-04
I don't know if it's been suggested, but Opera is one of the lightest browsers I have seen around. Same is true for Arch, in regards to distros.

---

### Post by digger95 on 2008-05-04
I'm using Zenwalk which is a very nice light distro.  Not as light as DSL and some others, but I find it a very good combination of 'lightweight' and 'not bad to look at'.  Not sure a lighter setup will really help you that much though.  Flash sucks up cpu regardless and always send mine into the 90-100% range.  When I visit flash-intensive sites my fans always kick up to high gear so I know my CPU is really working.

---

### Post by Dr Small on 2008-05-04
Try SliTaz. I heard about it from K.Mandla. It is very lightweight (as a livecd) and has a bunch of different software installed on it. For a lightweight browser, go with Dillo or w3m..

---

### Post by mips on 2008-05-05
Flash is a cpu killer. I don't think it matters much which browser you use but I understand you wanting to shave off some of the cpu usage and make things a bit leaner.

Dunno how true this is but I heard that swfdec requires less cpu than flash or gnash. Can anyone confirm this?

---

### Post by potrzebie on 2008-05-07
Flash will always be upping the cpu usage, no matter what distro you choose, no matter which browser. That said, I have an old 700 mhz p3 laptop and used a ca. 2000 p3 600 mhz as my main desktop until about a year and a half ago. Some things to consider:
[LIST=1]
[*]Distro. You're using Arch, so you're probably pretty clean when it comes to background services, etc. I used Slackware on the desktop, zenwalk on the laptop, and found them really well-suited for optimization, but these days I'd throw Arch at the same hardware if I were net-connected, slackware if I wanted to do all the setup offline.
[*]Desktop Environment: Say no. Use a window manager, fluxbox or openbox, and be happier. Although zen, slack, and arch all have clean, uncluttered xfce builds, and it's pretty nice, it's still heavy, especially if ram is low.
[*]Browser: I love firefox enough to put up with its shortcomings on old hardware. I don't use many more plugins than adblock plus and greasemonkey, and never opend more than about four tabs. Opera is nice too though, but it always runs smoothly up to a certain point and then gets greedy with ram or something, ymmv.
[*]Compile a custom kernel: This works on almost any type of hardware. Don't be fooled by architechture optimized browsers or distros in and of themselves. Your kernel can make a huge, noticeable difference. Read the faq at kernel.org, and the relevant pages on your ditro's wiki or docs about compiling a kernel. It's easy enough to do, useful to learn, and it's "leet" or something...this is linux after all. If nothing else, keep all those extraneous graphics card drivers, lan hardware drivers, and filesystems out of your kernel so that it's smaller, and make sure you're compiling for the specific processor type you have.
[/LIST]

And beyond all those things, do all the obvious little tweaks...dropping your color depth, using a low-overhead filesystem like ext2, optimizing swap space and usage: see K. Mandla's blog ([here's]("http://kmandla.wordpress.com/2007/03/16/ten-things-you-can-do-keep-an-old-computer-useful/") a nice page to start from) for a perfect roundup off all that.

Oh, as for streaming radio using flash...is it a feed with an alternative format? Is there an option for m3u, wma, or real streams of the same content? You could always open those in totem, xine, or vlc, and lower your cpu use right away. I listen to a station every saturday morning that has several feeds and find that on old hardware, choosing it's wma stream and opening it in totem rather than using a plugin or the real media stream is smooth and low on ram and cpu usage. But not all radio has multiple streams so if you can't, you can't.

---

