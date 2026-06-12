---
title: "Audacious Skins"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Krishnan on 2007-11-06
Is there anyway i can change the audacious skins. If then please tell me the procedure

---

### Post by jordanmthomas on 2007-11-06
You should use winamp 2.x skins or XMMS skins for audacious.

[http://www.winamp.com/skins](http://www.winamp.com/skins)   (make sure you get classic skins)
[http://www.customize.org/list/winamp2](http://www.customize.org/list/winamp2)
[http://skinz.org/skins.phtml?category=21](http://skinz.org/skins.phtml?category=21)

Copy any skin you download in to 
```
~/.local/share/audacious/Skins
```

Then, in audacious, right click the player and go into the preferences to change your skin.  Hope this helps.

---

### Post by Krishnan on 2007-11-07
Thanks a lot

---

### Post by jordanmthomas on 2007-11-07
If the folder doesn't exist, just create it.  Audacious should pick up on it.  

Also, you can copy the skins into /usr/share/audacious/Skins (if this doesn't exist, you may want to consider reinstalling audacious)

---

### Post by Krishnan on 2007-11-07
I got the folder audacious there but now Iam getting an error while copying the file under skins of audacious i.e. Error while copying to usr/share/audacious/skins. You do not have permission to write to this folder

---

### Post by jordanmthomas on 2007-11-07
do it with sudo 
```
sudo cp nameofsin /usr/share/audacious/Skins
```

or launch a file browser as root:
```
gksudo nautilus
```

---

### Post by Tsu Doh Nymh on 2008-01-20
> **jordanmthomas said:**
> do it with sudo 
```
sudo cp nameofsin /usr/share/audacious/Skins
```

or launch a file browser as root:
```
gksudo nautilus
```

I can use the command line, but I'm curious: Is there a way for non-technical users to use the GUI to do this? It seems to me that they should be able to do things like this without using sudo and the command line. I'm considering changing permissions on the whole /usr directory to allow all to avoid problems like this.

---

### Post by jordanmthomas on 2008-01-20
Certainly, just press alt + F2 (like the windows run command)
and type in
```
gksudo nautilus
```

You can make a launcher to put on your panel that runs this as well.

Don't change permissions on /usr because then anyone on your system could mess with it pretty badly.

---

### Post by DMK62 on 2008-01-20
I would definitely leave the permissions on etc alone. The skins can be placed in 2 locations. usr/share...  and local/share... Open nautilus to your Home directory and go to View>Show Hidden Files and go to local and then share and there should be an audacious folder in there and inside that there is a skins folder ( read post by jordanmthomas ). If you go outside of your home folder and want to do anything more than view you will have to have sudo/root  access. 

hth 

Dale

---

### Post by DMK62 on 2008-01-20
Long day lol.... don't change the permissions on usr and follow his instructions as per his nov 6th post. It's about as easy as it will get. The Xmms player was a lot more easier when it came to adding skins. Xmms is no longer in development but still available in the repositories. Some of the formats such as flac ( and its decoder ) will not work but it handles ogg and mp3 well.

Dale

---

### Post by johnnylavah on 2008-02-25
> **jordanmthomas said:**
> Certainly, just press alt + F2 (like the windows run command)
and type in
```
gksudo nautilus
```

You can make a launcher to put on your panel that runs this as well.

Don't change permissions on /usr because then anyone on your system could mess with it pretty badly.

that works nicely...thanks!

---

