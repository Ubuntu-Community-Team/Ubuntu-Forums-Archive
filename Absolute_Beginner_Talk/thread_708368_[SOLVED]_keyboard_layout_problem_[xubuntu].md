---
title: "[SOLVED] keyboard layout problem [xubuntu]"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by oloapota on 2008-02-26
Hello everybody!
I switched to Linux yesterday, and I think it's great!
I chose xubuntu coz I have an old pc
Just seem to have a little problem about the keyboard layout
at the login, it's in italian   -as I want it, I'm from Italy
But then it switches to us layout:mad::confused:
I followed these instructions:
[http://linux.about.com/od/xubuntu_doc/a/xubudg24t01.htm](http://linux.about.com/od/xubuntu_doc/a/xubudg24t01.htm)
and managed to complete step 1 -that is, modyfing the xorg.conf file
I wrote "it" where it said "us"
But I cannot do step 2!
When I type setxkbmap <language_code> on a terminal, it says
bash: syntax error near unexpected token 'newline'

Isn't "it" the right code for italian layout?
what puzzles me more is that it's in italian at login, but switches to us afterwards:confused:
Thanks for your help

---

### Post by oloapota on 2008-02-27
Can't anybody help me please?
I'm very happy I switched to Xubuntu (I've never even booted win xp since) but this keyboard problem is a little annoying: I use the pc to write my graduation thesis and sometimes it takes me ages to find a special character-it's taking me ages to write this post as well LOL
As I said, I looked it up on the internet, and found the instructions to fix the problem, but I can't manage to get them to work
thanks

---

### Post by mister_pink on 2008-02-27
Not sure why that isnt working, and I havent used xubuntu in a while, but I'm sure there must be an easy way to do this using the GUI. In gnome its just under the system preferences menu. Have a hunt around for keyboard settings somewhere. I imagine you have both us and italian layouts added, but it defaults to us, so youd need to remove the us one.
What is the exact command you type on the command line, it should be just:
setxkbmap it

---

### Post by oloapota on 2008-02-27
:oops:
I typed setxbmap <it>! :(
Thank you mister pink! I managed to configure everything else that I needed just fine, but this simple thing was beyond me :-\"

---

