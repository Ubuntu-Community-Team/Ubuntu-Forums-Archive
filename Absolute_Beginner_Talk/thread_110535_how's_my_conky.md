---
title: "how's my conky?"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by fuscia on 2005-12-31
[IMG]http://img.photobucket.com/albums/v342/unknownentity/conky.jpg[/IMG]

if it sucks, what should it be?

oh, i'm using openbox. i have a 700mhz celeron with 256ram and a 10gig hd.

xorg's kind of high, isn't it?

---

### Post by towsonu2003 on 2005-12-31
temperatures (0 degrees) and networking (up & down) look like they dont work?
here is mine, if interested (background is part of my desktop pic (which is also my avatar)) don't know why but I felt the need to censor (black out) some info. I'm paranoid...

I forgot to mention: I'm in love with conky!

PS. I think my memory percentages (at the bottom) are not working well, but not sure...

---

### Post by fuscia on 2005-12-31
ok, here's something i just realized - percentages of what? your xorg says 9.something and mine says 39.something. is that because you're running more stuff than i? is there something wrong with my xorg?

---

### Post by towsonu2003 on 2005-12-31
[QUOTE=fuscia]ok, here's something i just realized - percentages of what? your xorg says 9.something and mine says 39.something. is that because you're running more stuff than i? is there something wrong with my xorg?[/QUOTE]
lol, no
as I mentioned, I am pretty sure my conky's percentages are screwed... I played around too much with it... I now use that stuff mostly to see which app is screwing my system (the one in red, usually is firefox ;) ) instead of looking at percentages...
I use top for the percentages if I see something really wron with percentages...

oh, and, I've got 1GB ram you have 256MB so percentages are different in that way too...

//edit// now that I think about this, I guess my percentages are not broken after all ehueheh, it's all about math :P

---

### Post by fuscia on 2005-12-31
[QUOTE=towsonu2003]oh, and, I've got 1GB ram you have 256MB so percentages are different in that way too...[/QUOTE]

ooooooooooooooooooooh! i see.

---

### Post by ninotob on 2005-12-31
Hey thanks -- I'd never seen conky before.  I have twice the memory, so the percentage usage difference for Xorg between you and me isn't as much as it looks, but I think you're using roughly twice the ram -- Here's a screenshot of mine:

---

### Post by fuscia on 2005-12-31
i rebooted and now it's down to 14something.

---

### Post by mcduck on 2005-12-31
Conky Screenshots? Nice. Here's mine:

---

### Post by towsonu2003 on 2005-12-31
very nice screenshots coming in :) nice thread

interesting to see the swap usage of pple... 

[QUOTE=fuscia]i rebooted and now it's down to 14something.[/QUOTE]
maybe a memory leak? my memory leaks are usually linked to firefox (hence running the nightly build)... oh, and, instead of rebooting, sudo /etc/init.d/gdm restart would do the trick? I wouldn't worry too much (conky makes you dizzy and paranoid but you'll get used to it hehe)

[quote=mcduck]Here's mine[/quote]very nice use of fonts... I would love to see the .conkyrc of that (GPL'd right? ;) )... here is mine, if interesting to anyone (hopefully attached)...

---

### Post by Swab on 2005-12-31
My CPU Temp isn't working either!

---

### Post by towsonu2003 on 2005-12-31
[QUOTE=Swab]My CPU Temp isn't working either![/QUOTE]
I think that's about an acpi thing, have no idea though. I use the cat /(somethingsomething)/temp(somethingsomething) in the conkyrc to show my temp... (see my attached conkyrc) --it refreshes the output of cat and shows it inside conky -> it's not so nice (resource 'hungrier') but works anyway :)

edit: not cat, tail (5am...) sorry :)

---

### Post by Swab on 2005-12-31
[QUOTE=towsonu2003]I think that's about an acpi thing, have no idea though. I use the cat /(somethingsomething)/temp(somethingsomething) in the conkyrc to show my temp... (see my attached conkyrc) -it's not so nice but works anyway :)[/QUOTE]

${color #ff4500}CPU ${tail /proc/acpi/thermal_zone/THRM/temperature 1 

Is this the line?  The problem is I don't have a /proc/acpi/thermal_zone/THRM/ directory...

---

### Post by towsonu2003 on 2005-12-31
[QUOTE=Swab]${color #ff4500}CPU ${tail /proc/acpi/thermal_zone/THRM/temperature 1 

Is this the line?  The problem is I don't have a /proc/acpi/thermal_zone/THRM/ directory...[/QUOTE]
oh yes tail -sorry about that...
maybe there is something similar under your /proc/acpi/ directory somewhere? I really have no clue though... hopefully an expert will take a look in here and enlightens us :)

---

### Post by Swab on 2005-12-31
[QUOTE=towsonu2003]oh yes tail -sorry about that...
maybe there is something similar under your /proc/acpi/ directory somewhere? I really have no clue though... hopefully an expert will take a look in here and enlightens us :)[/QUOTE]

Device manager shows my CPU as unknown vendor and device.... I'm running 686 kernel on AMD64 CPU... maybe I need to switch to K7?

---

### Post by towsonu2003 on 2005-12-31
[QUOTE=Swab]Device manager shows my CPU as unknown vendor and device....[/QUOTE]
same here -> device manager shows unknown processor, but running intel celeron, kernel 686...

---

### Post by fog on 2005-12-31
Here is mine:

[IMG]http://img415.imageshack.us/img415/8915/screenshot4sc.jpg[/IMG]

---

### Post by mcduck on 2005-12-31
[QUOTE=towsonu2003]
very nice use of fonts... I would love to see the .conkyrc of that (GPL'd right? ;) )... here is mine, if interesting to anyone (hopefully attached)...[/QUOTE]
Thanks. And it's GPL'd now ;)

I removed the swap meter as during last 8 months my computer has used swap 2 times, and even then not enough to be seen on the meter.. I just love Linux :D

edit: I changed green and red fonts to a bit darker colors..

---

### Post by towsonu2003 on 2005-12-31
[QUOTE=mcduck]Thanks. And it's GPL'd now ;)
edit: I changed green and red fonts to a bit darker colors..[/QUOTE]
lol 
how did you manage to change the fonts? I can't change them at all to anything else then the ones in default sample file??

---

### Post by mcduck on 2005-12-31
[QUOTE=towsonu2003]lol 
how did you manage to change the fonts? I can't change them at all to anything else then the ones in default sample file??[/QUOTE]Did you install it from repositories? I'm using conky_1.3.3-1_i386.deb from Conky's web site. The one in repositories did nothing but segfaulted whatever I put in my conkyrc..

---

### Post by towsonu2003 on 2005-12-31
[QUOTE=mcduck]Did you install it from repositories? I'm using conky_1.3.3-1_i386.deb from Conky's web site. The one in repositories did nothing but segfaulted whatever I put in my conkyrc..[/QUOTE]
I've the repos one (1.3.1) but it did not segfaulted on this laptop... 
but I'm unable to find a place that describes how the font thing works with it -it can't find the fonts I try out- (and I dont have a background on how to use backgrounds and programming at all) I read somewhere to download xfont-artwiz but no clue after that either...

I think I got the sample conkyrc from their web site, may be that made a difference in terms of segfault? no clue though...

may be I should open up a new thread bc. this is forking the thread... ? And I'd love to see more conky pics in here (and their conkyrc files maybe ;) )
here it is -so that I wont fork OP's thread any more than I already did (sorry) [http://ubuntuforums.org/showthread.php?p=617155#post617155](http://ubuntuforums.org/showthread.php?p=617155#post617155)

I'd like to see OP's new conky screenshot if s/he changes it at all ;)

---

### Post by jrjr on 2006-07-29
.

---

### Post by Swab on 2006-07-29
Strange that you resurrected this thread now, I was just browsing it half an hour ago!

---

### Post by jrjr on 2006-07-29
.

---

### Post by catlett on 2006-07-29
Just FYI...The ubuntu repository version is not a good version to use. You should download and compile or get the debian package.
Don't believe me though, here is the conky maintainers statement.
#
> Q: Conky or <insert conky feature here> doesn't work in Ubuntu!

A: The Conky package in the ubuntu repositories is not properly built, and its horribly out of date. It's recommended that you first file a bug report with the ubuntu package maintainer, and then you should proceed to either: a. download and compile the package yourself or b. use the properly built package from [http://packages.debian.org/unstable/utils/conky](http://packages.debian.org/unstable/utils/conky). The Conky developers have attempted (on a number of occasions) to get the ubuntu developers to fix the Conky package, however they have been unresponsive.
Go here and they have the links [http://conky.sourceforge.net/faq.html](http://conky.sourceforge.net/faq.html)

---

### Post by jrjr on 2006-07-29
.

---

### Post by catlett on 2006-07-29
I just tried to change to the debian package by uninstalling the synaptic conky and then downloading/installing the debian package deb,
NO SUCH LUCK. There is a dependency issue. Here's the output
```
catlett@ubuntu:~/Desktop$ sudo dpkg -i conky_1.4.2-1_i386.deb
Password:
Selecting previously deselected package conky.
(Reading database ... 135522 files and directories currently installed.)
Unpacking conky (from conky_1.4.2-1_i386.deb) ...
dpkg: dependency problems prevent configuration of conky:
 conky depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 conky depends on libfreetype6 (>= 2.2); however:
  Version of libfreetype6 on system is 2.1.10-1ubuntu2.2.
dpkg: error processing conky (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 conky
```
I guess we are stuck with the buggy ubuntu version until the Ubuntu devs act on it.

[COLOR="Red"]EDIT:[/COLOR] This guide details a way around the repository conky and a way around the debian package. I didn't try and compile the latest conky, I just used the 1.4.2 package that the post linked to.   [http://www.ubuntuforums.org/showthread.php?t=205865](http://www.ubuntuforums.org/showthread.php?t=205865)
[IMG]http://i80.photobucket.com/albums/j180/brthomas503/conky.jpg[/IMG]

---

