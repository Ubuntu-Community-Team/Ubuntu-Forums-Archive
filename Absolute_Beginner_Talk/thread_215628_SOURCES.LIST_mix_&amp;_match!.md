---
title: "SOURCES.LIST mix &amp; match!"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by ProjectGod on 2006-07-14
hello

hmmm this may be the wrong place to ask. perhaps a really stupid question. but what's stopping someone from adding ubuntu repositories into another debian based distro's /etc/apt/sources.list?

i really want to try and risk it... i heard no two linux system has the exact same structure... for example slight variations in the FHS (file hierarchy system) where each distro places different objects in different directories...

i'm wondering cause i really want to assemble my own extremely light weight linux desktop machine that consists of a standard DSL installation... and then add the useful packages only found from ubuntu sources.

any feedback appreciated. :D

---

### Post by OpsVentus on 2006-07-14
Yes it's possible. And the reason why people normally won't use repository's from other distro's is becaus the FHS is different and some programs from the other repo won't work, becaus of that.

So if your want your own distro you can use the repos of Ubuntu/Debian, but you can wonder if you really got your own distro. When your using other repro's

---

### Post by ubuntu_demon on 2006-07-14
It's not adviced to just add some repositories to your sources.list . You should first make sure they work well with Ubuntu otherwise you will get package dependency problems which might be very ugly and hard to solve.

Here's some more information :

my recommended Dapper sources.list
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

What are your favorite non-official repositories for Dapper?
[http://www.ubuntuforums.org/showthread.php?t=206506](http://www.ubuntuforums.org/showthread.php?t=206506)

---

### Post by ProjectGod on 2006-07-14
excellent! thanks for the replys. i'll check the urls out. 

a friend of mine uses DSL extensively. she showed me how simple it was to install and how damn quick it was to reinstall if i stuff up on something. i was stoked. but the packages it offers in it's repos are quite limited... 

cheers for this. :D

---

