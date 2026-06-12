---
title: "Automatic shutdown of Firefox"
date: 2005-06-11
forum: Absolute Beginner Talk
---

### Post by Kapre on 2005-06-11
Hiyall!!

Can someone please help me? My firefox automagically shutsdown when I'm visiting some websites (actually my kids when they are playing some game on miniclip and other kid sites).

Is this somekind of a bug or something? ](*,) 

Any info would be very much appreciated.

Ke

---

### Post by Njall on 2005-06-11
[QUOTE=Kapre]Hiyall!!

Can someone please help me? My firefox automagically shutsdown when I'm visiting some websites (actually my kids when they are playing some game on miniclip and other kid sites).

Is this somekind of a bug or something? ](*,) 

Any info would be very much appreciated.

Ke[/QUOTE]
 Which version of Firefox?  

Are there any error messages?  

Do you have Sun Java installed?  (look for /usr/lib/j2re1.5-sun)

What web site and game(s)?

---

### Post by Xian on 2005-06-11
Also make sure the flash plugin is properly in place.
That will shut FF down in a heartbeat.

---

### Post by poofyhairguy on 2005-06-11
[QUOTE=Kapre]

Is this somekind of a bug or something? [/QUOTE]

Kinda. It more like flaws on Firefox's part. I bet their sitesare Flash heavy- flash can lock up some firefox. I advise:

A. Installing Epiphany . It uses less resources than Firefox and doesn't crash as much.

B. Install Galeon. Same thing as epiphany.

C. Use WINE to install IE

---

### Post by desdinova on 2005-06-11
Id go for Opera before IE tho ;-)

---

### Post by Kapre on 2005-06-11
Whoa! This really is the Linux of choice! Thank you everyone!!  :)  :)  I've never had this kind of a response from other forums (when I started using linux)....

Just to let you know, I'm using Ffox 1.0.4 (which is the latest?? - been upgrading it thru the repos). There was no error (just straight shutdown [as if you clicked the "x"]). I did not install the Java plug-in (is this necessary?).

I've checked the Opera website and Galeon website. Seems like I'll go with Galeon  since it is part of Gnome. Question is how would I install it? (should I make this as a new thread?). 

I'm new to linux (even though I've been trying it for almost a year now [from RH9]) but can't seem to get the xperience to install packages which is not part of the distro (I downloaded gdesklet 0.35rc1 last night and cant get it to work {it just went to my desktop after I unzipped it and cant get it to work}).

This is getting to be a novel now....Again thank you very much and I hope I can get my friends to install and use this extra special distro....  \\:D/ 

Kapre :smile:

---

### Post by jdong on 2005-06-11
Firefox 1.0.4 is a package from the Ubuntu Backports Project. I have received other complaints about this, too ([http://ubuntuforums.org/showthread.php?t=41031)](http://ubuntuforums.org/showthread.php?t=41031)). If you can give me a list of sites where this crash happens, that'd be great, because I can't reproduce it!

---

### Post by Kapre on 2005-06-11
Jdong,

It happened on Miniclip.com; edheads.com and it also happened one time while I was browsing on ubuntu website.

Kapre

---

### Post by jdong on 2005-06-11
Both sites use Flash... that's something in common. What method of installing Flash did you guys use.

Can you run firefox from a Terminal, then get the output (if any) upon crashing?

---

### Post by Kapre on 2005-06-11
I used the synaptic pkg manager to install the plugin.

How do I do the running of Ffox in terminal (i'm very sorry - I'm still a nooby)?  ](*,)  

Kapre

---

### Post by jdong on 2005-06-11
Sorry about all of the trouble this is causing; now, it seems that it's a Java problem. In the other thread, I'm getting a more seasoned Linux user to try a couple of commands/methods of fixing this.

Once I find a solution with them, I'll relay that to you. For now, I don't want to put you through this pain ;)

---

### Post by Kapre on 2005-06-11
THANK YOU!!! 

That is why this Distro ROCKS!!! Because of people like you (and everyone in this forum). I've been with Ubuntu for 2 weeks now but with the support that I'm getting I dont see a reason going back to M$.

Kapre

---

### Post by jdong on 2005-06-11
We're all glad to hear that. Please hang tight while I try to figure out what's wrong with the Firefox package.

---

### Post by poofyhairguy on 2005-06-11
[QUOTE=Kapre]I used the synaptic pkg manager to install the plugin.
[/QUOTE]

Thats how you install the other browsers as well. In fact, I advise epiphany over galleon because it is basically a newer version (the person who made galeon quit to make epiphany. Epiphany is the "official" browser of Gnome.

For future reference, until you move bast the novice level in Ubuntu, use synaptic to install EVERYTHING!!! Its hard to get source programs to work. There are few nice graphical "next,next,next" installers in Linux.

---

### Post by jdong on 2005-06-13
Ok, after a bit more debugging, we've almost conclusively shown that this behavior is caused by a recent Linux kernel update.

A bug report has been filed:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=11824](https://bugzilla.ubuntu.com/show_bug.cgi?id=11824)

I'll keep you updated on the situation, with a possible workaround soon.

---

