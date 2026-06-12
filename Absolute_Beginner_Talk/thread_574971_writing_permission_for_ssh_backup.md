---
title: "writing permission for ssh backup"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by SVWander on 2007-10-13
I keep beating my head up again a wall trying to backup with ssh. I cannot seem to write correct permissions to back up my laptop. I have tried simple backup with ssh but I always get an error message telling me I lack permission. In the terminal what commands do I use to give it permission? 
Say my server is named simply "server" the file I wish to write to is /home/laptop/ I have tried:
chown -R root:users /home/laptop
chmod -R ug+rwx,o+rx-w /home/laptop
but that doesn't solve the problem.
What am I doing wrong? Oh I tried simply copying a file using nuatilus while connected to the server and get about the same message, so somehow I have to learn how to use the correct commands.
Tim

---

### Post by julian67 on 2007-10-13
> **SVWander said:**
> I keep beating my head up again a wall trying to backup with ssh. I cannot seem to write correct permissions to back up my laptop. I have tried simple backup with ssh but I always get an error message telling me I lack permission. In the terminal what commands do I use to give it permission? 
Say my server is named simply "server" the file I wish to write to is /home/laptop/ I have tried:
chown -R root:users /home/laptop
chmod -R ug+rwx,o+rx-w /home/laptop
but that doesn't solve the problem.
What am I doing wrong? Oh I tried simply copying a file using nuatilus while connected to the server and get about the same message, so somehow I have to learn how to use the correct commands.
Tim

It's not entirely clear from the above description what you want to do but it seems you want to back up files from your laptop to your server?  Or are you trying to back up files from the server to the laptop? /home/laptop/ is on the server or the laptop? "simple backup" refers to an application or is your description of what you're doing? It's better to explicitly specify things that may seem obvious to you or people will offer advice based on false assumptions. 

But anyway you probably should be looking at using a tool such as rsync either with its own daemon or in conjunction with ssh with key authentication. It's actually pretty easy but you need to read the rsync man page. rsync is perfect for incremental back ups across a network.

---

### Post by SVWander on 2007-10-14
> **julian67 said:**
> It's not entirely clear from the above description what you want to do but it seems you want to back up files from your laptop to your server?  Or are you trying to back up files from the server to the laptop? /home/laptop/ is on the server or the laptop? "simple backup" refers to an application or is your description of what you're doing? It's better to explicitly specify things that may seem obvious to you or people will offer advice based on false assumptions. 

But anyway you probably should be looking at using a tool such as rsync either with its own daemon or in conjunction with ssh with key authentication. It's actually pretty easy but you need to read the rsync man page. rsync is perfect for incremental back ups across a network.

julian67, I am not the brightest fish is the sea and man pages confuse me. Do you know a howto that might explain the subject in a manner that I might be able to understand? Also what would be wrong with just copying and pasting these folders to the server. And yes, I am trying to back up my work on the laptop to the server. So that if there is a problem with this laptop I will have a backup of my work. Or in case I decided to upgrade to the later this month. 

Thank you, Tim

---

### Post by julian67 on 2007-10-14
I'm certainly not a natural with lots of this stuff either, being old enough to have gone right through the  education system without even seeing any computer other than a Sinclair Spectrum and starting my working life in a giant filing department...a huge local government department dedicated to just filing bits of paper and microfiche (microfiche was hi tech!) ...not a computer in sight...I then moved into the printshop where I worked with blue pencils, cutting boards, scalpels and offset litho machines and have since spent part of my life working in a photographic darkroom....I'm collecting redundant skills....I'm expecting  computers to be phased out any day now. 

There are several good resources I've used. I can't recommend strongly enough the podcasts at [Linux Reality]("http://www.linuxreality.com/")

> Linux Reality is a podcast aimed at the new Linux user. Our intent is to start from the beginning, and to take it slowly. We will help Windows and Macintosh users learn about the history of Linux, the importance of the principles of free and open-source software, and the exciting Linux community. We will help users understand the differences between Linux distributions and help people with choosing the right distribution with which to experiment. We will demonstrate how users can try Linux without disturbing their Windows operating system at all, and will also walk people through a Linux distribution installation for those that choose to take a more permanent step. In short, we will explain how it works &#8212; in plain, simple, and non-geek terminology.

For a good howto on ssh you can find several here at ubuntuforums with a search. For example [http://ubuntuforums.org/showthread.php?t=30709]("http://ubuntuforums.org/showthread.php?t=30709")

There's a great article about rsync  [here]("http://www.linux.com/feature/117236") and another one [here](http://everythinglinux.org/rsync/index.html)

---

