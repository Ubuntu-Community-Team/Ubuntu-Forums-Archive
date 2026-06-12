---
title: "sound is too quiet"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by fatherdaly on 2008-01-23
I've read other threads about this same problem, and the solution was the alsa mixer

Here's mine:

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.14 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: Realtek ALC861                                                         &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master                                                                 &#9474;
&#9474;                       &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;                                     &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;         &#9484;&#9472;&#9472;&#9488;          &#9492;&#9472;&#9472;&#9496;          &#9500;&#9472;&#9472;&#9508;          &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;         &#9474;
&#9474;         &#9474;OO&#9474;                        &#9474;OO&#9474;          &#9474;MM&#9474;          &#9474;MM&#9474;         &#9474;
&#9474;         &#9492;&#9472;&#9472;&#9496;                        &#9492;&#9472;&#9472;&#9496;          &#9492;&#9472;&#9472;&#9496;          &#9492;&#9472;&#9472;&#9496;         &#9474;
&#9474;                     100<>100      100<>100                                   &#9474;
&#9474;      < Master >       PCM           Mic         Caller I      Off-hook       &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
```

the PCM is set to max and still the sound is really quiet.

any Ideas?

---

### Post by KingWilliam on 2008-01-23
shouldn't the master be set louder to? Not sure, just guessing ;)

---

### Post by dannyboy79 on 2008-01-23
when you click on the volume icon in the upper right corner, then click device under the File menu, do you have alsa or oss picked? if you want to control it via PCM, I think you need to have the OSS driver picked. just a thought.

---

### Post by KingWilliam on 2008-01-23
I control my sound via PCM and have the ALSA driver selected there;)

---

### Post by fatherdaly on 2008-01-23
I don't know if I can change the master.

I've tried to change it but nothing I do has an effect on it so I presumed you can't change it...  can you change it?

---

### Post by dannyboy79 on 2008-01-23
are you issuing 
sudo alsamixer?
I don't think a user has access to change alsamixer but I could be wrong here.

---

### Post by fatherdaly on 2008-01-23
I open the terminal and type "alsamixer"

and then it opens up and I can change PCM and Mic.

Thanks for helping

---

### Post by fatherdaly on 2008-01-23
Thanks for all the help everyone, I found an answer on another thread.

All I needed to do was go to System > Preferences > Sound

Then I changed all the drop down menus to ALSA (except from Default Mixer Tracks)

And then reboot.

Thanks for the help everyone, and I hope this helps anyone else with the same problem
[B]
EDIT: scratch that. I just rebooted and its as quiet as ever. ARGH![/B]

---

### Post by fatherdaly on 2008-01-23
Ok so I found a page with a fix for the problem:

[**Here**]("http://ww2.coastal.edu/jcsteele/gutsy-S4134.html")

turns out that most of the laptops in this particular range have similar problems.

It says I need to edit:

 /etc/modprobe.d/alsa-base

How can I do this??

---

### Post by dannyboy79 on 2008-01-23
gksudo gedit /etc/modprobe.d/alsa-base

or you can use kate (if using Kubuntu) or good terminal editor is nano (that's what I use to edit files when I ssh'd into my box at home)

---

