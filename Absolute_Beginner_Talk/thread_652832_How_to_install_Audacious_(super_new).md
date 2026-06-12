---
title: "How to install Audacious (super new)?"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by koreninja on 2007-12-29
Hello,

First of all I'm new to Ubuntu, I learn fast though.. but..I'm so lost, I have tried the Add/Remove thing but couldn't find audacious in there. I went into the terminal and started typing stuff that it said in the audacious audacious-1.4.5.tgz thing but that didn't do anything (lol),, 

First of all is Audacious right for me? I'm looking for something similar to winamp (streaming radio stations are what I'm after)..

On the Audacious website there are some files, what do I get exactly? And how do I install it? I tried alt f2 and putting audacious-1.4.5.tgz but it didn't do anything.. 

Is there anyway I can tap into my other partition that has Vista on it and use my music from there? 

I'm basically learning Linux for myself, it's not something that I really need but I love to learn new things.. I've been using windows since I was 12 (now 23) and I think it's time to transition over.. :guitar:

Would love some help. Thanks in advance,

KN

---

### Post by zhouxing on 2007-12-29
> **koreninja said:**
> Hello,

First of all I'm new to Ubuntu, I learn fast though.. but..I'm so lost, I have tried the Add/Remove thing but couldn't find audacious in there. I went into the terminal and started typing stuff that it said in the audacious audacious-1.4.5.tgz thing but that didn't do anything (lol),, 

First of all is Audacious right for me? I'm looking for something similar to winamp (streaming radio stations are what I'm after)..

On the Audacious website there are some files, what do I get exactly? And how do I install it? I tried alt f2 and putting audacious-1.4.5.tgz but it didn't do anything.. 

Is there anyway I can tap into my other partition that has Vista on it and use my music from there? 

I'm basically learning Linux for myself, it's not something that I really need but I love to learn new things.. I've been using windows since I was 12 (now 23) and I think it's time to transition over.. :guitar:

Would love some help. Thanks in advance,

KN

Try type this in the terminal:

sudo apt-get install audacious

It should install audacious in your Ubuntu.

[http://acm.buaa.edu.cn/lqs/lyriczilla-old/lyriczilla-plugin-audacious-0.1.44-i386.deb](http://acm.buaa.edu.cn/lqs/lyriczilla-old/lyriczilla-plugin-audacious-0.1.44-i386.deb)

You can also download the lyric plug for audacious from above link.

---

### Post by Sef on 2007-12-29
> First of all I'm new to Ubuntu, I learn fast though.. but..I'm so lost, I have tried the Add/Remove thing but couldn't find audacious in there. 

Audacious is in Add/Remove.   Change the top right box to 'All Available Applications' and type audacious in search.

---

### Post by billgoldberg on 2007-12-29
1. install audacious
system --> administration --> synaptic package manager
Press the search button, enter audacious. Apply 
(you can also install extra plugins there)

It is now installed (applications, sound and video, audacious)

Right-click and mp3 file, click properties, then the tab "open with" and pick audacious there.
(this will make mp3 files open with audacious instead of totem)

---

### Post by koreninja on 2007-12-29
Thanks guys, super fast response.

Is there anyway for me to tap into my Vista partition to listen to the music I have stored there? 

Guess I have a lot of reading to do. :)

KN

---

### Post by zhouxing on 2007-12-29
> **koreninja said:**
> Thanks guys, super fast response.

Is there anyway for me to tap into my Vista partition to listen to the music I have stored there? 

Guess I have a lot of reading to do. :)

KN

From Ubuntu 7.10, you can access your Visa partition freely to read & write, meaning you can listen to music, edit doc, even delete unwanted files (be carefully though). This version of ubuntu has integrated NTFS writer so that you can access NTFS partition without a fuss.

---

### Post by koreninja on 2007-12-29
I get unable to mount and then a ton of code. What I'm doing is going to Places - Computer and selecting the vista drive. Maybe I'm going to the wrong place. I have Ubuntu and Vista on the same hard drive. I just created another partition. It says something about windows is in use.

---

### Post by zhouxing on 2007-12-29
> **koreninja said:**
> I get unable to mount and then a ton of code. What I'm doing is going to Places - Computer and selecting the vista drive. Maybe I'm going to the wrong place. I have Ubuntu and Vista on the same hard drive. I just created another partition. It says something about windows is in use.

To install Ubuntu and Visa on the same harddisk is common but it should be on different partitions. I bet you are dual boot to Vista and Ubuntu. Is Vista installed in driver C?

Sometimes, when you shut down your Vista improperly (sudden power off etc), you can't find or mount Vista drives in Ubuntu. Try to boot in to Vista normally, shut it down normally and reboot into Ubuntu to find out what will happen.

---

### Post by billgoldberg on 2007-12-29
I had the same problem, you need to close vista properly (using the quit button) for it to work. If you just cut the pc power to restart the pc, it could be that ubuntu won't be able to access vista partition.

---

### Post by koreninja on 2007-12-29
Yeah, I am dual booting using GRUB. It is giving me two choices when it fails to mount.  

1: If you have windows then disconnect the external devices by clicking on safely remove hardware in windows taskbar.

2: Use a force option. 

I'm on a Sony VAIO laptop which is horribly picky about the drivers it uses. Everything on the laptop is functioning perfect though (which i didn't expect with Ubuntu due to Sony forcing their drivers), could there be a chance it is pulling from one of the drivers on my Vista partition and thus keeping windows active? I have no idea what I'm talking about, just a shot in the dark. 

But yeah, I always do a clean shutdown when I exit Vista (Start - Restart) then came into Ubuntu. Does this mean I should completely shutdown my laptop then boot into Ubuntu?  

KN

---

### Post by Sef on 2007-12-29
> But yeah, I always do a clean shutdown when I exit Vista (Start - Restart) then came into Ubuntu. Does this mean I should completely shutdown my laptop then boot into Ubuntu?

Reboot does completely shutdown your system.  But once it does, it is set to reboot instead of turning off.

---

### Post by Perfect Storm on 2007-12-29
If you want absolutly install the latest version I wrote a compiling guide: [http://polarbeardk.blogspot.com/2007/11/build-audacious-from-source-710-64bit.html](http://polarbeardk.blogspot.com/2007/11/build-audacious-from-source-710-64bit.html)

---

### Post by koreninja on 2007-12-29
Ah.. Yes!

I shutdown completely from Ubuntu and left my laptop off for a minute then came back and it still wouldn't work. So this time I went into Vista and did a shutdown from Vista and waited a minute. Then booted into Ubuntu and this time it works. It just seems odd that shutting down completely from Ubuntu (my laptop was dead-off) didn't work. That I had to shutdown from Vista though, made it work. Interesting.. 

Anyhow thanks a ton to everyone who responded. :)
Really helpful community, Thanks Guys.

KN

---

### Post by zhouxing on 2007-12-29
> **koreninja said:**
> Ah.. Yes!

I shutdown completely from Ubuntu and left my laptop off for a minute then came back and it still wouldn't work. So this time I went into Vista and did a shutdown from Vista and waited a minute. Then booted into Ubuntu and this time it works. It just seems odd that shutting down completely from Ubuntu (my laptop was dead-off) didn't work. That I had to shutdown from Vista though, made it work. Interesting.. 

Anyhow thanks a ton to everyone who responded. :)
Really helpful community, Thanks Guys.

KN

If you don't shutdown from Vista completely, your NTFS partitions may have some errors so that Ubuntu could not mount them. Now that you are back on track, just remember this tip in case you have the same situation again.

---

