---
title: "Krita doesn't start"
date: 2009-12-14
forum: Art &amp; Design
---

### Post by nakedfanatic on 2009-12-14
Hi,

I've installed Krita from the repos but it doesn't start. I'm running Ubuntu 9.10.

When I try to launch fro the terminal I get this output:

[I]ian@ian-laptop:~$ krita
Session management error: None of the authentication protocols specified are supported
kdeinit: Aborting. No write access to '/home/ian/.ICEauthority'.
KCrash: Application 'krita' crashing...
Warning: connect() failed: : No such file or directory
KCrash cannot reach kdeinit, launching directly.[/I]

This dialog also pops up:

[IMG]http://ianwitham.wordpress.com/files/2009/12/screenshot-dcop-communications-error-krita.png[/IMG]

Can any one help? I'd really like to try Krita's 16 bit editing capabilities. Thanks.

---

### Post by Exodist on 2009-12-14
check to see if kdebase is installed. Looks like kdeinit isnt..

---

### Post by nakedfanatic on 2009-12-14
Thanks... kdebase wasn't installed so I installed it. However, now when I log in I get a dialog saying "Could not update ICEauthority file /home/ian/.ICEauthority."

Krita still doesn't start.

.ICEauthority does exist... ls -a looks like:

*-rw------- 1 root root 138365 2009-12-13 15:53 /home/ian/.ICEauthority*

Any ideas??

---

### Post by Exodist on 2009-12-14
> **nakedfanatic said:**
> Thanks... kdebase wasn't installed so I installed it. However, now when I log in I get a dialog saying "Could not update ICEauthority file /home/ian/.ICEauthority."

Krita still doesn't start.

.ICEauthority does exist... ls -a looks like:

*-rw------- 1 root root 138365 2009-12-13 15:53 /home/ian/.ICEauthority*

Any ideas??
Install it as well?

---

### Post by thienhaxanh2405 on 2009-12-14
I'm too, Can you help me ???
[right][IMG]http://laptopviet.info/thienhaxanh2405/thx.gif[/IMG][/right]

---

### Post by Exodist on 2009-12-14
> **thienhaxanh2405 said:**
> I'm too, Can you help me ???
[RIGHT][IMG]http://laptopviet.info/thienhaxanh2405/thx.gif[/IMG][/RIGHT]

Hard to help with such very little information that you supplied. 
But if the program says "Cant start xxxx" or "Failed to ini xxxx" or just plain not found.. Look it up in synaptic and install it. Other then that I am not a developer or even a user of Krita so I cant help more then that.

---

### Post by kayosiii on 2009-12-14
dcop was an infrastructural part of KDE3 it has been replaced by dbus in kde 4. I am not sure why Krita would *need* dcop running but this may be part of the issue. 

A 2.1 version was released just recently which is a couple of years more modern than the version you are using (though still not as stable as the authors would like it to be). you might be able to track down a PPA for it from the kubuntu.org website.

---

### Post by nakedfanatic on 2009-12-15
Thanks for the suggestions, they put me on the right track.

The problem was that I had installed the krita package, not the krita-kde4 package.

It still crashes if I try to actually do any image manipulation, but hey that's a whole other story I'm sure.

---

