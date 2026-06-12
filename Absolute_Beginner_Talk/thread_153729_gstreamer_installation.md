---
title: "gstreamer installation?"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by unbuntu on 2006-04-01
Hi,

I'm trying to get gstreamer0.8 installed on my ubuntu5.1.  But it seems quite frustrating so far...

I used synatptic package manager, and chose libgstreamer to install, and was told that I need libglib2-ruby, and when I tried to apt-get that package, it told me I need libruby1.8...and it's not installable...I tried apt-get libruby1.8 anyway, but was told there's no installation candidate for that package...

What do I do now?

---

### Post by unbuntu on 2006-04-01
Nobody's even read my post...?
Am I on the right forum?

---

### Post by Mustard on 2006-04-01
[QUOTE=unbuntu]Nobody's even read my post...?
Am I on the right forum?[/QUOTE]
Try not to feel neglected.  It's just a case of waiting for an answer from someone who **knows** the answer.  Not everyone would know.  I'm just thinking about it atm.  I thought gstreamer 0.8 was already installed, so I'm reading up on it atm.

---

### Post by Mustard on 2006-04-01
I would say you haven't enabled the universe and multiverse repositories yet...

[http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse](http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse)

---

### Post by unbuntu on 2006-04-01
[QUOTE=Mustard]I would say you haven't enabled the universe and multiverse repositories yet...

[http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse](http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse)[/QUOTE]

Thank you for the link.  Well, my goal is to play avi/wmv files on Ubuntu and I've already searched the forum and read several guides, including the "unofficial ubuntu guide", but most of the codec packages need to be installed suggested by that guide are not installable.  Now that I enabled universe and multiverse, it still says that some dependencies are not met.

[QUOTE=Mustard]Try not to feel neglected.  It's just a case of waiting for an answer from someone who **knows** the answer.  Not everyone would know.  I'm just thinking about it atm.  I thought gstreamer 0.8 was already installed, so I'm reading up on it atm.[/QUOTE]
Sorry...I was just wondering if I am on the right forum, since there's no views even after 10-15 minutes of my original post.

---

### Post by Mustard on 2006-04-01
After you change your sources, you generally need to hit the 'reload' button in Synaptic, or you can close Synaptic and do it from the command line using...

```
sudo apt-get update
#this command updates the package list from online repositories
```

---

### Post by Mustard on 2006-04-01
[QUOTE=unbuntu]Thank you for the link.  Well, my goal is to play avi/wmv files on Ubuntu and I've already searched the forum and read several guides, including the "unofficial ubuntu guide", but most of the codec packages need to be installed suggested by that guide are not installable.  Now that I enabled universe and multiverse, it still says that some dependencies are not met.


Sorry...I was just wondering if I am on the right forum, since there's no views even after 10-15 minutes of my original post.[/QUOTE]

When you read the 'unofficial guides' make sure you check out the links in each instruction.  For instance if it is telling you how to setup codecs, it normally comes with instructions on how to enable repositories too.  For instance, using this guide as an example [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu) take note of the comments in bold that I have added below.  These first parts are not there for show.  They are meant to be read. :)

[quote=unofficial guide 5.10] How to install Multimedia Codecs

    * Read #General Notes  **<---These notes are important**
    * Read #How to add extra repositories **<---This is very important**

sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
sudo apt-get install w32codecs
gst-register-0.8
[/quote]

This guide above adds 'extra repositories' other than the just the universe and multiverse.  It also adds the Penguin Liberation Front repositories, so that you can download the w32codecs.  Without this repository being enabled their instructions won't work.

If you want to see the official guide on how to do this ( including instructions on w32codecs) try this link...

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by unbuntu on 2006-04-01
[QUOTE=Mustard]After you change your sources, you generally need to hit the 'reload' button in Synaptic, or you can close Synaptic and do it from the command line using...

```
sudo apt-get update
#this command updates the package list from online repositories
```[/QUOTE]

Well...it seems the problem is fixed.  Since the apt-get sources I have are Canadian sources, and apparently they don't have some of the packages(...), now I changed /etc/apt/sources.list to the one suggested by the starter guide 
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
and I can install these packages.  Thank you anyway.

---

### Post by Mustard on 2006-04-01
If you get errors and unmet dependencies, then you should post the actual error messages and we can take a look at them and see what the problem might be.  In this particular case I think the problem is you are getting ahead of yourself and not reading the instructions completely.

---

### Post by Mustard on 2006-04-01
[QUOTE=unbuntu]Well...it seems the problem is fixed.  Since the apt-get sources I have are Canadian sources, and apparently they don't have some of the packages(...), now I changed /etc/apt/sources.list to the one suggested by the starter guide 
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
and I can install these packages.  Thank you anyway.[/QUOTE]

I hope you are using 5.04, because that sources.list in that guide are for 5.04 Hoary Hedgehog release.  You could be creating a real problem for yourself if you are using 5.10 Breezy Badger release. :)

The updated 5.10 Breezy Badger unofficial guide is here.. [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

---

### Post by unbuntu on 2006-04-01
[QUOTE=Mustard]I hope you are using 5.04, because that sources.list in that guide are for 5.04 Hoary Hedgehog release.  You could be creating a real problem for yourself if you are using 5.10 Breezy Badger release. :)

The updated 5.10 Breezy Badger unofficial guide is here.. [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)[/QUOTE]


Geeez...anyways, I've updated that, and hopefully it won't be a problem...at least I've got mplayer installed :)

Thanks man.

---

### Post by Mustard on 2006-04-01
[QUOTE=unbuntu]Geeez...anyways, I've updated that, and hopefully it won't be a problem...at least I've got mplayer installed :)

Thanks man.[/QUOTE]

So just to confirm in my mind what is happening.  You have changed the sources.list back to Breezy Badger 5.10 sources.list now (the sources.list from the latest unofficial 5.10 guide)?

If so thats good. :)  You don't want to be mixing old stuff from 5.04 with the new stuff in 5.10.  I'm surprised it didnt start telling you that it was going to uninstall half your system. :)

---

### Post by unbuntu on 2006-04-01
[QUOTE=Mustard]So just to confirm in my mind what is happening.  You have changed the sources.list back to Breezy Badger 5.10 sources.list now (the sources.list from the latest unofficial 5.10 guide)?
[/QUOTE]

That's right.

---

