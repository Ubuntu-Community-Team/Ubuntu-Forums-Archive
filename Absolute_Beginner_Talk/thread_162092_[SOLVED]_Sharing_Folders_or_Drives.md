---
title: "[SOLVED] Sharing Folders or Drives"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by joeartis on 2006-04-18
I have 2 machines with windows xp on and 1 with Ubuntu, I would like to file and folder share between all 3 machines like I can between the 2 xp machines, is this possible? and if so how do I do it? Thanks in advance to any one who can help

---

### Post by stig on 2006-04-18
Hi,
Try Nautilus-Share:

[http://gentoo.ovibes.net/nautilus-share/mediawiki-1.4.4/index.php/Accueil](http://gentoo.ovibes.net/nautilus-share/mediawiki-1.4.4/index.php/Accueil)

It's very easy - just a quick download then a couple of changes in Nautilus file manager. It worked for me and I'm a newbie!

---

### Post by joeartis on 2006-04-18
What is nautilus and how do I open it?

---

### Post by B3Nji on 2006-04-20
[QUOTE=joeartis]What is nautilus and how do I open it?[/QUOTE]

nautilus is your file manager. 

It is equivalent to Windows Explorer in XP. You are using it when you are viewing your files.

---

### Post by rubrboots on 2006-04-20
Hey joeartis

I am a newbie as well but this is how i did it. First install Samba using synaptic. 
Then go to share folders option (i think its in the administration menu. And +add a the folder that you want to share.

Now when you try to access the folder from a windows machine it might ask you for a password and username, none that you enter will work. If this is the case you have to make a change: 

```
sudo gedit /etc/samba/smb.conf
```

You will see a the line security = user in the smb.conf file type in security = share just below it so it looks like below.>

```
; security = user
  security = share
```

Then save and restart samba.

```
sudo /etc/init.d/samba restart
```

Try this, if you still have problems I will try to help

---

### Post by DJ-Power on 2006-12-31
Thanks rubrboots that worked for me perfectly.
Regards
DJP :)

---

