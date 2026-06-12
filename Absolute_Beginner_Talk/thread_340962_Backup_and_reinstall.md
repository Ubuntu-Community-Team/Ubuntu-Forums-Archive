---
title: "Backup and reinstall"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by gigaferz on 2007-01-17
Hello!
I have been using ubuntu for almost 4 months now.

Most of the times I figure out my own problems, however I am not always that lucky.

I installed Kubuntu over ubuntu 3 weeks ago, and I noticed it was taking my system more time to boot up.

It has been taking a lot of time to "read files necesary to boot,Load drivers,," etc,etc...

And when Gnome was on the screen it was taking up to 4 minutes to be ready to use. (Was that because I customized it?).

After the Kubuntu installation it just got worse.  Also I know it could be the hard disk, but I need to try anything else before tossing it away.

I takes up to 3 minutes to open an openoffice spreadsheet.

Webbrowsing and thunderbird work fine.

I just want to know if there is a way to perform a REpair Installation, or do I need to wipe out the hard drive?

right now I'll backup my files to a flash drive. How do I back up my emails in thunderbird? Should I just drag and drop the directory into my flash drive?

Also how do you delete old kernels, it reminds me of the $$$unistallnnnnn$$$ files in windows xp,  I have a small hard drive thats why I care about space.

Besides Im going this way because I do not have the time to troubleshoot and fix the system.

Any help would be appreciated.

Thank you.

---

### Post by bodhi.zazen on 2007-01-18
Remove old kernels via synaptic. Save 1 working kernel "just in case".

As far at time to start stuff, well I'm not too sure about that ....

---

### Post by riven0 on 2007-01-18
:-k I'm not sure about your particular case, but I know slowdowns can sometimes be related to network problems. As a test can you try this in the terminal:

> ping google.com

and post the results here. As for Gnome; what kind of customizations did you do?

---

### Post by gigaferz on 2007-01-18
PING google.com (64.233.167.99) 56(84) bytes of data.
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=1 ttl=242 time=122 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=2 ttl=242 time=126 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=3 ttl=242 time=142 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=4 ttl=242 time=122 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=5 ttl=242 time=117 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=6 ttl=242 time=112 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=7 ttl=242 time=113 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=8 ttl=242 time=117 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=9 ttl=242 time=198 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=10 ttl=242 time=137 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=11 ttl=242 time=140 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=12 ttl=242 time=114 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=13 ttl=242 time=169 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=14 ttl=242 time=176 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=15 ttl=242 time=180 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=16 ttl=242 time=133 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=17 ttl=242 time=125 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=18 ttl=242 time=279 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=19 ttl=242 time=349 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=20 ttl=242 time=338 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=21 ttl=242 time=456 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=22 ttl=242 time=412 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=23 ttl=242 time=494 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=24 ttl=242 time=368 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=25 ttl=242 time=234 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=26 ttl=242 time=355 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=27 ttl=242 time=197 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=28 ttl=242 time=180 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=29 ttl=242 time=289 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=30 ttl=242 time=191 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=31 ttl=242 time=141 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=32 ttl=242 time=172 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=33 ttl=242 time=389 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=34 ttl=242 time=369 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=35 ttl=242 time=409 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=36 ttl=242 time=290 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=37 ttl=242 time=497 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=38 ttl=242 time=528 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=39 ttl=242 time=842 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=40 ttl=242 time=422 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=41 ttl=242 time=154 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=42 ttl=242 time=290 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=43 ttl=242 time=253 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=44 ttl=242 time=219 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=45 ttl=242 time=374 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=46 ttl=242 time=396 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=47 ttl=242 time=526 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=48 ttl=242 time=356 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=49 ttl=242 time=323 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=50 ttl=242 time=247 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=51 ttl=242 time=212 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=52 ttl=242 time=199 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=53 ttl=242 time=155 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=54 ttl=242 time=114 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=55 ttl=242 time=133 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=56 ttl=242 time=128 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=57 ttl=242 time=144 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=58 ttl=242 time=349 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=59 ttl=242 time=131 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=60 ttl=242 time=460 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=61 ttl=242 time=414 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=62 ttl=242 time=300 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=63 ttl=242 time=587 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=64 ttl=242 time=497 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=65 ttl=242 time=309 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=66 ttl=242 time=169 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=67 ttl=242 time=116 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=68 ttl=242 time=120 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=69 ttl=242 time=172 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=70 ttl=242 time=360 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=72 ttl=242 time=257 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=73 ttl=242 time=280 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=74 ttl=242 time=371 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=75 ttl=242 time=148 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=76 ttl=242 time=254 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=77 ttl=242 time=201 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=78 ttl=242 time=208 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=79 ttl=242 time=257 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=80 ttl=242 time=361 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=81 ttl=242 time=494 ms

[1]+  Stopped                 ping google.com

It just kept going so I stopped it.

And about the customizations, It was not something fancy.

I downloaded a couple of themes, and wallpapers, I removed evolution, and got thunderbird, I followed a guide to have the computer look like a  Mac. I did not do anything complicated, I just did the basic stuff.

---

### Post by jvc26 on 2007-01-18
In the guide you did to make it like a mac, how much customization was there - any specific apps you used for it - i.e. is it using a blinds-esque application like windows blinds or was it just small changes to the desktop look and feel? As if it was an app that could be slowing you down by being slow loading/resource heavy or something like that.
Il

---

### Post by gigaferz on 2007-01-18
mh...no nothing like that, was just mac icons,a theme, wallpaper, and  some setting on the task bar.

[http://www.taimila.com/ubuntuosx.php](http://www.taimila.com/ubuntuosx.php)  

thats it, I only did the simplest things I could. No scripts or  complex instructions, I did not even did it all.

maybe I uninstalled something because I like clean and fast systems, so I was trimming it down...

This is ~the time it takes for me to boot.

2 minutes for reading files needed to boot,
2 minutes for restricted drivers,
then I get all the system messages, included  a scanpce, line 27, in not found...
after that a black screen with 2 random ascci code blocks....
it lasts 40 secs,
then I get the log in screen,
then a blue screen for about 1:30 
finaly I get the kde loading screen, it lasts 1 min,
when its supposed to be ready to go I get an amarok  window and it takes another 2 minustes for the system to respond properly....

I will reinstal tomorrow,
hopefully it was not ubuntu but the hard drive,

Thank you,

---

### Post by gigaferz on 2007-01-22
Hello!

I did a new installation.
And it was running good.
Later I got easy ubuntu and automatix, it took me a while because i needed some  extra files.

After this, I turned the computer off, and It takes almost 3 minutes and 30 sec. to start..
This was on friday.

Now , today, it is as abad as it was before, (i have not installed any updates),
After selecting the kernel, it takes 3 minutes, then later when is preparing restricted drivers, it takes up to 5 minutes, And when is finally loading more stuff (after logging in)
it needs a couple of minutes more..

Can it be the hard disk?

I will uninstall automatix and easyubuntu just to be sure.

---

