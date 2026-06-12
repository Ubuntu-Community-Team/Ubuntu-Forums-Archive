---
title: "&quot;restricted&quot;"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-04-21
I'm in the middle of cleaning my computer from any software\formats\code\whatever that's not open sotrce, preferably GPL.

I understand that the "restricted" section contains some stuff that is not totaly free, my question is, is it safe to disable it?

Unfortunately, the linux kernek is under "restricted"... does that mean that I won't get updates?
I've seen that a few linux modules are also under the restricted section, the modules:
madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl, fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcdslusba,
   fcpci, fcpcmcia, fcpcmcia_cs, fcusb, fxusb (AVM ISDN)
 - ltmodem (Winmodem)

I guess I should't delete them...
Is it absolutely necessary to have the restricted section enabled? because it really will be a bother...:( 

And about the "universe" one, that's free software, right?

Thanks,
Josh](*,) :)

---

### Post by Mustard on 2006-04-21
I wonder whether you should just go with a pure Debian install. :)

[http://www.us.debian.org/social_contract](http://www.us.debian.org/social_contract)

Do you have a wireless card that needs madwifi?
Do you have a nvidia card or ATI card?
Are you using a winmodem?

If your answer is no to all of these questions, then you have no need to install most of the above software.  I would assume they are not installed in fact (given that you answer no to all those questions).

If they are not installed there is nothing to uninstall.  Just remove the restricted section from your sources.list and stick with the stuff that has the appropriate licences.

---

### Post by Caligula on 2006-04-21
hmm... I might actually try Debian, but I heard that it's quite complicated...
And how do I know my architecture anyway?

Is debian complicated? the installation, all that, I'm new at linux, so I don't know...
What do you say?

---

### Post by pbaehr on 2006-04-21
I did not find the installation of debian to be any more complicated than ubuntu and since ubuntu is based on debian using them extremely similar.

---

### Post by Caligula on 2006-04-21
Are you sure?
Please consider that I'm new to the whole thing...
My ubuntu installation went wuite smoothly, because I didn't need to do anything...

What about hardware support? is it as good as in ubuntu?

The installation manual looks extremely scary to me...

Do you think I'll manage to install debian? I don't know much about my computer, do I need to configure the hardware manually or is it detecting it automaticaly?

thanks...

---

### Post by Caligula on 2006-04-21
When I think about it, according to my computer my operating system is Debian.. lol

All my hardware works fine in Ubuntu, does that meant it'll work on debian?
How much is Ubuntu based on Debian? is it the same system and only different packages? or are there differences in the core as well?

---

### Post by daageep on 2006-04-21
Caligula,

i went through the exact thing you are going through, but i think you should get used to ubuntu first. 

my friend first started me on debian (he did the install for me) unstable with XFCE a few years ago. i found that debian (unless you install gnome/kde i guess) was not "guified" enough for newbies to use. i did not really know how to do anything. after going back to windows for a little and literally getting banned from my dorm's internet EVERY DAY because i kept getting viruses from fresh windows installs, i moved to ubuntu on my notebook and loved the gui-ness. however, ubuntu could not get my ipw2100 centrino wifi card and a few small things working, and the gui was not helping at all. i felt that the gnome gui only had a few options i could "configure", but they are assuming the card is working already. i read enough documents and got enough command-line experience (in ubuntu) configuring everything without gui that i moved to debian.

regarding the install, i think its more difficult than ubuntu for sureeeee. there are some good debian-install docs out there, so you may want to read those first. you have to decide the partitions for your hard drive, answer a bunch of questions about hardware that are not so intuitive (i still just chose the defaults most of the time they ask me), install X, and some other stuff. for me i choose the base install of debian which drops me to a blank console after installation, then i install everything from the groundup. hardware detection is not nearly as good as ubuntu in my opinion from a fresh install.

summary: get used to ubuntu first (move away from synaptic to apt-get, only use gui when you really need to) then move to debian. debian's install and usage are harder than ubuntu but imo there is more control.

edit: i have not yet found a well-populated and friendly pure debian community. its hard to ask for help in irc (they just ignore me! lol). that's why i still lurk these forums. solutions/tips here will apply to debian most of the time.

---

### Post by Caligula on 2006-04-21
So what you're saying is that for debian I need more technical knowledge and command line experience, both of which I don't have, I've used Linux for the first time ten days ago.. lol
I manage great in ubuntu, find it very simple after a bit of getting used to and reading the right HOWTOs.

I guess I'll just stay in Ubuntu for a while, a few months to get used to the command line... and about the command line, is there a web browser that's working throught the terminal? to view webpages without the GUI that is... and hebrew encoding](*,) 

Is there a "guide to the command line" that I can learn stuff from? I really like the idea of the command line, I like minimalism, and even when I was in windows I always liked using DOS and wanted to learn more about it...

I agree with you about the support with debian, I went to the IRC, and they're not really nice guys... In basic, I've got the feeling that the whole debian community is not as friendly, is that true or just a feeling?

And just for my conscience...
Who actually developes Ubuntu? is it Canonical? 
I don't like capitalism(in nice words) so obviously I don't like companies... Is Ubuntu a community software? It's all a bit weird...
Is it just sponsored by Canonical or actually developed by them?

thanks for your help:)
Josh

---

### Post by az on 2006-04-21
To answer your original question, you can safely get rid of the restricted repository as well as remove the linux-restricted-modules packages if you don't want to use any of the hardware that it supports.

I think (not sure) there are some firmware blobs in the linux-image packages, but whether that is not free-libre software is a matter of opinion.  The linux-image packages are not in the restricted repos but in the main or security repos.

You can have a completely GPL-compatible system by installing software only from the main and universe repositories.  Anything that is non DFSG (Debian free software guidelines) cannot go into those repositories.  Ubuntu makes a choice to distribute some binary-only drivers, but the offending drivers are packaged for easy removal.


[QUOTE=Caligula]
And just for my conscience...
Who actually developes Ubuntu? is it Canonical? [/QUOTE]

Many thousand people develop free-libre software.  Ubuntu tries to be a collection of the finest free-libre software available.  It takes some developer skill to ship all the software so that it all works together.  In that sense, Canonical help with the development of the software.  

Launchpad is a tool they are developing that aids in the development of free software.  It has translation tools and bug-fixing tools that ship the fixes back upstream so that improvements made to Ubuntu can make their way into other distros.

The Ubuntu distibution itself is mostly undertaken by Canonical, but with a lot of community support.  As I understan it, over time, the goal is for the community to take on more of the work.  For example, the Community Council started out with four Canonical employees.  The next members of the CC will include people who are not Canonical employees.

Canonical's goal is to prove that free-libre software is viable.  Ubuntu is and will always be free (as in liberty as well as in cost).  Canonical is a for-profit business that wants to make money from the free software business model: professional services and support.


[QUOTE=Caligula]
I don't like capitalism(in nice words) so obviously I don't like companies... Is Ubuntu a community software? It's all a bit weird...[/QUOTE]

Free software is all about software not being property.  That does not mean that nobody should pay developers, but that the code they write belongs to everybody at the end of the day.  A proprietary software developer does not own the code she writes at the end of the day - it belings to her employer.  A free-libre software developer gets to keep the code (since it belongs to everybody) as well as the paycheck.

Since the software is free, you don't have to subscribe to the free software philosophy to use it.  But that's not your question.

My point is that Canonical is a company and they want to make money.  Your rights to use, study, modify and distribute all the code are well protected by the free-libre software way.  You don't really have to deal with Canonical to use Ubuntu.

Also, the direction that Ubuntu will take probably will depend more and more on the community than the sponsoring company.  But time will tell.  Since this is free-libre software, it probably is better business to let the market (the developer community) decide what to do, as opposed to a proprietary software venture.


[QUOTE=Caligula]
Is it just sponsored by Canonical or actually developed by them?

thanks for your help:)
Josh[/QUOTE]

There are a few dozen Canonical employees in total, AFAIK.

---

### Post by Caligula on 2006-04-21
Right... that was quite a helful message:)

> the offending drivers are packaged for easy removal.
How can I remove them? just removing everything that comes under "restricted copyright" is safe?

And also, it doesn't make sense, the linux KERNEL is in the "restricted" section, I guess I shouldn't remove it...

Here are a few screenshots to explain my worries... fpcmcia, is that not the network cable?

on screenshot.png, is that not the kernel?

Thanks

---

### Post by Mustard on 2006-04-21
Before you go removing any of the stuff thats necessary for your nvidia card, I would reconfigure xorg.conf to use the vesa generic drivers.  Otherwise your going to end up losing your GUI.

```
sudo dpkg-reconfigure xserver-xorg
```

When you get to the video drivers choice, switch it to vesa.

---

### Post by gr0kzer0 on 2006-04-21
Going "pure" FOSS is a big step that may leave you with a box that is no longer, in your view, "user-friendly". Some people wouldn't be affected by the loss of, say, nvidia drivers and mp3 and dvd codecs - other people couldn't cope without them! Before you take steps to remove all non-free material from your system, make sure you know what each piece does.

I have only been messing with linux for a couple of months, I'm still a total n00b, there's no way I could make a decision like that yet. Even though I identify very strongly with the FOSS ideal, and don't, for instance, use mp3 or dvd codecs, I don't _know_ enough about what everything does to start removing drivers. And as for messing with the kernel... Yikes!

---

### Post by Caligula on 2006-04-21
That's exactly why I'm asking that here...
I don't know enough to know what's safe to remove and what not, so I'm asking:)

About the nvidia drivers, I'm going to try switch to the other ones, if everything still works I'll delete the nvidia one...

---

### Post by Caligula on 2006-04-21
hmmm...
It actually doesn't use nvidia, it uses savage...
does that mean it's safe to remove the nvidia stuff?

---

### Post by brentoboy on 2006-04-21
Caligula,

keep the restricted repo, and enable the universe.
the only thing you dont want is the multiverse.

the ubuntu kernel has to be open source, becuase it is compiled into the linux kernel, and GPL requires derivitive works to be GPL.

the universe is just opensource stuff that isnt supported by the ubuntu team.
the multiverse is free software that is not necessarily distributable without agreeing to a license.  so dont use the multiverse.

there are other things in the restricted area that you might want to remove, but if your goal is free, open source, then rest easy without playing around too much, ubuntu has gone though greate lengths to stay free and open.

you can remove the adobe pdf viewer, and add the gnu one, but there realy are only a few apps that arent FOSS--remember, we are built on debian, which is the king of gnu.  the main differnce between ubuntu and debian is not proprietary software, it is a kernel built this century, and support for apps that havnt had time to reach debian's definition of stable. all wrapped up with python script GUI options to make things easier.

---

### Post by az on 2006-04-21
By default, the system uses the free-libre nv or ATI drivers.  You have to do work to get ubuntu to use the binary-only drivers.  If you haven't done that, don't worry.  Remove the drivers you're not using.


The screenshots you posted show the linux-restricted-modules package and the nvidia binary-only drivers.  You posted the linux-386 package which is in restricted.  

That's a good point.

That package is not the actual kernel, it is a meta package.  For those who use both the free and non-free linux modules, the linux-386 package will depend on the corresponding kernel and restricted drivers package.  You can sefely remove that package.

You also have the linux-image-386 package, which depends on the latest kernel image package, but not the restricted modules.  That way, you can easily remove the restricted modules and not forgo updating your system when the time comes.


apt-cache show linux-image-386
Package: linux-image-386
Priority: optional
Section: base
Installed-Size: 52
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 2.6.15.19
Depends: linux-image-2.6.15-20-386
Filename: pool/main/l/linux-meta/linux-image-386_2.6.15.19_i386.deb
Size: 23248
MD5sum: 913815bc09fcca70fd5bb0f8c1168305
Description: Linux kernel image on 386.
 This package will always depend on the latest kernel image available
 for 386.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

ubuntu@ubuntu:~$ apt-cache show linux-386
Package: linux-386
Priority: optional
Section: restricted/base
Installed-Size: 52
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 2.6.15.19
Depends: linux-image-386, linux-restricted-modules-386
Filename: pool/restricted/l/linux-meta/linux-386_2.6.15.19_i386.deb
Size: 23266
MD5sum: c4a62f824a6401610ff1b6344cbf9073
Description: Complete Linux kernel on 386.
 This package will always depend on the latest complete Linux kernel available
 for 386.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

ubuntu@ubuntu:~$

---

### Post by az on 2006-04-21
Post the output of 
lsmod
and I'll tell you if getting rid of restricted modules will bork your system.

Most people can get rid of it without any problems.

---

