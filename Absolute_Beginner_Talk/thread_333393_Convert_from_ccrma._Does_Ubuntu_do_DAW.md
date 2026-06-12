---
title: "Convert from ccrma. Does Ubuntu do DAW?"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Third Generation on 2007-01-07
I have a homebuilt(by me) computer, Athlon 900MHZ,500mb ram,pci wireless card (atheros chipset-Belkin), 180GB of HDs,Sony DVD burner, XFI audio card (also have audigy 2 if I need to swap that out.), MIDIMAN 2x2, external mixer, etc.  I've had all this running under SuSe 10.1 remastered, and FC5, but not so that it is reliable, or full function.
1.  Do I have enough 'horsepower' to create a DAW under Ubuntu, given my hardware?
2.  Are there low latency kernels (ingo, etc) that I can use to keep the latency very small under Ubuntu?
3.  I want to use ALSA and Jack, with Rosegarden and Ardour.  Are they supported here?
4.  Can I use RPMs with Ubuntu?
5.  Could I try the live distro and tell enough to encourage me to do the full install?

I guess that's a lot of questions for a first post, ubuntu is the only one of the 'majors' that I haven't tried, and the talk on the net is very positive about Ubuntu.  Also heard that there is something of an audio overlay that one could download to make the DAW conversion easier...anybody heard of that?

Thanks for any help
Joe Fay

---

### Post by eric71 on 2007-01-08
1.  You might be a little low on CPU and memory to do a lot with rosegarden if you are using effects and recording audio.  For midi it should be fine.  Ardour should be fine on these specs I think.

2.  For Edgy, a forum member called LuNeO has put together some gread audio debs, including low latency kernels.  see [http://devlinuxbr.codigolivre.org.br/](http://devlinuxbr.codigolivre.org.br/)

3. Jack and ALSA are supported just fine in Ubuntu.

4.  There is a program for converting RPMs to debs, but it is not genereally recommended.  You should find anything you need in Ubuntu's repositories. Ubuntu Studio, a project to develop a multimedia editing derivative of Ubuntu, plans to use only packages in official Ubuntu repositories [http://www.ubuntustudio.com/](http://www.ubuntustudio.com/) .  I think you can get most of what you could need from Ubuntu repositories, nearly as much as ccrma.

5.  The live cd doesn't include DAW related packages.  To really get a feel you would need to install it and then install things like qjackctl, ardour, and Rosegarden. I'm not sure what the status of Ubuntu Studio is now, but eventually I assume as Feisty Fawn progresses they will have a live/install cd that will allow you test most of these things.

I've been recording with Linux for a few months now and find Ubuntu an easy distribution to work with.  Newer versions of Ardour and Rosegarden which should be in Feisty will make it even better, and the development of Jokosher, a more Gnome-centric multitrack recorder with strong ties to Ubuntu has me very excited.

---

### Post by Third Generation on 2007-01-09
Thanks for the info and the links.  And I have a few more questions:

1. Where and when would I add the repositories to check for programs and updates...Is there a spot during the install where I will be asked to add repositories to check--some distros do it like that--or is there a file I need to edit after the install is done?

2. Is there a written list  of repo sites for Audiophiles to use to get what I need from for my DAW installation?...in other words, what are the repo links, and what is the format to add them to the list?  Sorry, I'm new to Ubuntu.

3. Are those LT kernels you mentioned precompiled, or do I need to do that, and is the link you included what I add to the repository list?

4. And finally, does MADWIFI work well on Ubuntu?  I have a Belkin card with Atheros chipset, so MADWIFI has been working great on everything I've tried...just MAKE and MAKE INSTALL and you're ready to reboot and set up your WEP key and other data to get you on line. 

I'm ready to install when I get answers to these last questions!

Thanks for all your help!
Joe Fay (aka Third Generation)

---

### Post by ihavenoname on 2007-01-09
> **Third Generation said:**
> Thanks for the info and the links.  And I have a few more questions:

1. Where and when would I add the repositories to check for programs and updates...Is there a spot during the install where I will be asked to add repositories to check--some distros do it like that--or is there a file I need to edit after the install is done?

2. Is there a written list  of repo sites for Audiophiles to use to get what I need from for my DAW installation?...in other words, what are the repo links, and what is the format to add them to the list?  Sorry, I'm new to Ubuntu.

3. Are those LT kernels you mentioned precompiled, or do I need to do that, and is the link you included what I add to the repository list?

4. And finally, does MADWIFI work well on Ubuntu?  I have a Belkin card with Atheros chipset, so MADWIFI has been working great on everything I've tried...just MAKE and MAKE INSTALL and you're ready to reboot and set up your WEP key and other data to get you on line. 

I'm ready to install when I get answers to these last questions!

Thanks for all your help!
Joe Fay (aka Third Generation)


I am not well versed in anything audio related. But I can help with the Ubuntu related stuff (I am quite familiar with Fedora though so if you need any "equivalents" or the likes, I can help you just pm me.) 

1. The repos can be added using Synaptic (in System>Administration I believe)

2. I don't think that his link leads to repos directly but there seems to be more information on the site that should help you.

3. I believe they are precompiled (assuming I read correctly)

4. In edgy itself madwifi works out of box. (So no make or make install, just boot and your set). However the Low Latency kernels are if I recall correctly based off of a newer version of the kernel than the one in Edgy, and it MAY have issues with madwifi. (This is if it is  based off of version 2.6.19-6 or later). You'll have to test this yourself to make sure. If it does have problems you maybe able to go around this with ndiswrapper. Or just install an earlier version of the 2.6.19 low latency kernel.

I hope this helps some what.:D

---

