---
title: "Bass Speak Sound Issue"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Cruciatum on 2008-03-10
Hey, my final (touch wood) problem, I'm running Ubuntu 7.10 on my Acer Aspire 7720G laptop, and I've got the sound working (albeit without it's Dolby Digital Live), but getting the little bass speaker on the underneath of the laptop working, is apparently beyond me.

I've looked for hours on Google for an answer, but obviously no luck.

It's just really annoying as all the songs and sounds have no depth to them and them sounding really cheap like a mobile phone.

Any ideas?

---

### Post by LuisGMarine on 2008-03-10
try editing your */etc/modprobe.d/alsa-base*?

type this command into a terminal :


```
gksu gedit /etc/modprobe.d/alsa-base
```


Near the bottom you should see a line like so:

```
options snd-hda-intel [COLOR="Red"]model=auto[/COLOR]
```

replace the line so it reads

```
options snd-hda-intel [COLOR="Lime"]model=acer[/COLOR]
```

If you don't have the line, add the one right above, reboot the computer and try sound.

---

### Post by Cruciatum on 2008-03-10
Yeah, that's how I got the front speakers to work, but bass speaker still does nothing.

---

### Post by LuisGMarine on 2008-03-10
Have you tried recompiling the alsa drivers?  Here is a post and a great guide to help you do so.  He made a script so all you have to do is run the script and it does all the hard work for you.

[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

Real easy to follow  , try that and then see if it works and let me know!

---

### Post by Cruciatum on 2008-03-10
Thanks a lot! I'll try that tomorrow, as it's really late here now :)

I'll let you know how it goes tomorrow.

---

### Post by Cruciatum on 2008-03-11
No luck :( maybe it's just something I'll have to sacrifice for Ubuntu.

I'm told you can get bass running by enabling the tone preference on the alsamixer, but I just can't seem to get that in my list of things.

---

