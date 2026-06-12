---
title: "yet another wireless internet problem!"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by bm13084 on 2008-03-25
I can't understand why I can't connect....


i pretty much followed [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) to get my usb trendnet card installed... in fact, im sure i did it right, since "wireless networks" now show up in networking, and because the card lights up, and I can find the names of available wireless networks in my area.  The problem comes in when i select a network from the list, because it just won't connect to it.  i know it can see the networks, because they have unique names... what would cause it to not connect? is it something simple?  i know it wouldnt let me add the ndiswrapper part in modules, but after restart, and plugging in my card... it starts up (which is fine by me... i use the card on two computers, so i'll just plug it in when i want to go online on this comp).

I am using gutsy and it is a dell latitude laptop... any help is very much appreciated! i know NOTHING about this OS so far haha

---

### Post by Het Irv on 2008-03-25
Are any/some/all of the wireless connections encrypted?  That may be giving you some problems.

---

### Post by bm13084 on 2008-03-25
no. im using a community network right now... it's open... the same one im trying to connect to on xubuntu...

currently on xp

---

### Post by Het Irv on 2008-03-25
I am assuming that you have a good signal strength.

What kind of USB dongle do you have?  Post output of: ```
lsusb
```

There may be some special compatibility issues with your wireless interface.

---

### Post by bm13084 on 2008-03-25
100% signal according to windows...

0bda:8189 Realtek semiconductor corp.

the walkthrough said to use windows drivers... but windows uses a third party network manager when i use this card... do you think that has anything to do with it?

---

### Post by Het Irv on 2008-03-25
It could be, but I doubt it.  
Do you have a wireless Icon in the top right?  If so what does it look like when you try to connect?

---

### Post by bm13084 on 2008-03-25
well, it's not a wireless icon like it would be in windows (graphically different), but when it's not connected to any network, it is two comps with an x between them.

if i click it, it shows me the two available networks in my area.  one is the one i use and the other rarely works (its a neighbors... it doesnt work on any of my comps though)... when i click my network... it turns into circles with an animated  circle in it... i assume the "trying to connect" animation.

it does that for a long time and i dont remember if i got an error message... i dont think i did.

i tried it again, and when i clicked the network, it did nothing... so i restarted (second time since i went through the steps) and now it wont recognize wireless anymore.  i tried re-installing the drivers in the gtk thing again, and it said they were already installed... it wont recognize the card anymore, except in lsusb... it's recognizing it in windows still, obviously, so its not the card... im so confused...

---

### Post by Het Irv on 2008-03-25
I don't think you installed it right in NDISWrapper,  
```
ndiswrapper -l
```

I think that command will list the installed drivers, check to make sure they are correct.

---

### Post by bm13084 on 2008-03-25
net8187b : driver installed

---

### Post by Het Irv on 2008-03-25
...and that's the windows driver..... hmmm..... odd..... 
when you get the icon that is the two dots with the animated circle,  the bottom dot represents your computer sending data and the top represents recieving.  The bottom should flash for a while (30 sec max) and then the to should light up for a sec before switching to bars.  

The only other idea that I have is to try a different network manager (Wicd is a good one).

---

### Post by bm13084 on 2008-03-25
how can i go about getting it without being able to connect to the internet?

---

### Post by Het Irv on 2008-03-25
Well... That was a pain to find, 
[https://sourceforge.net/project/showfiles.php?group_id=194573]("https://sourceforge.net/project/showfiles.php?group_id=194573")

Download the .deb file, If I remember right you have to jump some weird hoops to Install it (uninstalling the Default manager if I remember correctly).  If you have trouble, open a new thread, I can't remember how to do that.

---

