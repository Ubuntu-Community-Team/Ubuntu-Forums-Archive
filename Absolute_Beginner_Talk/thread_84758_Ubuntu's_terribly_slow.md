---
title: "Ubuntu's terribly slow"
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by No_Germs on 2005-10-31
compared to the speed i get with win xp, ubuntu is very slow. is this an expected behavior, or does ubuntu run as fast as windows normally?

---

### Post by Samuel on 2005-10-31
for me Ubuntu boots slower but runs faster than XP, but the speed of ubuntu is way down on the list of reasons why i prefer it to windows XP.

---

### Post by Kapre on 2005-10-31
[QUOTE=No_Germs]compared to the speed i get with win xp, ubuntu is very slow. is this an expected behavior, or does ubuntu run as fast as windows normally?[/QUOTE]

My Ubuntu runs faster than my XP...even though my computer is old (AMD 1.33 GHz). Are you running lots of apps on it (say firestarter, antivirus, music [xmms, streamtuner], java [on another thread eats up 1/4 of a gig in memory]etc.)? I'm running Streamtuner and BeepMedia (for my music as I'm reading thru the forum) and it's still running fine.

K

---

### Post by aysiu on 2005-10-31
[QUOTE=Samuel]for me Ubuntu boots slower but runs faster than XP[/QUOTE] Same here. To make still faster, use XFCE4.

---

### Post by matthew on 2005-10-31
I'm going to echo the others...for me Ubuntu boots a little slower than WinXP did (when XP was first installed, not after 6 months of use or more and lots of programs installed and in the registry). However, Ubuntu runs quite a bit faster for me than windows did.

---

### Post by No_Germs on 2005-10-31
i don't mind a long booting time- i'm talking about the run speed.
i don't need it to be that fast, either. i'm not playing 3d games on it or something like that. but it's Real slow... 1995 slow :) i mean,  i get to the state that i contemplate whatever i should double click on something because i know the loading will take half an hour....

---

### Post by Samuel on 2005-10-31
No_Germs there must be a problem somewhere unless your hardware just isnt upto it, have you tried installing xubuntu-desktop ? that runs very fast.
sudo apt-get install xubuntu-desktop
then choose xfce in session type at the login screen.
also if your using azureus or firefox dont leave them running for too long without restarting them, both supposedly have memory leaks

---

### Post by No_Germs on 2005-10-31
[QUOTE=Kapre]My Ubuntu runs faster than my XP...even though my computer is old (AMD 1.33 GHz). Are you running lots of apps on it (say firestarter, antivirus, music [xmms, streamtuner], java [on another thread eats up 1/4 of a gig in memory]etc.)? I'm running Streamtuner and BeepMedia (for my music as I'm reading thru the forum) and it's still running fine.
K[/QUOTE]
i have installed it two days ago. since then i've installed just the JRE, and Eclipse (a java IDE). but it's genrally slow. even when i just run firefox it's slow. and i'm not talking about the internet connection's speed, of course- i'm talking about the time it takes FF to change tabs, minimize and maximize, etc.
i should mention that i've installed it as dual boot along with XP, on a partition of 10 GB. i've seen that sometimes when people complain about this problem they are asked if they have put aside enough swap memory. i think swap has enough memory, but how can i make sure?

---

### Post by No_Germs on 2005-10-31
[QUOTE=Samuel]No_Germs there must be a problem somewhere unless your hardware just isnt upto it, have you tried installing xubuntu-desktop ? that runs very fast.
sudo apt-get install xubuntu-desktop
then choose xfce in session type at the login screen.
also if your using azureus or firefox dont leave them running for too long without restarting them, both supposedly have memory leaks[/QUOTE]
i haven't heard of xububtu, but i'll check it out... but isn't that going around the problem instead of solving it. i mean. if for all you guys ubuntu runs at least as fast as XP then i should figure out what's wrong.

memory leaks on Firefox? no way... well, anyway it happens even before i start FireFox...

---

### Post by No_Germs on 2005-10-31
ok, i've checked my partitions- the main partition is 9.6 GB, which of 5.6 GB are free. my swap partition is 500 MB, and is full (guess it always is full). so i guess the problem's not there....

---

### Post by poofyhairguy on 2005-10-31
[QUOTE=No_Germs]i have installed it two days ago. since then i've installed just the JRE, and Eclipse (a java IDE). but it's genrally slow. even when i just run firefox it's slow. and i'm not talking about the internet connection's speed, of course- i'm talking about the time it takes FF to change tabs, minimize and maximize, etc.[/QUOTE]

Three things. First is my guide:

[http://ubuntuforums.org/showthread.php?t=74197](http://ubuntuforums.org/showthread.php?t=74197)

Second, do you have an Nvidia card? I can help a lot if you do.

Third Firefox in Ubuntu is slower than Firefox in Windows. Its kinda a known thing around here, and the upcoming version is going to fix that (1.5). Till then myself and many other users use Epiphany:

> sudo apt-get install epiphany-browser

Enjoy.

---

### Post by aysiu on 2005-10-31
When you type ```
top
``` in a terminal, what's your output?

---

### Post by No_Germs on 2005-10-31
[QUOTE=poofyhairguy]
do you have an Nvidia card? I can help a lot if you do.
[/QUOTE]
yes, i do have Nvidia card... please help :)

---

### Post by Darrin on 2005-10-31
I get the same results as others here. Ubunut boots slower than xp. Seems to run equally as fast once fully loaded. I have noticed that even at the point in windows where it shows the desktop, I still have to wait about 20 seconds for everything to load fully for the system to be 100% usable. With Ubuntu as soon as the desktop appears, its ready to go.

---

### Post by No_Germs on 2005-10-31
[QUOTE=aysiu]When you type ```
top
``` in a terminal, what's your output?[/QUOTE]

top - 06:15:59 up  2:18,  2 users,  load average: 3.03, 2.17, 1.39
Tasks:  82 total,   2 running,  80 sleeping,   0 stopped,   0 zombie
Cpu(s): 55.5% us, 44.5% sy,  0.0% ni,  0.0% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   1036632k total,  1023068k used,    13564k free,    66528k buffers
Swap:   465844k total,        0k used,   465844k free,   514644k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
14402 noam      16   0  305m 161m  17m S 91.3 15.9   4:49.30 java
 8139 root      16   0  115m  31m 7624 R  6.0  3.2  10:41.54 Xorg
 8727 noam      15   0  167m 106m  22m S  1.7 10.5  25:29.30 firefox-bin
14637 noam      15   0 31488  13m 8844 S  1.0  1.3   0:04.48 gnome-terminal
14652 noam      16   0  2136 1024  816 R  0.7  0.1   0:00.76 top
 8632 noam      15   0 19616 9324 7040 S  0.3  0.9   0:01.20 trashapplet
    1 root      16   0  1564  532  460 S  0.0  0.1   0:01.51 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.15 events/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   88 root      10  -5     0    0    0 S  0.0  0.0   0:00.07 kblockd/0
  116 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  117 root      15   0     0    0    0 S  0.0  0.0   0:00.75 pdflush
  119 root      16  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  118 root      15   0     0    0    0 S  0.0  0.0   0:00.02 kswapd0

---

### Post by Kyral on 2005-11-01
1) How much RAM do you have. Linux is acting slow because its swapping like crazy.

2) The JRE takes up 250 MB in memory. There is your problem

---

### Post by aysiu on 2005-11-01
[QUOTE=Kyral]1) How much RAM do you have. Linux is acting slow because its swapping like crazy.[/quote] It looks like it's using zero swap, actually. Am I reading it wrong? It also looks as if there's 1 GB of RAM, with almost all of it being used.

> 
2) The JRE takes up 250 MB in memory. There is your problem Yeah, any app that uses more memory than Firefox is going to get you in trouble...

---

### Post by Kyral on 2005-11-01
[I] Yeah, any app that uses more memory than Firefox is going to get you in trouble...


[/I]Izzat sarcasm or am I being paranoid..or really tired ;P

---

### Post by poofyhairguy on 2005-11-01
[QUOTE=No_Germs]yes, i do have Nvidia card... please help :)[/QUOTE]

First install the nvidia drivers:

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

Then add the 

>         Option          "RenderAccel"           "true"

line like my howto says to do (follow guide):

[http://ubuntuforums.org/showthread.php?t=75527](http://ubuntuforums.org/showthread.php?t=75527)

Just using renderaccel is very stable for me and fast.

---

### Post by Doc.Caliban on 2005-11-01
[QUOTE=poofyhairguy]Just using renderaccel is very stable for me and fast.[/QUOTE]

Just to clarify, are you saying that running the Composite Manager with only the entry  **Option "RenderAccel" "true"** will NOT invoke the otherwise promised x-server crashes?

-Doc

---

### Post by poofyhairguy on 2005-11-01
[QUOTE=Doc.Caliban]Just to clarify, are you saying that running the Composite Manager with only the entry  **Option "RenderAccel" "true"** will NOT invoke the otherwise promised x-server crashes?

-Doc[/QUOTE]


Not quite. What I am saying is that using the renderaccel speeds up the desktop even if you don't use a Composite Manager. Its what I do on my grilfriend's laptop that has a weaker video card so xcompmgr crashes a lot on it. Renderaccel provides nice desktop acceration- not as nice as a Composite Manager of course but I don't get as many redraw issues when I enable it.

Xcompmgr WILL crash if you use it. I have found no way around it. I can now go long periods without it happening, but every two weeks or so it wil crash. Last night it did and sucked all my work with it- its the price I happily pay I guess.

Renderaccel by itself can be very stable, so I advise people try it.

---

### Post by Doc.Caliban on 2005-11-01
Ah, then I guess I'm not clear on one point:

Do you have to install Xcompmgr to use the Renderaccel option?

Also, you mention using Renderaccel on your girlfriend's computer because it has a less powerfull GPU.  Will the option help someone with a high end GPU?

Thanks for your time,

-Doc

---

### Post by twistadrulerz on 2005-11-01
Agree with u

---

### Post by poofyhairguy on 2005-11-01
[QUOTE=Doc.Caliban]Ah, then I guess I'm not clear on one point:

Do you have to install Xcompmgr to use the Renderaccel option?[/QUOTE]

No. The option is the feature of the Nvidia driver that allows you to have accerated Xcompmgr. It needs the extension to work well, not the other way around. The option accerated 2D and will accerate a Compositor if you are using one.


> 
Also, you mention using Renderaccel on your girlfriend's computer because it has a less powerfull GPU.  Will the option help someone with a high end GPU?


Yep. I use it on my 6600GT ALL the time. But I also use Xcompmgr all the time because I can't stand a desktop without it now. But when I turn xcompmgr off I still get the full advantages of renderaccel. 

Its awesome. By itself renderaccel makes the desktop much better; then you can use this option to make Xcompmgr work as well as it can.

---

### Post by dom on 2005-11-01
[QUOTE=No_Germs]ok, i've checked my partitions- the main partition is 9.6 GB, which of 5.6 GB are free. my swap partition is 500 MB, and is full (guess it always is full). so i guess the problem's not there....[/QUOTE]

(edited myself)
the swap looks fine according to you're TOP report. See later post.

---

### Post by No_Germs on 2005-11-01
[QUOTE=aysiu]It looks like it's using zero swap, actually. Am I reading it wrong? It also looks as if there's 1 GB of RAM, with almost all of it being used.
trouble...[/QUOTE]
so what's the final verdict... what should i do?
should i expand my swap partition and is it normal for the Jre to take up 250 mb, or not?

---

### Post by Stormx on 2005-11-01
Look on page 2, and follow the nvidia guide! It is not normal for Jre to take up 250mb, any app that takes up that amount of memory should be eyed carefully

---

### Post by No_Germs on 2005-11-01
[QUOTE=Stormx]Look on page 2, and follow the nvidia guide! It is not normal for Jre to take up 250mb, any app that takes up that amount of memory should be eyed carefully[/QUOTE]
i've followed the nvidia guide. the question is,is that the difference between slow and normal, i.e everyone does it and if they don't they don't get the normal XP speed, or maybe it's the difference between fast and faster, only those who wish it be even faster than it was at the begining use it.

i think the 250 MB are normal- it's Eclipse, a Java IDE that runs completley on java...

---

### Post by dom on 2005-11-01
eclipse iv memory hungry, very so, in my experience. I find it is slow to load and do things and chews lots of mem.

for info about swap size setting, see google

[http://www.google.ie/search?hl=en&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=linux+size+swap&btnG=Search&meta=](http://www.google.ie/search?hl=en&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=linux+size+swap&btnG=Search&meta=)

it depends on your usage. 

Your Virtual memory is RAM + SWAP. This must be more than the memory requirements of all the process you want to run concurrently. 

So if everything you will ever run at one will use <1GB, you won't need any swap.

If it will use, say, 3Gb, you will need 2GB swap, etc.

Afaik it's no harm to have too much swap, the system should use it only when it needs to.

for details, read the many threads, articles, etc available on-line.

From the top posting you showed earlier, if that is typical then your swap size should be fine, as you are not even using all of the RAM. So something else is slowing you down.

If you ever see "Mem" and "Swap" both having all or nearly all of their full availability in use, then increase the SWAP.

---

### Post by No_Germs on 2005-11-01
to poofyhairyguy-
i've installed the nvidia driver and did the changes your guide explained.
indeed, like your guide said, after i hit ctrl+alt+backspace and restarted, i needed to type startx in order to restart everything...
the problem is, now i wanted to shut down my computer, but after i've selected "shut down", i got the command line saying "waiting for x to finish" or something like that... it this a known issue, and how can i solve it (i have not shut my computer since)?

---

### Post by Doc.Caliban on 2005-11-01
[QUOTE=poofyhairguy]No. The option is the feature of the Nvidia driver that allows you to have accerated Xcompmgr.[/QUOTE]

Great, I've enabled it and switched from "nv" to "nvidia".  Things do seem to be a little snapier.

Any other tips for getting the most out of my Go 6800 ultra in GNOME?

Thanks again, and sorry if I hijacked the thread a bit.

-Doc

---

### Post by No_Germs on 2005-11-01
yes, my question did get a little bumped off by this conversation :)
is it possible to move it to a different thread?

---

### Post by poofyhairguy on 2005-11-01
[QUOTE=No_Germs]yes, my question did get a little bumped off by this conversation :)
is it possible to move it to a different thread?[/QUOTE]


PM me and I will help you personally.

---

