---
title: "Is there anything like VobSub on Linux"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by Amorphous_Snake on 2006-07-26
I have been trying to get subtitles for AVI file (XVIDs and DIVXs) to work properly. I need a program that is independant from a media player, just like VobSub. The media players I have for Ubuntu are not good with handling subtitles. This includes VLN and MPlayer. Totem doesn't run subtitle files.

I need a program that recognizes IDX/SUB and SRT file types. Also, on Windows, VobSub could read from the IDX/SUB file combo even if the SUB file is RARed (to reduce size, to make them fit on a 700 MB CD). Also, I want to be able to change font size, colour and add effects like shadows.

In short I need VobSub!!!

Help!

---

### Post by arochester on 2006-07-26
Avidemux?

---

### Post by vitesse on 2006-07-26
I think the only way is to translate from sub format to srt.

Mplayer load and play srt. files.

You could use subrip to subtitle decoding. But it's a pain, because you hafta doit manually.

And works only on Windowz.

Peace!

---

### Post by Amorphous_Snake on 2006-07-26
Arochester: Thanks, but I want a program like VobSub not like VirtualDub, but thanks anyway because I was going to ask this question someday!

Vitesse: I want something that will use the subs that I already have, and I want it to be on Linux. I have VobSub on Windows. Read my question please.

---

### Post by Amorphous_Snake on 2006-07-28
Hello... Can someone help me?

---

### Post by flamarro on 2006-07-28
Hi,
like me, this is a must for me, handling subtitles in ubuntu, that keeps reminding me about BSPlayer. Its been a pain in the ***.
All the players you talked about read subtitles, VLC, MPLAYER, TOTEM (xine or gstream ), the only thing is that subtitles must have the exac same name as the film ( film.avi  film.srt ) and be in the same directory. More, i have an ATI with TVOUT and when i select the driver to be opengl, i see the movie with very good quality but lose subtitles, i wonder why.
Avidemux has a subtitle converter from IDX to SRT, never used... 
VLC has a way to load subtitles from browsing where they actualy are.
Totem for me has the better quality subtitles, we can change the size as well by changing the totem-config file and they play on the black part of the film also. to my knowldge, is the only one to do it.
I really don't know if i could be of some help... :( 

PS:sorry for my english

---

### Post by generalleoff on 2006-07-28
You won't find anything. Decent media players is one of the fields Linux is extremely lacking in compared to Windows. Sure there are plenty of media players that can play tons of formats (VLC, MPlayer) but there are none that are as coherent, complete, or feature rich as players like Media Player Classic (VobSub is part of this program), BS Player, or Zoom Player are on Windows.

My personal preference is Zoom Player plus the external versions of the Media Player Classic codecs plus ffdshow (basically the same as MPlayer). I have been trying to get it working under Wine but have had no luck.

---

### Post by Amorphous_Snake on 2006-07-28
Zoom Player is my favourite too in Windows. Too bad that it's not in Linux.

Why can't those Linux developers make things easy for us?!!!

---

### Post by Amorphous_Snake on 2006-07-28
> **flamarro said:**
> Hi,
like me, this is a must for me, handling subtitles in ubuntu, that keeps reminding me about BSPlayer. Its been a pain in the ***.
All the players you talked about read subtitles, VLC, MPLAYER, TOTEM (xine or gstream ), the only thing is that subtitles must have the exac same name as the film ( film.avi  film.srt ) and be in the same directory. More, i have an ATI with TVOUT and when i select the driver to be opengl, i see the movie with very good quality but lose subtitles, i wonder why.
Avidemux has a subtitle converter from IDX to SRT, never used... 
VLC has a way to load subtitles from browsing where they actualy are.
Totem for me has the better quality subtitles, we can change the size as well by changing the totem-config file and they play on the black part of the film also. to my knowldge, is the only one to do it.
I really don't know if i could be of some help... :( 

PS:sorry for my english

I will try with Totem. I will keep you informed.

There is nothing wrong with your English. (It's not my native tongue too.)

---

### Post by benuski on 2006-07-28
If you really need it, you could try downloading Wine and then dowloading the program that you want, and try installing it and running it through Wine.  Wine is a Windows emulation layer for Linux, and you can get decent results sometimes running windows programs using it.  You have to go to the repositories to download it, download the installer for whatever windows program you want, right click and say open with Wine, and it should take care of the rest.  I'm not too sure about the specifics, because I haven't used wine much, but its worth a try.

---

### Post by evaldas on 2006-08-21
> **flamarro said:**
> Hi,
like me, this is a must for me, handling subtitles in ubuntu, that keeps reminding me about BSPlayer. Its been a pain in the ***.
All the players you talked about read subtitles, VLC, MPLAYER, TOTEM (xine or gstream ), the only thing is that subtitles must have the exac same name as the film ( film.avi  film.srt ) and be in the same directory. More, i have an ATI with TVOUT and when i select the driver to be opengl, i see the movie with very good quality but lose subtitles, i wonder why.
Avidemux has a subtitle converter from IDX to SRT, never used... 
VLC has a way to load subtitles from browsing where they actualy are.
Totem for me has the better quality subtitles, we can change the size as well by changing the totem-config file and they play on the black part of the film also. to my knowldge, is the only one to do it.
I really don't know if i could be of some help... :( 

PS:sorry for my english
maybe you can tell exactly how to view subtitles in totem-gstreamer? I also have pair of .idx/.sub files, and I can't get totem to display them. I miss vobsub too.

---

### Post by flamarro on 2006-08-23
hi there,
well i don't use totem-gstreamer because i can't, in the config file it uses, change the position of the subtitles, wich i can change using totem-xine, don't ask me why... As i told you, you only have to have the same name of the movie in the same directory, like video.avi then you must have video.srt in that same directory. As you play the movie the subtitles are there too without having to do anything. Then, to change the font or position of the subs you edit the totem_config file that is on .gnome2. I can put the subtitles in the black border, the problem is that i can't see the movie with tvout. :-( 
I use VLC because of this
I hope that helps

---

### Post by bobbyubun on 2008-06-17
Since I got this page as first google search result  I need to reply here that Totem Movie Player 2.22.1 is support srt subtitle like Vobsub and you just need the srt file name the same as your movie name

---

