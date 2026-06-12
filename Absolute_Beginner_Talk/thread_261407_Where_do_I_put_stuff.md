---
title: "Where do I put stuff?"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by mr. quippy on 2006-09-20
Hmm.. This file system looks elegant, but very difficult. Lots of folders with very short names to memorize!   

I have just downloaded and extracted the eclipse development environment (which seems to execute quite happily from the desktop) and am now wondering where to put it. Also wondering where I put my files (songs, documents, etc). So far everything is either in desktop limbo, or in a folder in the file browser  that is convieniently named after me. 

In rough terms, could someone please explain what equivalent of the "My Documents" and the "Program Files" folders in Windows is? Or perhaps link me to a slightly more complicated intro? 

Much appreciated :)

---

### Post by elpuerco on 2006-09-20
Create a load of folders in you home folder, data, music video etc and away you go.

I was told to install apps into /opt

Sure someone else will expand

---

### Post by mr. quippy on 2006-09-20
> **elpuerco said:**
> I was told to install apps into /opt
Hmm.. Just tried to copy the elipse/ directory into /opt/. no dice. Apparently I don't have the permission to do so. I know you can use sudo to get past this, but is there any way to use sudo while in the GUI?

---

### Post by undertherift on 2006-09-20
I asked this question when i started.  "WHere the heck is program files on my Ubuntu Linux Unix system?" :)  

The answer is simple - and the reason why you can't find the answer...  
There isn't a "place".  Most people have their own methods.  Some like doing it in the home directory (/home/*/).  I've been using (as per the recommednations of others), /usr/local/.  Just by convention.

A little bit of elaboration - as i understand it, you can trace back commands using two commands - Which, and Whereis.
for example...
```

vik@ubuntu:~$ which vi
/usr/bin/vi
vik@ubuntu:~$ whereis vi
vi: /usr/bin/vi /usr/bin/X11/vi /usr/share/man/man1/vi.1.gz

```

Note: Those are links.  (Shortcuts, if you will.)  When you get to that directory, typing ls -l will show you what those links point to.  This way you can see where all the things point to, and how the general file structure is.  

I've found that links to your basic commands (the ones like ls, rm, ...) reside in /bin or /sbin.  Globally run applications (emacs, vi..) will reside in /usr/bin.  

I hope this helps - i've learned alot of this the long way while fighting with systems.  Hope this helps!

---

### Post by bluefrog on 2006-09-20
my document is your home  (/home/your-user)
there you do what you want.

Other folders in the filesystem are not important to know for a simple user (you will get to learn what they do if necessary with a bit of time)

to install program you may have to sudo if installing from command line.
Otherwise in general try to see in synaptic (program/packet manager) if you can find what you want to install. it will be simpler to begin with.

James

---

### Post by slimdog360 on 2006-09-20
I believe you can get eclipse from synaptic which will do it for you, but as an aside you should check out the top link in my sig if your a bit sketchy on the file system etc.

---

### Post by 3rdgear on 2006-09-20
> **mr. quippy said:**
> Hmm.. This file system looks elegant, but very difficult. Lots of folders with very short names to memorize!   

I have just downloaded and extracted the eclipse development environment (which seems to execute quite happily from the desktop) and am now wondering where to put it. Also wondering where I put my files (songs, documents, etc). So far everything is either in desktop limbo, or in a folder in the file browser  that is convieniently named after me. 

In rough terms, could someone please explain what equivalent of the "My Documents" and the "Program Files" folders in Windows is? Or perhaps link me to a slightly more complicated intro? 

Much appreciated :)

There is no equivalent in linux to the windows folders. Your home directory is /home/(yourname). Create folders to put your files in, not sure where to find program files, although, I managed to browse through my filesystem and found a folder with many programs in it. couldn't remember which one.

---

### Post by mr. quippy on 2006-09-20
> **slimdog360 said:**
> I believe you can get eclipse from synaptic which will do it for you, but as an aside you should check out the top link in my sig if your a bit sketchy on the file system etc.
Can't use synaptic due to ISP limiting my bandwidth. In order to avoid getting capped, I've gotta download from them. I can't install the JRE to see your tutorials for the same reason, although I'll be sure to download everything from synaptic overnight the second I finally do get capped ;).

---

