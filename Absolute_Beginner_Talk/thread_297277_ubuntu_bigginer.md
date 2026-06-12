---
title: "ubuntu bigginer"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by ivanquijano on 2006-11-10
hi, i just install ubuntu in my computer. i do not know anything about linux. someone told me to get [www.getautomatix.com](www.getautomatix.com) but i do not jnow how to install, i have used windows all my life. i diced to change, ik have both operating systems in the computer.
what i do to make the mp3 play?
in windows u dowload an install, but here i  have no idea, please help me out!!!

ivan

---

### Post by adwait on 2006-11-10
You can use automatix, just open up Synaptic under System>Administration. In there, search for automatix and install it. Then run automatix via the menu

---

### Post by digby on 2006-11-11
Also, the [Ubuntu How To Guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") my be very useful for you.

---

### Post by Camellia on 2006-11-11
system -> admin -> Synaptic Package Manager

then Search for "gstreamer0.10", install everything you get in the result page except those with a second suffix
i.e. install
gstreamer0.10-*
but not
gstreamer0.10-*-*

ps: you don't have to install all of them, but this is kinda easier...

HTH

---

