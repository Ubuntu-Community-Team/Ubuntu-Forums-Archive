---
title: "A few newbie issues"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by kuku on 2005-10-04
I installed Ubuntu on a dual boot with XP yesterday.  I don't have too much experience with linux, so I have the following questions:

1) I want to update my graphic drivers (Radeon 9800 pro), so I downloaded the file provided by ATI, but don't know how to run/install it.  It is a .RUN file and defaults to being opened with a text editor.

2) I have the similar issue with FireFox.  I downloaded the latest version to the Desktop, extracted the files from it, but don't know how to run the installer.

3) My sound doesn't work correctly.  I have a Soundblaster Audigy, so I am assuming there probably isn't much support for it yet.  The SB website had no drivers for it.  The sounds come out as fuzzy, and don't resemble what they should be sounding like.

Thanks for the help!

---

### Post by nitricacid on 2005-10-04
1&2. Rite click on the .run file then click properties, in ther permissions tab click the little box next to where it says 'is excutable'. You will also have to do this for the FireFox installer.
Just click the firefox installer (once you checked the box to make it excutable) and it should start the install process.
I don't know about the ATI driver i never install one

Basicly to make all files excutable just rite click them and check the 'is exctuable' box.
After doing so and you click the icon and nothing happens you will then have to open a terminal window and copy and paste the item you are trying to run into the terminal and then press enter.

I am not quite clear on installing some files but i think the .RUN file should install itself normally with like a step by step install that shows in the terminal.

---

### Post by aysiu on 2005-10-04
[QUOTE=kuku]
2) I have the similar issue with FireFox.  I downloaded the latest version to the Desktop, extracted the files from it, but don't know how to run the installer.[/QUOTE] You don't need to. Just type this into a terminal ```
sudo apt-get update
sudo apt-get install firefox
``` If you absolutely insist on using the .tar.gz (for example, if you're using 1.5 beta), just double-click the .tar.gz. Click "extract." A new folder (extracted) will pop up. If there's something called Firefox-installer, click on that. If there isn't, just click on the file called Firefox--not to be confused with firefox-bin

---

### Post by kuku on 2005-10-04
As for the ATI driver , I did what you said and it starts its process, but then pops up the message that I need to be a "Super-User" to install?  How do I accomplish that?

---

### Post by mr_mop on 2005-10-04
Doesn't firefox come pre-installed with ubuntu?

Oh and use sudo for installing anything.  it gets round the problems of permissions.

---

### Post by kuku on 2005-10-04
Not sure how to use "sudo."  I have the terminal window open, but what do I type after sudo for it to install the drivers?  I tried using the ATI file name but that didnt work.

---

### Post by nitricacid on 2005-10-04
when installing always type sudo b4 everything else

Sudo is the root\admin, if anything ever asks for a root\admin password just use the one you login to your desktop with.

---

### Post by mikedtemple on 2005-10-04
I strongly suggest you check out the [ubuntu guide]("http://www.ubuntuguide.org").  It helped me learn, learn, learn about linux and Ubuntu! :D  It's got some great info on the basics.  
As for your question- remember Ubuntu (all Linux actually) takes file permissions very seriously.  Therefore to do anything, you have to be the "super user".  The sudo command does that for you.  It will ask you for a password.  Just enter the one you use to log on.
For example:
apt-get install mozilla-firefox
won't work.  You'll get the error you got earlier.  But-
sudo apt-get intall mozilla-firefox
will ask you for a password-then download and install firefox!  Don't be afraid of all the text.  If you apt-get enough, you'll start to learn what it's doing.
One more suggestion- from one noob to another.  If you want to really learn linux- READ everything you can!  Most likely, no one on the forums will yell 'RTFM' at you, which is great, but scanning the forums, taking books out, etc. can make you a much more proficient user!
(Shameless plug for Mako coming up...)  Check out the [Debian/GNU Linux bible]("http://www.amazon.com/exec/obidos/tg/detail/-/0764576445/qid=1128438894/sr=8-1/ref=pd_bbs_1/104-5652600-5622350?v=glance&s=books&n=507846").  One of the principal Ubuntu developers helped write it.  It's not *exactly* Ubuntu (Ubuntu is based on Debian), but it's a good primer on Linux.  That combined with these forums saved me from breaking my box a lot!
Hope this helps!

---

### Post by UbuWu on 2005-10-04
Just be careful what you do with sudo, you can also break your system with it.

---

### Post by kuku on 2005-10-04
Thanks for all of the help guys.  I've got the video card drivers installed, and got my sound working through a little digging.

---

