---
title: "[SOLVED] Should I install &amp;quot;Edgy Main&amp;quot;? or Is it something that's built into Ubuntu 7."
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by ahuman on 2008-02-24
> **tango_ninja said:**
> I added this line of code (repository) to my repository sources list. This is a text file found in my computer directory under  **/usr/apt/sources.list** 
...To modify this file, I  used gedit:

```
sudo gedit /usr/apt/sources.list
```
add your line to this text file, save and close. mission accomplished :)    make sense?

After I followed those instructions I got an error-message (seen below). **[COLOR="Red"]What should I do after I get the following error-message? Should I install "edgy main" (or is it built in to Ubuntu 7.10-Gusty)?: [/COLOR]**

[img]http://img229.imageshack.us/img229/4536/screenshotsourceslistusrs5.png[/img]

---

### Post by warbird on 2008-02-24
your sources.list file is in /etc/apt/sources.list, not /usr/apt/

---

### Post by ahuman on 2008-02-24
[COLOR="DarkRed"]Thanks for your help. I appreciate you.[/COLOR]

---

### Post by northern lights on 2008-02-24
Even though the thread being solved (good thin you caught on the marking early) and your Beryl problem having been sorted also, one hint for the future: Your profile says you run Gutsy, right? Why would you wanna add an edgy repo in the first place? Wrong parameter there...

---

