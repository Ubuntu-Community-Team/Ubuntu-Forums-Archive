---
title: "Mplayer plug-in"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by FadedReality on 2008-02-10
When I try to play streaming video with the mplayer plug-in I can hear the sound but no video plays. Where the video should be it just shows some text.

---

### Post by JoshuaRL on 2008-02-10
Have you installed the ubuntu-restricted-extras package?

What type of streaming media is it?

---

### Post by FadedReality on 2008-02-10
wmv and realmedia

I just downloaded a wmv on the desktop and played it using mplayer and it worked fine. 

ubuntu-restricted-extras package

Unsure I installed some codecs and then un-installed it or at least think I uninstalled them since I live in the u.s.a.

---

### Post by JoshuaRL on 2008-02-10
That would be your issue then.  Since they're closed formats then Ubuntu doesn't ship with them.  But you can go into the Add/Remove or Synaptic and look for that package and one called Helix.  That'll be for RealMedia.

---

### Post by FadedReality on 2008-02-10
How can I make sure I got rid of the other codecs?

---

### Post by JoshuaRL on 2008-02-10
Why do you want to?  If you install those it will give you a whole host of codecs.  And it won't hurt if you have others.

---

### Post by FadedReality on 2008-02-10
Its illegal in the u.s.a. to have them or at least thats what it said on a few sites I've seen.

---

### Post by PeterJS on 2008-02-10
Yes technically under the letter of the law they are illegal, but consider this:
1) Are said laws sane?
2) Are they just?
3) Are you personally likely to get prosecuted?

The packages you want to check for are w32-codecs,  gstreamer0.10-plugins-ugly-multiverse, gstreamer0.10-plugins-bad-multiverse, and liblame0, libdvdcss2

---

### Post by FadedReality on 2008-02-10
Thanks I'll install all the codecs I can except those. I know its a lame law but out of the 1/1000 chance I do get in trouble I wouldn't be able to afford the lawsuit I'd rather stay legal.

---

