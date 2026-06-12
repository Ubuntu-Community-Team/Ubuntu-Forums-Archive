---
title: "Is there some sort of 'Complete Idiots Guide' floating around?"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by Fingolfin269 on 2006-09-09
I'm getting fairly frustrated with this.  I am doing my due diligence and downloading instructions for everything I want to do.  I read them top to bottom and back and find them all to be very information.  However, all of them leave out at least one thing due to assuming that every person reading them is at least somewhat knowledgable with the system.

For example, I'm currently trying to get my Linksys wireless USB dongle to work with ubuntu.  I have instructions on how to accomplish this but apparently everything has to be done from a command line (is this true for everything in linux?).  This is fine but the instructions leave out one important thing.... how do you pull up the command line. :p  I can't find it anywhere.

---

### Post by taurus on 2006-09-09
Applications -> Accessories -> Terminal!!!

---

### Post by snapcase16 on 2006-09-09
The command line can accessed from the terminal. If you go to Applications/Accessories/Terminal, you'll be all set. The closest I have found to a guide which covers many subjects is: [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper). Your best bet is to copy and paste the commands from various guides into the terminal. Good luck.

---

### Post by Omnios on 2006-09-09
There is a know your terminal commands link in my signature with many pages with different formats. Also some are good for reference to look up  certain commands

---

### Post by Fingolfin269 on 2006-09-09
I've been screwing around with the terminal but every one of the commands I type in (based on other guides) tell me something like:

"Bash: Invalid Command"

I just found the ctrl-alt-f1 command and all of the stuff works in this mode.  This is kind of weird to me and is going to take a lot of getting used to. :p

---

### Post by taurus on 2006-09-09
What commands are you talking about?  Maybe you need to run them with sudo...

---

### Post by Fingolfin269 on 2006-09-09
If I type in sudo it gives me the exact same error.  I tried typing ls, mkdir, etc. and it always says that.  I wanted to make a new directory so I typed in 'mkdir X' or something like that (following a guide) and got the same error.

---

### Post by Fingolfin269 on 2006-09-09
You have got to be kidding me........

It did not recognize the command because I was typing in uppercase. :P  Give me a break!!

---

### Post by taurus on 2006-09-09
> **Fingolfin269 said:**
> You have got to be kidding me........

It did not recognize the command because I was typing in uppercase. :P  Give me a break!!
This is Linux (Unix), NOT that stupid Windows.  Upper cases are not the same as lower cases here...  ](*,)

---

### Post by Fingolfin269 on 2006-09-09
I'm starting to appreciate the simplicity of Windows even with it's downside.  I can't even trust instructions such as below to work.  I get to the proper directory but now all I get is 'make is an invalid command'.  I don't mind screwing around in a command line but I want things to work without having to fight with it.  All I want this thing to do is connect to the internet with my Linksys wireless adapter using WPA.  That is all I will ever use this thing for! :p

Downloading 
===========

Download the latest version of the ndiswrapper sources from here and
extract it with the command

  tar zxvf ndiswrapper-version.tar.gz

This will create ndiswrapper-version directory. Change to that
directory and run

  make uninstall
  make

Login as root and run
  make install

---

### Post by jimrz on 2006-09-09
> **Fingolfin269 said:**
> I'm starting to appreciate the simplicity of Windows even with it's downside.  I can't even trust instructions such as below to work.  I get to the proper directory but now all I get is 'make is an invalid command'.  I don't mind screwing around in a command line but I want things to work without having to fight with it.  All I want this thing to do is connect to the internet with my Linksys wireless adapter using WPA.  That is all I will ever use this thing for! :p

Downloading 
===========

Download the latest version of the ndiswrapper sources from here and
extract it with the command

  tar zxvf ndiswrapper-version.tar.gz

This will create ndiswrapper-version directory. Change to that
directory and run

  make uninstall
  make

Login as root and run
  make install

do you have build-essential installed? sounds like not. you can install from synaptic

or try using the ndiswrapper included in your current ubuntu kernel + ndiswrapper-utils (also available via synaptic).

---

### Post by taurus on 2006-09-09
Before you run make, you need to install build-essential.  From a terminal, Applications -> Accessories -> Terminal, type

```

sudo aptitude build-essential

```
Then, 

```

make
sudo make install
-or-
sudo checkinstall

```

---

### Post by Fingolfin269 on 2006-09-09
See, this is the sort of thing I mean.  I would have had no idea how in the world to do any of that had I not posted here.  

Is there a version of Ubuntu that comes with pretty much everything you need already installed?  Or is there a list of things I will want to do immediately upon installing because, chances are, it is something I will need that is not installed with the initial OS?

---

### Post by taurus on 2006-09-09
If you care enough to read the README or INSTALL that comes with the source, then it would tell you exactly what you have to do to build and install it!!!  :rolleyes: 

Otherwise, use apt-get/aptitude/synaptic to install the binary directly so you don't have to worry about building anything...

---

### Post by bodhi.zazen on 2006-09-09
> **Fingolfin269 said:**
> I'm starting to appreciate the simplicity of Windows even with it's downside.  I can't even trust instructions such as below to work.  I get to the proper directory but now all I get is 'make is an invalid command'.  I don't mind screwing around in a command line but I want things to work without having to fight with it.  All I want this thing to do is connect to the internet with my Linksys wireless adapter using WPA.  That is all I will ever use this thing for! :p

Do not confuse familiarity with ease. Windows is familiar to you and seems easier. Wait untill you have years of experience with Linux, then compair.

Guide: [color=brown]Beginning Ubuntu Linux From Novice to Professional[/color]
[color=brown]By Keir Thomas; Apress[/color]

Guide to command line:
[Linux commands; Ubuntu forums](http://ubuntuforums.org/showthread.php?t=253770&highlight=unix%2A)

---

### Post by Omnios on 2006-09-09
Hi hi, if you want some heavy Linux learning you might want to check out.
[http://rute.2038bug.com/rute.html.gz](http://rute.2038bug.com/rute.html.gz)

---

