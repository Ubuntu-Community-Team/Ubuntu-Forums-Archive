---
title: "Can I save downloaded programs to CD?"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by mrdaryljones on 2006-11-09
Both me and my friend have very slow internet, about 3kbs. i have spent ages (nights) downloading all of these programs and drivers like automatix ect. i want to put ubuntu on his computer and put all these programs and updates (it took me 12 hours to download all the updates after first installing ubuntu) on his computer quickly like from a CD. how can i do this? thx

---

### Post by bsussman on 2006-11-09
Unless you have made changes to the defaults, they should be in /ver/cache/apt/archives

When you mount the cd on the other machine, you will need to use dpkg to install .



Or modify your sources.list to include a local directory so that automatix, synaptic, or another front end can see them.  Or try to mimic the directory structure on the install cd and include your special cd in the sources.list file. This is possible but most folks do not bother.  

dpkg is not that hard.  And automatix should be able to manage them when you are done.

---

### Post by deanlinkous on 2006-11-09
If you are talking about stuff installed using apt/synaptic then look into
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
or the apt-move command.

---

### Post by mrdaryljones on 2006-11-10
thx heap for this but im really new (less than a week) to ubuntu. if you have the time and patience, could you spell it out, like what is dpkg and do i type this in the terminal. Can i just copy the files from /var/cache/apt/archives on to a CD then from the CD to this folder on his system. please spell it out for me. thx very much for your help

---

### Post by mrdaryljones on 2006-11-10
oh and as for APTonCD, how do i know if i installed using apt/synaptic, all the programs i downloaded have come from Automatix and the Add/Remove.

---

### Post by Bachstelze on 2006-11-10
In theory, yes, you can but you'll find out quite soon that it can quickly become *very* tedious because you'll have to manage dependencies manually. For exemple, say you want to install package A. Package A depends on package B, that means package A can't work if package B is not installed as well. All right, you install A and B. But if B depends on C and D, C depends on E, F and G, F depends on H, D depends on I, J, K and L, you can imagine the mess.

That's where APT comes to thge rescue, it will do all of it automagically, but it needs to have the list of available packages and whete it can get it from, most often from the Internet. If you want to use it offline (on a CD for example), you'll neet to prepare the CD, just copying the DEBs onto it won't do, so you can use AptOnCD as was mentioned earlier or switch to Debian, which has 21 CDs full of apt-gettable packages.

**EDIT :** another approach, and maybe an easier one if you can get the two machines near and network tham, would be to setup an [Apt proxy](https://help.ubuntu.com/community/AptProxy?action=show&redirect=AptProxyHowTo).

---

### Post by deanlinkous on 2006-11-10
> **mrdaryljones said:**
> oh and as for APTonCD, how do i know if i installed using apt/synaptic, all the programs i downloaded have come from Automatix and the Add/Remove.

As far as I know add/remove uses apt/synaptic in some form or fashion. Someone please correct me if I am wrong. So I would think APTonCD should work great or the apt-move command. You could look in /var/cache/apt/archives and see what all is in there.

Automatix is a seperate utility I think and I am not sure what it downloads or where it saves anything at.

---

### Post by Bachstelze on 2006-11-10
YUou are perfectly right :) And as far as I know, Automatix (badly) uses Apt, too.

---

