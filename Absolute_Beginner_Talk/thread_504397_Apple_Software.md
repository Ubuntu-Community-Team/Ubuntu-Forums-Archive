---
title: "Apple Software"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Sabayenda on 2007-07-19
This is my very first post, so, whatever.
Since linux and OSX are both Unix based, and OSX has the capabilities of running linux programs, is it possible for me to run apple software in Feisty?  I know a lot of people will think I'm crazy for asking this, but I really, really, really, REally want to run iTunes because I've tried all the music programs that came with ubuntu, and (no offense) they kinda really suck.  I can hook up my iPod fine, and take files off (which IS cool) but I can't really get music ON to my iPod, and I've tried Amarok (which always, always crashes, it never even gets to import my library, it just crashes everytime) Rythmbox doesn't crash, but it doesn't support iPod, and also, none of these are able to access iTunes music store.  I tried a trial version of  a program that ran windows software and it advertised iTunes, which is why I installed it, but it was iTunes version 4, and it refused to connect to the music store, so I deleted it because I felt gypped.  So....
I know I said a lot, but my question is:

Is there a program I can install in feisty that will allow me to run itunes for mac?

---

### Post by misfitpierce on 2007-07-19
Firstly they dont suck... iTunes sucks... Secondly... no. You could try running iTunes through Wine if you would like but thats about it. Apple is greedy by taking from the open source community and never giving back iTunes, Safari or Quicktime like they do for windows.

---

### Post by Kobalt on 2007-07-19
If you really want iTunes that badly then you should try to run the Windows version through wine, like misfitpierce said, but the only thing it has that (for example) Amarok doesn't have is the iTunes music store. And don't get me started on what Amarok can do and iTunes can't...
I have an iPod and I sync it with Amarok just fine, without a crash (even though I use an unstable version of Ubuntu!). I really think you must be doing something wrong here.

---

### Post by Sabayenda on 2007-07-22
well, I have a fresh install of Ubuntu, and I didn't even bother to install Amorok this time because it was so terrible, it never got past trying to import my library....so it was completely useless. i like rhythmbox better because it imports my library with no problems, but it does funky stuff to my iPod, deletes playlist listings ( the playlist is still there, but nothing on the list) deletes all my star ratings, messes up my smart playlists (which I absolutely love)  and makes near impossible to put my iPod to sleep.  So that's why I say they suck.
I'm still using Ubuntu, I love it so much, just this one issue is driving me nuts, if I could get it resolved my computer would be perfect and I would love it even more.   
Until then, I'll just have to save up for a mac(which wouldn't have this issue), cause no more windows for me! sorry

---

### Post by aktiwers on 2007-07-22
Take a look here:
[http://frankscorner.org/index.php?p=itunes6](http://frankscorner.org/index.php?p=itunes6)

Or check some of these apps out:
[http://www.getdeb.net/category.php?id=1](http://www.getdeb.net/category.php?id=1)

There are some players and Ipod apps there.

---

### Post by RomeReactor on 2007-07-22
Hi. Have you tried [gtkpod]("http://www.gtkpod.org/about.html")? you can find it through Synaptic/Adept. If you want AAC and MP4 support, install **gtkpod-aac**. For either of those install also the suggested packages (right-click on **gtkpod** or **gtkpod-aac** once you find them in Synaptic, and  click on the packages in **Mark Suggested for Installation**; or to install from the terminal/konsole:
```
sudo apt-get install gtkpod mp3gain recode
```
or
```
sudo apt-get install gtkpod-aac mp3gain recode
```

Also, you haven't specified if your desktop is Gnome (Ubuntu) or KDE (Kubuntu).

---

### Post by vanden12 on 2007-07-22
I heard very good thing from banshee and  Exaile.. Tho it would be nice to see the ITMS ever once in a while...

---

### Post by Sabayenda on 2007-08-08
ok, I installed gtkpod, and it seemed like it was just what I needed. Everything looked okay in the  program, I said save changes, it 'wrote' to my iPod, and I unmounted it.
Then I go to my playlists, and instead of giving me empty playlists like in Rhythmbox, it completely deleted all of my smart playlists, and I even made a new one in gtkpod....GRRRRRR!
I'm pretty sure I did everything right, it doesn't make sense to me why a program that is supposed to do something does the complete opposite...

---

### Post by arbulus on 2007-08-08
> **Kobalt said:**
> If you really want iTunes that badly then you should try to run the Windows version through wine, like misfitpierce said, but the only thing it has that (for example) Amarok doesn't have is the iTunes music store. And don't get me started on what Amarok can do and iTunes can't...
I have an iPod and I sync it with Amarok just fine, without a crash (even though I use an unstable version of Ubuntu!). I really think you must be doing something wrong here.

I disagree.  
I've been trying to run Amarok and have had no success.  It's VERY slow to launch, and it took 3 tries before I could get my library loaded (it kept crashing and would actually freeze my entire system so that I had to reboot to fix it).  Once I finally got my librarby loaded, whenever I actually do anything like try to play songs or get album artwork, it crashes. 

I really want to use Amarok, but it is very, very unstable.

---

### Post by Sabayenda on 2007-08-15
Vanden12, Banshee is great! It's very much like iTunes, lets me search and it syncs with my iPod! Now I don't have to use windows ever again!!! I'm so excited!

---

