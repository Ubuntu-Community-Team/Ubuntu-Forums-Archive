---
title: "Microphone In Xubuntu"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2008-01-10
Hi there. My laptop is running the latest release of Xubuntu. I want to be able to record sound with a microphone, however when I plug it in and fire up Skype or some sound recording software, no sound is recorded.

Can anyone help me out? The laptop is a Thinkpad 600E and I'm connecting the mic via a standrad connection. Its not USB or anything.

---

### Post by jken146 on 2008-01-11
Have you got the mic volume turned up?  Press Alt+F2 and type **xfce4-mixer** to get the volume control app.

---

### Post by Crumpets and Jam on 2008-01-11
> **jken146 said:**
> Have you got the mic volume turned up?  Press Alt+F2 and type **xfce4-mixer** to get the volume control app.

Thanks for the response. Even when I turn the micropohne slider all the way to the top I still have the same problem.

---

### Post by Crumpets and Jam on 2008-01-11
Anyone think they have a solution?

---

### Post by tc10b on 2008-01-11
Underneath the slider, there is a little speaker which mutes and unmutes the mic. Have you tried clicking that?

---

### Post by Crumpets and Jam on 2008-01-11
> **tc10b said:**
> Underneath the slider, there is a little speaker which mutes and unmutes the mic. Have you tried clicking that?

Hmm. Thats not there for me, even when I expand the window. This is what it looks like.

[[IMG]http://img223.imageshack.us/img223/9831/screenshotlr8.th.png[/IMG]](http://img223.imageshack.us/img223/9831/screenshotlr8.png)

---

### Post by tc10b on 2008-01-11
Sorry my mistake, that's the gnome control.

Click the mic playback boost switch, that should help.

When you do that, you may get feedback so start with the slider down low first!

---

### Post by Crumpets and Jam on 2008-01-12
> **tc10b said:**
> Sorry my mistake, that's the gnome control.

Click the mic playback boost switch, that should help.

When you do that, you may get feedback so start with the slider down low first!

After doing what you suggested, it still isn't picking up any sound as far as I can tell.

---

### Post by Crumpets and Jam on 2008-01-13
Anybody got any other ideas?

---

### Post by Crumpets and Jam on 2008-01-14
Please?

---

### Post by Crumpets and Jam on 2008-01-15
Really sorry that I keep bumping my thread.

Any thoughts though anyone?

---

### Post by gobuntu on 2008-01-18
Hi Crumpets,

On top of settings at the Mixer sliders, you'd still need to specify the Recording Device IN THE RECORDING SOFTWARE that you'd be using.

For instance, in Audacity, you do that at Edit/Preferences and then set the Recording Device to whatever device your mic is.

Typically, Recording Device: ALSA default will work for a conventional microphone plugged into the PC.

Also, make sure your mic works OK.

Good luck.

---

### Post by DkkD on 2008-05-11
Open alsamixer, find "CAPTURE" and set the volume to the max, then press the TAB key to open capture settings and set MIC as the defult capture device. Hope it helps.

---

