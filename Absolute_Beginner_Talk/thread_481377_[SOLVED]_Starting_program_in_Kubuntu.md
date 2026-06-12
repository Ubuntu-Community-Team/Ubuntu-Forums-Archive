---
title: "[SOLVED] Starting program in Kubuntu"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Balazs_noob on 2007-06-22
Hy guys

i have just switched from Ubuntu to Kubuntu just to try it :)
and i would have a small problem :)
i didn't found it yet where could i start programs after Startup
in Ubuntu i found it in Sessions ...

Another one :D
beryl doesn't show the window decorator..
i have tried emerald , heliodor and aquamarin non of them worked :(
besides from that beryl works fine :)

Thanks in advance , Balázs

---

### Post by Balazs_noob on 2007-06-22
nobody ?? :(

---

### Post by benerivo on 2007-06-22
Fot startup programs I put a link in the /home/yourusername/.kde/Autostart folder. It's a bit like the startup folder in windows if you know that one. When in your home folder you will need to select View>Show Hidden Files to make the hidden folder appear (.kde is one of them).

---

### Post by Balazs_noob on 2007-06-22
thanks benerivo.... :)
it works :D

---

### Post by Orochi on 2007-06-22
Are you just running beryl or are you running beryl-manager? I don't know how it works in Kubuntu, but in Ubuntu if you're running beryl-manager you can right click on the Beryl icon in the tray and choose your window decorator. Try doing that and setting it to Emerald maybe?

---

### Post by Balazs_noob on 2007-06-23
yeah i use beryl - manager and tried to set it to emerald but it still didn't show anything :(

thats why i installed heliodor too, another window decorator but that doesn't worked either :(

---

### Post by Gvaz on 2007-06-24
> **benerivo said:**
> Fot startup programs I put a link in the /home/yourusername/.kde/Autostart folder. It's a bit like the startup folder in windows if you know that one. When in your home folder you will need to select View>Show Hidden Files to make the hidden folder appear (.kde is one of them).

i did that, and i have it open, but like, WHAT do i add? im a little lost, a shortcut to beryl? how?
also can i do the same thing for conky?

---

### Post by benerivo on 2007-06-24
Yes, you would add a link (ie. a 'shortcut') for the program you want to startup automatically. I'm having to recall off the top of my head, but i believe when you're in the Autostart folder, you right click and choose the 'Create Link to Application' option. Then you will need to find out where in the file system the program actually is. The executable file for each program usually lies in /usr/bin. For example beryl is /usr/bin/beryl, and firefox is /usr/lib/firefox/firefox


As a general tip, if you want to find out where in your filesystem a program has been installed to, then go in to a terminal and type...
whereis programname

For example...
whereis beryl

or...
whereis conky

---

