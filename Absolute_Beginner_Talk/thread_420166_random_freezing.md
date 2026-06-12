---
title: "random freezing"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by xboxbman on 2007-04-23
I recently upgraded my desktop motherboard, graphics card and CPU.  I had initially kept the same verion of Ubuntu on the hdd, and all seemed well except for the occasional freeze.  I would leave the pc alone for a few minutes and it would just lock up.  Or sometimes it would lock up while I was using it.  With the release of Feisty, I decided to go with a clean install.  But it's still freezing.  It's a real pain, because it freezes while I'm in the middle of installing stuff.  I thinking this is some kind of hardware problem, like dodgy RAM or something.  I am currently using the generic kernel with an AMD64 X2.  Would not using the 64bit kernel cause this?  It jsut finished it's first pass through memtest86+ that's on the live disc and passed with no errors.  I'm totally at a loss here

---

### Post by MikeEvans on 2007-04-23
Sounds like a thermal problem.  Try doing some heavy processing on it for 10 minutes and then check the temp.

```
acpi -t
```

---

### Post by xboxbman on 2007-04-24
> **MikeEvans said:**
> Sounds like a thermal problem.  Try doing some heavy processing on it for 10 minutes and then check the temp.

```
acpi -t
```

It gives me "no support for device type :thermal"

---

### Post by AlexenderReez on 2007-04-24
if want to check temperature for sytem...better use sensor-applet ...of course you need to install sensor detector for that...

---

### Post by xboxbman on 2007-04-24
> **reez0105 said:**
> if want to check temperature for sytem...better use sensor-applet ...of course you need to install sensor detector for that...

where do i get sensor detector?

---

### Post by AlexenderReez on 2007-04-24
this guide still work...but escape when it ask to execute python there....we doesn't need it...

> [http://news.softpedia.com/news/How-to-Install-lm-sensors-on-Ubuntu-47205.shtml](http://news.softpedia.com/news/How-to-Install-lm-sensors-on-Ubuntu-47205.shtml)

---

### Post by MikeEvans on 2007-04-27
Not sure how to fix acpi but other people with the same problem seem to have had success with a system monitor called Conky which can be installed through Synaptic.  Here is Conky's site:

[http://conky.sourceforge.net/]("http://conky.sourceforge.net/")

Is you case well ventilated?  Here is a short guide on proper case cooling:

[http://www.xoxide.com/computer-cooling.html]("http://www.xoxide.com/computer-cooling.html")

Your issue can be caused by other things like an overloaded power supply.  Conky may help you determine that also.

---

