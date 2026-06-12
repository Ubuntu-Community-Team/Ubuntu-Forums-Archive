---
title: "Corrupt file error installing Ubuntu server"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by hoghunter on 2007-07-23
I have tried three different burned CDs and I keep geyying a corrupt file error during my install of Ubuntu server.  The last time it was **gzip_1.3.5-12_i386.deb**, I don't know if that was the file name before.  I performed a check of the CD before running the install and it passed.  I am pretty frustrated because I cannot figure out what is going on.  

Any help would be gratefully accepted.  I have tried both the latest version and the LTS version.

---

### Post by wolfen69 on 2007-07-24
are you checking your md5? are you verifying the disc after you burn it?

---

### Post by benx009 on 2007-07-24
> **hoghunter said:**
> I have tried three different burned CDs and I keep geyying a corrupt file error during my install of Ubuntu server.  The last time it was **gzip_1.3.5-12_i386.deb**, I don't know if that was the file name before.  I performed a check of the CD before running the install and it passed.  I am pretty frustrated because I cannot figure out what is going on.  

Any help would be gratefully accepted.  I have tried both the latest version and the LTS version.

hmmm, why don't you try burning the disc again at a slower speed? that usually works for some.

---

### Post by inyoka on 2007-07-24
> **hoghunter said:**
> I have tried three different burned CDs and I keep geyying a corrupt file error during my install of Ubuntu server.  The last time it was **gzip_1.3.5-12_i386.deb**, I don't know if that was the file name before.  I performed a check of the CD before running the install and it passed.  I am pretty frustrated because I cannot figure out what is going on.  

Any help would be gratefully accepted.  I have tried both the latest version and the LTS version.

If it stalls during an installation like this the most likely explanation is a problem during either the reading from or writing to the cd.  When I get this problem I normally ensure that I burn the cd slowly.  Also try installing using a different cd-rom drive, if you can try using the cdrom that burnt the cd in the first place.  

In the long term consider ordering the ubuntu cd's from the website, they tend to be of much higher quality.  Of course you should listen to hoghunter as well, and always check the md5.

[COLOR="Blue"][[COLOR="Blue"]_Information on checking md5 can be found here._[/COLOR]]("http://ubuntuguide.org/wiki/Ubuntu:Feisty/CDDVDBurning")[/COLOR]

Please let us know how you get on.

---

### Post by FleetAdmiral74 on 2007-07-24
Have you burnt disks of this size/type before with any difficulty, or is this specific to ubuntu?

---

### Post by hoghunter on 2007-07-24
Thank you all for the responses.  To the questions about the cdrom, I suspected the speed of the burn so I used the slowest speed available and no I haven't had problems with that cd burner on any other discs.  I wish I had known there could be this level of finickiness as I would have burned the cd on the old copy of Windows XP that *was *on that PC ***before ***I started the Ubuntu install. :(  Now I must disassemble the device and swap drives.  

As to the recommendation that I purchase the CD for Ubuntu, I generally don't mind buying software after I successfully try it out.  In this case, this is my fourth or fifth foray into the Linux realm. Each of the earlier ones resulted in unsatisfactory results for various reasons.  With all the buzz around Ubuntu, I figure it is worth a look.  Until, I am able to install and manage it, I will not be able to determine if I am going to stick with it.  I must say, this is a bad mark for me.

I have iso files for all of the Microsoft OS's I suuport and I can burn them and use them without problem. I am really bad at keeping track of physical disks. So the thought of being dependent on that media concerns me.

To the person who recommended I check the MD5, I must say "WTH?"  I do not know what a MD5 is nor do I know how to check one.  To the person who posted the link to how to check a MD5, THANKS. I will look into that.

<SET SOAPBOX=ON>
If you don't want to hear the rantings of someone who wishes he could love Linux but is forced to stay with Windows then, skip this section.  I put this little blurb here because I expect a bunch of responses to my lack of knowledge regarding either MD5 or CD burning. It seems that whenever I talk to people about Linux I seem to run into people who are bent on convincing me I need to know more about my OS and I should be responsible for learning how to manage my machine.  I had hoped Ubuntu was a departure from this camp. Unfortunately, I am beginning to suspect that Ubuntu is not the answer I had hopped it would be.  I love the idea of Linus and GNU software.  I have been a systems professional for nearly thirty years.  There was a time many years ago when I actually got jazzed by how an OS worked internally.  Heck back in the early Eighties I wrote machine code not assembler, but actual machine code because we didn't have an assembler.  I also worked on a team that developed a programming language that was sold commercially.  But that was then and this is now.  Now I have six kids, two jobs and no spare time.   Nowadays, a computer is just a tool I use to accomplish many tasks. This server is meant to serve email and only that.  I really don't want to become a guru of  Linux or Windows for that matter.  I just want to use it.  I am a guru of databases and that forces me to use various OS platforms.  But I would prefer to know as little as I can about a particular platform as I can and still get my work done. 

I do hope for the day when I can kiss Microsoft goodbye, but I do not think that time is here yet.  I am not giving up completely, but I have to keep in mind that the end result is I have to support this device.  I have just so many hours in the week and supporting an email server is something don't want to spend my time doing.  I can pay someone to give me access to an email server.  It just doesn't make sense to me that I should have to. Especially when I have a few PCs sitting around unused.

PS none of this was intended to start a flame war or provoke anyone.  I simply have been down this road so many times in the past that I can anticipate the route and want to cut off some of the noise so I can focus on the issue at hand:** Getting a working mail server setup**.
<SET SOAPBOX=OFF>

---

### Post by hyper_ch on 2007-07-24
I hope you know, that if you want to setup a mail server you will require a dedicated IP. Well, you are not really required to get a ded. IP but most email servers I know do not accept mails from dynamic IPs.

---

### Post by hoghunter on 2007-07-24
Thanks for the advice.  I have a dedicated IP over a fractional T1.  I host several Windows web servers over it. I don't want to stand up an exchange server for a simple POP server. For that matter, I really don't plan on using this as a full blown mail server right off.  Eventually perhaps, but the initial purpose is to house the system emails we get to our domains.  In that regard we really only need the POP aspect.  I have an STMP server running in Windows.  Now if this implementation is easy enough, I may migrate that SMTP server to this box to off load the processing of our outbound mail.  The outbound mail if for people to get notified of changes similar to how this site sends notices when a message is posted.

---

### Post by hoghunter on 2007-07-24
When I looked at the website that described the MD5 check, it seemed to show how I could do it with an operational Ubuntu system.  Unfortunately, I do not have a working system to start with.  I wonder if it would be possible to boot with the CD and not install to the hard disk.  Then I could transfer the ISO image to a USB drive and use that to burn a disk on the Ubuntu machine.  Hopefully that disk will work for a hard disk install.

Seeing as I am a complete newbie with Ubuntu, is there anything in that approach that would be faulty? I can try that tonight.  Unfortunately, I have to do all of this work in my spare time as it is not within the realm of my daya to day job.

---

### Post by qamelian on 2007-07-24
> **hoghunter said:**
>  As to the recommendation that I purchase the CD for Ubuntu, I generally don't mind buying software after I successfully try it out.  In this case, this is my fourth or fifth foray into the Linux realm. Each of the earlier ones resulted in unsatisfactory results for various reasons.  With all the buzz around Ubuntu, I figure it is worth a look.  Until, I am able to install and manage it, I will not be able to determine if I am going to stick with it.  I must say, this is a bad mark for me. No one said anything about purchasing the CD. If you go to the Shippit page on the Ubuntu website, Canonical will ship you one or more professionally produced Ubuntu CDs free of charge. And they pay the shipping. It's their way of getting Ubuntu into as many hands as possible. You can't ask for a better deal!

---

### Post by hyper_ch on 2007-07-24
Various ways to install ubuntu:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[https://wiki.ubuntu.com/CommonProblemsInstall](https://wiki.ubuntu.com/CommonProblemsInstall)

---

### Post by asmoore82 on 2007-07-24
have you tested the RAM in this machine with Memtest86+ ?

---

### Post by dca on 2007-07-24
I recommend the 6.06LTS Server Edition for what you're trying to accomplish versus 7.04 Server Edition.
 
*I couldn't afford to buy Windows Exchange Server even if I took a third mortgage out on my house.*

---

### Post by hoghunter on 2007-07-24
> **hyper_ch said:**
> Various ways to install ubuntu:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[https://wiki.ubuntu.com/CommonProblemsInstall](https://wiki.ubuntu.com/CommonProblemsInstall)


Wow!  Great info!  Thanks

---

### Post by hoghunter on 2007-07-24
> **dca said:**
> I recommend the 6.06LTS Server Edition for what you're trying to accomplish versus 7.04 Server Edition.
 
*I couldn't afford to buy Windows Exchange Server even if I took a third mortgage out on my house.*

Yes, I tried both, but I was inclined to install the LTS version.

---

### Post by hoghunter on 2007-07-24
> **qamelian said:**
> No one said anything about purchasing the CD. If you go to the Shippit page on the Ubuntu website, Canonical will ship you one or more professionally produced Ubuntu CDs free of charge. And they pay the shipping. It's their way of getting Ubuntu into as many hands as possible. You can't ask for a better deal!

**COOL!**

---

### Post by hoghunter on 2007-07-24
> **asmoore82 said:**
> have you tested the RAM in this machine with Memtest86+ ?

No, I haven't but the PC has been running Windows for years without issue.

---

### Post by hoghunter on 2007-07-24
> **qamelian said:**
> No one said anything about purchasing the CD. If you go to the Shippit page on the Ubuntu website, Canonical will ship you one or more professionally produced Ubuntu CDs free of charge. And they pay the shipping. It's their way of getting Ubuntu into as many hands as possible. You can't ask for a better deal!

My original response to your post was COOL!.  Then I saw the Shippit page and it says I have to wait **ten weeks** for the 7.04 version not even the LTS version!  Come on!

---

### Post by hoghunter on 2007-07-24
> **wolfen69 said:**
> are you checking your md5? are you verifying the disc after you burn it?

I ran the MD5 utility and I got 5ad76d8b380ab5be713e5daa9ea84475 but I don't know where to the value to compare it to.

---

### Post by hoghunter on 2007-07-24
Is there a way to copy the ISO file to the hard disk without the OS?  If so, maybe I can install from there. 

I am buying a CD, but I also want to get working.

---

### Post by hoghunter on 2007-07-25
Son of a ____!  I created a CD with another PC and it got an error too!  But I thought it was the same error so I didn't write it down because I expected it to quit like the other times.  Not this time.  It continued long enough for me to say something I shouldn't and begin posting this.  But then it lived up to my expectations and died.  Only further on in the process.  

The message says: Warning: Failure while configuring base packages.  This will be attempted 5 times.

Further on another message came up: Unable to install initramfs-tools blah blah blah

Since I seem to have a viable disk partition with some of the files on it, I wonder if I can get creative.  Like boot one of those CD based Linux (KNOPIX I think) and use it to download the image to the partition and install from there.  Or perhaps create a CD on the PC I am installing to.

---

### Post by hyper_ch on 2007-07-25
I dunno what you all have available at your place but have a look at the link I gave you about the various ways to install ubuntu... if you have a second computer or usb stick or have a fast connection for using the mini-iso...

---

### Post by hoghunter on 2007-07-25
Unfortunately, the PC I am installing oncannot boot from USB. :-(

I think I may need to give up until I can buy a new PC for Ubuntu.  The one I have is a AMD 2700 with 1 Gig of memory.  It would make a nice mail server.

---

### Post by Pebbie on 2007-07-25
im not sure bout yours. i just downloaded my 7.04 then burn it into CD with 12X spd. took around 4min for me

---

### Post by hyper_ch on 2007-07-25
hoghunter: Well, I think your computer should be able to boot from USB...

You need to enter the bios and set the according settings... I have a way older computer than you and I can boot from USB...

---

### Post by hoghunter on 2007-07-25
> hoghunter: Well, I think your computer should be able to boot from USB...

You need to enter the bios and set the according settings... I have a way older computer than you and I can boot from USB...

This one doesn't support it.  I know how to configure the bios, unfortunately for whatever reason this one doesn't.  The BOIS is from 2003 which is a time when USB was not nearly as popular as today.

---

### Post by hoghunter on 2007-07-25
> **Pebbie said:**
> im not sure bout yours. i just downloaded my 7.04 then burn it into CD with 12X spd. took around 4min for me

It isn't the speed.  I have downloaded and burned five discs using twoo different PCs.  Each one eventually gets an error.  I am talking server here and I am talking mostly the 6.o6 LTS version. Although I did try the 7.04 version once.  

I have tested them with MD5 checks and I have tested the memory on the PC.  I have also verified them using the Linux Boot Menu.

I mentioned this to a friend of mine and he said he had a disk but then his was a desktop disk.  When he thought about it, h recalled having trouble with the server version also.

---

### Post by hoghunter on 2007-07-25
**YAH HOO!** Install complete! I grabbed a different PC and it worked fine.  The bummer is I did not realize the server edition is without an xwindows interface.  Argh.  I hate command prompts.  It's been too many years since the old Unix days to remember the commands and editors.  I suppose i can try to apt-get a xwindow environment but then I suppose I could install the desktop and use it.

---

### Post by hyper_ch on 2007-07-26
You can easily install the x-environment, just enter

```

sudo aptitude install ubuntu-desktop

```
for the Gnome Desktop

or
```

sudo aptitude install kubuntu-desktop

```
for the KDE Desktop

or
```

sudo aptitude install xubuntu-desktop

```
for the Xfce Desktop (my preferred one)

This will then download and install the stuff that you would have as if you installed from the Desktop CD.

If you want to go a bit lighter, use this syntax instead:

```

sudo aptitude install -R **...**ubuntu-desktop

```
That will only install the required components of each desktop and not all recommended applications.

---

### Post by hoghunter on 2007-07-26
hyper_ch

**You are such a nice guy**.  I am so grateful to you for your detailed responses.  Honestly, I don't think I could hav figured half of this out on my own.

I actually installed the whole desktop version last night.  Then I screwed it up by changing the display settings because part of the screen was being cut off.  Well after I changed the settings, my viedo was unreadable.  I guess the setting I choose was wrong.  I kind of expected it to do like Windows does, where it changes it and waits 15 seconds to see if you like it.  If you don't say you do like it, it assumes you couldn't see the screen so it reverts back.  I thought that was a standard, but now I realize it wasn't.  So tonight I will reinstall server then I'll follow your directions to install the ubuntu shell.

Again that you so much!

Thom

---

### Post by hoghunter on 2007-07-26
> **hyper_ch said:**
> You can easily install the x-environment, just enter

```

sudo aptitude install ubuntu-desktop

```
for the Gnome Desktop

or
```

sudo aptitude install kubuntu-desktop

```
for the KDE Desktop

or
```

sudo aptitude install xubuntu-desktop

```
for the Xfce Desktop (my preferred one)

This will then download and install the stuff that you would have as if you installed from the Desktop CD.

If you want to go a bit lighter, use this syntax instead:

```

sudo aptitude install -R **...**ubuntu-desktop

```
That will only install the required components of each desktop and not all recommended applications.

When I tried this, I got a message This aptitude does not have *Super Cow Powers.*

---

### Post by hyper_ch on 2007-07-27
what did you try exactley?

---

### Post by hoghunter on 2007-07-27
I tried:
```
sudo aptitude install ubuntu-desktop
```

---

### Post by hyper_ch on 2007-07-28
Do you have an internet connection on the computer you're trying this?

Could you post the whole error message you get?

---

### Post by hoghunter on 2007-07-29
Yes the PC is connected to the Internet.  I found a another set up instructions for installing a windowing environment at another site.

It seems like I got it installed but I am not sure which command did it. ** Thanks for the help.**  NOw I am working on standing up the mail server.  I did find a great site for that  [here: ]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10")

I am struggling with some issues around the SSL setup for PosFix.

---

