---
title: "Rosegarden unconfigured?"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-02-26
Hi I have been installing Rosegarden and it's dependencies and i thought I had everything but then when i went to open it it said there was an error so I went into the terminal and well you'll see below:
 
root@carla-desktop:~/Desktop# dpkg -i rosegarden4_1.2.4-1_all.deb
(Reading database ... 90001 files and directories currently installed.)
Preparing to replace rosegarden4 1:1.2.4-1 (using rosegarden4_1.2.4-1_all.deb) ...
Unpacking replacement rosegarden4 ...
dpkg: dependency problems prevent configuration of rosegarden4:
 rosegarden4 depends on rosegarden (>= 1:1.2.4-1); however:
  Package rosegarden is not configured yet.
dpkg: error processing rosegarden4 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rosegarden4

I know that I was a bit confused with one dependency. It was khelpcenter. I thought it was odd since this is kde and i work with gnome. I hope i am explaining this ok.


and these two are also unconfigured. I don't know what that means and what to do about it:

root@carla-desktop:~/Desktop# gramofile_1.6-7_i386.deb
bash: gramofile_1.6-7_i386.deb: command not found
root@carla-desktop:~/Desktop# dpkg -i gramofile_1.6-7_i386.deb
(Reading database ... 90001 files and directories currently installed.)
Preparing to replace gramofile 1.6-7 (using gramofile_1.6-7_i386.deb) ...
Unpacking replacement gramofile ...
dpkg: dependency problems prevent configuration of gramofile:
 gramofile depends on fftw2 | fftw2-double; however:
  Package fftw2 is not configured yet.
  Package fftw2-double is not installed.
  Package fftw2 which provides fftw2-double is not configured yet.
dpkg: error processing gramofile (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gramofile
root@carla-desktop:~/Desktop# xmms-singit_0.1.28-3build1_i386.deb
bash: xmms-singit_0.1.28-3build1_i386.deb: command not found
root@carla-desktop:~/Desktop# dpkg -i xmms-singit_0.1.28-3build1_i386.deb
(Reading database ... 90001 files and directories currently installed.)
Preparing to replace xmms-singit 0.1.28-3build1 (using xmms-singit_0.1.28-3build1_i386.deb) ...
Unpacking replacement xmms-singit ...
dpkg: dependency problems prevent configuration of xmms-singit:
 xmms-singit depends on libgtk1.2 (>= 1.2.10-4); however:
  Package libgtk1.2 is not configured yet.
 xmms-singit depends on xmms (>= 1.2.10+cvs20050809); however:
  Package xmms is not installed.
dpkg: error processing xmms-singit (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xmms-singit

---

### Post by louis_nichols on 2007-02-26
Try this: open synaptic, then select Edit>Fix broken packages. This should solve things one way or another. That is, it will try to keep all installed packages and only install needed dependencies, but if those are not found, it will uninstall the packages.

---

### Post by rapattack1 on 2007-02-26
OK I did this. I think the problem is they are for KDE. What a pity. I really wanted Rosegarden in particular.

---

### Post by rapattack1 on 2007-03-05
I couldn't do the fix. I don't remember why. I seem to not have the repositories set up right. I had to uninstall or delete it. Am I supposed to have a line entered in the third party section. I am trying to understand this repository thing. I can't seem to even get upgrades or anything.

---

### Post by louis_nichols on 2007-03-05
The "repository thing" is theoreticallu easy: they are just software sources.

Now, you probably got it by now that installing software in Linux is different from windows, in that there are dependencies. So, a piece of software depends on another piece of software. This used to be rare in windows, although lately there are more and more applications that require the .NET framework to be installed. Likewise, you've probably encountered errors of "missing runtime". I used to get these for some applications compiled in Visual Basic. Those require the VB runtime engine. Software in Linux always works like this. Basically, the only package that wouldn't depend on anything is the kernel, but even it has some dependencies, namely device drivers. It would work without them, but it would be pretty useless. Then there are other packages, called libraries, that perform basic tasks and are almost universally needed. Then there are other pieces of software that depend on more software and more libraries. You can picture this as a very complicated tree.

Problems arise when a piece of software, lets call it A, gets upgraded. Basically, this means that new features are added. So if another software B uses those new features, it can't work with older versions of A, because they don't provide those features. Backwards compatibility is almost never broken, though. This means that if software B depends on software A, version 1, it will certainly work with software A, versions 2, 3 and so on. there are some small exceptions from this, but they are solved by naming conventions. For example GTK comes in several versions: GTK1.2, GTK+, GTK2.0. While they have similar names and the same origins and provide similar functionality, these are quite different pieces of software.

Now, the problem you encountered is because rosegarden asks for newer versions of libgtk1.2 and xmms than you have installed. I checked and newer versions ARE available, just like zour rosegarden requires. So what you need to do first is to open synaptic, click Reload, then Mark all upgrades and then Apply. This is in fact what you should do regularly, to keep your system up-to-date. I am assuming here that you use Ubuntu Edgy Eft or Dapper or at least Breezy, which are the ones still maintained, AFAIK.

Another thing to do is, rather than downloading a deb and trying to install it using *dpkg -i*, try to find a repository that contains that deb package. This means that you just need to add that repository to your list, in the third party section (I think this was what you were asking) and install the package using synaptic. This has the advantage that it searches all dependencies and solves them. So it installs all the packages you need for rosegarden. If you do not find such a repository, you have to take care of the dependencies "by hand", which means searching for them in synaptic and installing them.

OK. Hope this was clear. Bottom line is that the problem you encountered is not a complicated one, although it may seem like this to a beginner, and will be easily solved. You will see that in a very short amount of time you will know enough to understand such problems and solve them yourself.

---

### Post by rapattack1 on 2007-03-06
Yep I do see what your saying in a way but if the experience is not there then there is no way to see what went wrong. I am still stuck but I am not going to give up and go back to crappy old windoze. I will just have to leave rosegarden for now as I have spent far too much time on it.  I have Edgy btw and don't have rosegarden now as synaptic deleted it. Well it was never fully installed.
I have been very successful at installing the basic stuff needed to get on the net with dialup and after installing stuff on one machine have now done it on 5 others(friends as well to get them away from windoze). Plus I finally got some stuff like Audacity and a few plugins/tools.

The repository has been a problem for me since day one. I do not know why but on most of the machines I just cannot get it to work so that is why I used dpkg -i .
Anyway I will probably have to rely on my trusty Linux friend that sometimes comes over to my place and gets me out of the mud. I am trying to learn but also have a medical condition that limits my time spent on the net and reading too much.

---

### Post by rapattack1 on 2007-03-10
Well now that I have synaptic working properly I got Rosegarden that way but there is an error when opening it to do with Jack. I downloaded it but I am still getting the error. This is the error: Sequencer startup failed-Midi subsystem has failed to iniatialise. then there is an ok button which I pressed and the program opened.

---

### Post by rapattack1 on 2007-03-16
Hi here is the error when I go to open Rosegarden. There is also an error when I try to do the same with any of the Jack stuff. I have Jack control, Jack EQ and Jack Rack. I have been told to get Jack so I got all these.

---

### Post by louis_nichols on 2007-03-16
Do you have a sound card with midi capabilities? Or some midi card? (I don't know very much about midi devices). If not, then the error is normal and you should simply ignore it. Maybe, try to search through the settings for some option to disable searching midi devices or disable midi altogether. It's been a while since I last playe with rosegarden, so I can't give you a definite answer. I seem to remember getting that error too, though.

---

### Post by rapattack1 on 2007-03-17
I think the sound card has midi capabilities. I really haven't delved into midi! I have a separate soundcard for the sole purpose of making music. I think there maybe some confusion with it but I really don't understand it. There is a program called soundconfig and my linux friend said he was going to use it to get everything running better  I guess.

---

