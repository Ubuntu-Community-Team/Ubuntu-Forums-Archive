---
title: "manual installation troubles"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Helven Ink on 2008-01-21
I can't get online, I have the Intel3945 wifi card with Gutsy Gibbon, and after trying everything else I can find to try and failing, I decided to try installing wicd.
I d/led the .deb from sourceforge, and copied it to my laptop. I double clicked it, and it immediately displayed the error "conflicts with installed package, Network Manager" ...so I uninstalled network manager, rebooted, and tried again, and it still says  "conflicts with installed package, Network Manager"
...wtf?
anyone have any idea on how to help me with this?

                      Jon

---

### Post by Helven Ink on 2008-01-22
bump

---

### Post by spiderbatdad on 2008-01-22
this card should work fine. sometimes NM takes a little trail and error configuring..try roaming mode. could you post the output of ```
sudo lshw -C net
```

you may need wpa supplicant

---

### Post by Helven Ink on 2008-01-22
The card doesn't work, I've scouring the forums, and trying all the different methods that people have posted to try and get this specific wifi card to connect, and all of them have failed.
The only possible fix I haven't tried is installing wicd to replace network manager, and I can't do that for some reason. It's starting to get on my nerves... =p
I also can't reinstall network manager now... I tried loading it from the ubuntu disc, but it doesn't seem to work.

---

### Post by AshG on 2008-01-22
(0.476000).. MP-BIOS bug:8254 timer not connected to IO-APIC
(0.476000) Kernel panic- not syncing: IO-APIC timer doesn't work! Boot with apic+debug and send a report. Then try booting with the 'noapic' option.


That is the message I am getting when I tried to install. Anyone can help me? 
I am a complete novice and would appreciate simple language replies.
Thanks


AshG

---

### Post by spiderbatdad on 2008-01-22
is your notification area missing? it usually resides there...maybe right click on panel and select add to panel...sorry if this is too obvious, and you tried all this. If you've removed the notification area, you'll need to add one. wicd...i know nothing about.

maybe this post will help.[http://ubuntuforums.org/showthread.php?t=307659&page=2](http://ubuntuforums.org/showthread.php?t=307659&page=2)

---

### Post by Helven Ink on 2008-01-22
I don't know what you mean by notification area...
I'm pretty green here.

---

### Post by spiderbatdad on 2008-01-22
the notification area is part of your top panel...upper right, begins with two vertical row of 6 little dots, usually time & date are there and a shut down button.

---

### Post by Helven Ink on 2008-01-22
I don't see 2 vertical rows of 6 dots, Just time and date, shutdown, network connections show search entry, and mic options

---

### Post by spiderbatdad on 2008-01-22
lol there are now 2 threads with this wireless card on the first page of the Forum. The other is Help! by Shron. I'm sorry I don't have a quick solution for you. Only have what I read in the link above. You should be able to right click in the notification area and add a network monitor applet. oh! or add the notification area to your panel

---

### Post by Helven Ink on 2008-01-22
As far as I've been able to tell, there at least 10 or 15 threads dedicated to problems with the intel 3945 wifi card... I've read most of them, and none of them have been able to help... It's really frustrating. As common an issue as this is, you'd think there would be a fix by now... =p
...erm an all inclusive fix maybe...  heh

---

### Post by spiderbatdad on 2008-01-22
are you trying to connect to an encrytped network? If so, there are some difficulties. You will surely need wpa supplicant from synaptic, and i believe the encryption key sometimes needs to be in quotes.

---

### Post by Helven Ink on 2008-01-22
I put the key in quotes, and I connected! ...but I still can't access the net.
Where can I get the WPA supplicant?

---

