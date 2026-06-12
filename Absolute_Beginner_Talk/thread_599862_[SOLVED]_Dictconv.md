---
title: "[SOLVED] Dictconv ????"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by ENigma885 on 2007-11-01
i'm totally new to Linux in general and Ubuntu in specific...i really like the idea to make something for humans not for market and pure business ...(i just felt like saying this :))

my problem is that i feel that i can't do things that seem very primitive to  many Linux users .

like:...i used to run Babylon dic. in my Windows pc.Now after the Ubuntu switch i missed my beloved dictionary . i heard of some alternatives like StarDict and others..and there's a tool to convert the .bgl Babylon dictionaries to Stardict ones.. it's Dictconv 
i dunno how to use it i googled it then i came up with a step by step instruction [here]("http://blog.shevin.info/2007/04/how-to-implement-babylon-dictionaries.html")
wat makes that a problem is that i dunno wat the writer's talking about although it's-as i said- primitive .like when the writer said :"then enter this : sudo ./configure". Enter this where? ...i thought it's the writer's problem .so i searched for Dictconv somewhere else .i found [this]("http://linux.softpedia.com/get/Education/Dictconv-23446.shtml#")
Under Installation: they wrote "$ ./configure --help
$ ./configure [options]
$ make all install" wtf i dunno wat that could be? - i know it's somekind of commands but where should i write them ...dunno

may b my whole problem is that i used Windows more than enough i know.:(.

but i think u can help me to get rid of this monopoly ..i'm sure u will

---

### Post by taurus on 2007-11-01
You enter those commands into a terminal, Applications -> Accessories -> Terminal.

---

### Post by Hospadar on 2007-11-01
yep, you'll run those from a terminal.

Also note: you'll probably need to prepend the "make all install" command with "sudo" so it looks like "sudo make all install" because the install command will probably copy files to system areas of your machine that are normally write-protected so you don't accidentally tamper with important things.

Furthermore, what you are doing with these commands is compiling source code, so you'll need the compiler (gcc/g++) and the general linux build tools (the "make" program).  You can install these easily through synaptic package manager (System->Administration->Synaptic) and search for "build-essential" and install it, or, in the command line, enter "sudo apt-get install build-essential"

Also, you can look at the configure options, but you probably won't need to actually use any of them.  Just make sure you have any dependancies you might need (any ones you do need can probably be installed from synaptic, make sure you get the <dependancy you need>-dev package as well as the dependancy, as these contain the code files you need to compile stuff.

Good luck!

---

### Post by nogamal on 2007-12-20
I cannot manage to use  dictconv! 
I hit cd dictconv as instructed, and terminal tells me "no such file or directory"
I have installed it already but I do not understand how to use it. It's sitting on my desktop, and I extracted the file, but when I follow the directions given here ([http://blog.shevin.info/2007/04/how-to-implement-babylon-dictionaries.html](http://blog.shevin.info/2007/04/how-to-implement-babylon-dictionaries.html)) or here ([http://ktranslator.sourceforge.net/download.html](http://ktranslator.sourceforge.net/download.html)) it just doesn't work - it won't respond to the cd commands or to the configure commands. I'm completely new to this and am sure that I'm just doing something wrong. Any idea what though?

I'd really appreciate some help...
thanks!

---

### Post by hyper_ch on 2007-12-20
Isn't there a gDesklet that will do translations?

---

### Post by christhemonkey on 2007-12-20
If the file is on your desktop, then you need to type this:
```
cd Desktop/dictconv<Press tab now> 
```

Then you should be able to follow the instructions in [that blog.]("http://blog.shevin.info/2007/04/how-to-implement-babylon-dictionaries.html")

EDIT: To proceed with the his instructions i found i needed to install build-essential libxml2-dev and dictzip use this command to install them:
```
sudo apt-get install build-essential libxml2-dev dictzip 
```


I have compiled dictconv, so if you really cant manage installing it (try again please!) then you could probably send me the files and i can convert them for you.

---

### Post by nogamal on 2007-12-20
> **christhemonkey said:**
> If the file is on your desktop, then you need to type this:
```
cd Desktop/dictconv<Press tab now> 
```

Then you should be able to follow the instructions in [that blog.]("http://blog.shevin.info/2007/04/how-to-implement-babylon-dictionaries.html")

EDIT: To proceed with the his instructions i found i needed to install build-essential libxml2-dev and dictzip use this command to install them:
```
sudo apt-get install build-essential libxml2-dev dictzip 
```


I have compiled dictconv, so if you really cant manage installing it (try again please!) then you could probably send me the files and i can convert them for you.

Thank you so much christhemonkey what you suggested did the trick. However, I now encounter another problem! When I try to convert the BGL to ifo terminal tells me the following:
nogamal@nogamal-laptop:~/Desktop/dictconv-0.2$ dictconv Babylon_English_Arabic.BGL -o Babylon_English_Arabic.ifo
Error openning Babylon_English_Arabic.BGL
Error converting Babylon_English_Arabic.ifo

What am I doing wrong now...?
Thanks again!

---

### Post by christhemonkey on 2007-12-20
Did you put the Babylon_English_Arabic.BGL in the same directory as the dictconv executable?

---

### Post by jefenet on 2008-04-08
help me please

I can't install dictconv.


root@jefenet-laptop:/home/jefenet/dictconv-0.2# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... Invalid configuration `i686-pc-linux-': machine `i686-pc-linux' not recognized
configure: error: /bin/bash ./config.sub i686-pc-linux- failed



how I Can solve this?

Invalid configuration `i686-pc-linux-': machine `i686-pc-linux' not recognized

---

### Post by ENigma885 on 2008-04-08
> **jefenet said:**
> 


how I Can solve this?

Invalid configuration `i686-pc-linux-': machine `i686-pc-linux' not recognized

i recommend installing StarDic from **Synaptic Package Manager** (System>>Administration>>Synaptic Package Manager) 
In this way ,u will avoid dependencies mazes and unrecognized errors like that one u got .

---

### Post by jefenet on 2008-04-08
> **ENigma885 said:**
> i recommend installing StarDic from **Synaptic Package Manager** (System>>Administration>>Synaptic Package Manager) 
In this way ,u will avoid dependencies mazes and unrecognized errors like that one u got .

yes, i have intalled stardict. i did this System>>Administration>>Synaptic.

stardict is ready but dictconv no found.

---

### Post by ENigma885 on 2008-04-08
I think u need to install build-essentials package

 " sudo apt-get install build-essential" 

the same problem was discussed [here]("http://ubuntuforums.org/showthread.php?t=193504")

---

### Post by jefenet on 2008-04-12
i did this but I have a problem

root@jefenet-laptop:/home/jefenet/dictconv-0.2# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... Invalid configuration `i686-pc-linux-': machine `i686-pc-linux' not recognized
configure: error: /bin/bash ./config.sub i686-pc-linux- failed



help me please

---

### Post by ENigma885 on 2008-04-12
Well..According to this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=193504") installing "build-essential" should have solved ur problem...but apparently it didn't work for u.

So i have two suggestion here as a temporary solution:

**1.** u can download ready-converted StarDict dictionaries ...u will find dozens of sites 
ex. [[COLOR="Red"]http://xdxf.revdanica.com/down/index.php[/COLOR]]("http://xdxf.revdanica.com/down/index.php")(choose StarDict format from Other Options menu before u make ur search)
Another one would be [[COLOR="Red"]StarDict official website[/COLOR] ]("http://stardict.sourceforge.net/Dictionaries.php") 
U can also google for other websites .

after downloading extract the downloaded dictionary (u should by then get a Folder containing 3 files  .dict.dz , .idx and .ifo) 
move the folder to Stardict dictionaries folder 
```
cp -r Folder /usr/share/stardict/dic
``` 
and u r done  

**2.** I personally can help =) u can send me ur .bgl dictionaries ,i convert and send them back to u (i can send u my email add. in a private message if u r interested)

---

### Post by go_beep_yourself on 2008-05-09
> **jefenet said:**
> help me please

I can't install dictconv.


root@jefenet-laptop:/home/jefenet/dictconv-0.2# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... Invalid configuration `i686-pc-linux-': machine `i686-pc-linux' not recognized
configure: error: /bin/bash ./config.sub i686-pc-linux- failed



how I Can solve this?

Invalid configuration `i686-pc-linux-': machine `i686-pc-linux' not recognized

sudo apt-get build-dep stardict

---

### Post by iiutui on 2008-06-16
I also can't install dictconv.

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables

How can I solve this?

---

### Post by ENigma885 on 2008-07-10
[SIZE="3"]_For all the ppl facing problems installing "Dictconv" _
[/SIZE]
i have _[attached]("http://ubuntuforums.org/attachment.php?attachmentid=77128&d=1215686947") _ dictconv in a .deb package, meaning that u don't have to compile it form source, [COLOR="Red"]just double click and install[/COLOR].

I have converted it form source code using Checkinstall hope it's useful
and if u have any problems using Dictconv reply here or send me a private message, be sure that i will do my best to help.

---

