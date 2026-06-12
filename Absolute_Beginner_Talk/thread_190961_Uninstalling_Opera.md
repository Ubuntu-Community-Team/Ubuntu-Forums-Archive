---
title: "Uninstalling Opera"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by ramcosca on 2006-06-06
Hello all.
I decided to give Opera a tryout, see if I could find something that would change my Firefox use. I played with it a bit but instantaneously found it irritating.
But that's not the point... I try to remove is using Add/Remove Applications and just can't, it isn't there. Since I'm new to Linux, I'd like some help: how can I remove it using the Terminal?
Thanks.

---

### Post by ProjectGod on 2006-06-06
not 100% sure but try:

**sudo aptitude remove --purge opera**

it just might work. not sure cause i'm on a windows machine right now ](*,) :-\"

---

### Post by ramcosca on 2006-06-06
Hey, thanks! It uninstalled!
If you'd be so kind as to explain that code... I want to learn!

---

### Post by ProjectGod on 2006-06-06
well... sudo is the command to temporarily give a normal user "super user" or "administrative" rights so that they may go about doing system configuration etcetc

there are basically 3 primary tools on ubuntu on which you can use to install software / packages... they are:

the apt system
synaptic (gui package manager)
aptitude (a front end to apt system)

so sudo aptitude basically calls on the utility aptitude... 

next... remove this is a parameter for the utility... 

next --purge... what this does is remove the configuration files for the software / package in question... in this case OPERA!

so basically the command flows like this... call on super user! use aptitude! remove and purge OPERA from the system!

check these links out... very practical

[B][COLOR="MediumTurquoise"]ubuntuguide.org
linuxnewbieguide.org
wiki.ubuntu.com[/COLOR][/B]

also type this and you'll get a host of information on each utility

**man aptitude**
or

**aptitude --help**

---

### Post by Sef on 2006-06-06
> sudo aptitude remove --purge opera

> If you'd be so kind as to explain that code

sudo is a fake root.  [Click here for more info.]("https://wiki.ubuntu.com/RootSudo")

aptitude is an updated apt-get.  Use it whenever you install something.  Makes unistalling much easier.

-- purge gets rid of everything that installed with the program you are removing.

---

### Post by ramcosca on 2006-06-06
Thank you, thank you, thank you to both. I am glad Ubuntu has the back up of this community!

---

### Post by ramcosca on 2006-06-06
[QUOTE=ProjectGod]also type this and you'll get a host of information on each utility

man aptitude
or

aptitude --help[/QUOTE]Wow, this is new, fascinating and very helpful! Thanks! =D>

---

