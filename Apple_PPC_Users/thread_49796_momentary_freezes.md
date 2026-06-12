---
title: "momentary freezes"
date: 2005-07-17
forum: Apple PPC Users
---

### Post by chascon on 2005-07-17
Has anyone noticed the below?  It's been reported but there has been no response.

Description:  	 Opened: 2005-07-10 08:55 UTC
I'm running a iMac DV and sometime after hoary went official I noticed that I
get reproducible momentary freezes in X when doing one of about two things.

The first is while scrolling the scoll bar up or down only while in dialog
windows.  ie, xmms's popup window to select tunes.

Another instance is dragging windows around.  Thus I have removed "show content
while moving window" option.  I don't believe this to be a matter of having a
slow processor as with warty and other distros, there was no noticeable
prolonged complete stop.  I can't even log into a console untill the freeze is
over in approx. 30+ secs.  Once the freeze is over, I get sent into console if I
pressed the keys to do so while freezed.

The last reproducible freeze happens when changing styles in fluxbox.  The
effects are the same as above.  
X loads slowly after startx, but this might be because I'm running XFS now.  All
the above are repeatable with ext3. 

For reference I have ubuntu on a P1 233mhz and it flies thru the fluxbox style
changes, and has yet to feel any of these effects.  This did not happen while
hoary was in development.  I beleve it to be a kernel problem as I recall this
started after a update/upgrade in which a kernel-image (the first apparently in
a long line) was installed. 

uname -r
2.6.10-5-powerpc

---

### Post by guu on 2005-07-19
First run 'top' in a terminal and see what application is hogging the cpu during the time the computer becomes unresponsive.

Note the pid (process id) of the hogging process.

Run 'strace -fp $pid' where $pid is the hogging pid. When the hogging occurs, you will probably see thousands of identical system calls in the terminal running strace.

Now you know what process is hogging, and what it is doing when it is hogging.

You can then use that information to make a more refined help request.

---

### Post by chascon on 2005-07-22
I don't mean to sound ungratefull but wouldn't running top after the fact prove useless since top will go into effect after the freeze, even if I manage to type top into a shell or term, therefore demonstrating non-hogging apps running harmoniously?  It seems that this would be too late.

---

### Post by chascon on 2005-07-27
I guess I coould try running top before I repeat the freeze, and see how it affects top.  Hopefully this will not skip over the freeze "backend" info. 

Unfortunately I can't perform this right now as I decided to try nbsd macppc because it seems that Gnu-linux support for my aging iMac DV seems to be wanning on various points.  I think the problem, in part, is a lack of people running Gnu-linux-ppc on this hardware (or just not a lot of people being 'loud'), Rage 128 accel is buggy, and a simply lack of devs running older macppc (no, pegassus doesn't count,  they are not macs).  It seems that I'm the only one reporting bugs on this hardware to devs and, to a lesser extent, to the forum.  I mean I know there are others hit with the same problems because they sometimes respond to my posts, but they don't get involved with bug reporting (or just contributing to bug reports), ie., the very long thread on warty and Rage 128 freezes when accel was enabed case in point on forum response.
See [http://ubuntuforums.org/showthread.php?t=3723&highlight=Rage+128+accel+freeze](http://ubuntuforums.org/showthread.php?t=3723&highlight=Rage+128+accel+freeze)

 Maybe its the 'mac cult' mentality but linux-macppc people seem lazy, the "mac mentality" of being pampered and having big brother decide on one's behalf.  Frankly I'm tired of seemingly being the only one reporting on bugs with iMac DVs.  Nbsd was a hell, I mean HELL, to install, but I'm in the hopes that'll it'll be more 'stable' than otherwise.  I wrote the install down and plan to post it on the web for those in the same boat that can't make heads or tails out of the nbsd install notes, which looks to be in a state of confusing (dis?)repair.  More to come ...

I love debian, maybe I'll put it back on my iMac DV if I don't like nbsd.  There are things I already don't like about nbsd, but these are initial and akin to one's wife not fully capping the toothpaste, just somewhat minor or just different.  I think I'll leave ubuntu-ppc on my ibook though.

And before someone thinks I'm criticizing ubuntu or debian, I'm not.  This reflects on all linux-ppc distros as I've tried almost all of them on the machine in question.  Ubuntu is the best of them all in my experience in as far as usuability, feasability, ease of use/install/upgrade, and configuration.

---

### Post by zxee on 2005-07-27
Chascon, Just wanted to respond to this...I use a athlon homebuilt and have about eight distros installed. I kind of left apple for awhile and played around with linux.  Slacintosh might have been a great distro but like all ppc distros it's supported like an unwanted distant relative. ( I know, slackintosh isn't supported at all ) And I think that is more the problem than coddled mac users-people who use macs AND linux are few in number (comparitively) and we just don't get "no respect". Of course apple doesn't help the situation with their closed hardware e.g. airport extreme. 
I still like some things about macs, which I'm begining to think is a personal flaw i.e. always struggling to get linux working on apple's weird hardware.
You seem to have a lot of knowledge and experiance, Chascon, so you've probably tried fedora. I am at the fedora forum a bit and recently saw a post that 
someone had FC4 working well on a 450 DV (imac). 
BTW I recently acquired a 500Mhz DV SE  and after editing xorg.conf I have had nothing but freezes, hangs, and commenting out all my edits hasn't changed that. I couldn't tell what the system was like after I 1st installed it ( before editing xorg) because my mouse wasn't recognized. I'm not giving up on linux but trying to get it working on ppc is a real PITA!

---

### Post by chascon on 2005-07-27
Lets see now. Out of the top of my head, I've tried ydl 3 and 4, debian woody and sarge, mandriva-ppc (back then mandrake 9 and 10), and suse back when there was a ppc port (7?, it had a horrible installer which didn't install for me if I remember), a live-ppc cd of Rock linux, and an experimental knoppix-ppc.  The only ones I have not tried is gentoo, slackware ('cause it disappeared before I found out about it), and the newly fashioned sourcemage port to ppc.

Concerning the Rage 128 video card in our iMacs:
About a year ago, all of the distros I tried had a accel/crash problem.  They installed with it disabled for good reason.  The work around was to install daenzer's non-official port debian xfree (at least for me but not for others).

In some debian correspondance Ben Herrenschmidt? admitted that Rage 128 accel has always been buggy.
[http://lists.debian.org/debian-powerpc/2005/03/msg00239.html](http://lists.debian.org/debian-powerpc/2005/03/msg00239.html)

More on to come

---

### Post by zxee on 2005-07-27
[QUOTE=chascon]Lets see now. Out of the top of my head, I've tried ydl 3 and 4, debian woody and sarge, mandriva-ppc (back then mandrake 9 and 10), and suse back when there was a ppc port (7?, it had a horrible installer which didn't install for me if I remember), a live-ppc cd of Rock linux, and an experimental knoppix-ppc.  The only ones I have not tried is gentoo, slackware ('cause it disappeared before I found out about it), and the newly fashioned sourcemage port to ppc.

Concerning the Rage 128 video card in our iMacs:
About a year ago, all of the distros I tried had a accel/crash problem.  They installed with it disabled for good reason.  The work around was to install daenzer's non-official port debian xfree (at least for me but not for others).

In some debian correspondance Ben Herrenschmidt? admitted that Rage 128 accel has always been buggy.
[http://lists.debian.org/debian-powerpc/2005/03/msg00239.html](http://lists.debian.org/debian-powerpc/2005/03/msg00239.html)

More on to come[/QUOTE]
 I guess I owe ubuntu ( the develpers-anyway ) an apology for what I said earlier. I went back to my orginal xorg.conf and using a bargin basement usb mouse x started and I'm typing this from ubuntu's gnome right now! Why there is such a difference recognizing usb mice I don't understand, but I have no hangs, freezes, or the super slow response I saw earlier either. 
BTW my imac only has 192MB of ram. I'll probably add more. It's not as fast as my 1Ghz athlon running ubuntu 5.0.4 but it's not bad either.

---

### Post by chascon on 2005-07-29
yeah, I was going to mention /dev/input/mice works with usb mice.
As for getting some speed out of that try a minimal install.  It's takes a little longer but you should see performance gains out of it.  And stay away from gnome, especially kde.
If you not ready for fluxbox or the like, try xfce4.  It's more of a desktop environment than just a window manager.

For a minimal install set of instructions try:
[http://www.ubuntuppc.info/61.html](http://www.ubuntuppc.info/61.html)

You can also set accel to work for an even more speedier machine, but if you have the Rage 128 or any variation you might get unexplained 'cause crashes.  Look at the link I mentioned earlier in reference to Rage 128 problems to see how I got around it.  Beware, it doesn't work for everybody, although hoary did not necessitate anything but removing xscreensaver and its screensavers.  You might want to try this if you still happen to have the odd permanent freeze or unexplanined crash.  It works for me on hte iMac DV.

---

### Post by chascon on 2005-08-07
Well I finally installed nbsd on my iMac DV.  It runs fairly well and as all bsds I've tried boots up really fast.  I've also installed onto a p1 and it runs better than even a ubuntu server install running the fast reiser fs (reiser starts up  pretty fast [still, on ppc and from personal experience I don't trust reiser]).  Even a server install of ubuntu makes the machine sound as if it was choking, on its last breath, about to explode sort of thing when starting mozilla in ubuntu.  In turn, obsd still takes it's time opening up large gui programs but without the excessive harddrive rattling.  Thus, you might be better of running nbsd on iMac DVs considering they are older computers and bsds seem to be less strenious for old machines (mind you the iMac DV is still a far superior machine to the evil intel p1s).

There are a few awefull wakeup calls though.  Installing nbsd may NOT be straight forward including figuring out how to install it, due to their plethora of different install methods depending on what machine, firmware, etc.  Thus, my future manual at [http://www.ubuntuppc.info](http://www.ubuntuppc.info) Once you have it set up, the user experience really is not different than linux, unless of course you figure apt-get, synaptic, etc, of course.


The main disappointment was that it doesn't seem to run accel for my Rage 128.  I tried but I get a freeze.  Thus, I no longer think this issue is a linux kernel issue but a dri and/or Rage 128 driver issue.  Consequrently I give my koodos to the devs for this issue seems to not be of their creation or fault, although they could own a iMac DV or two so that they could trouble shoot it.

---

### Post by chascon on 2005-09-04
My netbsd-macppc install is up and running at
[http://ubuntuppc.info/index.php?node=67](http://ubuntuppc.info/index.php?node=67)

I'm still fixing it so that '/' doesn't make words italic.

Wind Warriors Boxing & Muy Thai club Webpage:
[http://www3.telus.net/public/lusseau/](http://www3.telus.net/public/lusseau/)

Ubuntu-ppc Gnu-linux-ppc Published Documents:
[http://ubuntuppc.info/](http://ubuntuppc.info/)

---

