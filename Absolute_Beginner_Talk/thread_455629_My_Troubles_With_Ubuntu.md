---
title: "My Troubles With Ubuntu"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by eball on 2007-05-26
First of all, let me say this: in just one version, ubuntu has progressed miles. Last time I experimented with it (6.10), my computer couldn't even connect to the internet via firefox! But even now, there are some issues that are making me boot windows more :S

1. Dual-Screening. I have an ATI x1650 card (*sigh*) and i have not seen a way to dual screen. I do, however, have beryl/xgl running and that is very nice. but it also brings me to the next thing:

2. Damn artifacts! If i do not have a desktop background (which i have still not figured out how to set for my other 3 sides of the cube), all of the nice effects never go away! I can drag a menu down, and as long as its on a transparent background, it will never appear to go away. This could just be bad drivers (proprietary) but the little update icon just came on for the drivers, so well see.

3. Rhythmbox. For being the widest-acclaimed media player, the sound kinda sucks. It has no bass response and sounds muted in comparison to windows media player. I shouldn't have to turn up my sub a lot each time i boot linux. Also it found the media on my windows drive ONCE and can play it if I unlock it, but it wont automatically update the songs/etc so i have to resort to manually opening 4000 songs. Thats not right. And whats with not being able to import playlists?

4. Unlocking Hard Drives. Why do i have to authorize my computer to look at my NFTS windows drive?

those are my only problems with linux, which is otherwise amazing. In my windows box, firefox will crash randomly, along with the rest of the compy. But as music and productivity means a lot to me (along with eyecandy :D), I may have to go back to windows...

---

### Post by Pizzarth on 2007-05-26
1)no idea, sorry
2)just set all the backgrounds to it? don't know about the menu's I guess that might just be how beryl works, only used it a little bit.
3)dunno, I just used amaroK, gnome or KDE. try it, it's nice.
4)...eh? my paritions are just added as media and I have easy access, and can open thigns in order. 

"But as music and productivity means a lot to me (along with eyecandy ), I may have to go back to windows..."

I wouldn't want to go back into windows, myself :)
Media is important to you, me too. I have installed ubuntustudio, which has a great-looking dark-gnome and cool blue icon( just my opinion) and comes with a lot of photo and audio editing and playing software. Applications>>Sound&Video fills up my screen. Only problem I had was that the vesa driver was being used in the xorg.conf file and wouldn't work, but that was a simple problem to fix. Other inconveniences: it's bigger install file, you'll need a DVD, and it's not a livecd. meh, not too troublesome.

Sorry I couldn't be of much help

---

### Post by Znupi on 2007-05-26
1. Same as Pizzarth.
2. Umm... **System -> Preferences -> Desktop Background** should change the background on all desktops. Maybe you're on Kubuntu? About the menus never going away, it must be a problem with drivers, it works perfectly here. (ATI X550)
3. Rythmbox **can** import playlists. **Music -> Playlist -> Load from File**.
4. Same as Pizzarth.

**EDIT:** Might've found what's causing your problem with number 2. Fire up Beryl Settings Manager and go to **General Options -> General Options -> Desktop Background** and if **Desktop manager supports viewports** is checked, uncheck it! I hope this solves it...

---

### Post by eball on 2007-05-29
So most of my problems have been fixed now :D

I switched over to amorok and in the process understood where mounted drives are in the file system. damn i felt dumb as hell. and thanks to znupi, the background issue is fixed :)

but i still cant import windows media player playlists. no media player will take em :S

and heres my vision for dual boxing: have one desktop on each monitor, each with its own cube. I think i have to use Xinerama, but i have no clue. if you know, please help me on that one :)

---

### Post by sloggerkhan on 2007-05-29
there are at least 2 ways to get 2 desktops with ati and xinerama is one of them I suggest a forum search, as there are lots of tutorials on it. Also, you might try ubuntu wikki. I'd tell you except that I haven't done it in a while and I dumped my old xorg.conf files that had it set up.

---

### Post by Brightbelt on 2007-05-29
Eball,
I have an ATI x1650. How did you install your accelerated graphics card driver without your system crashing???

Thanks for any tips, Frank

---

### Post by Znupi on 2007-05-29
> **eball said:**
> and heres my vision for dual boxing: have one desktop on each monitor
Fire up **Beryl Settings Manager** and go to **Desktop -> Desktop Cube -> Options** and look for **MultiMonitor Mode** and select **Multiple Cubes**.

---

### Post by eball on 2007-05-29
@ brightbelt: I just followed the guide at [wiki.cchtml]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") or [wiki.beryl-project]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL") and it set me all up :D

And i selected that and it doesnt effect it

---

