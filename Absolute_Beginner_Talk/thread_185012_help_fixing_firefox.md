---
title: "help fixing firefox"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by Mbuhrow on 2006-05-30
](*,) 
Hi. I'm a real linux noob. Besides some playing around with puppy, I've used linux for about four days. Today I wanted to upgrade firefox to 1.5. I tried looking around for an updater, but even the one in firefox said that no upgrades were available. So I downloaded 1.5 from the net. I'm going to make a long story short, I eventually removed my old install of ffx in an attempt to get 1.5 installed, it said that it would also remove some other dependent things, but they didn't look important so I went ahead. Bad. obviously 1.5 didn't work. also now apps-more applications is gone. so I can't install any web browser. I tried using the packages thing (forgot the name) under administrator to reinstall 1.0. when I try running ffx, I get a beige box with big red letters- xml parsing error. I need ffx to work, but it seems I gave myself bigger problems. So is there any way to restore what I wrecked, like a reinstall of the base system or something?
and if I must reinstall ubuntu, how do I do that in the most painless way, without messing up my windows and other partitions? thanks, and yes, I already KNOW I'm an idiot,](*,)  and careless, but I promise I'll never do it again. so please have mercy on me. ](*,)  btw, I'm using ubuntu 5.1
sorry I don't have more specific error messages, I'll get them tomorrow when I get home.

---

### Post by Sef on 2006-05-30
Dapper will be stable in a day (1 June), so just update to Dapper when it comes out.  There will be a button that you click to update Breezy to Dapper.

---

### Post by aysiu on 2006-05-30
I'm going to assume you're using Gnome. If you're using KDE instead, let me know.

It's not as bad as you may think.

First of all, to get back all the default applications, paste these commands into the terminal: ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
``` Then, to get Firefox 1.5, use [this script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5).

---

### Post by Mbuhrow on 2006-05-30
yeah, I'm using gnome. Ok, should I just upgrade to dapper tomorrow instead? and I found that script, but next time I will be sure to search the forums and wiki first, before messing around. thanks again. goodnight.

---

### Post by Mbuhrow on 2006-06-01
Okay, got it. I actually had some errors related to dependencies, a 'sudo aptitude remove firefox', followed by 'install firefox' and then finally 'install ubuntu-desktop' fixed everything. thanks again.

---

