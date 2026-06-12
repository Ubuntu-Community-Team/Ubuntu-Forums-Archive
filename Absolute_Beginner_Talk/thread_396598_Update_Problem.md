---
title: "Update Problem"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Punker on 2007-03-29
hey I installed Automatrix just to try it and I dident like it so I uninstalled it
as well I uninstalled wine now when I go to check for updates
I get this error can someone help me fix it because I'm soo sorry I installed thies programe's

: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_edgy-commercial_main_binary-i386_Packages)

I also like to say automatix messed up my BIOS I still use a old dos boot disk to look at my drive and the boot disk did not boot so I thought it was the boot disk went into my BIOS and everything was different so I set it all back like I had it and then tryed the boot disk still would not boot so I have a old redhat cd I used it to erase my drive
put boot disk back in after all this and it worked fine why was my BIOS and my computer acting like this I blame automatix sorry but their is a positive thought in mind about automatix #1 cant spell it  #2 the program does have potential and who ever wrote it has a lot of  potential as well but it messed up my computer but I learned from it

---

### Post by zvacet on 2007-03-29
You can go to your sorces list and delete double lines.
```
gksudo gedit /etc/apt/sources.list
```

Or you can completly delete your sorce list and replace it with 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

I use same source list.

---

### Post by Punker on 2007-03-29
ok now I'm getting lost sorry if I made you mad about the automatrix 
but anyway I delete the list and saved it now it's empty lol but its failed when it try's to get security updates in the software source what do I put in the list or what 
 nice thank you for the sight it was helpfull but I'm still haveing a problem

---

### Post by Delvien on 2007-03-29
It is best NOT TO USE AUTOMATIX.

Please read the guide below, it will tell you how to install pretty much anything you need:

[http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)

---

### Post by Punker on 2007-03-29
why please tell me I uninstalled it i'm safe? 
I complete removed it yes this sight it a big time help and my software source seems to be ok now I got some updates so this was good

---

### Post by Punker on 2007-03-29
should I do a reinstall of everything? I would realy hate to

---

### Post by zvacet on 2007-03-30
I´m not sure I understan you.Are you saying that your source list is empty?It is not supose to be empty,just replaced with one from link I posted to you.You don´t need to reinstall,just copy source list from link.Post source list you have now and we will see if something is wrong with it.

---

### Post by Punker on 2007-03-31
ho the help I got lastnight was great it went perfectley I had no erros after that.
I reinstalled anyway because I got up this morning and the ISP was down so I wanted to do everything correctley on what I have learned here and it get's better and better everytime thanks alot man no more automatix

---

### Post by Maestro23 on 2007-03-31
Glad you got it worked out Punker.  

Can you go and edit your first post to RESOLVED.  It will be under advanced.

---

### Post by compiledkernel on 2007-03-31
EasyUbuntu is a more clearly aggreeable and defined choice. 

Automatix is unsupported software by the community. These forums do not support it either. If you have difficulties with Automatix, you should refer back to their forums at [www.getautomatix.com](www.getautomatix.com) for further help.

Let me firmly reiterate that Automatix is just as it is --

"automatix is a script that tries to install some software, and often
fails and breaks systems. We don't provide support for it, and we strongly
discourage its use. Problems caused by Automatix are often hard to track
and solve, and it might sometimes be easier to !install a fresh copy of
Ubuntu."

---

### Post by Punker on 2007-04-02
> **Punker said:**
> hey I installed Automatrix just to try it and I dident like it so I uninstalled it
as well I uninstalled wine now when I go to check for updates
I get this error can someone help me fix it because I'm soo sorry I installed thies programe's

: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_edgy-commercial_main_binary-i386_Packages)

I also like to say automatix messed up my BIOS I still use a old dos boot disk to look at my drive and the boot disk did not boot so I thought it was the boot disk went into my BIOS and everything was different so I set it all back like I had it and then tryed the boot disk still would not boot so I have a old redhat cd I used it to erase my drive
put boot disk back in after all this and it worked fine why was my BIOS and my computer acting like this I blame automatix sorry but their is a positive thought in mind about automatix #1 cant spell it  #2 the program does have potential and who ever wrote it has a lot of  potential as well but it messed up my computer but I learned from it

compiledkernel

no more!    

[http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)
this is a much better guide as well as this forum this forum is like a big book for me its great as well as IRC

---

