---
title: "Possible fix for disabled cursor on keypress - mouseemu"
date: 2007-09-07
forum: Apple Intel Users
---

### Post by cyberdork33 on 2007-09-07
Hey guys, I ran across this today. I know that mouseemu was causing some issues for people (especially for games) in that it would disable the mouse movement when you were typing. 

Originally from here: [http://trw.wikidot.com/ubuntu-feisty-on-macbook](http://trw.wikidot.com/ubuntu-feisty-on-macbook)

> Mouse I have experienced a strange behavior with one of my installation. I cannot move mouse while I was pressing a key on the keyboard. A behavior that is useful for Touchpad but really annoying for mouse.
This is how to fix:
  ```
sudo gedit /etc/default/mouseemu
```Uncomment "TYPING_BLOCK...", change 300 to 0, save
```
sudo /etc/init.d/mouseemu restart
```You can also see this post for similar tweaks for the touchpad:
[http://ubuntuforums.org/showthread.php?t=434625]("http://ubuntuforums.org/showthread.php?t=434625&highlight=syndaemon")

---

### Post by ACLBandit on 2008-06-27
I love you. Seriously. 

I can play first person shooters again, since I can use mouse AND keyboard at the same time now. Thank you SO much!!

---

### Post by mordisk0 on 2008-07-07
I love you too. I'm a debian user and registered here just to say this to you.
 
 Thanks a lot!

---

