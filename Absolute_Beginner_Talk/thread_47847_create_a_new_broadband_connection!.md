---
title: "create a new broadband connection!"
date: 2005-07-10
forum: Absolute Beginner Talk
---

### Post by Snitz on 2005-07-10
I have found the command to create a new broadband connection:

**sudo pppoeconf**
[http://ubuntuguide.org/#configurenetworkconnections](http://ubuntuguide.org/#configurenetworkconnections)

but it's not quiet working.
first it says that it needs to detect my eth networkcards

[IMG]http://img.photobucket.com/albums/v217/snitz0/1.jpg[/IMG]

then

[IMG]http://img.photobucket.com/albums/v217/snitz0/2.jpg[/IMG]

and then

[IMG]http://img.photobucket.com/albums/v217/snitz0/3.jpg[/IMG]

but after it finishes scanning, it gives me this

[IMG]http://img.photobucket.com/albums/v217/snitz0/4.jpg[/IMG]

so please tell me what's the problem
and why can't I create a broadband connection (pppop) so I can connect to the internet?

---

### Post by Snitz on 2005-07-10
anyone please!

---

### Post by sapo on 2005-07-10
your modem is USB or connected to the ethernet card? if it is USB its not gonna work with pppoeconf.. you need another solution

---

### Post by Snitz on 2005-07-10
[QUOTE=sapo]your modem is USB or connected to the ethernet card? if it is USB its not gonna work with pppoeconf.. you need another solution[/QUOTE]
 it's connected through ethernet card, and it worked, as u see im not on ubuntu connected to the internet
but the thing is, I don't have to dial anything, the internet is connecting by itself on the startup
I don't know if there is or there isn't internet becoz im not the one who's connecting it
and I donno how to check to see how much sent/received bytes!!!

---

### Post by sapo on 2005-07-10
[QUOTE=Snitz]it's connected through ethernet card, and it worked, as u see im not on ubuntu connected to the internet
but the thing is, I don't have to dial anything, the internet is connecting by itself on the startup
I don't know if there is or there isn't internet becoz im not the one who's connecting it
and I donno how to check to see how much sent/received bytes!!![/QUOTE]


hehe thats normal.. to see the conection status just do it:

Right click on the gnome panel -> Add to Panel -> network monitor

Then right click in it -> properties -> general and chose ppp0 on the Connection menu...

Then you just have to double click the icon to see the status.. like this:

[[IMG]http://img71.imageshack.us/img71/6826/screenshot3xz.th.png[/IMG]](http://img71.imageshack.us/my.php?image=screenshot3xz.png)

And to connect manually.. type in a terminal: pppd call dsl-provider

---

### Post by Snitz on 2005-07-10
[QUOTE=sapo]hehe thats normal.. to see the conection status just do it:

Right click on the gnome panel -> Add to Panel -> network monitor

Then right click in it -> properties -> general and chose ppp0 on the Connection menu...

Then you just have to double click the icon to see the status.. like this:

[[IMG]http://img71.imageshack.us/img71/6826/screenshot3xz.th.png[/IMG]](http://img71.imageshack.us/my.php?image=screenshot3xz.png)

And to connect manually.. type in a terminal: pppd call dsl-provider[/QUOTE]
 I can't fine the gnome panel, where is located?

---

### Post by sapo on 2005-07-10
[QUOTE=Snitz]I can't fine the gnome panel, where is located?[/QUOTE]

its the top bar in my screenshot..

---

### Post by Snitz on 2005-07-10
[QUOTE=sapo]its the top bar in my screenshot..[/QUOTE]
 wooooooooooooow
dude you rock
thx for the tip!!!!

---

