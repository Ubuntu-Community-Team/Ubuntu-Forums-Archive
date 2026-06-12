---
title: "Update crapped my comp"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by johnnyw on 2007-10-20
I have posted this before but I got lil to no help..formatting my hdd aint an option

I have upgrade from dapper to 6.1 and my console looks weird ( see attach).. what shoudl I do??

[IMG]http://farm3.static.flickr.com/2160/1622295779_6ccb210428_o.png[/IMG]

thx

J

---

### Post by llamakc on 2007-10-20
Thanks for fixing the link. I'll see what I can dig up.

---

### Post by celticbhoy on 2007-10-20
Looks like it could be a font problem

---

### Post by HermanAB on 2007-10-20
If you have everything on a single partition, repartition so that you have a separate /home partition for your data, then re-install.  It only takes about 30 minutes to re-install Linux so I don't understand what your hangup with it is, unless you have all your data on a single partition - now you know why that is a bad idea.

---

### Post by adamorjames on 2007-10-20
Install the 139 updates and then see what happens.

---

### Post by llamakc on 2007-10-20
Have you tried resetting your fonts in System | Preferences? Perhaps you were using something that is no longer available?

---

### Post by fjf314 on 2007-10-20
> **adamorjames said:**
> Install the 139 updates and then see what happens.

I think that's just an image on the web page that's open.

---

### Post by celticbhoy on 2007-10-20
Looking at the screen it seems that the Terminal is working OK, just not displaying the menu's properly. So I dont think that re-formatting you HD is what is needed. I would look into the Font issue first to see if there is anything wierd there. Failing that try re-installing the Gnome-terminal through Synaptic.

---

### Post by Campingman on 2007-10-20
Can not help you with a solution but I have had this myself on a few occasions and I just restart to get rid of it.  Seems to happen when I have an issue with a picture viewer or a movie player.

---

### Post by adamorjames on 2007-10-20
> **fjf314 said:**
> I think that's just an image on the web page that's open.

ahhh :lolflag:

---

### Post by johnnyw on 2007-10-20
> **llamakc said:**
> Thanks for fixing the link. I'll see what I can dig up.

thanks m8

> **celticbhoy said:**
> Looks like it could be a font problem

hope so. in that case I would need some command as I cant enter folders ( it gives me a promp with some kind of a warning )

> **HermanAB said:**
> If you have everything on a single partition, repartition so that you have a separate /home partition for your data, then re-install.  It only takes about 30 minutes to re-install Linux so I don't understand what your hangup with it is, unless you have all your data on a single partition - now you know why that is a bad idea.
yep I have the whole OS in one partition. I am not very skilful ( a real noob really) when it comes to deal with partitions.. thats why I have attached an IDE drive as secondary with files I want to preserve no matter what

> **fjf314 said:**
> I think that's just an image on the web page that's open.

yep... thats right

Looking at the screen it seems that the Terminal is working OK, just not displaying the menu's properly. So I dont think that re-formatting you HD is what is needed. I would look into the Font issue first to see if there is anything wierd there. Failing that try re-installing the Gnome-terminal through Synaptic.

almost everything that uses fonts is crapped.. dont forget I also get error messages when opening folders.. cant make any more screenshots as everything is so destryed I can t even find proper menus in the menus bar :S

---

### Post by mivo on 2007-10-20
In your home directory, there is a folder called .fontconfig (it is hidden, you may need to turn on the display of hidden files). Rename this folder to something else and then restart X (ctrl+alt+backspace). If this does not fix it or you notice other problems, you can restore it.

The fact that Ubuntu is putting / on one partition in guided mode and does not even suggest the advantages of a separate /home partition is one of the distro's flaws (in my opinion). It backfires when people upgrade and experience issues.

---

### Post by johnnyw on 2007-10-20
thx m8. fisrt good answer.. will give it a shot

---

### Post by llamakc on 2007-10-20
That's a great idea about moving ~/.fontconfig and restarting X. I agree, the guided partition scheme should RECOMMEND a separate partition for /home and have a quick blurb about why it's a good idea. I wonder if there's an existing bug/request for that already?

---

