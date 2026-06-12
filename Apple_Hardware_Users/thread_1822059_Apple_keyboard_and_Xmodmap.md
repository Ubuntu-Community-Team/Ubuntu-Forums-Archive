---
title: "Apple keyboard and Xmodmap"
date: 2011-08-10
forum: Apple Hardware Users
---

### Post by Lasastard on 2011-08-10
Hi,

I thought I'd post this here since Apple users are the most affected by it (couldn't find a good guide that would help either).

I am one of those people running Ubuntu Server on a Mac Pro - but I ran into the apparently long-standing issue of the aluminum keyboard (int) assigning two keys incorrectly (<,> and °). Now, the solution is

xmodmap -e 'keycode 49 = less greater less greater bar brokenbar bar' -e 'keycode 94 = dead_circumflex degree dead_circumflex degree U2032 U2033 U2032'

But where do I put that so it is loaded on startup? Older guides talk about .xsession or .xinitrc - neither of which I can find on my Ubuntu 11.04 server installation.

Thanks for any advice!

/Marc

---

### Post by Pattn on 2011-08-10
At least your Keyboard works so far :P Did you have the XKB-configuration Error as well?

---

### Post by pauljwells on 2011-08-11
IIRC: Save those commands as a text file and save it as ~/.Xmodmap

I suppose you'd need to check if the prgram xmodmap is included in the server install.

---

