---
title: "AutoPlay DVD's"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by concerto on 2008-02-12
I think I accidentally erased the command to auto play movies.  now of course It's hard for me to play movies now.

When I go to...
System->Preferences->Removable Drives and Media
2nd tab "Multimedia"

What is supposed to be the command to auto play?
My command space is blank.

Thank you.

---

### Post by emarkd on 2008-02-12
I've got 

```
totem %m
```

but you could use another player

---

### Post by fenian on 2008-02-12
To open DVD's fullscreen with Xine use...
> 
xine -pfhq --no-splash dvd:// 

---

### Post by concerto on 2008-02-12
OH my !!!   It's alive!

It works.  I put the movie in and it starts to play.

Then it stops and an error pops up and says
"can not read from source"  and then everything stops.

---

### Post by sioc on 2008-05-10
Hi all !
I'd like to use smplayer to autoplay DVD's, but I've found no "multimedia" tab in System->Preferences->Removable Drives and Media
I use Ubuntu Hardy Heron but in french translation...
Present tabs are :
Appareil photos et caméscope | PDA | Imprimante et scanner | Périphérique de saisie
Meaning approximately :
Camera | PDA | Printer and scanner | Input peripheral

So I tried some arcane obscure science with the following :
gconftool -s /desktop/gnome/volume_manager/autoplay_dvd_command 'smplayer %d' --type=string
No effect ...

As I dislike totem, I apt-get removed it and remarked that no more option was visible in the mounted DVD directory to play it. When totem is installed, there IS a button at the top of the file browser that allow to 'open video player' when you browse the DVD directory. 

I feel all this is somewhat related, but I can't catch it all and make it all fine for me, so I need some help ^_^

Now I've reinstalled totem, but if anyone has a clue of how I can configure the autoplay for smplayer, that would be soooo nice !!!

---

### Post by tonyldo on 2008-05-19
I have the same problem and  i couldn't change the default dvd player to gxine. :(

I use ubuntu Hardy Heron - Portuguese brazilian

> **sioc said:**
> Hi all !
I'd like to use smplayer to autoplay DVD's, but I've found no "multimedia" tab in System->Preferences->Removable Drives and Media
I use Ubuntu Hardy Heron but in french translation...
Present tabs are :
Appareil photos et caméscope | PDA | Imprimante et scanner | Périphérique de saisie
Meaning approximately :
Camera | PDA | Printer and scanner | Input peripheral

So I tried some arcane obscure science with the following :
gconftool -s /desktop/gnome/volume_manager/autoplay_dvd_command 'smplayer %d' --type=string
No effect ...

As I dislike totem, I apt-get removed it and remarked that no more option was visible in the mounted DVD directory to play it. When totem is installed, there IS a button at the top of the file browser that allow to 'open video player' when you browse the DVD directory. 

I feel all this is somewhat related, but I can't catch it all and make it all fine for me, so I need some help ^_^

Now I've reinstalled totem, but if anyone has a clue of how I can configure the autoplay for smplayer, that would be soooo nice !!!

---

### Post by flowtron on 2008-06-01
Well - I found this thread : [http://ubuntuforums.org/showthread.php?p=4936234](http://ubuntuforums.org/showthread.php?p=4936234)
Which does indeed bring up a menu-driven (GUI) way to change the auto-play program ... but I can only select movie-player or gxine ... I'd like to use VLC, if you don't mind ... setting the "/desktop/gnome/volume_manager/autoplay_dvd_command" didn't change a thing for me either ... and after setting the value via the menu to gxine I still can't find any value matching that :-P

Another thing about auto-play - if I'm logged in with two users into Gnome the auto-play also starts on the currently inactive desktop ... how rubish is that?

Ubuntu is rapidly becoming just as annoying as Windows in regard to "doing stuff silently" and "not bothering the users with technicalities" ... that's all fine & good for newbies ... but what about people who _want_ to know .. and have FULL control over their system ... which is the reason I moved to linux, really.

Well ... I'll keep at it, it's always been like this with me and Ubuntu .. ever since Dapper Drake - each release does really annoying stuff (IMO) and I have to wrestle with it for ages until I find the "ubuntu way" of doing it ... no wonder the Debian people are so mad at this distribution ... ah well, at least it's usually got the most current drivers and stuff, so I'll still be sticking with it, even though I agree with the (wonderful) people of Debian GNU/Linux ... you just can't have it all - stable & reliable system AND cutting edge drivers :-/

---

