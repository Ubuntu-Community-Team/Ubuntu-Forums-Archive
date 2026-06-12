---
title: "Issues with GNOME terminal &amp; installing apps"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by aeto on 2006-06-23
Hey there folks i was hoping i would nvr have to b so typically-noob & bother u guys down here but oh well tough luck :lol: Am new to linux (ofcourse i am thats y im posting here, no?)..Just started a week or two ago after I got fed up with my XP (actually i got fed up w/ my system). But how my love for Linux started is just like that, instantaneous. 

I don't regret, and will b dual-booting after i get a new machine. Tried Kubuntu, Ubuntu, Fedora, then Ubuntu now. Kubuntu had probs with the package manager, Fedora had some major issues (might b due to faulty DVD burning), and Ubuntu turns out just nice..managed to get my environment to look as good as Kubuntu's KDE. All's well except for a few minor problems i'm facing..Would love it if any1 could help :rolleyes: 

1. Some apps that i downloaded & installed through Synaptic never showed up (in the apps menu, or anywhere i could think of) :???: 

2. I don't see a way to completely erase a DVD RW.

3. Can i actually "burn as MP3"? I know the cd creators can burn "MP3 Formats" but can they create an MP3 CD? Or any app in particular?

4. Something related to (1) but am guessing it might b because of incompatibility with GNOME. I installed KTab but it never showed up. Is it really because of incompatibilty? I can run a few KDE apps though. Are there any other Guitar Pro 4 (or 5) alternatives?

5. 3D apps like Blender & Wings3D are giving me very slow frame rates. Any way to solve that? Even a few simple Linux 3D games fail to provide 2FPS :mad: 

6. There is a way to to browse through my files in GUI and modify contents right? Because by default it can't b done without the terminal. Sometimes i have to rename files with spaces just for moving/copying's sake hahah.

7. How do i save & exit the following?

[IMG]http://img101.imageshack.us/img101/8130/consoleedit1cp.jpg[/IMG]

8. Why isn't the following working?

[IMG]http://img139.imageshack.us/img139/1086/consoleproblem8dd.jpg[/IMG]

Well i think thats about it....FOR NOW :mrgreen: I've heard pretty good comments about this forum so I'm sure there is ample of good help around (and i can already see that after reading through a few threads). Thanks beforehand! (hope this isnt too long/much)

---

### Post by bukwirm on 2006-06-23
1. Some applications (WINE, for example) must be run though the command line. List the specific programs for more advice.

6. Clicking Places > Home will launch the file browser.

7. Look at the bottom of the screen. The '^' charcter means press the control key, and Writeout means save.

---

### Post by catlett on 2006-06-23
Try trhe Debian menu. It will show up under Application as an entry. This menu shows all your installed applications whereas the default gnome menu doesn't. It should install with just this but sometimes you need the second command. If it doesn't show up right away it should after you restart. ```
sudo apt-get install menu
```  ```
sudo apt-get install menu-xdg 
```
As for mp3 applications etc. Browse through Synaptic Package Manager. There are thousands of applications in there. You will find what you want. If you know the command line you can burn iso and such from there with "burn". This is the description. 
> Burn is a program/script written in Python that aims to quickly and
simply make audio CDs and backup of your data. It performs any of its
feature invoking it only once and with one and only one command line.
No previous ISO creation command is needed.

Other than creating audio CDs from .ogg, .mp3, .wav (even together),
copy CDs, create Data-CD (storage, backups, etc.) and create a CD from an
existing ISO image, "burn" does a lot of other things. Among them: compute
if there is necessary free space for temporary files (images and audio
files), warn if size is bigger than CD capacity, manage multisession CDs.

Basically burn features:
  · Data-CD (files and dirs storage)
  · Audio-CD (from mp3, ogg vorbis, wav)
  · ISO-CD (burns an ISO)
  · Copy-CD (copy CDs) That is just one example of an application you might not have known was available. It takes a little bit of hunting but it's worth it. "Burn" is my main burning app now, I burn an iso in the time it takes for others to open up their gui burning frontend.

Good luck. Hope Debian and the advice helps at least a littlP.S. The file browser is called "Nautilus" it can be launched from the panel by hitting on "Places" and then "Home" or "Computer". You can launch it in the terminal just by entering it's name ```
nautilus
``` If you want to browse as root (or administrator in windows talk) so you can change permisions in the "properties" sub section to the right-click menu etc. Enter this to launch as root ```
gksudo nautilus
```

---

### Post by aeto on 2006-06-23
hey thanks guys! that solves almost all the problems..phew. Noticed the Debian menu for the first time..that's really helpful. All my apps are there..Even Kguitar (sorry its not KTab lol). The "^" in the command, i actually thought it was indeed the alt to the "6" key hahah.

Whoa the first time i tried to open up nautilus as GUI root user [8], it failed. But now its alright. Yet the "sudo apt-get <appnamehere>" still isnt working.

Ok abt the WINE thing, i actually just tried that once, following the steps to install Shockwave (thats when i came to [7]. Let's say i open up a certain xyz.exe with WINE. After installation, how do i open the respective apps (the programs, documents etc)? Any command?

Hmm..7, 6, 4, & 1 solved. That leaves 2,3, 5 & 8 (the apt-get prob). 

Can't a DVD RW be erased? It seems that every cd creating app doesnt have that option..erase is only for CD RW. 

The other problem with most audio burning apps is that they write according to time, and not space (now this is what i mean by "burn as MP3". Using up 700MB & not 120min). I'll keep searching for such apps but if any of u have any knowledge, do let me know..Thanks again!

---

