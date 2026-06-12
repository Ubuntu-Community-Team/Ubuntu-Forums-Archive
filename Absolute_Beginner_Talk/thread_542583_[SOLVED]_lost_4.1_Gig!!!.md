---
title: "[SOLVED] lost 4.1 Gig?!?!?!?"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by tonytux on 2007-09-04
I tried to log in the other day and got this gdm error msg basically stating that I was out of space on my root or home drives.(Bugs have been  reported [here]("http://https://bugs.launchpad.net/gdm/+bug/35217") and [here]("http://https://bugs.launchpad.net/bugs/66143")) Ok no biggie, login as root and get rid of stuff right..I did, like 4.1 gigs of stuff. I "df -h"ed and it showed me 4.1 gig of free space on my root partition.  
which gave me room for what I thought might be needed with some updates, and allowed me to login as my normal user name.  So I apt-get upgraded and that says it would free like 54kb or something, so I'm thinking no sweat right.  Well I had to reboot, one of the updates being a kernal header, and then I try logging in again as my user again and got the gdm no more space error again!  I log in as root and see that the 4.1 gigs that took me over an hour to free was now completely gone and my root partition is back to 100% use.
I'm not looking for a fix on the bug, I'm looking for a reason why 4.1 gigs of free space dissapeared without me doing anything extra to warrent the use of space.
ok, I know i just need a new HD, but I'd enjoy using my box until then.
my setup is as fallows....
2   80gig WesternDigital HDs
1 into 4 parts 20gig root, 5 gig home, 512mb swap the rest movies and books(about 50gig)
the other 80 gig is dedicated to my music library.
I have a spare 20gig HD that I'm gonna throw /usr onto to try and free about 6 gig or so and do the appropriate mounting etc. I'd just like to know what happened to the original 4.1.

---

### Post by hyper_ch on 2007-09-04
did you really delete those 4.1 GB or were they just moved to the trash bin?

---

### Post by tonytux on 2007-09-04
I don't use the trash bin I use the shift+delete keys, and alot of the space was from removing unused programs using apt-get and synaptic together, but i will check to see if I put ANYTHING in the trash, I forgot abut that thing

---

### Post by hyper_ch on 2007-09-04
Yeah, shift-delete should really delete it...

---

### Post by misfitpierce on 2007-09-04
Indeed :) Cannot see why it would not unless it stopped liking you :)

---

### Post by tonytux on 2007-09-04
nothing in user's trash, and I just removed 154mb of software again as root and again it took it back, is it something to do with the whole journaling thing with ext3 or am I just losing my marbles?

---

### Post by tonytux on 2007-09-04
should I post onto the bug report and add in my 2 cents there too?

rhetoricle question already did

---

### Post by tonytux on 2007-09-04
Check this out, I used the handy disk usage analyzer and found that 13.9 gig of my root partition is being eaten by my /var/log directory.  Further didgging I find that my "messages.o, kern.log.o, messages, kern.log, syslog.o,acpid, and syslog" are all 1.5 gig or larger.  Almost all of these files had naturaly been appended to within the last few hours, obiviously a real time logging system.  Is there a safe way to remove like the first gig or so worth of data to cut down on disk usage?

---

### Post by tonytux on 2007-09-04
I found a tutorial for setting up a server and it mentions a utility to rotate and limit the size of the logs on the machine, but now that i'm doing this after the fact I'm really bogging my box down just trying to use the standard log viewer to  see if I can do the same, or atleast reduce the size they're at now.  Maybe this rotation and limitation should be some kind of standard for the general public distro, you know the aver schmo who doesn't care much about the last 8 months of log files.........
oh look at that, I just crashed Gnome trying to view my logs....
now what to do...?

---

### Post by tonytux on 2007-09-04
solved by stopping sysklogd(the system logger for me)
```
sudo /etc/init.d/sysklogd stop
```
then just removed all logs
```
sudo rm -rf /var/log/*
```
then restarted sysklog
```
sudo /etc/init.d/sysklogd restart
```

this freed up 14 gigs on my root partition!!!!!!!

and i feel dumb for not thinking of it being that simple...
remember kids, check and clean out your system logs on a regular basis

---

### Post by hyper_ch on 2007-09-04
wow, 14 gigs of log files... how did you achieve that?

---

### Post by tonytux on 2007-09-04
not checking them for 6 months, having lots of extra server apps running that I never used or needed (I cleaned for space), and other progs that had logging daemons that I thought I needed for some obscure reasons that are now lost to me....basically being short sighted:)

---

### Post by hyper_ch on 2007-09-04
it still sounds like very much... I have to check tonight how much space my logs use...

---

### Post by tonytux on 2007-09-04
and I broke my firewall for like 2 weeks and had all that server stuff trying to reach out, plus never ever turning off my box unless I feel the need to restart. it's always on 24/7/366, my firewall was blocking like everything, about 3 entries per minute just on that alone for 2 weeks can add up to alot....

---

### Post by hyper_ch on 2007-09-04
I have three server runnings and I don't think I have so much logs...

---

