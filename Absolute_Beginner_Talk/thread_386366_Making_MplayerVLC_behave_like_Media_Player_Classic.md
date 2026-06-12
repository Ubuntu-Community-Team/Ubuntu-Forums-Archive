---
title: "Making Mplayer/VLC behave like Media Player Classic"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by kinson on 2007-03-16
Hi guys,

I'm just about to format my Ubuntu to reinstall Ubuntu(?) :P ...mainly cause I wanna repartion and reformat the drives to a different file system, and I wanna muck around from the start again anyways :P

Since I was starting over, I wanted some help with mplayer or vlc. Right now I've been more or less satisfied with those 2. But they don't behave quite like my favourite media player classic.

Some of the things I'm looking for are:
1)1 screen. Unlike mplayer which has a seperate dialog for controls(which takes up 2 icons on my taskbar, it gets cluttered very fast. Especially when I have like 5 videos open or something(I don't wanna use a playlist), there'll be like 10 dialog boxes down there :(

2) Space bar pause and click on the screen(video) to pause. I loved this feature :) Whenever somebody talked to me when I was watching a video, I could just *click or hit spacebar and listen. rather than poke around for an icon :(

3) real media *.rm files. I'm not sure its whether cause I'm using AMD64 version of Ubuntu(I plan to format to i386), and i didn't install the codecs properly, but mplayer doesn't always seem to play it.  And when it does, and i try to seek, it goes back to the beginning of the video :(

So I was wondering whether anybody knows of any skins/plugins to make it function(at least in interface terms) like media player classic. It'd make my life a lot easier when viewing videos :P I poked around the forums and couldn't find anything :(

In all honestly, I'm sorely tempted to install Kubuntu, as KDE sometimes seems very interesting. But since I'm still rather fresh, I guess I'll be sticking to Ubuntu 6.06 for the mo :p

Cheers and thanks in advance, :)
Kinson.

---

### Post by mills on 2007-03-16
have you tried movie player

it has just the one screen, can puase with "p" or right click on screen but not sure about your 3rd requirement

ps.. kubuntu isnt that scary to install.. i was shocked at how simple it was. took about 5mins and a few clicks

---

### Post by kinson on 2007-03-25
Sorry for the late late reply. I forgot to set the instant email notification, and thought nobody replied, :p

Anyways, "movie player" is totem right? I didn't have too good an experience when I used it, but surprisingly, its handling the rm files very well, as well as the seeking. It doesn't seek instantly to the place where I click in the progress bar, but that'd be really really picky. So thanks a lot for the tip :)

Btw, I don't have any fear for installing Kubuntu, in fact I installed it last night, and had a bit of a hassle getting my wireless card to connect to me router. It had a lot more trouble connecting, compared to my Ubuntu. Anyways, I quickly switched back to Ubuntu, and I must say, I'm much happier with GNOME now. But of course, thats just my personal opinion, no biggie :)

I tried installing a skin for my mplayer, but it doens't seem to be working, lol. I'll work on that another time.

I still haven't found a "one media player to rule them all" in Ubuntu yet. Like Media Player Classic in windoze :(

Thanks again :)

Cheers,
Kinson.

---

### Post by kobewan on 2007-03-30
Try xine with xine-ui: 

-It has fully configurable keyboard shortcuts (and I mean fully configurable), and I believe the default pause is mapped to space. 

-Totem uses the xine engine, so it will play .rm files just as well. 

-It's not entirely onescreen, but it's very close. It will give you a player window and a floating control box. Middle-click in the player window, and the controls go away. 

It also has something which makes me like it more than Media Player Classic : onscreen display. When you change the volume or skip around in the file, it will show an overlay similiar to VLC so that it never gets in your way and you don't have to ever leave fullscreen. 

I personally use VLC for everything but .rm, for which I use xine. Xine is, however, the only media player I would even consider using instead of VLC.

---

### Post by eddyr on 2007-04-03
Thanks for the suggestion. Xine is perfect ^^

---

### Post by kinson on 2007-04-06
@kobewan

Thanks for the suggestion :) So far it seems to be doing what I want it to do, short of swapping the floating menu bar(I never understand why people like those things) for the attached one. What I like about Media Player Classic is that in full screen mode, when my mouse moves to the lower part of the video, the controls pop up fromt he bottom..and since the controls are full screen(horizontally), its great for seeking movies...if Its short like those floating ones...just trying to seek *slightly* to the right will make it seek like 10 mins or so.. :p

Anyways, thanks a lot for the suggestion again :) I'll be using Xine for the moment, and hopefully I find a way to get my controls dockable+auto show/hide :)

Cheers,
Kinson

---

### Post by Limitlesschannels on 2007-05-10
I still haven't found a medi player that is nearly as satisfying as Media Player Classic, to me.  I just really dislike that floating menu thing.

---

### Post by kinson on 2007-05-10
> **Limitlesschannels said:**
> I still haven't found a medi player that is nearly as satisfying as Media Player Classic, to me.  I just really dislike that floating menu thing.

Agreed :(

---

### Post by Liet_Kynes on 2008-02-06
> **Limitlesschannels said:**
> I still haven't found a medi player that is nearly as satisfying as Media Player Classic, to me.  I just really dislike that floating menu thing.


There are many things I miss about MPC. But the thing I probably miss most is freely resizing the aspect ratio while media is playing with the numpad. Especially with videos in which the black bars are encoded into the file.

Also skipping around in a file with Keyboard. Ability to change fullscreen resolution to something other than desktop resolution.

Anyone with a suggestion of a MPC replacement? Please not vlc. I don't even like it on Windows (Although I do like the clone video plugin to have the same movie playing on all 4 desktops in Beryl :) )


Oh yes and ho can I forget the most important shutdown when finished :)

---

### Post by aldreis on 2008-02-08
I would recommend [SMPlayer](http://smplayer.sourceforge.net/), a superb frontend for MPlayer, that adds pretty much all of the desired features mentioned earlier:

[LIST][*]Single window interface, if desired. No 'floating menu thing'. 
[*]Can be configured to pause by clicking the video or hitting the spacebar.
[*]Controls do pop-up when you move the mouse to the bottom
[*]Can be configured to resize aspect ratio on the fly using the numpad[/list]

Oh, and it can shutdown when finished. ;)

---

### Post by Liet_Kynes on 2008-02-08
> **aldreis said:**
> I would recommend [SMPlayer](http://smplayer.sourceforge.net/), a superb frontend for MPlayer, that adds pretty much all of the desired features mentioned earlier:

[LIST][*]Single window interface, if desired. No 'floating menu thing'. 
[*]Can be configured to pause by clicking the video or hitting the spacebar.
[*]Controls do pop-up when you move the mouse to the bottom
[*]Can be configured to resize aspect ratio on the fly using the numpad[/list]

Oh, and it can shutdown when finished. ;)

I'm gonna check out smplayer right now aldreis. And thanks for the hint :)

---

