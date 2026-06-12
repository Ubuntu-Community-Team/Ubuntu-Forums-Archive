---
title: "Survey: Downloading Ubuntu updates under Windows"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by jerryrw on 2007-04-13
I am in the process of writing a program that will (hopefully) enable a Windows or other working *nix system with an internet connection to download updates and new software for an Ubuntu box that has no network connection.  I am basically asking if there is enough of an interest in something like this for me to go through the process of putting it up on sourceforge or launchpad.  Right now I envision the following usage scenarios:

Ubuntu box with no internet at home but you have internet at work but windows only

Dual booters that can't get networking to work under Ubuntu

Servers with a mixed network of workstations can make local repos without mirroing the whole multiverse.

I've got dependency resolution(the hard part)  mostly working and I hope to be moving to something resembling an alpha release late next week.  Tag this thread if you have questions about, need for, or interest in a program like this.

Thanks
Jerry

---

### Post by caffienefree on 2007-04-14
I'm a little curious about how this would (functionally) work. The program windows-side would need to have some idea of both the packages installed on a ubuntu box as well as the current version number. How are you going to manage the synchronization between the two?

I don't have an actual need for this, but I'd be willing to bug test it once an alpha version is made available. Depending on the language, I might also be able to debug. What is it written in?

---

### Post by Chilli Bob on 2007-04-14
This is exactly what I need. Will keep an eye on this thread!!!

---

### Post by jerryrw on 2007-04-14
I am writing it in Python for portability.  My basic Idea is to have three separate scripts. An Ubuntu script that copies the necessary data from the dpkg package database (status) and then the user will have to copy this file to a removable media.  Take this removable media to a Windows box or more likely any internet connected machine and that script will scan the installed packages from the offline one and resolve dependencies for it.  the connected machine downloads the packages and deps.  Put these on removable media annd take them to the offline box where a third script uses dpkg to make a local repo and do the actual installing.

The biggest hurdle that I have had so far is that  since I am targeting a windows machine I can't use any dpkg library routines.  I have had to reinvent the wheel on package comparison routines.  The strategy used in dpkg uses pointers extensively and translating this to Python without pointers per-say is ugly.  My routine SEEMS to be doing ok, but in my unit testing I have noticed some versions in the 'wild' package lists found on the ubuntu archives that I cant visually tell which version is newer.  I am going to have to take the comparison module to a debian/ubuntu system and write another test script to dun real dpkg against the same test data.

---

### Post by aysiu on 2007-04-14
I see this as being more useful for *installing new programs* than installing updates, seeing as most updates are security-related, and if you're not connected to the internet, the only security that matters is physical security.

That said, the ability to download new programs (including all the necessary dependencies) on another machine is a good thing. So, yes, this effort would be appreciated by many people.

---

### Post by jerryrw on 2007-04-17
Just an update that the project is still going forward.
I agree with aysiu that updates are not as important in this scenario, and installing new packages was actually my main motivation for this project.  With that said, updates are drastically easier to program as package resolution is MUCH easier.  I now understand why no one has done this before.  Package resolution is one of those HARD problems in computer science.  It is actually MP-complete, but current package managers basically do a best guess.

The version comparison routines all came together today, and it is resolving first order deps on the updates and matching synaptic (mostly).  I think I can get dep resolution "good enough" do do basic installs in time for my self imposed deadline of Friday.(was trying to match release date with FF)

One thing that I can use community help for is a name for the project.  Any Ideas?

---

### Post by LaRoza on 2007-04-17
That is a most useful idea especially if you do not need to install the program on the computer (Windows)

---

### Post by aysiu on 2007-04-17
AG4WIN - *apt-get* for Windows?

OPM - Off-line package management

Ubuntuoffline

By the way, when you're looking at dependencies, are you looking directly at the repository servers or [http://packages.ubuntu.com](http://packages.ubuntu.com) ?

---

### Post by bobplano on 2007-04-17
yes this is a good idea especially the people who need to get ndiswrapper and are completely new to linux.

as for names maybe like win-get

---

### Post by aysiu on 2007-04-17
*win-get* is cool.

---

### Post by jerryrw on 2007-04-17
I also like win-get.  I'll see if I get more suggestions before I make a decision.

I am currently connecting directly with the archives (US).  I am using the sources.list files from my three test machines(one each Daper,Edgy,Feisty) and they already had the sources set up in it.  The script will use any valid sources.list you feed it(I hope)  I do want to add the ability to scan for mirrors but that is a lower priority at this time.
This is a great time to do this as the real package system for Feisty is moving fast and allows for great unit testing against real world data.

Thanks for the input everyone.

Jerry

---

### Post by jerryrw on 2007-04-17
win get is already taken at source forge
[URL="http://sourceforge.net/projects/windows-get"]
http://sourceforge.net/projects/windows-get[/URL]

---

### Post by skyhopper88 on 2007-04-17
This could come in handy for new installs. I had a few problems when I first started, something like this would have been a great thing to have.

---

### Post by briealeida on 2007-06-11
I know it's been a while but is this project still ongoing?

It seemed promising!

---

### Post by Crinos512 on 2007-07-20
Awww.... it ends like that?

this would have been VERY useful as I only have broadband on my MS-only work computers. :(

---

### Post by Mornedhel on 2007-07-20
Isn't there something like that already ? I think it's called apt-zip. Of course it doesn't work under Windows, but it still works great between Linuxes.

---

