---
title: "I am such a newbie to anything linux related! Help!"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by pthickett on 2006-11-14
Hi,

I have got to the point where i want to know just how much better using a linux os would be over windows, and i must have chosen ubuntu pretty randomly, but it seems (correct me if i am wrong) to be designed to be used by more windows familiar users?

Basically i have a few questions:

I am worried about drivers, will ubuntu pick up all the necessary drivers i will need for my computer? I have a philips laptop, pretty new, all the components are pretty standard.

I will want to set it up to dual boot, as there are a few windows specific programs that i will still want to use, is this as simple as having two windows os's installed? or do i have to do anything funky, or be concerned about the order in which i install them?

Will ubuntu be able to use pretty common apps like msn messenger, and will the office program allow me to import a .pst outlook personal folder (with all my emails, contacts and calendar info)?

Whats the media support like, will i be able to get hold of media players that will support common mp3, aac, etc music files that seem to be the product of having an ipod, and about ipods, will it be able to support my ipod?

If anyone can help that would be great, or direct me to a different linux os if anyone thinks that would suit me better.

Regards

Pete

---

### Post by Bachstelze on 2006-11-14
Hi and welcome to Ubuntu :)

1. Please be more precise, what hardware exacly do you have ? You could also search for yur lappy in the Hardware Support page in the Wiki.

2. No, it's simpler :D If you already have Windows installed, just resize the Windows partition, install Ubuntu in the free space and you should be ready to go.

3. Don(t know about Outlook, never used it.

4. I have an iPod and it works perfectly with Amarok but I use only mp3, don't know about AAC. Have a look ar the Restricted Formats page in the Wiki.

---

### Post by DannyG on 2006-11-14
In answer to your questions, Ubuntu is a good OS to use if your introducing yourself to Windows, however, unlike Windows, Ubuntu gives you a lot more of a System Admin sort of situation, where as Windows is more for people who aren't interested in configuring their OS's right down to the very bone.

Ubuntu comes with OpenOffice.org as standard, which is a fantastic Office Suite (you can get a Windows version to get yourself familiar with it, but its more or less identical to Microsoft Office, but a lot more stable). And OpenOffice.org does support most Microsoft Office file types, but check out the site to see if they support .pst.

If you were to install Ubuntu onto the same HD as Windows, Grub would be installed which allows you to select which OS you want to boot into, simple as that. I've never had any trouble dual booting between Ubuntu and Windows, and no very techinical configuration was needed.

Ubuntu does, ofcourse, support MP3, wav, etc but in order to watch DivX, XviD, DVD etc you can download some packages via apt-get (which is the package management system, allowing you very easy access to thousands of programs).

There are lots of MSN-like programs available for Linux, the most common probably being aMSN which gives a near identical replication of MSN Messenger. Very easy to use and setup.

Any other questions, just ask...

Daniel.

---

### Post by mblinux on 2006-11-14
Well, doing a forum search for everything you've asked will provide answers for all your questions, but let me reply what I can (in my little time):

Drivers: You'll have no problem with drivers. Some efforts may request wireless devices and video cards (video cards: if you want the latest drivers). Maybe you'll have to configure your favourite resolutions if not available: Also tv-out and dual monitors system need some tweaking but this forum has all the answers.

Dual booting : Really easy. Remember to install Windows first, make room in you hard drive with a tool like Partition Magic, or any other window or linux (maybe a linux live-cd with a) program for disk management. If you'll need to reinstall windows you'll have to reconfigure Grub and during install be carefull to not delete the linux partitions. In general for linux you'll need 2 partitions: the main partitions / and a swap partition. Automatic partitioning will do the job for you, but if you search these forums you can configure your partitions as you like.

MSN messenger: Yes, there is something like MSN for linux: amsn or you can try other messengers like GAIM.

.pst : I don't know.

Media players: I suggest Amarok and mplayer or VLC. Are easy to install specially following instructions that you'll find in this forum. You'll have to install mp3 support and maybe some other codecs. It depends what you need.

Ipod: I don't know, I'm a Creative's fan. Again I have to suggest the search feature of this forum.

---

### Post by monkieie on 2006-11-14
concerning the outlook messages,

see here:
[http://www.experts-exchange.com/Operating_Systems/Linux/Q_21024960.html]("http://www.experts-exchange.com/Operating_Systems/Linux/Q_21024960.html")

if you have OE probs:
[http://www.ubuntuforums.org/showthread.php?t=210638]("http://www.ubuntuforums.org/showthread.php?t=210638")

otherwise I can only suggest using the search facility in the forum. :mrgreen:

---

### Post by Swab on 2006-11-14
> **DannyG said:**
> 
Ubuntu comes with OpenOffice.org as standard, which is a fantastic Office Suite (you can get a Windows version to get yourself familiar with it, but its more or less identical to Microsoft Office, but a lot more stable). And OpenOffice.org does support most Microsoft Office file types, but check out the site to see if they support .pst.


Ummm, OpenOffice is no way near identical to MS Office, anyone who uses their office suite for more than simple letters can tell you that.  I dislike Microsoft as much as anyone else but MS Office is still the superior product.    Also seeing as there is no email client in OpenOffice, it will not know what to do with .pst files.

---

### Post by IYY on 2006-11-14
Hi,

> I have got to the point where i want to know just how much better using a linux os would be over windows, and i must have chosen ubuntu pretty randomly, but it seems (correct me if i am wrong) to be designed to be used by more windows familiar users?


This is not really true. Ubuntu is not at all designed to be familiar to Windows users, but rather does things the GNU/Linux way. For example, it does not include nonfree codecs like mp3 and wmv (they are very easy to install, though). It does not have the same menu structure as Windows. Many things are done through the command line. This approach may seem more complex at first, but most users find out that in reality it is better and easier, once you get used to it. Linux is not very good at being Windows, but it's excellent at being Linux!

If you want a distribution that tries to be more like Windows, go with Linspire or even SUSE.

However, I think Ubuntu is a very good choice.


> I am worried about drivers, will ubuntu pick up all the necessary drivers i will need for my computer? I have a philips laptop, pretty new, all the components are pretty standard.

There is no guarantee that it will. Some drivers are kept a secret by the company, and not only will it not include official drivers, but will keep the specs of the device a secret so that nobody can write their own drivers. This is common with certain wireless adapters. There is a solution that involves a wrapper around the Windows driver in this particular case.

To check what works and what doesn't, just run the LiveCD. You don't have to install anything on your drive.

> I will want to set it up to dual boot, as there are a few windows specific programs that i will still want to use, is this as simple as having two windows os's installed? or do i have to do anything funky, or be concerned about the order in which i install them?

The Ubuntu CD allows you to easily resize your Windows partition and set up dual boot, however, remember the following:

1. Whenever installing a new OS, be it Windows or Ubuntu, always back up your most important data. It's better to do this than be sorry later.

2. Ubuntu will allow you to resize a Windows partition and live alongside with it nicely, but Windows does not do the same. So, you must first install Windows and *then* Ubuntu.

> Will ubuntu be able to use pretty common apps like msn messenger, and will the office program allow me to import a .pst outlook personal folder (with all my emails, contacts and calendar info)?


A fairly small amount of applications work on both Linux and Windows (that is, if you don't include open source apps like Firefox and Open Office, all of which work even better on Linux). Among what works is Skype, the Yahoo messenger client, Google Earth and Picasa, some 3D shooter games from id, etc.

Office and MSN messenger don't work. It's possible to emulate Windows programs through Wine, but it can sometimes be a buggy process.

Luckily, almost every Windows program has a free equivalent in the Linux world. Instead of Microsoft Office, use Open Office. Instead of Outlook, use Evolution or Thunderbird. Instead of any IM software, use Gaim (it's compatible with your AIM, Yahoo, MSN, IRC and other accounts.)

There are some ways to convert your pst file, but I never personally tried it. A google search brings up solution like these: [http://linux.uta.edu/article.php?pid=5](http://linux.uta.edu/article.php?pid=5)

 
> Whats the media support like, will i be able to get hold of media players that will support common mp3, aac, etc music files that seem to be the product of having an ipod, and about ipods, will it be able to support my ipod?

iPods are supported. Most media players (and there are many, so you can pick one depending on your choice of organization pattern) will play any files for which you have codecs installed. Most common codecs can be easily downloaded from the repositories, see the Ubuntu Guide:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

I'm not sure whether or not your AAC files can be played, but they can easily be converted to MP3 with a command like,

```
ffmpeg -i input.m4a -acodec mp3 -ac 2 -ab 128 output.mp3
```

---

### Post by pthickett on 2006-11-14
Cool, well thanks everyone for your help, i think i am almost ready to get it up and running.

For my .pst file, i was going to download thunderbird in windows and apparently i can import a .pst file to that, then export it to a more linux friendly format to re-import it into thunderbird when i install that on ubuntu.

So i guess i just boot up my machine with the cd in the drive and boot off it? and is it possible to resize partitions during that process? one last thing, what file format will it use, i take it it wont be ntfs!!

Thanks again

---

### Post by hyper_ch on 2006-11-14
Well, if you can import the .pst file to TB in windows, all you need to do then to run that stuff on linux is copy the content of your tb profile folder into linux :) (basically make the windows ntfs drive - if it is one - readable to linux and after copying chmowning the files to your user)

---

### Post by Swab on 2006-11-14
> **pthickett said:**
> Cool, well thanks everyone for your help, i think i am almost ready to get it up and running.

For my .pst file, i was going to download thunderbird in windows and apparently i can import a .pst file to that, then export it to a more linux friendly format to re-import it into thunderbird when i install that on ubuntu.

So i guess i just boot up my machine with the cd in the drive and boot off it? and is it possible to resize partitions during that process? one last thing, what file format will it use, i take it it wont be ntfs!!

Thanks again

You should be able to resize your Windows partition during install.   If not, try defragging it in Windows, then restarting the install.  

The default file system for Ubuntu is ext3.

---

### Post by marx2k on 2006-11-14
One thing you should know before resizing/reformatting/moving partitions in GParted from the Ubuntu Live CD..

This version of GParted is older than the current release and I think for your purposes you will not need any other version.

However, if you do end up needing to move a partition over to the left and then resize...

(situation: Your partition list on hda1 is...
40GB NTFS | 50GB EXT3 | 2GB  SWAP

...you decide you want to make your NTFS partition smaller and want to expand your EXT3 partition...

So now you have...
30GB NTFS | 10GB Unused Space | 50GB EXT3 | 2GB SWAP

You would want to use that 10GB unused space.  You would have to slide the 50GB EXT3 partition to the left and then expand it from the right (Youll see what Im talking about if you ever use GParted :)

With the Ubuntu LiveCD GParted, you can't do it.  You need the GParted LiveCD in order to do this.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Just a warning in case you ever need to do this.  Personally it took me a day or two to figure out that even though youre supposed to be able to do this in the GParted from the Ubuntu LiveCD, you can't.

Thought I'd save you some time :) 

Beyond that, setting up Ubuntu is really a breeze. Even setting up XP AFTER Ubuntu isn't too hard to fix.  It's basically 3 or 4 command lines run from gnome-terminal from the Ubu Live CD.  But definately MUCH easier to do it by throwing XP on the drive first THEN Linux

---

### Post by pthickett on 2006-11-14
Guys,

Just so you know, install went straight forward, now running 50gig xp partition, and 10gig for ubuntu and its running perfectly. There is one issue that it cant find the driver for the multi card reader built into my laptop, but thats not really causing an issue.

In terms of getting my emails across, i managed to export my contacts from thunderbird (on my xp os) and get them into the ubuntu install of t-bird, no luck yet with the emails, but that doesnt really bother me as its a googlemail account and if i really need to find emails i can log onto the web.

In terms of further guidance, i want to try and use my ipod with ubuntu if thats possible. So does anyone know how best to go about doing that?

Also one of you mentioned earlier how its best to use command lines, i guess in the terminal, is there any guides about how to learn how to get to grips with that?

thanks

---

### Post by Swab on 2006-11-14
> **pthickett said:**
> Guys,

Just so you know, install went straight forward, now running 50gig xp partition, and 10gig for ubuntu and its running perfectly. There is one issue that it cant find the driver for the multi card reader built into my laptop, but thats not really causing an issue.

In terms of getting my emails across, i managed to export my contacts from thunderbird (on my xp os) and get them into the ubuntu install of t-bird, no luck yet with the emails, but that doesnt really bother me as its a googlemail account and if i really need to find emails i can log onto the web.

In terms of further guidance, i want to try and use my ipod with ubuntu if thats possible. So does anyone know how best to go about doing that?

Also one of you mentioned earlier how its best to use command lines, i guess in the terminal, is there any guides about how to learn how to get to grips with that?

thanks

Perhaps [this]("http://www.linuxcommand.org/") might help with using the command line.

---

### Post by Frak on 2006-11-14
1. Just to make you feel a litle better about drivers, Ubuntu Linux has been ruled as having more driver support than Window$

2. Ubuntu automaticaly installs GRUB, a dual booter, and just plain booter, because most Linux users also use Window$, or some other OS.

3. AMSN is your answer to MSN, though I recommend GAIM, Thunderbird and Evolution can save to that format (.pst).

4. And finally after some installed drivers, using EasyUbuntu (recommended for n00bs), Automatix 2.0(recommended for more advanced users, but still easy to use), or just freehand (not recommended), the Audio is awsome, and for a podcaster use Democracy Player.

Thanks for Asking, love mindjoggers.

---

### Post by Frak on 2006-11-14
And for the seccond question...

1. Yes you can resize within Ubuntu, whether installing or not (resizing is always done when installing to make space for the partition).

2. Ext 3, and then a swap file.

---

### Post by mdsmedia on 2006-11-14
> **Frak said:**
> 1. Just to make you feel a litle better about drivers, Ubuntu Linux has been ruled as having more driver support than Window$Can you quote a source for this one? I'd love to bookmark/print/save it to show the NBM zealots. :twisted:

---

### Post by Buck2348 on 2006-11-14
>A fairly small amount of applications work on both Linux and Windows (that >is, if you don't include open source apps like Firefox and Open Office, all >of which work even better on Linux). Among what works is Skype, the Yahoo >messenger client, Google Earth and Picasa, some 3D shooter games from id, >etc.

How can I get Picasa and Google Earth to work in Ubuntu--do I need to install them here, or is there a way to run the Windows installations from Ubuntu?  Thank you.

Buck

---

### Post by mdsmedia on 2006-11-14
> **Buck2348 said:**
> ..snip..

How can I get Picasa and Google Earth to work in Ubuntu--do I need to install them here, or is there a way to run the Windows installations from Ubuntu?  Thank you.

BuckThere are native Linux versions of GoogleEarth and Picasa. I'm not sure if they're in the Ubuntu repositories. I've installed GoogleEarth, but not Picasa, but I can't remember if I downloaded from Google or from the repositories. Do a search in Synaptic to see if they're in the repos. Sorry, I'm not at my Ubuntu machine.

---

### Post by mblinux on 2006-11-15
I think that GoogleEarth and Picasa are also available through Automatix2 (easy installation for various software, utils and plugins). [http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by pthickett on 2006-11-15
Right guys, whats the best music library manager/music player/ipod manager for ubuntu, i have had a look at a few different programs but there is no word of ipod support.

Will an ipod just show up as an external hardrive/usb drive similar to a usb flash drive?

cheers

Pete

---

### Post by closey on 2006-12-24
> **pthickett said:**
> Right guys, whats the best music library manager/music player/ipod manager for ubuntu, i have had a look at a few different programs but there is no word of ipod support.

Will an ipod just show up as an external hardrive/usb drive similar to a usb flash drive?

cheers

Pete

The iPod should show up at a USB drive automatically, yes. I think there's a program called gtkpod out there which will connect to the library etc.

---

### Post by Frak on 2006-12-24
> **pthickett said:**
> Right guys, whats the best music library manager/music player/ipod manager for ubuntu, i have had a look at a few different programs but there is no word of ipod support.

Will an ipod just show up as an external hardrive/usb drive similar to a usb flash drive?

cheers

Pete
Use AmaroK, it is in the repositories, ready for installation, identified my iPod on startup and worked perfectly on all my computers.  Possibly the most popular music player on Linux, and I wish they would port it to Windows so I could use it on there too, Windows Media Player sucks, I upgraded WMP and it looks strikingly like AmaroK, and it sucks and its slow, so hopefully one day they'll do that, but, back on subject, use AmaroK.

---

