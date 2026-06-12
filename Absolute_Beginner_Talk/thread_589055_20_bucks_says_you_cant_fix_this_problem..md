---
title: "20 bucks says you cant fix this problem."
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by mbailey1 on 2007-10-23
so i saw the upgrade for the new version. i started it rebooted and then finished by fixing some broken files with synaptic. then i walk away and while it is downloading my little bro logged off b/c he wanted to play that stupid robot game. then the screen was black i knew i was screwed from that point. so i restarted the computer message pops up says welcome aplication cannot be found trying another (i clicked ok) same thing happened over and over till a blue screen comes up, said somthing like welcome screen restarted 6 times could have big problem. i am a noob no idea what to do. please help.

old dell computer if thats helpful.

---

### Post by Pumalite on 2007-10-23
Better reinstall after saving data. 256 MB of RAM or less> Xubuntu Alternate CD.

---

### Post by vertexoflife on 2007-10-23
Do you know anything else about the computer?

Can you afford to a fresh install (wipe the memory off your hard drive) or is there stuff you need to save?

---

### Post by asmoore82 on 2007-10-23
restart the computer and pick "recovery mode" from the boot options
when you get to a root prompt (#) run this to try to clean up the package mess ...

```
# apt-get update
# apt-get check
```

you may get an error about a stale lockfile;
if so, ***carefully*** delete that file with the `rm` command

... I would prefer 10 crisp 2-dollar bills.

---

### Post by mbailey1 on 2007-10-23
what does carefully delete with rm command mean
and what would happen after than everything reverts back to normal?

sorry for the stupidity and lying to you about paying but dude
i get E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem

---

### Post by Paulmd on 2007-10-24
> **mbailey1 said:**
> what does carefully delete with rm command mean
and what would happen after than everything reverts back to normal?

sorry for the stupidity and lying to you about paying but dude
i get E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem

What do you get when you run  'dpkg --configure -a' in the terminal?


type

dpkg --configure -a

press enter

---

### Post by dimbulb1024 on 2007-10-24
Damn, I don't know.  I could have use that 20 bucks :lolflag:

---

### Post by fruitsofherwomb on 2007-10-24
Do the Souja Boy to Superman?! At least I tried :/

---

### Post by mbailey1 on 2007-10-24
paulmd, you have gotten the closest. heres the scoop it did everything, instaled downloaded but then came up with 'errors were encountered while processing: screen'

whats next wise ubuntu paul?

---

### Post by Paulmd on 2007-10-24
> **mbailey1 said:**
> paulmd, you have gotten the closest. heres the scoop it did everything, instaled downloaded but then came up with 'errors were encountered while processing: screen'

whats next wise ubuntu paul?

 in the terminal

sudo apt-get install ubuntu-desktop

maybe.

after that, have another go with dpkg --configure -a

---

### Post by CaptainInsaneO on 2007-10-24
I'll kick your little bro's *** for 20 bucks. Problem solved. Where's my money? :lolflag:

---

### Post by mbailey1 on 2007-10-24
how do you know this stuff man thats seriousosly amazing except i type it dpkg --configure -a and then nothing happens just another root command slot apears. i am going to try a restart normal see what happens..... same thing. any idea whats going on

---

### Post by Paulmd on 2007-10-24
> **mbailey1 said:**
> how do you know this stuff man thats seriousosly amazing except i type it dpkg --configure -a and then nothing happens just another root command slot apears. i am going to try a restart normal see what happens..... same thing. any idea whats going on

I'll get back to you when I have my Ubuntu machine front of me (i'm Using an XP machine at present)

---

### Post by mbailey1 on 2007-10-24
thanks for putting time in man dont know where i would be w/o your genius

---

### Post by Paulmd on 2007-10-24
> **mbailey1 said:**
> how do you know this stuff man thats seriousosly amazing except i type it dpkg --configure -a and then nothing happens just another root command slot apears. i am going to try a restart normal see what happens..... same thing. any idea whats going on

some things to try in the terminal

sudo apt-get autoremove
sudo apt-get autoclean

sudo apt-get --fix-broken
sudo apt-get build-dep ubuntu-desktop

also try

 sudo dpkg --configure -a

---

### Post by mbailey1 on 2007-10-25
i tried all of em, my login application is still not found!

---

### Post by macogw on 2007-10-25
sudo apt-get install gdm

?

---

### Post by LowSky on 2007-10-25
Dont forget the sudo

```
sudo dpkg  --configure -a
```

or use sudo-i to stay as root user for a while instead of per command

---

### Post by mbailey1 on 2007-10-25
i tried every single thing given to me at least twice. now it says 'the greeter application appears to be crashing.' then it tires to find another one and the same message pops up. keep the commands coming hopefully it will work sometimes soon.

---

### Post by mbailey1 on 2007-10-25
hey i got an idea, i have a ubuntu cd, can i just tell the computer to download the greeting program off the cd via root comand?

---

### Post by tomauty on 2007-10-25
> **fruitsofherwomb said:**
> Do the Souja Boy to Superman?! At least I tried :/

I like your Half Japanese avatar. I have Charmed Life.

---

### Post by mbailey1 on 2007-10-27
well i figured it out. i am now running on gusty i think. 
i used

sudo apt-get upgrade

i think all of the unfinished packages were finished and it worked again

---

### Post by CaptainInsaneO on 2007-10-27
apt-get upgrade just upgrades your applications, if you want to upgrade your distro use dist-upgrade.

---

