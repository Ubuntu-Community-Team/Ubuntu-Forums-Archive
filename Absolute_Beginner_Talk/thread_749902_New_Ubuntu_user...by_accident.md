---
title: "New Ubuntu user...by accident"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by sifon187 on 2008-04-08
I have know of Linux for years, but I have always been scared to try any of the distributions. I thought Linux was "nothing compared to windows" and windows was the one and only master OS. Well yesterday evening I made a decision to dual boot xp mce and Ubuntu. I have been running ubuntu a few weeks on vmware, but at half the capicity. I wanted to experience ubuntu at "full power". I googled the dual boot setup and began the steps. Well along the way, either I missed a step or I did not following the tutorial, but windows was over writting by Ubuntu. I also managed to partion my external as well :confused: Next time I will get more sleep before I make a major decision. Anyway, after a few grub errors and a few smokes I got Ubuntu running. At first I was confused and scared. Things seemed very strange to me. I kept trying to find the start menu :rolleyes:. But as I went along and read a few things on the net...I have found Ubuntu and linux in general a very awesome OS. Graphically Ubuntu looks much better then XP and my CPU seems to preform smoother. I am excited to learn new things with Ubuntu. Only one thing truly confuses me How the hell do I install a program I download directly from the internet. I have the Package Manager figured out, but the rest I am still learning. 

P.S. I am not a newb to computers in General, just to Linux. But I feel like the day I got my first computer. Willing as much as possible. Its hard starting over but it will be fun

---

### Post by Therion on 2008-04-08
Welcome aboard.  

That strange feeling you are currently experiencing is called ... FREEDOM.  Try to relax and just breathe through it.  Don't worry, you'll get used to it.

---

### Post by vishzilla on 2008-04-08
You can use the package manager to install the applications in the repository. Additionally you can check Applications->Add/Remove to see what program you can actually install.
You can read [this]("https://help.ubuntu.com/community/SoftwareManagement") for more information

---

### Post by sifon187 on 2008-04-08
I started having withdrawls...for an hour,,,once I got Ubuntu running all that went away

---

### Post by Epic Plecostomus on 2008-04-08
Once you learn a few key terminal-commands you'll be an unstoppable Linux God.   Or at least able to implement some of the tweeks and improvements you'll come across on this forum.   

For example if you have a painfully slow boot (over 60 seconds) there is a method to edit one of the files using terminal to correct the problem.

My video drivers were installed via terminal and I set up Sensors using it as well.

THIS IS WHAT SETS LINUX APART in my opinion.   You can do ANYTHING on here, anything at all.  You are not limited to what Microsoft says you can and cannot do.

Good luck, and remember... they aren't mistakes they are learning experiences... I myself have had to reinstall three times because of my learnings.  :p

---

### Post by Therion on 2008-04-08
> **sifon187 said:**
> ... either I missed a step or I did not following the tutorial, but windows was over writting by Ubuntu.
Well, since you're entrenched at this point I guess I can tell you... That whole Windows being wiped out thing?  Yeah... Ummmm...  

That was no accident.

<cough>

---

### Post by clarknova on 2008-04-08
Given that you understand the package manager, I just want to stress that it is the preferred way to install and remove packages/programs.

Sometimes you want/need a package that isn't in the supported repositories. In some cases you can add an unsupported site to your repositories list, update, then use the package manager to install your package and keep it up to date. With this method you want to be sure you trust your added repository. I think you can get Google Earth and Skype by this method.

The next method is the less desirable, because it doesn't manage a package's dependencies and it doesn't update itself. Look for an installer package ending in .deb. Once downloaded you can double-click these and use your password to install the package. Debian .deb files will usually work, but Ubuntu flavoured .debs are preferred when available. dpkg is a cli that also works for this. Brother printer and scanner drivers work this way.

If you can only find a .rpm installer you'll have to convert it to a .deb on the cli using alien (available in the repos). This doesn't always work. I have installed LaCie's lightscribe utilities via this method.

Another installer method is a binary or scripted installer. These can be easy or messy. Sometimes you just double-click the icon or you can use the cli to do "sudo sh installer.bin". Vmware provides one of these, as does the Quake 4 demo and Google Earth, but then at least two of the preceding are available through one of the above-mentioned methods.

If all else fails, you can always download and compile source code. I'm not getting into that here.

Good luck.

db

---

### Post by savagenator on 2008-04-08
read the thread in my sig, and please comment on how I can improve it. It may be able to help you.

---

### Post by pastalavista on 2008-04-08
I am a noob too and although I was successful doing a dual boot on my Vista pre-installed laptop, I am now using Ubuntu almost exclusively. I only boot Vista when I want to play certain games that don't run very well on Wine. I have had great success with a program I found in the Synaptic Package Manager called GDebi Package Installer which works beautifully for .deb packages. I still have difficulty with tar.gz packages but .deb packages install as slick and easy as Windows with GDebi. Also I got a lot of help HERE

---

### Post by pastalavista on 2008-04-08
sorry, html was off... go here: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by ramjet_1953 on 2008-04-09
Welcome aboard!

A little advice, if I may?

With software, there is a plethora of stuff available to you, if you just enable the extra repositories.

Let's take it a step at a time.

1. Navigate to [COLOR="Blue"]Applications>Add Remove[/COLOR]

2. When the window opens, look to the top far right and click on the [COLOR="Blue"]up/down arrow in the Show box.
[/COLOR]
3. Select [COLOR="Blue"]All Available Applications[/COLOR].

You will now have heaps of extra software that you can install painlessly.

Stick with this for a while, before venturing into Synaptic and enabling any extra repositories.

Still further down the track, you can install the [COLOR="Blue"]build-essential[/COLOR] package and have fun with compiling and installing software from scratch.

However, take it a step at a time and enjoy. Too many people want to start compiling immediately, don't understand about dependency requirements and then blame Linux, instead of their own lack of knowledge.

Regards,
Roger :cool:

---

### Post by sifon187 on 2008-04-09
THanks for all the info. I am starting to understand the install process pretty well. Already have installed a few programs I needed. I am oging to take one step at a time though. You cannot run before you walk.

---

### Post by esttorhe on 2008-04-09
> **pastalavista said:**
> ... I still have difficulty with tar.gz packages...

```
> tar -xf <packageName.tar.gz>
```

then read the README :P
they give you step by step installation instructions, although not all installations runs as smooth as one would wish

---

