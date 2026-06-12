---
title: "I want some kind of wireless notifier."
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by gergtreble on 2007-02-18
Hey. Just installed xubuntu on my girlfriends laptop. Its running great. Wireless is working, and im downloading amarok and open office as I type.

Now. theres just one thing thats missing. In ubuntu theres a nice little icon in the system tray that lets me know the wireless is connected.

Is there anything I can download for xubuntu that will give me the same or similar functionality?

Also is there a tutorial anywhere about how to confugure launcher buttons? Ive stupidly deleted the firefox launcher next to "applications" and I cant figure out 1)How to get it back and 2)where the hell the firefox  ".exe" (forgive the windows terminology) is located.

Thanks in advance.

---

### Post by taurus on 2007-02-18
1.  I think you are looking for Network Manager.  Open a terminal and type
```
sudo aptitude update
sudo aptitude install network-manager
```

2.  If you want to run firefox from a terminal, just type
```
firefox
```

---

### Post by reacocard on 2007-02-18
> **taurus said:**
> 1.  I think you are looking for Network Manager.  Open a terminal and type
```
sudo aptitude update
sudo aptitude install network-manager
```

2.  If you want to run firefox from a terminal, just type
```
firefox
```

Actually, to get the icon, he needs to
```
sudo apt-get install network-manager-gnome
```
as well. Then to launch the icon, run
```
nm-applet
```
You can have it start at login by adding it in Settings -> Autostarted Applications

---

### Post by gergtreble on 2007-02-18
Ah! right! 

I was wondering why there was no icon.

So should I uninstall what Ive done and then reinstall with that code?

---

### Post by gergtreble on 2007-02-18
Ok i just did all that. Got the icon sat up there in the top right hand corner of my nice blue xubuntu descktop, but its taunting me by telling me theres no nework connection. Even though im sat here using the internet.

Weird eh?

---

### Post by taurus on 2007-02-18
Click the icon with the right button and configure it to look for the right network card.

---

### Post by gergtreble on 2007-02-18
When I right click on it I get 4 choices.

Enable Networking (ticked)
Connection Information (greyed out)
About
Remove.

Are you sure this works with xubuntu?

---

### Post by gergtreble on 2007-02-19
Ok ive stuck with this for a while and just cant get it working under xubuntu. I also tried kwirelessmonitor, which looked like it was exactly what I wanted. Unfortunately that ran for about 1min then crashed every time. 

So any other ideas? Im this close to sacking off XFCE and just installing gnome over the top.

---

### Post by Jussi01 on 2007-02-19
Try wifi-radar. I have a feeling it works on xfce...

---

### Post by gergtreble on 2007-02-19
Ok i will.

Thanks.

---

### Post by gergtreble on 2007-02-19
Just tried it. 

Looks like a nice little app. But is there any way to configure it so it sits in the system tray?

---

### Post by Jussi01 on 2007-02-19
Weid, It used to do it on mine no problems... I will have a look.

---

### Post by nike984 on 2007-02-19
I think that the wifi does not show up because there is some options in your configuration.
Take a look at /usr/share/doc/network-manger/readme.debian
It's the network-manager configuration document.

Then open /etc/network/interfaces
using gedit or whatever text editor that you prefer and 

delete any additional options expect  "auto" & "dhcp" terms

in wifi device. (look at readme.debian documents)

Then save the file and wifi device will show up.



You can also put the system tray icon by right clicking the panel 


and click 'add to the panel ' , add the network-manager icon in the list. 



good luck :lolflag:

---

### Post by gergtreble on 2007-02-19
Thanks nike. Got the network manager running on my wireless card now. Its not realy what I was after. I was kind of hoping to find something that will measure my wireless strength and sutch. But this is a useful little applet.

---

