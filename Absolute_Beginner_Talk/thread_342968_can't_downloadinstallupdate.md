---
title: "can't download/install/update"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by julm on 2007-01-20
I just finished installing Ubuntu on my computer, and I'm trying to update my software and get wireless working, etc, but when I try to download the updates or packages, it gives me an error saying it was unable to fetch the things. I'm using the amd64 version of Ubuntu. Is there something I have to do?

---

### Post by mikewhatever on 2007-01-20
Since you only just installed, try following instructions on this page [http://users.bigpond.net.au/hermanzone/p5.htm](http://users.bigpond.net.au/hermanzone/p5.htm)

---

### Post by julm on 2007-01-20
hmm, I tried following the instructions on that site, but I can't update. When I tried updating from Synaptic, I get the error:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

I'm pretty sure it's not my internet connection at fault because I can post this...

---

### Post by mikewhatever on 2007-01-20
Can you specify some of the repositories that where not found? Meanwhile you can update what is available.

---

### Post by julm on 2007-01-20
none of the repositories were found.

---

### Post by mikewhatever on 2007-01-20
Are standard repositories enabled?

---

### Post by julm on 2007-01-20
I'm not sure. How do I check?

---

### Post by mikewhatever on 2007-01-20
See the link above. There is alot more than updating.

---

### Post by julm on 2007-01-20
uhh well when I did the sudo gedit /etc/apt/sources.lst, there was nothing inside the file...

---

### Post by mikewhatever on 2007-01-20
```
sudo gedit /etc/apt/sources.list
```

This one works. Don't know why the page says 'lst' and not 'list'.

---

### Post by subdee on 2007-01-20
> I'm trying to[...]get wireless working

I'm assuming you're connected by wire to the internet for now right?

---

### Post by julm on 2007-01-20
Ok, I uncommented the lines and everything, but Synaptic still is unable to connect to the repositories, giving me the same error message. And yes, I'm connected by wire.

---

### Post by mikewhatever on 2007-01-20
Another thing I can think of, is trying to check in System->Administration->Software Sources->Internet Updates. See if the boxes are checked there.

---

### Post by julm on 2007-01-20
The box "Check for updates automatically" is checked. Do all 3 have to be checked?

---

### Post by mikewhatever on 2007-01-20
That's not the point. Are 'important security updates' and recommended updates' boxes checked?

---

### Post by julm on 2007-01-20
I don't see those options. I'm running Dapper btw >_>. Does that make any difference?

---

### Post by mikewhatever on 2007-01-20
I  don't know, but it could. See the screenshot of mine.

---

### Post by julm on 2007-01-20
For me, the Software Updates is called Software Properties, and there's only the internet updates section (equivalent of your automatic updates), not ubuntu updates.

---

### Post by mikewhatever on 2007-01-20
Don't know what to say. Sorry I've wasted your time here. I hope some Dapper 64 expert will turn up. At least we kept the post on top.

---

### Post by burntmonk on 2007-03-07
I have this same problem...

I get the same error message and everything, but I'm not running Dapper 64, just regular Dapper.

---

