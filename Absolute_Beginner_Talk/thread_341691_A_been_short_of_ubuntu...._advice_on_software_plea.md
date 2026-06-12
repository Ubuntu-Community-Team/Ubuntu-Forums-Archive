---
title: "A been short of ubuntu.... advice on software please."
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by billingsworld on 2007-01-19
Hi,

I backed up my data and did clean installs of various distro's.  Of the bunch, 6.1 recognized most of my devices and my printers work.  Now that I have settled on Edgy, I have a few questions about software:

- Is Synaptic the only place I can get software or is it the place where software can be installed and dependcies are checked?  I guess if it's the later, than for now, it's the place I should stick to.

- I am not an open source zealot, yet, but I do want to co-habitate with the outside computing world and need to play the evil file types.  Is Mplayer the only thing I need?

- I have figured out that my home directory is a separate partition - hooray! that's what I did in windows.  Is Evolution data stored there as well?  I can't find any reference to it so I think not.

- I used to use Ghost to backup my C: drive onto my d: drive (where all my data was stored), is there a drive image program that works just as well?  If so, can I store the image files in my \home directory or is that a no-no.  I just know I am going to break ubuntu, I'd rather restore from an image.

- I need a firewall - I dunno, I just think it's prudent.  Is there something recommended?


Any help is appreciated.

Thanks.

---

### Post by MkfIbK7a on 2007-01-19
synaptic checks dependencies for you

mplayer should work with most of your needs

i dont beleive evolution data is saved there

im sure there is a backup program like ghost yes i believe you can store images in home

try firestarter

---

### Post by bodhi.zazen on 2007-01-19
> **billingsworld said:**
> Hi,

I backed up my data and did clean installs of various distro's.  Of the bunch, 6.1 recognized most of my devices and my printers work.  Now that I have settled on Edgy, I have a few questions about software:

Cool :)

> - Is Synaptic the only place I can get software or is it the place where software can be installed and dependcies are checked?  I guess if it's the later, than for now, it's the place I should stick to.

For now stay with synaptic.

You can install a lot beyond that, see here:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

The second site is down, but check it out when it comes back up :p

> - I am not an open source zealot, yet, but I do want to co-habitate with the outside computing world and need to play the evil file types.  Is Mplayer the only thing I need?

Well, what do you need. Nvidia drivers, multimedia, what ??

For multimedia start here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

	[http://www.ubuntuforums.org/showthread.php?&t=182902](http://www.ubuntuforums.org/showthread.php?&t=182902)


> - I have figured out that my home directory is a separate partition - hooray! that's what I did in windows.  Is Evolution data stored there as well?  I can't find any reference to it so I think not.

Yea, all your data is in home. Some stuff is "hidden" Starts with a . "dot files"

In nautilus (your file browser) : View -> check off "show hidden files"

> - I used to use Ghost to backup my C: drive onto my d: drive (where all my data was stored), is there a drive image program that works just as well?  If so, can I store the image files in my \home directory or is that a no-no.  I just know I am going to break ubuntu, I'd rather restore from an image.

Sure you can store your iso's in /home

You can mount them just like a cd if you want.

> - I need a firewall - I dunno, I just think it's prudent.  Is there something recommended?

Well that can be a hot topic :p

Linux is much more secure then where you came from. Take a look at firestarter or guard dog.

> Any help is appreciated.

Thanks.

Well that should get you started....

---

### Post by The Noble on 2007-01-19
Synaptic is merely a front-end for apt-get. Ubuntu also comes with aptitude if that suits your fancy. To add more software packages, add the repos into your /etc/apt/sources.list that you would like. Most .deb files work as well.

EDIT: Posted a little late. I suggest following bodhi's advice, though!

---

### Post by Sef on 2007-01-19
> - Is Synaptic the only place I can get software or is it the place where software can be installed and dependcies are checked?

No.  Read [Psychocat's installing software]("http://www.psychocats.net/ubuntu/installingsoftware").

> - I am not an open source zealot, yet, but I do want to co-habitate with the outside computing world and need to play the evil file types. Is Mplayer the only thing I need?

Have you enabled the [repositories]("https://help.ubuntu.com/community/Repositories")?

Have you read [restricted formats]("https://help.ubuntu.com/community/RestrictedFormats")?

If their is a DRM on the item being played, Ubuntu will not be able to play it.

Finally, Applications > Add/Remove > Sound and Video for other players.

> - I used to use Ghost to backup my C: drive onto my d: drive (where all my data was stored), is there a drive image program that works just as well? If so, can I store the image files in my \home directory or is that a no-no. I just know I am going to break ubuntu, I'd rather restore from an image.

Check out [Partimage]("http://partimage.org/Main_Page").  I believe it is in the repositories, but the site would have a more recent version.

> - I need a firewall - I dunno, I just think it's prudent. Is there something recommended?

Get firestarter.  It is in the repositories either through synaptic, or through the terminal.  To download it via the latter way:  Applications > Accessories > Terminal.  Then type in these two commands:

First, ```
sudo aptitude update
```

Second, ```
sudo aptitude install firestarter
```

---

### Post by Sef on 2007-01-19
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) is down and no longer working.  Which is a shame as it was a great site.

> Posted a little late.

Ditto.

---

### Post by tonyr1988 on 2007-01-19
To elaborate on #1:

Synaptic is a great way to install software. Like wert said, it'll check all the dependencies for you. But it's not the only way to install software. You can still install programs:

1) From Source. I'm not sure how often you've done this in the past, but you can use "sudo checkinstall" instead of "sudo make install" (once you download the checkinstall package from, you guessed it, Synaptic) and it'll add the newly installed program into Synaptic automatically. Make sense?

2) From *.deb Files. These are getting more prevalent on the interwebs as Ubuntu gets more popular. They're an easy way to install a program (without building the source) and are similar to an *.exe file. It'll do automatic dependency checks (usually) and it will also put an entry into your Synaptic list.

3) From *.rpm Files (and a few others). These are made for other Linux distros. But..you can download a program called alien (it's in Synaptic) that will convert them to *.deb's for you. This means you can install them automatically (with dependency checks usually) and have an entry into Synaptic.

In other words, you can install programs however you like, but you can keep everything organized in Synaptic. This keeps things cleaner. For example, you won't have to keep the source for a program just to uninstall it - just uncheck in Synaptic!

And for the "other formats" - did you have any particular ones in mind? Here are some resources:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[http://www.getautomatix.com/](http://www.getautomatix.com/)

They can help you get audio / video files up and running (MPlayer's a good one). If you wonder about documents / spreadsheets / etc, OpenOffice does a pretty good job at those (as long as you're not doing anything *too* fancy).

**PS Oops - I was late in my long-winded reply. Sorry! This community's too good. ;)**

---

### Post by billingsworld on 2007-01-19
Thanks for the help.

For those communist .mp3 files I have settled on XMMS, it's a lot like winamp and that's what I used to use.  It's not the purdiest audio player I have seen but it works and that's a good thing.

I don't know if I will encode all my files to Ogg, seems like a lot of work and the quality of what I have seems okay.  I got XMMS from Synaptic and it worked out of the shoot.

I am going to stick to the Synaptic tool for the moment, I don't think I have all the repositories setup properly but I will worry about that later.

---

### Post by tonyr1988 on 2007-01-19
Honestly, it's not necessary to re-encode everything to ogg. Don't get me wrong - .ogg is great philosophically (and technically), but you may experience problems if you're using them for anything other than playing on your computer (ex: most digital audio players don't support them), so you'd probably end up re-re-encoding them back to .mp3 anyway. :P

Lots of people love XMMS (I'm an Amarok guy myself :P), and if you want to make it look a little purdier, check out this:

[http://www.gnome-look.org/index.php?xcontentmode=130&PHPSESSID=0b2714a02e8e2015625b7015a3b2fa35](http://www.gnome-look.org/index.php?xcontentmode=130&PHPSESSID=0b2714a02e8e2015625b7015a3b2fa35)

Also, check out the [Unofficial Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") for help with things like getting extra repositories enabled.

I'm glad that things appear to be going well for you. Always feel free to ask for any more help you need.

---

### Post by billingsworld on 2007-01-20
That's excellent, thanks for the link.  The Winamp 5 like theme is excellent.  I am going to try out Amarok to see what it's about.

:guitar:

---

