---
title: "[SOLVED] Things to do after installing Ubuntu Gutsy"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-03-06
hello there

is there an alternative to Automatix (which works well for Ubuntu Feisty only, I suppose?), I can use to download the following on my freshly installed Ubuntu Gutsy (I really understand next-to-nothing about computers): 

- Acrobat Reader + Adobe Flash Player 
- all the necessary CODECS for Totem (to play DVDs in particular)
- anything basic that (as you know of) doesn't work "out of the box" when you install Gutsy but that you actually need. 

If such a program doesn't exist, it'd be great if anyone could direct me to any non-technical + for dummies article like "10 things to do after installing Ubuntu Gutsy". 

Many thanks. I really like Ubuntu, and I'm so glad I've finally managed to download it on my HP Pavillion laptop. It works great!

---

### Post by kpkeerthi on 2008-03-06
System -> Admin -> Software Source -> Enable Universe and Multiverse repositories.
Then,
```
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by kpkeerthi on 2008-03-06
You may also need to add [Medibuntu]("http://www.medibuntu.org/") repository

---

### Post by kesman on 2008-03-06
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

Has all the info about these things :)

There's already a pdf-reader in gutsy, and for DVD playback you need to install the dvd-library. There's bunch of stuff in that guide, and very easy to understand.

---

### Post by sanddgroper on 2008-03-06
Hi very first thing I would do is get the 3D graphics drivers working using
synaptic.

Cheers
Sandy

---

### Post by al.adab on 2008-03-06
Many thanks everyone. I really appreciate this.

I did what you suggested, and it seemed to have worked all right (except that I couldn't find any 3D graphics driver, where are they exactly?). 

Still I can't play a DVD. Totem gives me the msg "Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc." plus a link that leads me to a webpage about Gstreamers. 

Can you please tell me what I've got to do to install these Gstreamers? I don't seem to be able to find directions anywhere. 

Thanks again.

---

### Post by kpkeerthi on 2008-03-06
Did you run the command posted here [http://ubuntuforums.org/showpost.php?p=4463108&postcount=2](http://ubuntuforums.org/showpost.php?p=4463108&postcount=2) ?

---

### Post by kpkeerthi on 2008-03-06
See [http://packages.ubuntu.com/gutsy/ubuntu-restricted-extras](http://packages.ubuntu.com/gutsy/ubuntu-restricted-extras)

---

### Post by al.adab on 2008-03-06
Yes, I did run sudo aptitude install ubuntu-restricted-extras and sorry I don't understand what I'm supposed to do with [http://packages.ubuntu.com/gutsy/ubu...tricted-extras](http://packages.ubuntu.com/gutsy/ubu...tricted-extras) ... I've just noticed, by the way, that .avi video files work, unlike DVDs and VCDs. I'm speaking about the same videos I used to play no problem under Ubuntu Feisty (after downloading all the codecs through Automatix). 

On a separate note - unless I should start up a new thread - whenever I run a check on the Update Manager, once it's done it gives me the following msg:

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Any idea? Thanks.

---

### Post by Mauler5858 on 2008-03-06
If you are a windows convert you might find mapping the gnome system monitor to the ctrl+alt+delete key is nice.

---

### Post by Astarroth on 2008-03-06
I have installed Automatix on three Ubuntu 710 machines and it has worked on each of them straight off the bat. Of course I may have downloaded a different version of Automatix than you did.

---

### Post by LuisGMarine on 2008-03-06
What I usually do is think of everything that I do on the computer.  Make a list of hardware that you want to work.  For example, does sound work good, does wireless work good, can I mount my extra hdd , flash working good, java etc, then try to tackle each issue.

Ubuntu is a learning process.  I tend to find that I make lists and try to fix it, and that keeps you learning your system, and make sure you document everything.  This way you can pass on the knowledge to someone new that might be having the same problem, and when you re-install or upgrade if that particular thing breaks, you know off the bat how to fix it.

But like I said, just think of what you do on your PC and what you need and work on getting it.

---

### Post by phil90 on 2008-03-06
> **al.adab said:**
> Yes, I did run sudo aptitude install ubuntu-restricted-extras and sorry I don't understand what I'm supposed to do with [http://packages.ubuntu.com/gutsy/ubu...tricted-extras](http://packages.ubuntu.com/gutsy/ubu...tricted-extras) ... I've just noticed, by the way, that .avi video files work, unlike DVDs and VCDs. I'm speaking about the same videos I used to play no problem under Ubuntu Feisty (after downloading all the codecs through Automatix). 

On a separate note - unless I should start up a new thread - whenever I run a check on the Update Manager, once it's done it gives me the following msg:

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Any idea? Thanks.

Ok for the dvd. It seem like you already have medibuntu's reposity 

install the required package to read the dvds.

sudo apt-get install libdvdcss2


About your  Gpp error it appears you have a out of Sync archive

If so this commands should solve the issue. It was working in Breezy and it seem it still works for newer versions

$ sudo apt-get update -o Acquire::http::No-Cache=True



Hope this is going to help you

---

### Post by steveneddy on 2008-03-06
Try this [web site]("http://doc.gwos.org/doku.php/doc:ubuntu") and[ this site]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy") as well.

These two, especially the second one, will give all the info you will need to get started.

Good Luck.

---

### Post by Therion on 2008-03-06
[Creating Your Ultimate Ubuntu Desktop](http://linuxondesktop.blogspot.com/2007/11/creating-your-ultimate-ubuntu-710.html).

---

