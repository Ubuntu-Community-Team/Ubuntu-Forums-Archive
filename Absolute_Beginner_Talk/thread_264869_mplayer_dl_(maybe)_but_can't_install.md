---
title: "mplayer dl (maybe) but can't install?"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2006-09-25
[FONT="Comic Sans MS"]Greetings again from big dummy. I've been trying to get mplayer but without success. I thought I had downloaded it but can't find it with terminal (don't know how) but something is showing in file browser ; "index?.html.1" and "mplayer.download.html"
neither of which are of any clarity to the likes of me.
I tried to use Automatix and also Syn Pac Man but couldn't find any result.](*,) 
Probably something obvious, but I don't know where to begin looking. I have tried the wiki site and searched this forum, many entries of which are beyond my limited understanding, although that is improving [slowly].
Thank for all your help everyone, its really great to have help that actually makes things work, especially so after the windows experience.[/FONT]

---

### Post by deadgobby on 2006-09-25
Mplayer should be in synaptic, but if you just open up the terminal and just type in 
mplayer

gobby

---

### Post by jonathan21 on 2006-09-25
we all have our prferrences but i personally think vlc is better for watching movies and listening to music.you can find vlc in add and remove programs.also mplayer should be listed there.have you installed mplayer yet.if it installed just look in applications  under sound and video for mplayer.if its not there its best to install it from add and remove programs
hope i have helped and welcome to ubuntu.

---

### Post by carloslosgrande on 2006-09-25
Thanks Gobby but i actually did try that and got nothing, also tried variations to see if I was just syntaxing wrong but no joy.
Thanks also, Jonathon21, I looked there already and found nothing, but more to the point, I have VLC but it isn't working at all well for movies so I haven't really done much with it, which is also why I was trying to get mplayer. Maybe it would be easier to tweak VLC?

---

### Post by deadgobby on 2006-09-26
Well to view DVd movies, I use ogle myself. Once installed, just type ogle
in the terminal.
GObby

---

### Post by Phosphoric on 2006-09-27
I don't think mplayer is available in the repositories at the moment.  I've been trying to get it for a few days now with no success.

Can this sort of thing happen?  Is it pulled for some reason or is the file broken?

---

### Post by meborc on 2006-09-27
```
sudo apt-get update
apt-cache search mplayer
```
will show that the package is there... to install:
```
sudo apt-get install mplayer
```
after that just
```
mplayer [url|path/]filename

```
to start it

PS how to add extra repositories and how to install/find A LOT of stuff, check the dapper guide in my sig :)

---

### Post by Leeghoofd on 2006-09-27
I had issues while downloading Mplayer through Synaptic.
I managed to install the thing with Automatix tho.

Or you could just run VLC as an alternative, which seems to be working better anyway. ( altho this last part is just a very personal oppinion. )

edit: i just read that you already tried automatix and synaptic aswell, but perhaps you might want to be a bit more specific as to what error message you are getting there..

---

### Post by Malta paul on 2006-09-27
If its any help I find VLC works great, I also use Totem 1.4.3 using xine-lib ver 1.1.1.  Both play my DVD's no problem.
Have fun, Paul:)

---

### Post by carloslosgrande on 2006-09-27
Hi all, I don't get error messages other than file not found. So I've deleted what i had and have downloaded again from another mirror. i seem to have all the files and I've read thru their instructions again but still can't follow it! It seems to miss what is the most important part for me, ie Install.
I've got VLC and it doesn't do ANY video, so its obviosly missing something too. I've got Gxine as well but it jumps all the time.
I appreciate your help, thanks.](*,)

---

### Post by Phosphoric on 2006-09-27
Thanks for the heads up on the extra repositories, meborc.  I thought I had them all enabled but obviously not.  Now have mplayer installed and am trying to get to grips with it.

---

### Post by Leeghoofd on 2006-09-27
Still doens't explain why you couldn't download mplayer with automatix as that programm defines its own sources. ( one of the things that make it a security hazzard btw )

Anyway you got mplayer working so i guess this thread is more or less running at its end..

Still i'd recommend giving VLC another go, since its easier to use than mplayer. The reason for VLC not displaying video is probably that you have not installed the proper codecs. The proper codecs can also be downloaded with automatix. This might also solve potential other problems with other media players ( such Totem, kaffeine etc )

Good luck

---

