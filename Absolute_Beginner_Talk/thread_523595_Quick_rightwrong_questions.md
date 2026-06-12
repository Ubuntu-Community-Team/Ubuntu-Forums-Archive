---
title: "Quick right/wrong questions"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by dac10 on 2007-08-12
ive just got Ubuntu installed yesterday and so far its been much easier than i thought cause last time the internet wouldnt work and i gave up. now with the new 64bit version the internet worked straight away which means i have much more incentive to continue using it. this time however i am determined to rid myself of windows for good.

im finding the whole install thing a little difficult, ive read the sticky but ive got a few n00b questions if somebody could just tell me if im right or wrong thanks.

1) am i right in saying the synaptic packet manager is only used to install updates and OS software such as in windows updates? i think this because it gives you the list of packages and not you searching the internet for custom ones.

2) when you install custom software (such as my Nvidia drivers) you have to recompile it? cause when i open it it just gives me the list of folders/files it contains instead of a nice .exe file that im used to.

3) in order to install somthing you have to use a piece of software within the OS? such as packet manager or the add/remove utility.

thanks, please i am a complete newbie and i got a fair grasp of the stickie on installing but its still a little confusing.

---

### Post by bernied on 2007-08-12
None of these are quick right/wrong answers...

1 - Wrong. You can install anything that is in a repository with package managers. In the ideal ubuntu install, a package manager is used to install ALL software. For software that is not open source, you will need to enable non open-source repositories (they are out there). In contrast windows updates only installs microsoft software.

2 - Right and wrong. I'm not familiar with nvidia drivers per se, but I know that these are kernel modules, so must be matched to your current kernel. Maybe this is why you need to compile them in order to install them (and you will need to recompile them when you upgrade your linux kernel - watch out for this, check what you are updating before you just accept updates, because a kernel update will possibly break your system because your graphics will no longer work). But there is much software that is precompiled and packaged and will just work. The equivalent of the nice .exe file is the nice .deb package file, but this is the package, not an executable. Linux binaries generally don't have an extension (like .exe) to identify them. They will be marked as executable though.

3 - Mostly. There are exceptions (bash scripts for example).

---

### Post by steve.horsley on 2007-08-12
1) Wrong. Synaptic is much more than you think. Not only are the various parts of the operating system there, but a huge amount of open-source software is in the repositories too. There is no equivalent concept for Windows, and the closest I can thing of is if you think of is all those windows software finder web sites (2cows was the first I ever knew). Synaptic should be the first place you look, whatever you are looking for. I see loads of posts here from people who have gone looking round the web, found some source code and then start bitching how hard it is to install s/w on Linux when all they had to do was use Synaptic and install from the repositories. The reason that the web sites often only carry source code is that it is expected that the major distros will do the compilation and packaging for the users. 

2) Sometimes. Drivers will always need compiling for a particular kernel, so you are unlikely to see precompiled drivers on a manufacturers web site. Most application software isn't so tightly tied, so that a precompiled binary will work on many different Linux kernels, and many applications provide precompiled binaries. Frinstance, I am using the binaries for OpenOffice and Java that I downloaded from the web sites (despite versions being available in the Synaptic repositories) for various picky reasons.These were just downloaded and unzipped and copied to where I wanted - no compiling needed.

3) Depends. Some packages come as a .deb package that the nornmal package installer can use. I installed VirtualBox by downloading and double-clicking the .deb file. Incidentatlly, this involved the installer compiling a driver that was supplied on the .deb package. Other programs, I just download the precompiled binaries, unzip and copy to where I want.

---

