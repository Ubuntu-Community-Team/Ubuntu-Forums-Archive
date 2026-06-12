---
title: "Thinkpad no superkey?"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by raggit on 2006-09-01
There are a few commands that I would like to use but unfortunately they need a "SuperKey" but my thinkpad doesn't have that magic windows key. Can someone give me a run through of how on earth to set a key to be my superkey.  Keep in mind im in the newbie section but I know it has something to do with the gconf-editor..thanks guys

---

### Post by piccler on 2007-07-27
i'm having the same issue.

---

### Post by PatrickMB on 2007-10-21
Does anyone have any ideas on this? I am running Gutsy at the moment.

---

### Post by Whiffle on 2007-10-21
On mine I have it remapped to caps lock.    I never realized how little I use (ok, never use), the caps lock function.

Here's How:
[http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#Using_Caps_Lock_as_Super_L_.28Windows_key.29](http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#Using_Caps_Lock_as_Super_L_.28Windows_key.29)

---

### Post by PatrickMB on 2007-10-21
Ok, so I created the file .Xmodmap in my home directory. I added the bit of ```
! No Caps Lock
clear lock
!Caps Lock as Win key
add mod4 = Caps_Lock

``` to it and restarted X using CTR+ALT+BACKSPACE.  On restart it asked if i wanted to load .Xmodmap or ,Xmodmap (~). I selected the first one. So now my Caps lock key doesn't work, which is good, but it does not function as a Super or Windows key.

I have tried restarting X again to get the load dialog box back to see if I should load the other option, but thus far no luck on that. 

Any ideas?

Edit: I can not create a  new .Xmodmap file because it says the file already exists. However, I can not seem to find it. Any ideas on this?

---

### Post by virtualXTC on 2008-04-08
Considering that the file doesn't exist, it didn't seem like just it's creation would solve the problem.  I found this page which explains how to point the xmodmap program to the file:

[http://www.ubuntugeek.com/disable-and-enable-caps-lock-in-ubuntu.html](http://www.ubuntugeek.com/disable-and-enable-caps-lock-in-ubuntu.html)

For those of you who are lazy the terminal commands are:
```

xmodmap -pke > ~/.xmodmap.myown
cat >> ~/.xmodmap.myown
! No Caps Lock
clear lock
!Caps Lock as Win key
add mod4 = Caps_Lock

```
press <ctrl> C

```

xmodmap ~/.xmodmap.myown

```

---

