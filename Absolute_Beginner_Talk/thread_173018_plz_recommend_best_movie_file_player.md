---
title: "plz recommend best movie file player"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by a_0000 on 2006-05-09
hi... i am using ubuntu 6.06 beta 2 flight 7 and so far its working really nice :) in the past my installations have gone haywire following the installation of VMWare 5.5 but i havent installed it yet...

anyway can somebody plz recommend any good movie file players similar to MEDIA PLAYER CLASSIC, WINAMP, etc for ubuntu ?? can i "apt-get" anything really easily? btw i dont really like "mplayer" :S

---

### Post by arsenic23 on 2006-05-09
I mainly use [COLOR="DarkRed"]VLC[/COLOR] and [COLOR="DarkRed"]amarok[/COLOR], though I still have to use Mplayer for Windows Media crap.  [COLOR="DarkRed"]Totem[/COLOR] is ok as well, but I get odd side effects with alot of my movies in Totem.

---

### Post by uzi09 on 2006-05-09
for music/audio:
xmms (winamp clone)

for vids, so far the only thing i've had successfully work was xine/totem combo. i've had mplayer work before, but man i had to go through hell and high water to get that running (mplayer leagalities...sheesh).

i think you should be alright with xine if you follow this guide:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28xine-ui.29](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28xine-ui.29)

one thing to note, they didn't bother mentioning divx's and xvids, for them you need a couple of libs. lemme find em and i'll re-edit the post.

good luck (ur going to need it :D)

EDIT: k, so here are couple of the codecs i needed
```

sudo apt-get install libxine-extracodecs libxvidcore4
gst-register-0.8 --gst-plugin-pat=/usr/lib/gstreamer-0.10/

```

i believe that was it, but let us know if you have any other issues getting it up.

ps: the install of xine wasn't as bad as i'm making it sound :S, just that i found it really annonying and having to look for a lot of stuff isn't my favorite thing to be doing....i'd rather be watching a movie! ;) :D

EDIT(2): i guess i should also add, that i chose xine over others b-cuz it plays all the windows formats as well. personally, i think (g)mplayer is a great program, but it is a real pain to get working (on my system anyway). i'm still having a problem with it :S.

---

### Post by Monster_user on 2006-05-09
[QUOTE=a_0000]btw i dont really like "mplayer" :S[/QUOTE]
Funny, since I *Was* going to recommend GMplayer, and the WMP6 (WMP Classic) skin.

Amarok, and XMMS are the best MP3 and non-video multimedia players. IMHO (In My Humble Opinion).

Amarok has a powefull playlist manager, and many advanced features. XMMS has WinAMP 2 skin support, and is very simply by comparison. 

It is very extensible, though.  I added the Goom plugin, a dancing Tux, a volume normalizing plugin, and an Alarm clock. The volume normalizing, and Alarm feature, were the only things I missed from Music Match Jukebox 7. That was a cool player, especially with the "XJ75 Commando" theme. I am working on porting it to XMMS/WinAMP2.

As for Video Players. There are four good choices, and everything else. VLC, Xine, Mplayer, and RealPlayer.

**VLC** = Also touted as the "Quicktime compatible" cross-platform multimedia player.

**Xine** = THE X media player. I don't like the GUI though, it seems a little buggy. The Totem-Xine front-end works better.

**GMplayer** =  the GTK Mplayer GUI.

**Totem** = The Gnome media player. Totem-Gstreamer is poor, since Gstreamer does not support many of the popular codecs. However Totem-Xine works pretty good. 

**Kaffine** = One of the more popular KDE media players.

**Noatun** = The bundled KDE media player, atleast with KDE 3.3... It stinks. However, it seems to be similiar to WMP Classic, in that it plays the video in the Window, and looks like the rest of the desktop. Hmm, Totem fits that description, but does not feel like WMP6. I must be overlooking something.

**KMplayer** = This is my favorite KDE player, for some strange reason. It supports several media players as "plugins". Gstreamer, Xine, Mplayer, and more.

---

### Post by Caligula on 2006-05-09
for music I use amarok, when I was watching movies I was using totem or vlc, for movies i say keep it simple, choose the file and play it, for music I need more...

---

### Post by rajaiskandarshah on 2006-05-13
my 5 year old daughter uses totem-xine, vlc and kaffeine for watching her vcd movies. however we still get the odd vcd which will not play.

---

### Post by skippy81 on 2006-05-13
I would recommend VLC - its very minimal looking, but is actually pretty powerfull.  If you want a no-nonsense player then its the way to go.  The windows version of VLC is by far the best media solution for XP at the moment, since all the other programs are so bloated.

---

### Post by Caligula on 2006-05-13
> since all the other programs are so bloated.

didn't you forget MPC? that's my favourite player for windows.

---

### Post by khushman1 on 2006-05-14
real player is the best plater it can play almost all extensions and it can download updates on its own

---

### Post by patrick295767 on 2006-05-14
I like : 
```
totem
xmms
mplayer 
 
& kaffeine
```
  
Greetz

---

