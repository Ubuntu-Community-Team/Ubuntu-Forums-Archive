---
title: "Differences between Debian and Ubuntu"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by alkat on 2007-04-06
Hello,
I'm pretty new to this community and to the Ubuntu world. To be honest, I've been running Ubuntu for quite some time now on my girl-friend's PC but I haven't really worked on it much. For the past four years I've been using mainly Debian and I think I've learnt quite a few things about how to set up and maintain a Linux box - I wouldn't consider myself a newbie but I'm not a power user either.

Now I'm willing to switch to Ubuntu as soon as Feisty is released... Why? Well, maybe just because I like the idea of a great system (at least that's how it's described around the net) supported by a company and a community. The whole "democratic" principles of the Debian way of doing things is something I'm starting not to like anymore. I also don't like very much the extremistic views regarding free software: I mean, open source is a great thing, but I strongly believe that open source software and proprietary software can live together - I therefore appreciate the fact that some softwares like Opera or Skype are easily available on Ubuntu.

To make things short, let's say I pretty much agree with this article:
[http://www.madpenguin.org/cms/?m=show&id=7827](http://www.madpenguin.org/cms/?m=show&id=7827)

All that being said, I'd like to go back to the question of this thread: what are the differences between Ubuntu and Debian?

I'm particularly interested in understanding how the two kernels differ, what important or useful applications are there in Ubuntu which are not included in Debian, what the differences are in the way the two projects are managed, and so forth.

Thanks for any reply to this. I'd also appreciate links to any up-to-date and reliable documents online which talk about this.

Cheers,
Ale.

---

### Post by brennydoogles on 2007-04-06
> **alkat said:**
> Hello,
I'm pretty new to this community and to the Ubuntu world. To be honest, I've been running Ubuntu for quite some time now on my girl-friend's PC but I haven't really worked on it much. For the past four years I've been using mainly Debian and I think I've learnt quite a few things about how to set up and maintain a Linux box - I wouldn't consider myself a newbie but I'm not a power user either.

Now I'm willing to switch to Ubuntu as soon as Feisty is released... Why? Well, maybe just because I like the idea of a great system (at least that's how it's described around the net) supported by a company and a community. The whole "democratic" principles of the Debian way of doing things is something I'm starting not to like anymore. I also don't like very much the extremistic views regarding free software: I mean, open source is a great thing, but I strongly believe that open source software and proprietary software can live together - I therefore appreciate the fact that some softwares like Opera or Skype are easily available on Ubuntu.

To make things short, let's say I pretty much agree with this article:
[http://www.madpenguin.org/cms/?m=show&id=7827](http://www.madpenguin.org/cms/?m=show&id=7827)

All that being said, I'd like to go back to the question of this thread: what are the differences between Ubuntu and Debian?

I'm particularly interested in understanding how the two kernels differ, what important or useful applications are there in Ubuntu which are not included in Debian, what the differences are in the way the two projects are managed, and so forth.

Thanks for any reply to this. I'd also appreciate links to any up-to-date and reliable documents online which talk about this.

Cheers,
Ale.

That's a great question! Having not used Debian, I can't tell you firsthand about any differences, but I know that Ubuntu is based off of the Debian Kernel. You can still install software using .deb files, or using the synaptic package manager or source if you would like.

---

### Post by igknighted on 2007-04-06
Basically, the Ubuntu devs take a snapshot of Debian Sid every 6 months.  This basically becomes Ubuntu after some heavy patching to fix it all up.  Of course there is a bit more Ubuntu touch to the look and feel, a lot of pre-selecting applications (theres a one application per task guideline), and a few Ubuntu-community developed stuff (mostly py-gtk frontends to automate tasks and make config easier).  So basically, its not as stable as a true Debian release, but more up to date.  Its not by any means bleeding edge like Sid, as the packages are months old after the snapshot becomes the next release of Ubuntu, but thats where they come from.

---

### Post by az on 2007-04-06
> **alkat said:**
> Well, maybe just because I like the idea of a great system (at least that's how it's described around the net) supported by a company and a community. The whole "democratic" principles of the Debian way of doing things is something I'm starting not to like anymore. I also don't like very much the extremistic views regarding free software: I mean, open source is a great thing, but I strongly believe that open source software and proprietary software can live together - I therefore appreciate the fact that some softwares like Opera or Skype are easily available on Ubuntu..

1.  Debian is also supported by hundreds of companies around the world.  Ubuntu is also run by Democratic process - the governing boards are elected.
2. I think Ubuntu has just an extreme point of view regarding software freedom, it just has a nice way of saying it.  In fact, Ubuntu has had a great impact on the adoption of software freedom.


> **alkat said:**
> 
To make things short, let's say I pretty much agree with this article:
[http://www.madpenguin.org/cms/?m=show&id=7827](http://www.madpenguin.org/cms/?m=show&id=7827).

I skimmed that article and the author is misinformed about a number of things.  Ubuntu does not disregard any licences by shipping proprietary drivers.  

The author does more to make people who beleive in software freedom look bad than anyone else.  Not wanting to hijack this thread about this, that article should be ignored, IMHO.

> **alkat said:**
> 
All that being said, I'd like to go back to the question of this thread: what are the differences between Ubuntu and Debian?
.

Debian has two sides.  A slow and stable side and a fast-paced, cutting edge side.  Ubuntu takes a *small subset* of the packages in the cutting-edge version of debian and works on them to make them supportable.  Then, Ubuntu releases it and offers support for a determined period of time.  Releases are often and predictable.

Ubuntu does abide by the DFSG (Debian free software guidelines).  Debian has a non-free section just like Ubuntu does.  There is one difference, in that Ubuntu ships a handful of proprietary drivers on the install disk.  

> **alkat said:**
> 
I'm particularly interested in understanding how the two kernels differ, what important or useful applications are there in Ubuntu which are not included in Debian, what the differences are in the way the two projects are managed, and so forth.


You can completely remove all non-free software from a fresh ubuntu install by removing the linux-restricted-modules package from your system.

sudo apt-get remove linux-restricted-modules*
(Don't worry!  This will not remove your kernel.  This will remove linux-generic, but linux-image-generic will stay installed)

AFAIK, there are no important or useful applications that are only availble to Ubuntu (and not Debian).  There are a few irrelevant packages in the Dapper-commercial archive, but that is pretty limited.  Anything that is in Debian is in Ubuntu (either in main or universe).  LIkewise, anything that is in Ubuntu is offered back to debian. 

Due to the different release goals and procedures, there are differences between the packages and how they work together, but Ubuntu tries to sync back with Debian every time they release.  Ubuntu benefits from Debian and Debian benefits from Ubuntu.  One example is how the transition from xfree to xorg was done in Ubuntu before it was done in Debian.

---

### Post by alkat on 2007-04-06
Thank you all for your comments.

@az
When I was pointing to the difference that Ubuntu is supported by a company and a community, I meant that while Debian is mainly community-driven, in Ubuntu you have a strong leader and a company (Canonical) which is leading the development. Correct me if I'm wrong. 

The fact that Ubuntu ships proprietary drivers is, in my opinion, something extremely positive - that's one of the reasons why I'm planning to move to Ubuntu. I know that you can get most proprietary softwares in Debian through apt-get (again, I'm referring to Opera or Skype) but the difference is that these repositories are officially supported by Canonical ([http://ubuntu.wordpress.com/2006/07/08/introducing-the-dapper-commercial-repository/](http://ubuntu.wordpress.com/2006/07/08/introducing-the-dapper-commercial-repository/)) whereas in Debian those are not officially supported packages. 

I have the feeling that there is a difference in how Debian and Ubuntu welcome proprietary software into the OS.

I repeat that I do believe in the importance of open source software and formats, but I also think that it is important for a user to be able to install proprietary drivers without too much fuss.

Maybe the only drawback of moving from Debian to Ubuntu is the upgrade process. Going from one Debian version to the other is generally painless while it was a nightmare for me to upgrade from Edgy to Dapper... Is it so, or was I just unlucky?

Ale.

---

### Post by az on 2007-04-06
> **alkat said:**
> 
When I was pointing to the difference that Ubuntu is supported by a company and a community, I meant that while Debian is mainly community-driven, in Ubuntu you have a strong leader and a company (Canonical) which is leading the development. Correct me if I'm wrong. 

Debian is more or less a meritocracy-driven democracy.  Ubuntu is a democracy-driven disctatorship.

> **alkat said:**
> 
The fact that Ubuntu ships proprietary drivers is, in my opinion, something extremely positive - that's one of the reasons why I'm planning to move to Ubuntu. I know that you can get most proprietary softwares in Debian through apt-get (again, I'm referring to Opera or Skype) but the difference is that these repositories are officially supported by Canonical ([http://ubuntu.wordpress.com/2006/07/08/introducing-the-dapper-commercial-repository/](http://ubuntu.wordpress.com/2006/07/08/introducing-the-dapper-commercial-repository/)) whereas in Debian those are not officially supported packages. 

The Dapper-commercial repo is pretty much dead.  There is no commercial repository for Edgy or Feisty, and I beleive that some of the apps for Dapper are no longer there.  

> **alkat said:**
> 
I have the feeling that there is a difference in how Debian and Ubuntu welcome proprietary software into the OS.

I repeat that I do believe in the importance of open source software and formats, but I also think that it is important for a user to be able to install proprietary drivers without too much fuss.

I think Ubuntu draws a line between userspace applications and kernel drivers.  There are no non-free apps shipped with the distro.  There are non-free drivers where there are no free-libre alternatives.  

I wouldn't say that Ubuntu welcomes proprietary apps.  Maybe "tolerate" is a better word?  Proprietary apps like Opera and Realplayer are pretty much second-class citizens, and not even close to being as popular as their free-libre alternatives.   They are there and you get the choice to use them or not, but I doubt the typical Ubuntu user really cares about whether they are there or not.

I'm not speaking for the Ubuntu community;  this is just what I gather from my experience.

> **alkat said:**
> 
Maybe the only drawback of moving from Debian to Ubuntu is the upgrade process. Going from one Debian version to the other is generally painless while it was a nightmare for me to upgrade from Edgy to Dapper... Is it so, or was I just unlucky?

Ale.

It depends.  A lot of people have had troubles because of third-party applications.  If you install stuff only from Ubuntu repositories, you should have less trouble.

---

### Post by alkat on 2007-04-06
> **az said:**
> Debian is more or less a meritocracy-driven democracy.  Ubuntu is a democracy-driven disctatorship.

I've always loved dictatorships... :) 


> **az said:**
>  The Dapper-commercial repo is pretty much dead.  There is no commercial repository for Edgy or Feisty, and I beleive that some of the apps for Dapper are no longer there. 

Ouch... I didn't know that!


> **az said:**
> 
Proprietary apps like Opera and Realplayer are pretty much second-class citizens, and not even close to being as popular as their free-libre alternatives.   They are there and you get the choice to use them or not, but I doubt the typical Ubuntu user really cares about whether they are there or not.

As usual, I'm quite atypical... :)


> **az said:**
> 
It depends.  A lot of people have had troubles because of third-party applications.  If you install stuff only from Ubuntu repositories, you should have less trouble.


Do you mean software installed also from the multiverse and universe repositories? Is that software "safe"?

Ale.

---

### Post by az on 2007-04-06
> **alkat said:**
> 

Do you mean software installed also from the multiverse and universe repositories? Is that software "safe"?

Ale.

Yes, I mean universe and multiverse.  It should be safe.  Things known to bork your system include third-party scripts which install and configure your graphics card from source, and things like that.  There is no reason that a breakage in a package in universe should render your system unbootable.  No reason at all.

---

