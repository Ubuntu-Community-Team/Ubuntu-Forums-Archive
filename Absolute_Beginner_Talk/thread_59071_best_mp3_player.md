---
title: "best mp3 player"
date: 2005-08-22
forum: Absolute Beginner Talk
---

### Post by evansa4 on 2005-08-22
hi guys does any 1 have a mp3 player for  Gnome please post asap thanks

---

### Post by gammyhand on 2005-08-22
[QUOTE=evansa4]hi guys does any 1 have a mp3 player for  Gnome please post asap thanks[/QUOTE]
 beep rocks.

---

### Post by evansa4 on 2005-08-22
were can i get that from and were can i get the plugins

---

### Post by gammyhand on 2005-08-22
[QUOTE=evansa4]were can i get that from and were can i get the plugins[/QUOTE]
 [www.ubuntuguide.org](www.ubuntuguide.org) will explain plugins much better than me, and search for beep in synaptic to install it :)

---

### Post by evansa4 on 2005-08-22
thanks got new player and plug ins so thanks :-)

---

### Post by cayamara on 2005-08-22
Personally, I like amarok. Its a KDE app, but it still nicely integrates into the notification area of my Gnome desktop. I like it, because it has many features xmms/beep/... lack (IMHO).

Amarok lives at [http://amarok.kde.org/](http://amarok.kde.org/)  ;-)

---

### Post by KingBahamut on 2005-08-22
Amarok, Beep, XMMS, mp3blaster(a personal favorite of mine), mikmod, rhythmbox(nother personal favorite). 

Take your pick.

And actually if your running Gnome, Rythmbox does about the same as Amarok, though not as flashy looking.

---

### Post by xequence on 2005-08-22
I like the default one that comes with ubuntu, rythmbox. I only wish it had two things: ID3 Tag editing and a one second long fade out when pausing or switching songs like on media monkey on windows ;)

---

### Post by 67735 on 2005-08-22
Now that I've landed in the correct forum, can anyone tell me why I can install XMMS, Amarok, and Beep and none of them will play MP3s?

System sounds come out just fine.

Asus K8N Athlon 64 3000 running Ubuntu i386

---

### Post by earobinson on 2005-08-22
[QUOTE=67735]Now that I've landed in the correct forum, can anyone tell me why I can install XMMS, Amarok, and Beep and none of them will play MP3s?

System sounds come out just fine.

Asus K8N Athlon 64 3000 running Ubuntu i386[/QUOTE]
 a simple search on the forums would find this link sir [http://ubuntuguide.org/#xmms](http://ubuntuguide.org/#xmms)

---

### Post by flange on 2005-08-22
[QUOTE=cayamara]Personally, I like amarok. Its a KDE app, but it still nicely integrates into the notification area of my Gnome desktop. I like it, because it has many features xmms/beep/... lack (IMHO).

Amarok lives at [http://amarok.kde.org/](http://amarok.kde.org/)  ;-)[/QUOTE]
 I like Rhythmbox and Muine.

---

### Post by poofyhairguy on 2005-08-22
I like Muine best.

---

### Post by 67735 on 2005-08-22
Ok, I tried all that after your post.  XMMS hangs up and won't go away even after a killall boot to the head.  MP3 still evades me.  I will try again in the morning.
Thank you for your help.

---

### Post by aysiu on 2005-08-22
[QUOTE=67735]Ok, I tried all that after your post.  XMMS hangs up and won't go away even after a killall boot to the head.  MP3 still evades me.  I will try again in the morning.
Thank you for your help.[/QUOTE] You might need to do this.

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by Kapre on 2005-08-22
[QUOTE=67735]Ok, I tried all that after your post.  XMMS hangs up and won't go away even after a killall boot to the head.  MP3 still evades me.  I will try again in the morning.
Thank you for your help.[/QUOTE]
 67735 - try to set youre sound to use ESD (in XMMS or BEEP).

---

### Post by jobezone on 2005-08-23
[QUOTE=KingBahamut]Amarok, Beep, XMMS, mp3blaster(a personal favorite of mine), mikmod, rhythmbox(nother personal favorite). 

Take your pick.

And actually if your running Gnome, Rythmbox does about the same as Amarok, though not as flashy looking.[/QUOTE]
 mp3blaster is cool...
Some years ago I had a old computer laying around, which I used for viewing DVD's on my t.v. with a dxr2 decoder card (when dvd players were very expensive, this was pretty cheap in comparison). Anyway, after some time, it started having problems, etc, so I put linux in there. Since it would be in the living room i thought it should work as a sort of media center, or something, but working only with the keyboard. So I set it up to automatically login, and present a message of the day giving various options. I, or others, could then type the option they wanted, which was just a bash script which would execute a specified terminal application:
web - acess the internet (launched links)
chat - talk to people (lauched bitchx)
listentomusic[or something like this] - launched mp3blaster
getmusic - launched a very easy to use ncurses linux napster client.

The pc's soundcard was connected to the living room stereo, of course.
And that was it. After a while, I also got some games which ran under svgalib, which meant colors and stuff.
So I remember that mp3blaster was pretty cool. I also remember that browsing the net with no graphics was a completely different experience, with no graphics to distract from the real stuff.

---

### Post by 67735 on 2005-08-23
aysiu - That did it.  Thank you for the direction.

I'm learning, slowly learning.

XMMS still hangs up and won't close when I try to open an MP3 file.  It plays on Totem now without issues.

Any ideas about the hangup?

---

### Post by erikpiper on 2005-08-23
[QUOTE=67735]aysiu - That did it.  Thank you for the direction.

I'm learning, slowly learning.

XMMS still hangs up and won't close when I try to open an MP3 file.  It plays on Totem now without issues.

Any ideas about the hangup?[/QUOTE]

I had the same issue.  You NEED to set sound to use ESD. (It is in the optionsmenu) BEFORE trying to play a file.(For me, it crashes and only is fixed with a reboot!! Wierd.

---

### Post by evansa4 on 2005-08-23
thanks guys for telling me the best mp3 player thanks ;-)

---

### Post by 67735 on 2005-08-23
Okay, I looked in the options menu of XMMS and found nothing that resembled "ESD".

I did find a reference to ESD under System, Preferences, Multimedia Systems Selector and "Default Sink" was already set to ESD, but the "Default Source" was set to OSS, so I changed that to ESD and XMMS still hangs.

Realizing I'm a big pain, am I on the right track?  What is "Default Sink/Source"?

Thanks again for everyones' help.

---

### Post by erikpiper on 2005-08-23
[QUOTE=67735]Okay, I looked in the options menu of XMMS and found nothing that resembled "ESD".

I did find a reference to ESD under System, Preferences, Multimedia Systems Selector and "Default Sink" was already set to ESD, but the "Default Source" was set to OSS, so I changed that to ESD and XMMS still hangs.

Realizing I'm a big pain, am I on the right track?  What is "Default Sink/Source"?

Thanks again for everyones' help.[/QUOTE]
 Sorry I can't tell you where it is, but start XMMS, Then visualization plugins. Click the far left tab, and look for a drop down menu. And the next tab, exc. When you come to one, click it, and see if there is an ESD. Select it. The menu should be labled sound server or something.

(My XMMS is broken at the moment......)

It is the best player, I personally think.

---

