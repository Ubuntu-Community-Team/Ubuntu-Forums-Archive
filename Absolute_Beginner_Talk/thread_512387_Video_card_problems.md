---
title: "Video card problems"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-07-29
Hi guys, need your help again!

I have an ATI Xpress 200M card in my laptop and i want to get it running so i can play some 3d games! Im running feisty fawn on a 64-bit machine if that helps. Anything you can do to help me out would be great! Ive tried envy, but it didnt work :(

---

### Post by overdrank on 2007-07-29
> **ukulele_ninja said:**
> Hi guys, need your help again!

I have an ATI Xpress 200M card in my laptop and i want to get it running so i can play some 3d games! Im running feisty fawn on a 64-bit machine if that helps. Anything you can do to help me out would be great! Ive tried envy, but it didnt work :(

Hi maybe this " how to " will help
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
Good luck! :)

---

### Post by ukulele_ninja on 2007-07-29
I dont know if that worked or not... It says in my restricted drivers window that it is in use...how do i test it though? It still crashes when I try to run 3d games.

---

### Post by overdrank on 2007-07-29
> **ukulele_ninja said:**
> I dont know if that worked or not... It says in my restricted drivers window that it is in use...how do i test it though? It still crashes when I try to run 3d games.

You can run the command that is suggested by the "how to" in the terminal 
```
fglrxinfo
```

---

### Post by ukulele_ninja on 2007-07-29
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6474 (8.38.7)


thats my output...still crashes games though :(

---

### Post by overdrank on 2007-07-29
> **ukulele_ninja said:**
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6474 (8.38.7)


thats my output...still crashes games though :(

This to is from the "how to" 

If you are using an ATI Radeon Xpress 200M on an AMD64 CPU and the fglrx driver crashes with a blank screen on startup, change your BIOS settings to use the UMA+Sideport Video Mode with 128MB of Shared Video Memory. See [WWW] [http://ensode.net/ati_radeon_xpress_200m_linux.html](http://ensode.net/ati_radeon_xpress_200m_linux.html)

---

### Post by ukulele_ninja on 2007-07-29
What do you mean blank screen on startup? When I startup it asks me what OS I want but thats it.

---

### Post by overdrank on 2007-07-29
> **ukulele_ninja said:**
> What do you mean blank screen on startup? When I startup it asks me what OS I want but thats it.

I was just showing you the link that may help you. If your system crashes when trying to play a game then that link may help. I understand that you don't have a blank screen on startup but that link takes you to a page where they talk about getting the 3d acceleration working. :)

---

### Post by ukulele_ninja on 2007-07-29
Oh! ok sorry. I actually just tried Tremulous and it worked! So you must have fied my problem! Thanks man... now if only beryl will work! Any links to installing beryl on a 64-bit kubuntu?

---

