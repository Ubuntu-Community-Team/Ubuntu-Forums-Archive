---
title: "where the heck is debian?"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by gruvola on 2006-04-28
(total Ubuntu newbie so chill out on the flaming):  I can't find Debian anywhere on my Ubuntu menus - am I supposed to?  When I go into the application menus, the app doesn't seem to exist and it isn't in Synaptic Package Manager to add in.  There are other Debian apps, like debconf and debhelper, but. . .

The long version is:  I got a cheap computer from work that they didn't have a Windows license for (they could, and still can, give me NT) and my 9 y.o. needs a computer to do school work.  The IT guy thought I was sharp enough to give Linux a go so I decided to go for it.

Unfortunately the computer didn’t have a modem so I got a cheap one from MicroCenter (no help).  I then went to [www.linmodem.org](www.linmodem.org) and was able to download and run the tool to ID the chipset on terminal (I was mildly proud of myself), and I ID’d my kernel, too.  I then downloaded the driver from Linuxant and unzipped that on to my desktop.  But I can’t get the driver to run or the computer to recognize the .deb file.  I’ve tried several commands in terminal server (dpkg, etc.) and tried the ‘apt’ application (but it wasn’t that intuitive to me).

Did I install Ubuntu 5.10 incorrectly if I don’t have Debian?
Does this get any easier?
How do I unistall Linux and ‘wipe’ the harddrive if I chose to go back to NT?
Does anyone else miss DOS?

Thanks, gruvola

---

### Post by delta32 on 2006-04-28
No, you didn't install Ubuntu incorrectly. Debian is a distro, not an application. Ubuntu is based on Debian.

[http://www.debian.org/](http://www.debian.org/)

> **"gruvola"]Did I install Ubuntu 5.10 incorrectly if I don&#8217 said:**
> 
No.

[quote="gruvola"]Does this get any easier?
Depends on the person. 

> **"gruvola"]How do I unistall Linux and &#8216 said:**
> 
Just reformat and install Windows like normal.

[quote="gruvola"]Does anyone else miss DOS?
Not at all.

---

### Post by Qrk on 2006-04-28
1) No
2) Yes
3) Don't worry
4) a little

First lets make sure you did the dpkg command right.  Don't unzip the .deb, make sure you keep it as a the "archived" .deb package. A deb file is a program packaged so that Ubuntu can automatically install it. If you saved the .deb file to your desktop, try pasting this (line by line) into the terminal.

```
cd ~/Desktop
sudo dpkg -i *.deb
```

Debian is another Linux distro, not a program. Ubuntu is based on Debian, so there is a lot in common, but they are not the same thing.

---

### Post by ubuntu27 on 2006-04-28
I think he is talking about DEBIAN MENU... 


***Looking for Debian Menu How TO***

---

### Post by Sutekh on 2006-04-28
I think you are right ubuntu27.

In that case
```
sudo apt-get install menu
```
Gets the Debian menu.  Its in the universe repository, so you will have to enable that first...[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

---

### Post by ubuntu27 on 2006-04-28
[QUOTE=Sutekh]I think you are right ubuntu27.

In that case
```
sudo apt-get install menu
```
Gets the Debian menu.  Its in the universe repository, so you will have to enable that first...[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)[/QUOTE]


You bit me :D I was looking for a thread where it explains how to enable Debian Menu...
In the end, I found it in page 20 of my serach result, which it happend to be the last page :D

I'm so bad at looking for a specific stuff :D :rolleyes:

---

### Post by catlett on 2006-04-28
There are Debian apps on Ubuntu but Ubuntu is not Debian. Debian is a distro that has been around a while and is considered very stable. Debian doesn't put new stuff in there distro lightly. They are usually the last distro to add new apps. This assures stability but also assures other distros have more cutting edge software.
Because debian is so stable other distros build upon debian (everyhting is  open source, of course, and anyone can change /add), This is where Ubuntu comes in. Ubuntu started with a Debian base but changed/modifed/added to it. So it isn't debian but has alot of debian components. That is why you are seeeing debian apps but not debian.
The menu they are talking about is the debian menu(already stated). It can be added to the menu you are working with (the Gnome menu). I like it because it lists everythiung that is installed, something Gnome doesn't do.
There is a learning curve to linux. You might want to consider a dual boot with windows. That way you can get stuff done while you learn linux. Then you can erase the windows partition and turn it into  data partition.
Thius is a good how to. [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by gruvola on 2006-04-28
I am writing this from my new super-speedy 14.4 modem on Ubuntu!!:) :) 

Thanks to all.  The commands are definitely starting to make sense.  I actually like working in terminal (it's sort of DOS like).

So for $35 total, I have a functional computer for my kid.  We should configure thousands of old used machines with Ubuntu and save the world!!

Peace to all,
Gruv

p.s.  Yes it was the Debian Menu I was after, I'll fix that next.

---

### Post by ubuntu27 on 2006-04-28
[QUOTE=gruvola]I am writing this from my new super-speedy 14.4 modem on Ubuntu!!:) :) 

Thanks to all.  The commands are definitely starting to make sense.  I actually like working in terminal (it's sort of DOS like).

So for $35 total, I have a functional computer for my kid.  We should configure thousands of old used machines with Ubuntu and save the world!!

Peace to all,
Gruv

p.s.  Yes it was the Debian Menu I was after, I'll fix that next.[/QUOTE]

Good!.

If you have question on anything, just create a thread just like you did on this one :)

Happy Peaceful days with UBuntu Linux! :D

By the way, you may be interested in Finding tips and tricks [or other things] proven to work.

Here is the link: [http://doc.gwos.org/](http://doc.gwos.org/)

THat site is run and maintained by some Forum Members (a! Ha! Community is the word) that collects data from this Forums. They have arrenged so that us (people) can find things easer.


:)

---

### Post by Bloch on 2006-04-29
Good to hear someone having success.
How old is that computer by the way? Can you put it's specs up here? Try these commands at the terminal
cat /proc/cpuinfo
lspci

or use synaptic to install the program "System Information"

---

### Post by sophtpaw on 2006-04-29
[QUOTE=Bloch]Good to hear someone having success.
How old is that computer by the way? Can you put it's specs up here? Try these commands at the terminal
cat /proc/cpuinfo
lspci

or use synaptic to install the program "System Information"[/QUOTE]


System Information?

its not in my repos. Can you say more about this application?

--
sophtpaw

---

### Post by AndrewCaul on 2006-04-29
You installed it fine, it will get easier in the next version of Ubuntu, you can but I don't understand why you want to, and yes, but I blame Microsoft for ruining DOS in the newer versions of Windows.

---

### Post by Bloch on 2006-04-29
The package is called hardinfo
(It comes up as System Information in the menu)

Find it using synaptic (do a search) and install, or use the line
sudo apt-get install hardinfo

Not: synaptic is just a nice gui for apt-get. Any package can be installed using either, though it is nice to look at the package information synaptic provides

---

### Post by sophtpaw on 2006-04-29
[QUOTE=Bloch]The package is called hardinfo
(It comes up as System Information in the menu)

Find it using synaptic (do a search) and install, or use the line
sudo apt-get install hardinfo

Not: synaptic is just a nice gui for apt-get. Any package can be installed using either, though it is nice to look at the package information synaptic provides[/QUOTE]

HARDINFO!

kewl, thx for that. Never heard of it before. Installed it and now what? how do i make use of it?

thank you

--
sophtpaw

---

### Post by gruvola on 2006-04-29
Thanks again for the help, but just like the Debian Menu, System Information doesn't exist in my Synaptic, regardless of what left panel choice I make, including 'all'.  Any suggestions?

I really did think it was strange that a program like that didn't exist.  I've checked on a few things from Device Manager . . .

Peace,
Gruvola

---

### Post by Bloch on 2006-04-29
I meant the package is called hardinfo. When you install it using synaptic or using
sudo apt-get install hardinfo
it will appear on the Applications > System Tools menu under the name System Information.

It is in the universe repositories. Open synaptic. Go to Settings --> Repositories
Click on Ubuntu 5.10 Breezy Badger (binaries) and click Add. Tick off universe and multiverse. (Maybe you have already added these to your repositories by hand. The list of repositories is kept in /etc/apt/sources.list

I agree such a program should be on the default system. The information can however always be got at the terminal using the commands I posted a few posts back.

---

### Post by gruvola on 2006-04-29
I ran

sudo apt-get update

then (after the better part of 45 minutes on this slow modem)

sudo apt-get install hardinfo

and shazam - 'system infromation (hard info)' was in my apps menu.  Does this sound correct?  The system is a Pent III 500 MHz with a 8 gig hard drive and CD-ROM.

Peace,
SCA

p.s. now back to getting the Debian Menu added.

---

### Post by gruvola on 2006-04-29
I ran 
*sudo apt-get install menu*
and got
[I]Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  menu
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 387kB of archives.
After unpacking 1659kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe menu 2.1.25 [387kB]
Fetched 387kB in 4m17s (1504B/s)

Preconfiguring packages ...
Selecting previously deselected package menu.
(Reading database ... 59373 files and directories currently installed.)
Unpacking menu (from .../archives/menu_2.1.25_i386.deb) ...
Setting up menu (2.1.25) ...
[/I]
which kicked me back to $

where do I find the 'Menu' I was looking for?  I don't anything new under my apps menus - or am I not supposed to see anything?

gruvola

p.s. after running sudo apt-get update, the amount of apts to install on Synaptic went up dramatically!!

---

### Post by Sutekh on 2006-04-29
[QUOTE=gruvola]I ran 
*sudo apt-get install menu*
and got
[I]Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  menu
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 387kB of archives.
After unpacking 1659kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe menu 2.1.25 [387kB]
Fetched 387kB in 4m17s (1504B/s)

Preconfiguring packages ...
Selecting previously deselected package menu.
(Reading database ... 59373 files and directories currently installed.)
Unpacking menu (from .../archives/menu_2.1.25_i386.deb) ...
Setting up menu (2.1.25) ...
[/I]
which kicked me back to $

where do I find the 'Menu' I was looking for?  I don't anything new under my apps menus - or am I not supposed to see anything?

gruvola
[/quote]
That sounds like it was succesful.  You should have a new menu in Applications, called Debian.  

If it doesn't show up there, try opening the Menu Editor (Applications -> System Menu) and checking the box for the Debian menu, as it might be unchecked (greyed out)

[quote=gruvola]
p.s. after running sudo apt-get update, the amount of apts to install on Synaptic went up dramatically!![/QUOTE]
Oh yes! With the universe and multiverse repositories you will have *a lot* of software to choose from!

---

### Post by gruvola on 2006-04-29
update:

The 'Applications Menu Editor' does indeed show 'Debian' and is greyed out.  Single clicking in the box does not seem to have any effect.  Double clicking brings up a box showing the fields of 'Debian' 'The Debian Menu' and the Debian Icon.  But the 'click' doesn't seem to take.

Also, when I run the command in terminal again I get:
[I]kaylee@ubuntukaylee:~$ sudo apt-get install menu
Reading package lists... Done
Building dependency tree... Done
menu is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kaylee@ubuntukaylee:~$[/I]

which means to me everything I need is somewhere on this machine.

The only other thing I can think of is that many of the (now) dozens of Debian apps in Synaptic are not installed and I don't which I need, like 'debfoster', 'debget' , 'debconf - english'

Can you think of anything I'm missing?

Gruv

---

### Post by Buffalo Soldier on 2006-04-29
I think you have to log out and then login back again.

---

### Post by stewjack on 2006-04-29
[QUOTE=catlett]You might want to consider a dual boot with windows. That way you can get stuff done while you learn linux. Then you can erase the windows partition and turn it into  data partition.

This is a good how to. [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
[/QUOTE]

Thanks for that link Catlett. Dual booting has caused me problems in the past.  Maybe this material will improve my Linux track record.

Jack
Tampa, Florida

---

### Post by gruvola on 2006-05-01
So . . . I still don't have the 'The Debian Menu' anywhere in my apps . . . after logging in and out about 20 times, even powering down, I still can't 'check the box' in front of the Debian icon in the 'Applications Menu Editor' to enable it as an app.

I even tried making a new user profile as an Administrator thinking I didn't have the proper rights.

Any suggestions . . . 

Gruv

(see my previous posts in this thread - apt-get install menu in terminal was successful, etc.)

---

### Post by Sutekh on 2006-05-02
Hey gruvola, you also need to install [menu-xdg](http://packages.ubuntu.com/breezy/admin/menu-xdg)
```
sudo apt-get install menu-xdg
```
It converts the Debian menu into a structure that works for GNOME.  I had to go back and work out how I installed menu, and what else was installed to make it work.  This is what happens when you use automatic scripts, you never know what was installed to make something work.

---

### Post by mips on 2006-05-02
[QUOTE=gruvola]
The long version is:  I got a cheap computer from work that they didn't have a Windows license for (they could, and still can, give me NT) and my 9 y.o. needs a computer to do school work.  The IT guy thought I was sharp enough to give Linux a go so I decided to go for it.
[/QUOTE]

What are the specs of this computer, CPU, RAM, HD etc ?

If the specs are low you might want to consider [http://www.xubuntu.org/](http://www.xubuntu.org/) which is Ubuntu with xfce. 
Something else might be to look at at the educational version of ubuntu seeing it is for school, [http://edubuntu.org/](http://edubuntu.org/)

You can offcourse change ubuntu to include all feature of xubuntu or edubuntu simply by installing the software.

---

### Post by catlett on 2006-05-02
try ```
update-menus
```
This should refresh your menus and debian "should" be functional

---

### Post by Raavea on 2006-05-02
[QUOTE=gruvola]...
Thanks to all.  The commands are definitely starting to make sense.  I actually like working in terminal (it's sort of DOS like).
...[/QUOTE]
 Well, that stuff is all based on assembly language isn't it? Which means it's all similar... Then again, even if it isn't, most programmers make things obvious and simple, like I wouldn't set a command include file to be called 32543sdaabets.inc ... I'd call it command.inc or cmd.inc...

 Anyhow, I'm glad you got it all sorted, and I hope you instill the wonders of Linux into the next generation! You never know.. That nine year old may one day create a version of linux that kills microsoft forever! :twisted:

---

### Post by mips on 2006-05-02
[QUOTE=Raavea]Well, that stuff is all based on assembly language isn't it? [/QUOTE]

I don't really see the resemblance to assembly language and I've used a few ?

---

### Post by gruvola on 2006-05-02
OK, I ran this:

[I]kaylee@ubuntukaylee:~$ sudo apt-get install menu-xdg
Password:
Reading package lists... Done
Building dependency tree... Done
Package menu-xdg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package menu-xdg has no installation candidate
kaylee@ubuntukaylee:~$ sudo update-menus
kaylee@ubuntukaylee:~$[/I]

I see 'menu-xdg' is not available, and Debian Menu still doesn't work?!?  any ideas where I can get it?

also I see another thread titled:  **Re: How can I add debian menu to gnome applications menu?**  Tried to fix this same problem - all of this is the same issue!

---

### Post by Sutekh on 2006-05-02
menu-xdg should be there.  An error like that indicates some problem with your apt-get repository sources.

Are you using a local mirror (that you know of)?  If you open this file
```
sudo gedit /etc/apt/sources.list
```
Do your repositories look like this (an example entry)
```
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
```or like this (example of a local mirror for the US)
```
deb http://**us.**archive.ubuntu.com/ubuntu breezy-updates main restricted
```
If you have the latter type of repository, ie **us.**archive..., then remove the **us.** part, save the sources.list, and try again
```
sudo apt-get update
sudo apt-get install menu-xdg
```
I went through the install of **menu** and **menu-xdg** last night using **non-local** repositories and I was able to remove and re-install the Debian menu on my computer.



If this *still* doesn't install menu-xdg, you can get the package from an Ubuntu mirror directly, using the [Ubuntu Packages - menu-xdg](http://packages.ubuntu.com/breezy/admin/menu-xdg) webpage, and then install it using this command
```
sudo dpkg -i menu-xdg_0.2ubuntu1_all.deb
```

---

### Post by gruvola on 2006-05-02
not knowing that you were replying I thought I'd play a bit.

I went to [http://packages.debian.org/stable/admin/menu-xdg](http://packages.debian.org/stable/admin/menu-xdg)
and downloaded it from there onto my desktop and installed it via the instructions I got the other night to install the drivers for this modem (way back in this thread).

The Debian Menu Exists and run fine!!

Thanks so much for your help though.  I think I had better investigate all of your post to see if I have other problems.

Peace

---

### Post by Sutekh on 2006-05-02
Hey don't thank me, you worked it out yourself, which is even better! :D

I'm just glad you got it working.

---

### Post by Seinfeld on 2006-07-03
Just a word of advice.

Do not ever try to add Debian repos to sources.list. Although some packages may install correctly, it willl be very hard to remove them because of dependency problem. Being a Debian fan, I have tried that and screwed all my system up.
Ubuntu is a very stable distro at this point, although it does not update as fast as Debian etch or sid, it has a very comprehensive and robust up-to-date package system..

Just a word of advice :neutral:

---

