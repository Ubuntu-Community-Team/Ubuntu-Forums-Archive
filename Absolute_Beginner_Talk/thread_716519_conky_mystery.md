---
title: "conky mystery"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Stang94 on 2008-03-06
Hi there I have a quick question I have conky up and running but its in something like a widowed mode and not sitting on the desktop anyone have a idea how to go about fixing this thing .. Thanks again for the help [IMG]http://i131.photobucket.com/albums/p303/rdstang94/Screenshot.jpg[/IMG]   SORRY FOR THE LARGE PIC I DIDNT THINK IT WOULD BE THAT BIG

---

### Post by Meatshield on 2008-03-06
Since I was just doing this earlier today, just follow this link's setup:

[http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html](http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html)

But then before you save and close the config file add in:

```
background true
own_window_type desktop

```

and that should make the window disappear and have it sitting on the top left underneath the taskbar and any other windows, like you should want it I think. That config file also lets you edit it if you want it say in a different place (has to be in a corner though) and such. All the config file variables are here:

[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

Be sure also to go into the display code and make sure the interface it lists in the variables points to the right interface (so for my laptop's wireless this was eth1 not eth0)

But if you're not comfortable with that I'd be happy to make you a config file to get whatever effect you want out of it. :)

---

### Post by Stang94 on 2008-03-06
still not sure of how this is done yet do I just paste whats in the first link into the sample or what not sure sorry kinda new to conky

---

### Post by Stang94 on 2008-03-06
Ok whew I got it but now how do you fix it so that it dont close when I close out terminal lol

---

### Post by Stang94 on 2008-03-06
ok I guess I should of finished reading the link lol thanks again for your help it works great

---

