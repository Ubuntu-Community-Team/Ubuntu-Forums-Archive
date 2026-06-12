---
title: "Optimising ubuntu"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by bohboh on 2006-06-11
I discovered "top" command which tells me how much of my machines resources are being used up.

From a fresh install, is it worth looking into stopping services that i dont need. When i used xp, i would go into the services panel and stop certain services that i knew i would never need therefore speeding up my machine.

Is the same possible on ubuntu?

---

### Post by glotz on 2006-06-11
Sure, see [http://www.ubuntuforums.org/showthread.php?t=89491](http://www.ubuntuforums.org/showthread.php?t=89491)

I disabled for example RAID and bluetooth related items as I don't use em.

---

### Post by Dr. Nick on 2006-06-11
make sure you are reading your "top" results directly.

I explained it some in my 2nd post to this thread
[http://ubuntuforums.org/showthread.php?t=181804](http://ubuntuforums.org/showthread.php?t=181804)

You can disable some services as already mentioned aswell. I think alot of people misread top, I know I used to lol

---

### Post by bohboh on 2006-06-14
I am a linux convert having moved over from XP.

One thing i regularly did in XP was to run a tool called CCLEANER, this trawled my system looking for "crap" which took up space and made the system slow. This included everything from tmp files and directories to redundant registry entries.

Do i need to do the same with ubuntu?

As ongoing maintenance, do i need to be regularly doing anything? e.g. cleaning temp files / directories. Defragmenting. etc

---

### Post by glotz on 2006-06-14
Nope. Ccleaner was a nice tool on windows.

Linux doesn't have a registry to mess up and ext2/3 doesn't fragment, temp files are automatically taken care of. If you're in need for disk space, you might want to clear your package manager cache.

Welcome to the world of Ubuntu!

---

### Post by bohboh on 2006-06-14
[QUOTE=glotz]If you're in need for disk space, you might want to clear your package manager cache.[/QUOTE]

Does that mean doing apt-get clean ?

---

### Post by Dr. Nick on 2006-06-14
yep apt-get clean will erase all downloaded package installers. Its safe to do if you need the disk space.

---

### Post by bohboh on 2006-06-14
I think i am having problems with letting go of the idea that i no longer need to stay on top of "looking after my OS", with xp you needed AV, firewall (which some say you do on ubuntu), spyware, defrag, etc,etc

I think because my pc is so critical as its my source of income, i need to learn to let go. Thtas what years of MS does to you. :D

On a seperate note, i noticed your signature mentions "XGL/Compiz". I have seen the vids and it looks amazing and something i would like to add to  mine. Because i am new to linux and this is by main pc and source of work, can things go wrong? Seems like you have to do a lot to get it to work.

---

### Post by Dr. Nick on 2006-06-14
If you have a nvidia card or possibly ati  and already have the 3d drivers set up then it isnt to bad. It can mess up your computer but if you take precautions and watch what you are doing then it should be easily revirseable.

I  did mine a bit different from the tutorial, I think the way I did it may be easily reversible, I just havent had to try yet.

---

### Post by bohboh on 2006-06-14
Well i did it following this guide:

[http://www.compiz.net/viewtopic.php?id=389]("http://www.compiz.net/viewtopic.php?id=389")

I now have my screens wobblin' about all over the place.

A bit jerky, but a nice toy!:D

---

