---
title: "Installing Software"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by Riyonuk on 2007-01-11
How come when I want to install software from source, it requries a dependiancie, that dependency requires a dependency, etc. Does the chain stop?

If this is the case, is there a place to request a program be in the repositoreies? (Wow I cant spell).

---

### Post by taurus on 2007-01-11
What program do you have in mind here?  You probably need to install those -dev packages first before you can build it.

---

### Post by linuchsan on 2007-01-11
If you install a package from source, you have to read the install howto, before you get any further.

---

### Post by Riyonuk on 2007-01-11
I do, I'm installing Audacious. It requires 3 programs, one of those programs that it requires, requires another program, Im afraid to know if that program requires yet another program.

---

### Post by obsidion on 2007-01-11
> **Riyonuk said:**
> I do, I'm installing Audacious. It requires 3 programs, one of those programs that it requires, requires another program, Im afraid to know if that program requires yet another program.

  You have read this page right ?

[http://www.linuxfromscratch.org/blfs/view/svn/multimedia/audacious.html](http://www.linuxfromscratch.org/blfs/view/svn/multimedia/audacious.html)

---

### Post by Riyonuk on 2007-01-11
Well I just did, it sounds like its saying I dont need GTK, but I do, as "./configure" tells me I do.

---

### Post by obsidion on 2007-01-11
> **Riyonuk said:**
> Well I just did, it sounds like its saying I dont need GTK, but I do, as "./configure" tells me I do.


  Not sure where you are at,or what the package really wants, but try if you haven't already, installing the build-essential package.

---

### Post by PurplePenguin on 2007-01-11
Chasing dependencies does sort of suck, but it's quite rare (for me, anyway) to get something that won't install after I figure out which dependencies are needed.  Just keep trying, and if it complains about something not being there, install that (and any other dependencies which arise due to the new stuff), and try again. :)

This is why I absolutely love Synaptic!! :D

---

### Post by obsidion on 2007-01-11
Have a look at this thread

[http://www.ubuntuforums.org/showthread.php?t=308286](http://www.ubuntuforums.org/showthread.php?t=308286)

---

### Post by Riyonuk on 2007-01-12
Yes, too many dependecys :p, I orginally wanted to post this, but forgot to put it on my usb.

Why is installing software in Ubuntu so cruel?

Alrighty, so here is my situtation. I have one low-end computer with no internet access at my home. I installed Ubuntu 6.10 and all went smooth. I want to download and experience new programs, but of course no internet. I occasionly get internet for 2-3 hours when my neighbor turns on there router, but other than that..no internet. When that time of day occurs, I update Syanptic Package Manager, and try to squeeze in a few programs before my neighbors turn there router off again. So I decided today to go to the towns local library and download some programs on my USB.

I get there and forget they have windows, Yuck! I am suggested in an IRC room (I had to download mIRC, install on the desktop, etc) that Audacious is a good music player. I find the main site from a quick google search and proceed to the download section. What I see is something similar to this...(Keep in mind I'm writing this from memory at my internet-less pc.

--------------------------------
- Core Files -------------------
--------------------------------
- Audacious Stable version 1.0.0
- Audacious Plugin version 1.0.0

--------------------------------
- Dependencies -----------------
--------------------------------
- GTK         1.00
- LibGLADE    1.00
- TagLib      1.00


So I click on the 2 Core files and download them to my USB. I then click on each of the 3 Dependencies, which link me to there respectful sites. I find the programs, all .tar.gz, and download them also. So I'm pretty sure Ill be able to install this program. I walk home (Its raining...oh great u_u) and make it home. I start with GTK, doing the following steps.

- Dragging the .tar.gz archive to my desktop, right clicking it, and selecting "Extract Here".
- Open up a Terminal, typing "cd Desktop/GTK-1.00".
- Then I type "./configure" and it lists lots of text telling me I cant install

I'm like wtf? My PC has to be broken :p, so I proceed to format my hardrive and re-install Ubuntu for me 8th time (Literary, 12 if you count windows, these formats have happened all week). So after 30min, I boot my pc up and try it again. Nothing...so, I go back to the library and ask in the #ubuntu channel. They tell me to install the "build-essential" package. So I navigate on my Ubuntu cd to /pool/b/build-essential and find the deb. I install it and nothing happens...so I try to install audacios again, nothing...I then ask in the Ubuntu forums, and a Mod named "taurus" tell me to do..

- sudo apt-cdrom add
- sudo aptitude update
- sudo aptitude install build-essential

It then tells me that its actually installing programs, I read later that on psychocats, build-essential is a package that tells what other packages to install. I guess from clicking the deb, it didnt install those files. So I'm excited that its going to work this time. I try, and it gives me an error saying glib isnt installed. So now I must hunt down yet another file...it just never ends. Seeing as I cant install that one, I try installing another program, it requires that GTK also, and about 20 other dependances. So why is it .tar.gz cant come with the latest version of there dependencies? Ill be searching all night to find those, while if they were listed in the repositories, I would have did a click and install. Ubuntu is so cruel :(, if that glib requires another dependencie, Im gonna toss my pc out the window, this is just not cool.

Audacious requires GTK, which requires Glib, which will probably require some other program...

And another question for those of you who just have to install from source, otherwise you might die, how are you gonna upgrade? I mean isnt the apt-get dist upgrade using repositores, and not from source?

---

### Post by obsidion on 2007-01-12
Given your situation ie limited access, why go outside the standard repos to install something.
Why not install xmms instead. I downloaded Audacious used it for a while then decided this is just an xmms clone and uninstalled it. I know that if I was in your situation I would be checking out the stuff easily available to me rather than persuing something from outside the system.

---

### Post by Riyonuk on 2007-01-12
Pretty much everything is "outside the system" with no internet. And standard repos dont cut it, the software I want is usually not there. And as you can tell, trying to find all these dependecys is really frustrating and time consuming. They need to make a .ubu that includes the program and the latest dependencys. It seems Linux, IMO, is a OS in which you need Internet...

---

### Post by obsidion on 2007-01-12
> **Riyonuk said:**
> Pretty much everything is "outside the system" with no internet. And standard repos dont cut it, the software I want is usually not there. And as you can tell, trying to find all these dependecys is really frustrating and time consuming. They need to make a .ubu that includes the program and the latest dependencys. It seems Linux, IMO, is a OS in which you need Internet...


  Linux is an OS that is designed to use the internet yes and it is how it developed, why do you expect it to drop this fundamental part of itself to accomodate you?  Audiacious which you are in about is just not superior to xmms or a must given all the other music players available in the repos. You seem to have a fixation with certain software and are determined that this is the only software that works. It isn't .ubuntu has many alternatives and making life difficult for yourself and insisting on some piece of software that is hard for you to get is hardly the way to get to know how linux and ubuntu in particular behaves.
  The whole the piece of software I need is not there attitude, is more like I had this program on windows and now want the exact equivalent on ubuntu, rather than looking at what a program actually does and how it functions you want it to look and behave exactly as it did on windows. It isn't going to happen in most cases and until you get out of that attitude you are going to have a tough time with linux.

---

### Post by Riyonuk on 2007-01-13
Well I think its a good atitude to try some new programs, rather than sticking with safe native ones. I also never knew it was developed for the web, that saddens me. It just makes it somewhat harder to install programs. I installed Audacious and its not that great, just as you said.

---

