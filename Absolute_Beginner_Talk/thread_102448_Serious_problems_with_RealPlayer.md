---
title: "Serious problems with RealPlayer"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by harisund on 2005-12-12
I am trying to install realplayer, since I listen to a lot of online music and all of them are in realplayer format. 

Anyway, I go ahead and download the version 10 .deb file. 

I try to install it but I am required to install libstdc++5

A quick check, *dpkg -l libstdc++** gives

ii  libstdc++6                         4.0.1-4ubuntu9                     The GNU Standard C++ Library v3
ii  libstdc++6-4.0-dev                 4.0.1-4ubuntu9                     The GNU Standard C++ Library v3 (development files)

And *dpkg -i realplayer_10.0.6-0.0_i386.deb* gives
(Reading database ... 44921 files and directories currently installed.)
Preparing to replace realplayer 10.0.6-0.0 (using realplayer_10.0.6-0.0_i386.deb) ...
Unpacking replacement realplayer ...
dpkg: dependency problems prevent configuration of realplayer:
 realplayer depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing realplayer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 realplay

Does anybody know of any workaround? *apt-get dist-upgrade* is something I do regularly, and I am sure the 6th version of the standard C++ library is the current one. But realplayer wants me to install an older one. 

*apt-get install libstdc++5*
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libstdc++5: Depends: gcc-3.3-base (>= 1:3.3.6-8ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Of course, I have currently have gcc4.0-base. 

Anybody with any suggestions? Pretty much everything works, and I am running Ubuntu for my home server and on my Laptops (the HP customized Ubuntu works perfectly too) but I still need to boot back to Windows simply to listen to online music? 

Thanks, in advance

Oh and another thing. apt-get seems to remember the failed attept at installing realplayer, and is not allowing me to perform any sort of apt-get operation now. What do I do to make it forget the fact that I tried to install realplayer and it has broken dependancies?

---

### Post by akiro.yamamoto on 2005-12-12
This may seem a silly question.... But do you have your repositories correctly configured?
Try this: (There is no need to go to the CLI for this task)
Click :
System >> Administration >> Synaptic Package Manager.
Enter "YOUR" password.
Click:
Settings >> Repositories
Click :
Add
Click : (Check boxes)
Universe as well as Multiverse
Then Click: OK and OK again...
Synaptic may ask if you want to update the package information list...
Say Yes...
When Done ... Click :
Search
and type in : libstdc++5
It should come up in the results!
Click on the item and choose install..
That should be it....
You can also search for gcc 3 and install that first if you want...
I hope this helps.... I had a similar problem and this worked for me.. :smile:
Regards

---

### Post by harisund on 2005-12-12
To begin with, I prefer using the command line over synaptic. 

Basically what I did was remove all the commented out repositories in the */etc/apt/sources.list* file. I am guessing this enables all the repositories, right? 

Also, after a *server* installation, I installed *xubuntu-desktop*, hence I don't quite have the *System >> Administration >> Synaptic Package Manager *that you are talking about. (Or does *XFCE* have *Synaptic* somewhere I am not aware of?? Even then, I prefer command line please.)

Well..I could try gcc3  installation (again through command line) and get back .. 

So, is there synaptic in the XFCE installation through xubuntu-desktop ? 

Thanks

---

