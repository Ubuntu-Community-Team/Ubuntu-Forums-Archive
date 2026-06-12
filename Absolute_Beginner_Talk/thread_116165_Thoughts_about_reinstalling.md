---
title: "Thoughts about reinstalling"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by Kindred on 2006-01-12
When I installed ubuntu I installed my home dir on a seperate hdd as I had often read it's best to do this.. but then i'm thinking if I reinstall Ubuntu again for an upgrade or whatever i'll be left with random configs and dirs and stuff in my home directory that don't correspond with anything.  I guess people like this because then they keep their settings for programs, but for me it seems messy if you don't reinstall exactly the same things.. 

Is this how it works?  I already hate the mess left by programs leaving files around in my home dir after deletion (.gconf etc) so how would I be able to leave the actual data I have in my home dir (work, mp3s etc) while removing all the application configs if I reinstall? Could I just reinstall and then safely delete all that stuff (would the necessary things be automatically created again? I guess not huh.. )

Would there be an easy way to do this? If not, I think I would be best just putting all my data on a different hdd and leaving /home on the same partition as the filesystem, but it would be interesting to know for reference.. :)

---

### Post by davmac on 2006-01-12
Good question and I'm just thinking of doing something similar myself. What I'm planning to do is;

- backup everything first
- set up a new temporary user
- move all the stuff I want from /home/myuserid to /home/tempuserid
- login to tempuserid and delete myuserid
- reinstall ubuntu
- set up myuserid
- move everything from /home/tempuserid to /home/myuserid
- delete the temp user id

That should leave me with a fresh install an uncluttered home and all of my data safe and sound.

Hope this helps,

Dave Mac

---

### Post by Kindred on 2006-01-14
Thanks, that seems the best way to do it actually.

I imagine when you reinstall and set up your new user in the installation it'll just go and put it right by tempuserid in /home, so that would be fine.

---

### Post by Titus A Duxass on 2006-01-14
Take a look at this [http://www.novell.com/coolsolutions/feature/11865.html](http://www.novell.com/coolsolutions/feature/11865.html), it is mainly SuSE related but has a lot of useful info. about moving and saving the /home.

I have used it to move my /home directory (data only) from a SuSE machine to my kubuntu machine.

I also made a back up of my /home directory.

Hope it helps.
Titus

---

### Post by aysiu on 2006-01-14
[QUOTE=Kindred]
Is this how it works?  I already hate the mess left by programs leaving files around in my home dir after deletion (.gconf etc) so how would I be able to leave the actual data I have in my home dir (work, mp3s etc) while removing all the application configs if I reinstall? Could I just reinstall and then safely delete all that stuff (would the necessary things be automatically created again? I guess not huh.. )[/QUOTE] Yes. Just reinstall and then go to your /home directory and delete all the hidden files (the ones that start with .)

I think an easier way to do it would be to not have a separate /home partition and just leave your current /home partition as a "data" partition (you can even mount it at /data or something like that) and when you reinstall just have a / partition and a /data partition--that way /home will be created on the / partition with new config files and /data will be your old /home partition with all your data files and old config files.

By the way, I feel the same way as you about the config files... except .mozilla and .thunderbird, of course.

---

### Post by Kindred on 2006-01-14
Hm, if you just reinstall using a different user name then move the stuff over then delete the original user that would be fine, right? 

So usually if you wanted to keep everything the same would you just use the existing user name during the install set up?  I just read doing that creates permission errors? That doesn't make sense if that's true..

---

