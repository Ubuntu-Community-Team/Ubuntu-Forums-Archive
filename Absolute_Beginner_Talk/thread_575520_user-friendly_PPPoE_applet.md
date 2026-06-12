---
title: "user-friendly PPPoE applet"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by alex008 on 2007-10-14
Hi,

I have just configured PPPoE connection at my parent's home and it works like a charm.

The only problem is that I don't wanna teach my parents to type commands in the terminal to use the ADSL connection (for example, to connect or to disconnect).

Is there any user-friendly applet, which would allow to see the status of the connection, as well as terminate or reconnect it as needed?

Many thanks for your help,
Alex

---

### Post by rahimveron on 2007-10-14
I dont know about the gui but you can use command line:
Open Terminal:
To connect```
pon dsl-provider
```
To Disconnect```
poff dsl-provider
```

I am assuming that you know the above commands, but i have no idea about GUI version.

---

### Post by alex008 on 2007-10-17
I know that :-) It's just I don't want my parents and the kids to mess with the command line. 

Thus,  I was looking if there's some very simple graphical applet to connect/disconnect and see the traffic stats (just like the connection status applet in windows).

many thanks,
alex

---

### Post by orange2k on 2007-10-17
You can create small scripts that execute these commands and add appropriate shortcuts on the desktop - there would be no significant difference, you just wouldnt have to type them in the terminal...

---

### Post by trash on 2007-10-18
There was a promissing little program that I tried a year or two ago but for the life of me I can't remember the name:(.
The last release I tried was really flaky and the developer wasn't really working on it anymore. I dunno why there is so little interest creating a GOOD user friendly program for dsl users like all the moms and aunties(even myself) who just want to click an aplet in their panel.
Hope somebody here remembers the name of it soon, i need to find a solution for my mom.

---

### Post by rahimveron on 2007-10-21
If you use Gutsy then there is a program called GNOME PPP. Its in the repo.

---

### Post by zvacet on 2007-10-21
That is for dial-up.Maybe **gpppon** can help.

---

### Post by mikewhatever on 2007-10-21
> **alex008 said:**
> Hi,

I have just configured PPPoE connection at my parent's home and it works like a charm.

The only problem is that I don't wanna teach my parents to type commands in the terminal to use the ADSL connection (for example, to connect or to disconnect).

Is there any user-friendly applet, which would allow to see the status of the connection, as well as terminate or reconnect it as needed?

Many thanks for your help,
Alex

It looks like all you need to do is to create launchers to connect and to disconnect. You can have them on the desktop or on one of the panels. To do it, right click where you want it and select "Create a launcher".

---

### Post by rahimveron on 2007-10-23
@mike
Could you elaborate on that launcher like what commands to put, etc.

Ok i figured it out.
1: To Connect:  Right click on the desktop>Create a Launcher & Give it a suitable name like Internet On & enter ```
pon dsl-provider
``` in the command option & select Application in Launcher under Type.
To connect just Double Click the Launcher created.
2:To Disconnect same as previous just enter ```
poff dsl-provider
``` in the command option.
Voila.

---

### Post by trash on 2007-10-25
> **zvacet said:**
> That is for dial-up.Maybe **gpppon** can help.

Ya thats the one! anybody know if it's been improved lately? It didn't work well at all last time i tried it

---

### Post by julien.fs on 2007-10-27
Hi I was looking for the same thing than you for a little more comfort. I recommend you to install the package **network-manager-kde**(works on gnome)  you will have a tray icon in your taskbar. Then right click->dialup connections->and click start connection. When active this place allow you to hang-up. 
If you want a tray icon who shows you that your connection is active install the package **knetdockapp** and you will have on system tray a specific icon when active and an unplugged socket icon when inactive : by clicking you will have some transfer informations but unfortunatly not the elapsed time for the current session. Don't forget to setup both applications to launch at startup via the gnome manager "System->Preferences->Sessions". Very convenient  :)

Hope it helps

Julien

---

### Post by nezam05 on 2008-07-20
well i found a solution in roaringpenguine.com. but i don know how to work with it.
can anyone tell?

---

### Post by Redptc on 2008-07-21
> **nezam05 said:**
> well i found a solution in roaringpenguine.com. but i don know how to work with it.
can anyone tell?

Can you tell us a bit more? What was it you found? Give us a link and we might be able to help!

---

### Post by MrKlean on 2008-07-22
I use Gnome PPP on Hardy, to connect my laptop thru my cell...works great..no problems !!

---

### Post by Redptc on 2008-07-22
> **MrKlean said:**
> I use Gnome PPP on Hardy, to connect my laptop thru my cell...works great..no problems !!

Is there any more detail that you have available to us?

---

