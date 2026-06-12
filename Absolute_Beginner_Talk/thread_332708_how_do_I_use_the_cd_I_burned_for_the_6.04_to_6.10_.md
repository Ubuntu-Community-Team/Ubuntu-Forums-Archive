---
title: "how do I use the cd I burned for the 6.04 to 6.10 upgrade?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Scott A on 2007-01-06
how do I use the cd I burned for the 6.04 to 6.10 upgrade?

---

### Post by zekopeko on 2007-01-06
if you have the normal liveCD than you can't upgrade via CD , but if you have the ALTERNATE CD INSTALLER than i guess you should just put it in you CD/DVD and run synaptic. 

synaptic should recognize that the cd is a repo and should offer to add it to the list of repos.

after that just follow this wiki [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

EDIT: the upgrade from CD is given in the linked wiki

---

### Post by Scott A on 2007-01-06
is there a step by step process that will allow me to have synaptic see the CD?

---

### Post by jvc26 on 2007-01-06
You need the 'alternate installer cd'
The go to [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)
And follow:
> 
Upgrading using Update Manager

If you want to upgrade from 6.06 LTS to 6.10, run the following command (either via ALT-F2 or a terminal):
```

gksu "update-manager -c" 

```
The -c switch instructs Update Manager to look for upgrades. By default, the Ubuntu 6.06 LTS release will not offer that automatically because of its long support cycle and high stability.

If you have a working network connection, it should then inform you about a new release and offer to upgrade your system.

If you have the Edgy Alternate Install CD (not the Desktop CD), you can save bandwidth by using:
```

gksu "sh /cdrom/cdromupgrade" 

```


zekopeko had already pointed you in the right direction :)
Il

---

### Post by Scott A on 2007-01-06
i tried the gksu "sh /cdrom/cdromupgrade" and it did nothing. It acted like it was going to do something, but nothing happened. Could that be because I have it recorded to a dvd instead of a cd?

gksu "update-manager -c" would make me re-download the update all over again. Another 8 hours!

I do not have the Edgy Alternate Install CD.

I do not know what the ALTERNATE CD INSTALLER is or how to get to it. 

Is there a step by step process for having synaptic see the dvd or to see the file that was downloaded to my desktop? 

Maybe I just do not yet know how to use synaptic, or which buttons to push. 

Thanks again,
Scott A

---

### Post by jvc26 on 2007-01-06
The alternate cd is a different version of the install iso: You can get it from here:
[http://www.ubuntu.com/products/GetUbuntu/download#currentrelease](http://www.ubuntu.com/products/GetUbuntu/download#currentrelease)
Then you have to go to your local mirror
And go down to find a thing like:
ubuntu-6.10-alternate-amd64.iso
That is the alternate iso. Download it and then follow the instructions shown above.
> 
if you have the normal live CD than you **can't** upgrade via CD , but if you have the **ALTERNATE CD INSTALLER** than i guess you should just put it in you CD/DVD and run synaptic.

You have to have the alternate cd, which is a different version of the installer cd. It is a text based installer (but that does not matter for this purpose) rather than the live cd. Once you have the 6.10 cd you also then dont have the need to upgrade again until the next one comes out and should you need to install you can just run 6.10 straight on from the alternate cd rather than putting 6.06 on and upgrading.
Does that help any more?
Il

---

### Post by Scott A on 2007-01-06
Either I am not understanding the lingo, or I am not doing a good job at making my self clear. 

I have installed ubuntu 6.06 from the cd that ubuntu sent me a couple of weeks ago. 

Yesterday I spent all day downloading the upgrade to go from 6.06 to 6.10

That upgrade is on my desktop. I also burned it to a dvd. 

Is the installer cd a physical cd, like what I put in my computer cd drive?

I do not know what an alternate cd is. What is that?

If I can upgrade from 6.06 to 6.10 with what is on my desktop, or what I burned to the cd-rom, I would rather do that than take up bandwidth and another 8 hours of downloading. 

i tried the gksu "sh /cdrom/cdromupgrade" and it did nothing. It acted like it was going to do something, but nothing happened. Could that be because I have it recorded to a dvd instead of a cd?

gksu "update-manager -c" would make me re-download the update all over again. Another 8 hours!   I do not want to have another 8 hour download.

I do not have the Edgy Alternate Install CD.

I do not know what the ALTERNATE CD INSTALLER is or how to get to it. What is that?

Is there a step by step process for having synaptic see the dvd or to see the 6.06 to 6.10 upgrade file that was downloaded to my desktop?

Maybe I just do not yet know how to use synaptic, or which buttons to push.

Thanks again,
Scott A

---

### Post by jvc26 on 2007-01-06
> 
Either I am not understanding the lingo, or I am not doing a good job at making my self clear.

Thats not a problem, apologies for maybe not being clear earlier, was slightly mystified by the odd thing. (See below)

> 
That upgrade is on my desktop. I also burned it to a dvd.

Not sure what this file is - what is its extension and where did you get it from?

> 
Is the installer cd a physical cd, like what I put in my computer cd drive?

No it is an .iso file (a cd image) which you download and then burn to a cd. Once you have burnt it then it is a physical cd.

> 
i tried the gksu "sh /cdrom/cdromupgrade" and it did nothing. It acted like it was going to do something, but nothing happened. Could that be because I have it recorded to a dvd instead of a cd?

Thats unlikely to be the reason, more likely to be the fact that it could be a live cd version (does it load a gui when you boot the cd?) and hence is not the alternate install cd (see below)

> 
gksu "update-manager -c" would make me re-download the update all over again. Another 8 hours! I do not want to have another 8 hour download.

That may be the only way you can do this, but we shall see if you can avoid it.

> 
I do not have the Edgy Alternate Install CD.

I do not know what the ALTERNATE CD INSTALLER is or how to get to it. What is that?

You have already said that, and I explained it, apologies if I was not clear. The Alternate Install cd is a different cd version to the one you got through the post. It is a cd which instead of using the live cd GUI to allow you to install ubuntu it works through a text based installer. You can download it via the method I said earlier.

> 
Is there a step by step process for having synaptic see the dvd or to see the 6.06 to 6.10 upgrade file that was downloaded to my desktop?

I'm not 100% sure what you have downloaded - can you clarify further? When I used the upgrade I merely downloaded it via the update manager and that did all the stuff in one sitting, taking about 4-5hrs for the whole process. Did you download a new cd .iso file? (I.e. an image of the cd surface which you then burn to a cd to use to install edgy 6.10) Where did you get it from?

> 
Maybe I just do not yet know how to use synaptic, or which buttons to push.

Thats not a problem - we all learn through the same process - the simplest way to update is always to just go to the update manager and update via that. However, I hadnt heard of this method but the links which were sent about further up in this post showed that you can avoid having to download all the stuff if you have your hands on the 'alternate install cd' which is got via a download and then a burning of the iso. This is mainly if you already have a cd from another install and you're upgrading other pcs to prevent you having to download the updated version x number of times for x number of pcs.

Finally, I hope you manage to get this sorted without having to re-download that would be as you say a pain, please if trying to clarify a problem, dont just repeat yourself - it doesnt help people understand more detail/a different way of saying things is easier to make sense of.

Il

---

### Post by Scott A on 2007-01-06
Hey Illuvator!
That update manager thingy looks like a good idea! It looks like a much easier way to do what i want to do, even if it takes a while!

Is there a way to get WINE or Automatix2 through the update manager so that i can install windows programs?

Thanks again!

Scott A:)

---

### Post by jvc26 on 2007-01-06
Hey, here is one of the links you will use an awful lot when starting out:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
Pop on there, and read the sections about enabling extra repositories then the one installing automatix2 and then installing wine (which you can do as part of automatix2 its up to you)
Hope that helps :)
Il

---

### Post by Scott A on 2007-01-06
I realized i forgot to answer your message about where I got the update for ubuntu 6.06 to 6.10. Sorry. 

I think I got it (ubuntu-6.10-desktop-i386.iso.torrent) from the download section of the ubuntu main page or something close to the main page. 

By the way, what is a GUI?

How do you "boot" the cd in ubuntu? I am still so used to windows. Microsoft has warped my brain.

Thanks again!

---

### Post by Scott A on 2007-01-06
Hey!
that link [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) does have the answers to most of my questions!

I book marked the main list and some of the others for later!

Thanks!

---

### Post by macogw on 2007-01-06
GUI = Graphical User Interface ...not text
You downloaded the desktop cd.  That's the live cd.  If you put it in the cd drive and restart, it'll boot into a useable desktop without installing.  You need the text-installer, also known as the Alternate CD.

---

