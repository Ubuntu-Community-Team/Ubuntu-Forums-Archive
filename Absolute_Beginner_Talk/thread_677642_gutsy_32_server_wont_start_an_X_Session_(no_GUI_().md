---
title: "gutsy 32 server wont start an X Session? (no GUI :()"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by hoist1138 on 2008-01-25
Everything so far in gutsy server 32 bit version has been really straight forward, But I have not for the life of my been able to figure out how to get to the X11 gui interface.
Im pretty new to linux, 

if i do the 'startx' command it spits out this....
'X: cannot stat /etc/X11/X (no such file or directory), aborting. xinit: Server error'
Which is true, i go to the X11 dir and there isnt a file 'X' in there, I have read that I need to put this file in here as a symbolic Link? is that correct?

also I have read that i should run....
'sudo dpkg-reconfigure xserver-xorg'
but THEN I get.....
'package 'xserver-xorg' is not installed and no info is available.
use dpkg --info (= dpkg-deb --info) to examine the archive files,
and dpkg --contents (= dpkg-deb --content) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed'

Im just not sure what my next action to trouble shoot should be, I know its probably telling me exactly what to do in that message, but I need a veteran user's advice.
Help!

---

### Post by wolfen69 on 2008-01-25
not to sound too obvious, but did you install xorg?

---

### Post by emarkd on 2008-01-25
Try installing xorg by doing:

```
sudo apt-get install xserver-xorg
```

---

### Post by hoist1138 on 2008-01-25
good point....
Im not sure, now that i think about it....Leme try....

---

### Post by hoist1138 on 2008-01-25
**Thanks Guys!  **:)
That got me to a "pick your resolution screen" ...
I just hit enter, did some more installing and then.....

'Fatal server error:
No valid FontPath could be found.
XIO: fatal IO error 104 (connection reset by peer) on X server ":0.0"

but Im at least closer now,

this looks like a graphics card issue now? 
im using Leadtek A250 Ultra TD GeForce 4
Ti4600 128Mb DDR graphic card

---

### Post by wolfen69 on 2008-01-25
is it your goal to get to a working desktop?
try  xfce (IMO a good server GUI)
```
sudo apt-get install xfce4 thunar leafpad
```
then, startx will actually do something.

---

### Post by hoist1138 on 2008-01-25
another great point...Yes this is my ultimate goal.

let me try that now...

---

### Post by hoist1138 on 2008-01-25
ok it seemed to install fine......
heres a dumb questions now, how do I start it, or boot to Xfce?

thanks again wolfen69

---

### Post by salazar on 2008-01-25
startxfce4  

and hit enter , that will do the trick

[http://www.xfce.org](http://www.xfce.org)

---

### Post by Kilz on 2008-01-25
startx will also work.

---

### Post by wvrn on 2008-02-15
apt-get install xfonts-base

---

