---
title: "There is a strange rectangular box in the top left of my screen"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by chest_burster on 2006-12-07
I'm happily using Edgy Eft on my 4-year old Dell Latitude C610 laptop, but I've recently been plagued by a small rectangular box in the top left corner of my screen...

Any ideas?

---

### Post by amo-ej1 on 2006-12-07
i think a screenshot or something like that would be nice ;)

---

### Post by chest_burster on 2006-12-07
[IMG]http://static.flickr.com/119/316417999_24faf34257.jpg[/IMG]

Here's a screenshot.

---

### Post by amo-ej1 on 2006-12-07
looks ugly doesn't it ? :p

well you could do this:

open up a terminal, and type 'xwininfo' you will see your pointer change, then click into that square and paste the output here. Another option would be to type 'xkill', your pointer will turn into a little death head and clicking into it might kill it (if we start from the idea that it's some application behaving not the way it's supposed to do). (If xkill solves it you might wish to take a look at the process list and see which gets terminated)

but in any case, save any open files.

---

### Post by chest_burster on 2006-12-07
Here's the output:

xwininfo: Window id: 0x240d2e2 (has no name)

  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 25
  Height: 50
  Depth: 24
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: yes
  Map State: IsViewable
  Override Redirect State: yes
  Corners:  +0+0  -999+0  -999-718  +0-718
  -geometry 25x50+0+0

---

### Post by amo-ej1 on 2006-12-07
okay did you manage to xkill it ?

---

### Post by chest_burster on 2006-12-07
"xkill" didn't work, although the pointer looked pretty sweet. :)

---

### Post by doobit on 2006-12-07
Do you get a context menu when you right click on it?

---

### Post by hotbrainz on 2006-12-07
screen shot please

---

### Post by amo-ej1 on 2006-12-07
well ... you could start killing processes and see what finally terminates it ...

---

### Post by chest_burster on 2006-12-07
> **doobit said:**
> Do you get a context menu when you right click on it?

Afraid not.

---

### Post by chest_burster on 2006-12-07
A reboot killed Deathbox.  Thanks for all the tips, I'll try them when he inevitably returns.

---

### Post by doobit on 2006-12-07
Why don't you just only use the CLI? ;)

(I'm kidding!)

---

