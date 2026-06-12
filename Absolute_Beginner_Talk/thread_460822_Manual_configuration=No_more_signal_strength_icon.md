---
title: "Manual configuration=No more signal strength icon"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by khardbored on 2007-06-01
Whenever I manually configure my wireless internet, as opposed to roaming, I lose my signal strength icon in the  panel. Is there any way I can get this back? Maybe a dockapp sort of thing that will show me signal strength? THanks a bunch!

---

### Post by brooksbp on 2007-06-01
Are you using NetworkManager Applet?

---

### Post by khardbored on 2007-06-01
Sure am.

---

### Post by brooksbp on 2007-06-01
```
sudo nm-applet
```

---

### Post by khardbored on 2007-06-01
I already have that running. See, if I set it to roaming it shows a nice bar-guage that displays my signal strength as the icon. But by setting it to manual, no more bar goodness.

Maybe I'm just being picky.

---

### Post by brooksbp on 2007-06-01
interesting. can't find any info about nm-applet's icon.... hopefully someone else does

---

### Post by khardbored on 2007-06-01
I downloaded netapplet and got it all setup. Got the same icon with a bit more functionality. Awesome. Thanks for the suggestions though!

---

### Post by BluePlum on 2007-12-16
Im having the exact same problem, How did u actualy get the wireless signal bar icon back?

---

### Post by BluePlum on 2007-12-17
?????

---

### Post by the Didey on 2007-12-17
it appears that they got a different applet.

I don't know why this happens.....it's weird.



I do know that you can run use the "network monitor applet" which has more configuration options.

Right click on the panel and click add to panel.

It's in the system section.

EDIT: sorry just looked....if you use system monitor it has a network option but no signal strength......and the network monitor doesn't have any configure options. It shows your signal strength but not in the bar style.   I also looked and you can get netapplet from synaptic, and that seems to have made khardbored happy. Hope that makes up for the false info.

---

### Post by BluePlum on 2007-12-17
My Nm-applet doesnt show as bar form :(

---

### Post by the Didey on 2007-12-18
sorry I wasn't too clear the network monitor should have the strength on the side but it isn't in the "cell phone bar" style. 

here's some words about netapplet which is what the other poster went with.

try that maybe.

---

### Post by gumpontheweb on 2008-01-05
[http://ubuntuforums.org/showthread.php?t=637327&highlight=network+signal+strength+icon](http://ubuntuforums.org/showthread.php?t=637327&highlight=network+signal+strength+icon)

The "notification area" had to be added to the panel. All the way at the bottom of the panel additions.

---

