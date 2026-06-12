---
title: "questions about feisty fawn"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by simplekin on 2007-05-07
ok I got a bunch of questions and I am very new to this so sorry but going to have to explain it to me inch by inch, here they are:

1. Why is it when I go on youtube i don't hear any sound when playing a video
2. How can I make it so I have full access to the whole system
3. Where can I find a guide for the things you need to do right away when you install Feisty Fawn.
4. A program (Adept) is telling me I wont be able to install anything because I am not the root admin or something, how can I do what it asks me?
5. How can I enable copy and paste?



Thats it, thanks a lot!

---

### Post by Pigsflew on 2007-05-07
> **simplekin said:**
> ok I got a bunch of questions and I am very new to this so sorry but going to have to explain it to me inch by inch, here they are:

1. Why is it when I go on youtube i don't hear any sound when playing a video

This could be because of the sound card--do you hear sounds for anything else? like when logging in? Playing the demo music files?

> 2. How can I make it so I have full access to the whole system

Anything you want to do can be done by elevating privileges, using 'sudo' (SUperuser DO). If you are on the command line, typing 'sudo' before any command will temporarily elevate your privileges, provided you are on an administrative account.

If you do want to switch to the root user in a terminal session, you can always use "sudo su"; su (Switch User) defaults to switching to the Root account. It's not recommended that you do this, generally staying your own user keeps your settings clean and running things as root can be a tremendous risk to your system.

> 3. Where can I find a guide for the things you need to do right away when you install Feisty Fawn.

This isn't an official guide, but I personally would recommend [www.ubuntuguide.org](www.ubuntuguide.org). However, you should just explore the various menus first, there's a lot of things that Feisty will just do for you and will do it well.

> 4. A program (Adept) is telling me I wont be able to install anything because I am not the root admin or something, how can I do what it asks me?

If you're trying to run Adept from the command line, you can always run "sudo adept"; this will ask you for a password. If you're account was set up as an administrator, then just type your own password and it should allow you to install stuff. If you're running it from the KDE menu, it should ask you graphically for a password, in the same manner.

> 5. How can I enable copy and paste?

I'm not sure about this one. It should be enabled by default; you should be able to hit "ctrl+c" and "ctrl+v", respectively. You should also have copy and paste context menus... I've never actually heard of this being disabled. You can use the X way as well; highlight anything with the mouse, and middle click it should paste that text. These are not the same method; ctrl+v will not paste the middle-click text.

I don't use KDE, so some of this is me guessing a bit, but it should be mostly the same.

---

### Post by aysiu on 2007-05-07
Don't use *sudo adept*. If you must run it from the command-line, use ```
kdesu adept
``` 
Read more here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

But if you launch it from the menu item, that's how it should be already: KMenu > System > Adept Package Manager.

About permissions, read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by simplekin on 2007-05-07
OK, i checked if i hear a sound when logging in and that is a no no,  but I did hear it when I first booted up the operation system.

---

### Post by ubnewbie2 on 2007-05-07
> **simplekin said:**
> ok I got a bunch of questions and I am very new to this so sorry but going to have to explain it to me inch by inch, here they are:

1. Why is it when I go on youtube i don't hear any sound when playing a video
!

I have this problem as well. If you have sounds in other apps, like mp3 players etc, then chances are you've struck a fairly common problem with the flash player.  Search around, and you find heaps of hacks and possible fixes, even bug reports.  Sadly, nothing has yet worked for me - flash remains broken.

---

### Post by simplekin on 2007-05-07
bump? sound card problems I think, have a creative sound card

---

