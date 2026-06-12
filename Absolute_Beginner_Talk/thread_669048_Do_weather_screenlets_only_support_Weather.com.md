---
title: "Do weather screenlets only support Weather.com?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by blooboy on 2008-01-16
Hi Friends!
I have been trying to install weather screenlet. I live in a small town and my place isn't listed in weather.com website. When I saw other weather sites as well as google weather, my town's information was there.

Is there any way to gather weather information from any of those sites in place of weather.com?

Alex

---

### Post by mdebusk on 2008-01-16
> **blooboy said:**
> I live in a small town and my place isn't listed in weather.com website.

I am in a similar position and solved this issue for myself some time back. Please read [this post in comp.os.linux.misc]("http://groups.google.com/group/comp.os.linux.misc/msg/3f75f489a97eedad?dmode=source&output=gplain") for how I did it.

If anyone can do it more efficiently (it was a bit of a PITA) I'd love to know how.

---

### Post by blooboy on 2008-01-16
Thanks MDEBUSK for the advice, but I am a linux noob and the method suggested is a bit over the head for me :)

Moreover weather.com is US centric. Can it be done for towns in place like India, Thailand etc. Maybe by quoting land coordinates...



> **mdebusk said:**
> I am in a similar position and solved this issue for myself some time back. Please read [this post in comp.os.linux.misc]("http://groups.google.com/group/comp.os.linux.misc/msg/3f75f489a97eedad?dmode=source&output=gplain") for how I did it.

If anyone can do it more efficiently (it was a bit of a PITA) I'd love to know how.

---

### Post by mozetti on 2008-01-16
> **blooboy said:**
> Moreover weather.com is US centric. Can it be done for towns in place like India, Thailand etc. Maybe by quoting land coordinates...

Yes - go to weather.com and get the forecast for the foreign location you need. When the page loads, the address will look like this: ```
http://www.weather.com/outlook/travel/businesstraveler/local/_GMXX0138_?from=recentsearch
```

The part I underlined in the above code is the code needed for weather.com. I've used that in multiple weather reporting apps relying on weather.com and it worked.

---

