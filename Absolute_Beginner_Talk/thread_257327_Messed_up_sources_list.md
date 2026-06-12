---
title: "Messed up sources list"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-09-14
I dont know how i`ve managed this one but it seems ive ball`sed up my sources list.....OR list`S as they now are.
I have automatix on here so would need to keep that on my list but  whats the quickest and easiest way to get rid of what i dont want and keep what i do and have just ONE decent list 

Dont want to end up just creating another#-o 

The first time i installed i just copied and pasted some new source list i think but this time im sure i just used the "repositry function in synaptic?

This is the message i get about duplicate repo`s and the info within

W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_multiverse_binary-i386_Packages)

And this is how many i seem to have when i look in /etc/apt/

[ATTACH]15733[/ATTACH]

A right old mess....

EDIT:...NO comments on my crappy "wallpaper" i NEEDED to see the green green grass of "home" after 3 days installing and re-installing XP(without XP cd)

---

### Post by jordanmthomas on 2006-09-14
All you need to do to fix your errors is to edit sources.list and put a # at the beggining of lines that look like this
```

deb http://archive.ubuntu.com dapper-backports/ .....
```
There will be at least two each of them and you need to just make sure there are no duplicate entries.

(Even though you said you didn't want to make a new one, I would suggest it.  It isn't difficult)

---

### Post by Najand on 2006-09-14
Use [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic") to generate a new sources.list,  then copy and paste it to /etc/apt/sources/list

---

### Post by xpod on 2006-09-14
I also get this in the terminal when i do this
dad@dad-desktop:~$ gksudo gedit /etc/apt/sources.list
(gedit:10590): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
dad@dad-desktop:~$


I suppose THATS just a result of the above is it?

---

### Post by jordanmthomas on 2006-09-14
When this happens, does gedit still launch?
Also, most people use gksudo but I just use gksu.  Maybe that could help you out.

---

### Post by bulldog on 2006-09-14
Nope that's just a warning you get by using gksudo.

It's totally harmless so just keep using gksudo with apps with a GUI.

The bug is reported and classified as not urgent.

No worry's it's not gonna bite you and it has certainly nothing to do with your,a little messed up sources-list.:)

[Just comment out ##  the duplicates till you get no errors anymore]
After a few days when you realized you don't miss them,you can delete them.
But leaving them there is harmless too.

---

### Post by Najand on 2006-09-14
If you use repositories with gpg keys you need to import the keys from a key server, An easy way to do so, is:
```

gpg --keyserver subkeys.pgp.net --recv KEY
gpg --export --armor KEY | sudo apt-key add -

```
Change KEY with your gpg key number.

---

### Post by xpod on 2006-09-14
HAHA....Listen mate even the most harmless of tasks,app`s OR even "clicks"
can turm into the most bizzare of problems when it`s MOI thats doing the "clicking"

After 500 odd bloody posts you`d think i would KNOW how to undo the messes i make(could always uninstall eh....lol):biggrin: 

Im sure it`s that autommatix that was probably where things started to go wrong.....Im just NOW begining to realise what a waste of space it is.

Anyway....IF i do just generate one good new one how can i get RID of all the others.....I could`nt just send them to the waste basket as it was`nt an option.I understand the problem ok and know what i need to do ok BUT....

My mind just went blank when it came to the DOING IT!!

EDIT:> If you use repositories with gpg keys you need to import the keys from a key server, An easy way to do so, is:

SEE...NOW you`ve just complicated matters....LOL......I never had to GET no keys before so why would i now???excuse the ignorance

EDIT":...sorry...YES it still launches ok

---

### Post by Najand on 2006-09-14
> 

[QUOTE]If you use repositories with gpg keys you need to import the keys from a key server, An easy way to do so, is:

SEE...NOW you`ve just complicated matters....LOL......I never had to GET no keys before so why would i now???excuse the ignorance

EDIT":...sorry...YES it still launches ok[/QUOTE]

Hmm, some not official repositories (even official ones) are signed with gpg keys... I thought as you are editing your sources.list, you might need some if you are planning to add some new repositories.

---

### Post by xpod on 2006-09-14
All i want is the warning message to stop popping up when i use synaptic or add\remove and to have the best possible sources list.....and i suppose keep whatever automatix needs

And although it`s pedantic i`d also like rid of the numerous useless backup ones you can see in the /etc/apt/ file up there.
Looks like my backup`s have got backup`s.......WITH duplicates:biggrin:

---

### Post by xpod on 2006-09-14
This is my sources list as it is 

## Automatix sources.list
## This is automatically generated by Automatix


####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe restricted main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

# Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


##############################
### Automatix Repositories ###
##############################

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

## created by automatixrepo3

I dont see what the problem is meant to be#-o 

Where does it need the ##?
Or is it cause of one of those other ones it`s declaring duplicates?
Surely i can just delete the duplicate.......??????:confused:

EDIT:Those sorces lists you can see in the screenshot are the duplicates its on about...The "sources list" and "sources list.save" are both th same as are the two different back up ones..SO is it not just a case of removing THOSE duplicates????...Sorry if im confusing matters even more but i think thats what needs done

---

### Post by Najand on 2006-09-14
# means that line would be considered as comment and will ignore it. So, you  can use them as writing a discription about your file, a guidence, or just something that you want to be ignored after configuration.

---

### Post by xpod on 2006-09-14
yeah i know what it means mate :lol: but i just dont see wheres theres ANY duplicate entries in that list so it must be because i have actual complete duplicate sources lists no?????

---

### Post by Najand on 2006-09-14
> ## Automatix sources.list
## This is automatically generated by Automatix


####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe restricted main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

# Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

[COLOR="Blue"]deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse[/COLOR]

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


##############################
### Automatix Repositories ###
##############################

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

## created by automatixrepo3
The blue part

---

### Post by xpod on 2006-09-14
SEE....told you im hard work.
I scanned and scanned and scanned that bloody thing and STILL missed it#-o 

So those actual copies up there are nothing to worry about=D> 

I`ve fixed some pretty complicated stuff(xp...lol) for a pc noob in my short time doing this stuff BUT i always seem to have the most hassle when it comes to the simplest of things....:-\" 

thanks for that and forgive my ignorance:D

EDIT:...I still CANT see why THAT one is the prob as i see similar double entries with the "deb" then "deb-src" in front of them.
WHAT makes this one any different OR can i still not see the woods for the trees:confused: :biggrin:

EDIT.....EUREKA..THE PENNY HAS FINALLY DROPPED!!!!!!!!!!!!(i see it now):rolleyes:

---

### Post by Najand on 2006-09-14
> .I still CANT see why THAT one is the prob as i see similar double entries with the "deb" then "deb-src" in front of them.
WHAT makes this one any different OR can i still not see the woods for the trees
Becuase one belongs to the package and onne belongs to the source for that package,

---

