---
title: "Windows user has trouble installing programs"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Witling on 2007-09-08
Alas, I am thinking of saying goodbye to Linux and Unbuntu.

The Ubuntu installation worked wonderfully. But adding programs is a complete mystery to me. For me to add Thunderbird to a Windows installation I go to Mozilla, download Thunderbird (or just plain old have it installed on the fly), expand the zip file if I've downloaded it and choose Setup. I've got Thunderbird installed.

In Ubuntu I go to [http://www.mozilla.com/en-US/thunderbird/](http://www.mozilla.com/en-US/thunderbird/). Doesn't seem to matter whether I try to install this on the fly or download it. I get a downloaded file called Thunderbird-2.0.0.6.tar.gz. If I click on this I get a list of files. Anything called setup? No! Anything else that suggest to me, as a Windows kind of guy, which file starts the installation? No, not as far as I can see.

Now I don't expect Linux to work like Windows. And, I'm mindful of the fact that everything is easy if you know how to do it. But, installing new programs is overwhelming hard (or mysterious) for a Windows user.

Now clearly, this is a full grown operating system and new programs can be installed. But, from my point of view, what an aggravation. How about just clicking on an installation file and having it done. I can do this in Windows but when I go to the Mozilla site and say, “Install,” I don't see Bo after the “Install this Sucker” process.

The fault does not lie in Linux. But, dang nab it. Do I want to learn two of the world's complicate operating systems or just one?

And as for Evolution, it double files every incoming message in Junk and Webshots. Sigh!Solved

---

### Post by theredcross on 2007-09-08
Can't speak for evolution, but what you need is a good old fashioned package manager. I'm assuming you're using default ubuntu, i.e. Gnome, so Synaptic is your buddy. If it ain't in there, automatix hasn't let me down yet.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Synaptic_Package_Manager](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Synaptic_Package_Manager)

Ubuntuguide is a good place to go for questions you thought you ought to know, I still use it pretty often for little things I forget. Aaaanyway, have fun with that, and best of luck. It starts making a lot of sense when you get in the groove.

---

### Post by -SpaZ on 2007-09-08
Thunderbird is in the repos, you know that right?
```
sudo aptitude install mozilla-thunderbird
```

---

### Post by Tyke91 on 2007-09-08
you can easily install most things in ubuntu through one of three sources

The command line, open up a terminal and type
```
sudo apt-get install ***********
``` where the stars are the name of your program

The synaptic package manager
go to System>Administration>Synaptic Package Manager and install it from that

if synaptic is scary at first, go to Applications>Add/Remove Programs. Unlike windows, it will add programs too... ALOT of programs.

thunderbird can be downloaded and installed with any of these three sources



EDIT: sorry, i should have used 

```
sudo aptitude install *********
```

apt-get and aptitude do pretty much the same thing, but aptitude is better at handling the packages than apt-get is

---

### Post by steveneddy on 2007-09-08
Why didn't you just ask how to install a tar.gz file?

Seems easier than crying about it, doesn't it?

Maybe you would have good by looking in Synaptic.

---

### Post by Witling on 2007-09-08
Ah, StevenEddy, "Why didn't you just ask how to install a tar.gz file?"

Would that I knew how. As I said, everything is simple if you know how to do it.

For the others who replied, Thank you. I'll work through the messages. I want to go with Linux but learning new skills has the potential to be aggravating. StevenEddy, get a grip on yourslef.

---

### Post by oldos2er on 2007-09-08
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by dpar on 2007-09-09
When using Linux, forget you ever knew about Windoze. Once you get your head around it, Linux is WAY,WAY easier to install programs with.

---

### Post by Witling on 2007-09-09
Solved, using one of the package installation programs, as suggested. 

I repeat, I don't expect Linux (or Ubuntu) to work like the popular Redmond Washington operating system, but, it can be frustrating.

Thanks for the help.

---

### Post by BatsotO on 2007-09-09
yes, tar.gz can be frustating, but mostly there's alternate installation package, rpm for red hat family, and deb for debian family including ubuntu, but the simplest way would be using synaptic. tar.gz is not so bad once you get a grip on it. if everything is easy, there is no more fun.

---

