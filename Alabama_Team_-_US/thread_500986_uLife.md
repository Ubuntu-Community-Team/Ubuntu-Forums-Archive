---
title: "uLife"
date: 2007-07-14
forum: Alabama Team - US
---

### Post by johng4 on 2007-07-14
I've been working on putting together a metapackage of programs I'm nicknaming "uLife" in spirit of Mac's iLife.  Automatix has a similar package named iLinux which has a few of the programs, but doesn't cover the whole spectrum that iLife contains.

Problem.. I'm not familiar with packaging, let alone virtual packaging.  Also, I want to make a little GUI that allows a user to pick the programs they want to install, as well as offers them codecs that come with the standard warnings about them.

One work around is using the new APTURL protocol which will be coming in Gutsy (I don't have the link handy, but I have it installed on my uBook, and its very handy), and a web interface to add in the proper repos, and link to the packages.  That way its completely web based, and uses pre-existing repos to install everything needed.

Another concept would be to offer a CD with all the programs on it minus the codecs (which can't be distributed legally), but offer links to the codecs.

So, if anyone knows of some relevant documentation on meta-package creation, let me know.  I've been googling but I'm not finding anything useful.


uLife will contain...
Kino - Movie Editor.  I'm looking at PiTiVi as a possible alternative.
Banshee - Music Manager (also manages internet radio, and podcasts as well)
Democracy - Internet Media Manager (picks up where Banshee leaves off)
Jokosher - Music Composition.  Wired is a possible option as well.
Quanta - Web Development

---

### Post by crane on 2007-07-14
I believe I saw something on metapackages and creating packages for Ubuntu while looking through a book called Ubuntu Complete or something like that. I saw it tonight at Bookamillion. May find something good there.
 
Just be prepared to run into resistance. The ideas behind such things are great but they always turn out to be a script to install stuff, that could potentially lead to a broken system. If it doesn't integrate with the base OS properly it will cause problems.
 There are a lot of people who do not like Automatix and script based fix-all, and I am one of them. Ubuntu is making great advances in getting to an OS that has everything. I don't see a need for such programs. But that's just me. Others love them so good luck with it.
 I would be careful with the name as well. If uLife or iLinux become extremely popular I would bet Apple will call you to court over then name.

 **Note this is not meant as an attack on Automatix. I do not want this becoming another Battle over what people think is right or wrong for or against automatix. That has been done enough and is over.

---

### Post by johng4 on 2007-07-14
I wouldn't be creating anything that isnt in the standard Ubuntu repos, so much as a meta package that makes it easier for newer users, and users like myself who do a lot of installs/reinstalls, to get a suite of programs.

I'm not a fan of automatix myself either.  I think its good if you use Pioneer, but for Ubuntu I find it to be a slight irritation.  

A good concept to compare it to, is the ubuntu-desktop, kubuntu-desktop meta packages.  I'm adding nothing to it, just an ease of install.

The name could use some work, admittedly.

---

### Post by Nekiruhs on 2007-07-14
> **johng4 said:**
> I wouldn't be creating anything that isnt in the standard Ubuntu repos, so much as a meta package that makes it easier for newer users, and users like myself who do a lot of installs/reinstalls, to get a suite of programs.

I'm not a fan of automatix myself either.  I think its good if you use Pioneer, but for Ubuntu I find it to be a slight irritation.  

A good concept to compare it to, is the ubuntu-desktop, kubuntu-desktop meta packages.  I'm adding nothing to it, just an ease of install.

The name could use some work, admittedly.
Ya know, This really sounds like a job for a shell script! Just gimme a list of what you need installed and I can write it for ya.

---

### Post by johng4 on 2007-07-16
I could write the shell script. ;)  What I need is a GUI, and a meta-package. 

After thinking about it, I can probably do both more efficiently using APTURL and a webpage.

---

