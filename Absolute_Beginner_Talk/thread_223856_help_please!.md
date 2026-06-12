---
title: "help please!"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by rck_hitokiri on 2006-07-27
i finally got my sound card working... ESS audio drive... model es1868. but there is a catch... when i play mp3's the sound goes like its loosing pitch goes up and down.... how do i fix this? please help. P.S. thanks to all the good people that helped me makin this work.

---

### Post by The Noble on 2006-07-27
What app are you using? I very much doubt it is an application, but try another anyways. Also, get the latest kernel from the repos. If worse comes to worse, compile a kernel from one of the guides on this site, as better compatibility may have been added in a 2.6.16/17 kernel. Otherwise, I wouldn't know.

---

### Post by rck_hitokiri on 2006-07-27
im using the default rhythm box as a try.... xmms player sounded the same.... and amarok...well doesnt maker any sound at all bro.... im usin ubuntu 6.06 right now. if you need more info please let me know and ill post it here. thanks.

---

### Post by The Noble on 2006-07-27
The only other thing I can suggest would be to try a different kernel from the repos. Maybe someone knows some commands I don't, but I do remember that my desktop's sound didn't work at all, but an update fixed that (of the kernel).

Something to try: Is it only mp3's that don't work? Do oggs work well? If they do, try reinstalling your multimedia plugins. Follow:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by rck_hitokiri on 2006-07-27
im afraid even ogg is affected.... as well as mpeg and all the other codecs. im updating my kernels right now and opefully it'll get things fixed. thanks for your troubles man.

---

### Post by The Noble on 2006-07-27
It is no problem to me.... so I am happy to help. It may not be the kernel in this case. My reccommendation is to reinstall your gstreamer codecs. If they don't work, try using the xine codec (used with gxine and other players)

---

### Post by pistcivet on 2006-07-27
I'm sorry to hear you're having problems,
but I'm using that same sound card with Xubuntu on a
750 MHz machine with no trouble whatsoever (mp3 or ogg).

I was wondering how fast your CPU was. If its extremely slow, that could be a problem.

Maybe Xubuntu would be a better choice for you if you have a low-end machine (like mine) :)

Good luck! And if you find a resolution, please post it.

---

