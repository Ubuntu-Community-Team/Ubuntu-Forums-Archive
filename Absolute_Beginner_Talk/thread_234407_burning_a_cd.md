---
title: "burning a cd"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by da1nonlymikeo on 2006-08-11
hey guys! im attempting to burn a cd to play in my car and im using gnomebaker but when i go to drag my .mp3 files into the audio disk section a pop up apears saying i dont have the plugins needed for audio/mpeg.

 what plugin do i need and where do i get it? synaptic i suppose?

---

### Post by jordilin on 2006-08-11
Take a look at
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
it explains all the necessary to play, burn and all about mp3 and other propietary formats

---

### Post by JerMe on 2006-08-11
For the lazy:
```
sudo apt-get install gstreamer0.10-plugins-ugly
sudo apt-get install gstreamer0.8-misc
sudo apt-get install gstreamer0.8-mad
```

Then try gnomebaker again to see if it worked.

---

### Post by da1nonlymikeo on 2006-08-11
> **JerMe said:**
> For the lazy:
```
sudo apt-get install gstreamer0.10-plugins-ugly
sudo apt-get install gstreamer0.8-misc
sudo apt-get install gstreamer0.8-mad
```

Then try gnomebaker again to see if it worked.




 mike@mike-laptop:~$ sudo apt-get install gstreamer0.10-plugins-ugly
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mike@mike-laptop:~$


 i get that for the first command.

---

### Post by ThrobbingBrain66 on 2006-08-11
whenever i've gotten that it's cause i have synaptic open at the same time that i try to install something with the terminal

---

### Post by jordilin on 2006-08-11
> **da1nonlymikeo said:**
> mike@mike-laptop:~$ sudo apt-get install gstreamer0.10-plugins-ugly
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mike@mike-laptop:~$


 i get that for the first command.

You have synaptic open. Close it and type the commands

---

### Post by christhemonkey on 2006-08-11
When i installed Gnomebaker, it still depends on all the 0.8 versions of the Gstreamer framework.

So even if you install all the 0.10 plugins, it still won't work.

Just my £0.02

---

### Post by jordilin on 2006-08-11
> **christhemonkey said:**
> When i installed Gnomebaker, it still depends on all the 0.8 versions of the Gstreamer framework.

So even if you install all the 0.10 plugins, it still won't work.

Just my £0.02

Well, talking about preferences, I would go for K3b. There's no app like k3b in Gnome although bonfire looks promising:
[http://perso.orange.fr/bonfire/index.htm](http://perso.orange.fr/bonfire/index.htm)

---

### Post by weblinx on 2006-08-11
dont burn cd's, buy them from store...dont you like reading the credits and artwork that comes with pro packaged cd's
[Americuz Lost Angel.]("http://www.lost-angelz.com")

---

