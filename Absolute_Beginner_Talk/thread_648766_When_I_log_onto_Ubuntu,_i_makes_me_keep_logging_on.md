---
title: "When I log onto Ubuntu, i makes me keep logging on..."
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by hilariousness16 on 2007-12-24
:(:mad:

I inserted my username, pressed enter, inserted my password, pressed enter, ubuntu loads...

then the main menu came back again to enter my username and password...over and over...


i made a video if you didn't understand me...ignore my dad in the background

and yes i am asian lol

[http://s215.photobucket.com/albums/cc239/hilariousness16/?action=view&current=MOV00429.flv](http://s215.photobucket.com/albums/cc239/hilariousness16/?action=view&current=MOV00429.flv)

---

### Post by diatribe on 2007-12-24
is your video card set up properly? also are you using gnome kde or what?

---

### Post by hilariousness16 on 2007-12-24
i just installed 

sudo apt-get install git-core

and i restarted my laptop and i can't got on so i think my video card is fine

whats gnome? lol im a noob

---

### Post by hilariousness16 on 2007-12-24
bump

---

### Post by hilariousness16 on 2007-12-24
I also restarted a couples times but not working...:mad:

---

### Post by hilariousness16 on 2007-12-24
i made a video if you didn't understand me...ignore my dad in the background

and yes i am asian lol

[http://s215.photobucket.com/albums/cc239/hilariousness16/?action=view&current=MOV00429.flv](http://s215.photobucket.com/albums/cc239/hilariousness16/?action=view&current=MOV00429.flv)

---

### Post by fain on 2007-12-24
> **hilariousness16 said:**
> i just installed 

sudo apt-get install git-core

and i restarted my laptop and i can't got on so i think my video card is fine

whats gnome? lol im a noob

gnome is the desktop manager in Ubuntu. If you got Kubuntu you are using Kde, the desktop manager in it.

Check your logs in /var/log/ for clues. the auth log will tell you if your un or pw was correct or not. The xorg log will tell you if theres a video problem. Look at the syslog too.

you can do this by droping into a terminal (ctrl-alt-f1) and executing

```
ls /var/log
```

```
cat /var/log/filehere | more
```

or

```
tail -f /var/log/filehere
```

the latter will show the last few lines and append newer ones as they are logged. Be sure to replace "filehere" with a file in /var/log/

---

### Post by hilariousness16 on 2007-12-24
i still don't get how i actually log onto the ubuntu, i am positive my log ins were right

---

### Post by hilariousness16 on 2007-12-24
someone please help, each hour i can't log onto ubuntu is like getting smacked in the facee:lolflag:

---

### Post by daengbo on 2007-12-24
I'll guess that you set your personal resolution to something that isn't supported or you have a corruption in your cache somewhere.

First, try booting into recovery mode

#Add a new user
useradd guest

#Give the new user a password
passwd guest

then reboot and try to login as the guest. If it works, then you'll need to delete parts of your home directory.

---

### Post by hilariousness16 on 2007-12-24
when i did the passwd guest

it said 

Type in Unix Password: _

I can't type anything in..

---

### Post by LowSky on 2007-12-24
it wont show what your typing but it is there, its blocked out for security purposes

---

### Post by hilariousness16 on 2007-12-24
oooooo lol
let's see if this works

---

### Post by hilariousness16 on 2007-12-24
yeah it didn't work

---

### Post by daengbo on 2007-12-24
What exactly didn't work? The password didn't work? You couldn't log in as guest?

---

