---
title: "desktop no longer rotates"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by wobbly_bob on 2007-09-07
Hi, I had my desktop effects turned off because I was trying to solve a problem with video playback. I have turned them back on and now, for some reason, the desktop no longer rotates when I push the window to the edge. Also, the other desktops are totally blank when before I swear they were mirror images of my main desktop.

I tried searching, but I stuck, again... Big thanks to anybody for help :)

---

### Post by mysticmatrix on 2007-09-07
Well this is a known problem and causes trouble in desktop effects. That's why they are 'technology preview'. Anyways, the fix is to type on terminal.

To get the cube to work do this:
Code:

```
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1

```

PS: There is fix for that video problem thing, and is quite easy to find if you search the forums.

---

### Post by wobbly_bob on 2007-09-07
Cool, fixed it :)

Thanks a lot for your help. I actually fixed the playback issue. I posted earlier today, and some other members were nice enough to help me out. This is a cool community. It seems that Ubuntu really does mean something. Anyway,  It turned out, in the end, that all I had to do was switch the video output to X11 in VLC player and it worked fine.

I just wiped my windows away and installed Linux today, and loving it so far! I know nothing tho... so now I got those two little problems fixed I can go away and read up on how to use Linux and hopefully won't have to pester anybody here for awhile... lol

Thanks again.

---

