---
title: "Cursor waiting, gimme some commands...all eyes"
date: 2010-09-13
forum: Apple Hardware Users
---

### Post by techgrl on 2010-09-13
I would love to employ this (or even just edit mine) Xorg.conf if I could only get to a place to do so.

I have just installed now no less than 7 different versions of Linux on both G3/G4 towers. I also have some G3 iMacs to work on as well.

Here is my latest dilemma. What would you do next if:

1. You have successfully installed Squeeze

2. The install finalization prompts you to remove cd & restart

3. You remove CD, press return to Continue, system restarts

4. The system comes back up and you may either hit return at BOOT: or hit nothing at BOOK: and it will continue without you

5. Right before you think you will see your first run login, you see the following screen...(image attached).

6. Literally, I am asking what you would do next if when you invoke Control/Alt F1, you still only get the BOOT: prompt - not anything I would consider at terminal option to login

7. Or may I type root at BOOT:  ? I have tried and it doesn't prompt for PWD.

8. I have reinstalled more than twice.

Thank you.

---

### Post by techgrl on 2010-09-13
I FINALLY got into root terminal via Control/Alt F1

Then I typed ls

I cd to snoop around the various directories.

I ended up back at /

I then typed  VIEW xorg.conf.new

Now I am in the midst of figuring out how exactly to edit and save this conf so I might finally be able to have a display showing GNOME desktop.

---

### Post by linuxopjemac on 2010-09-13
What exact Mac are you using ? Give me a link in everymac.com pls.

---

### Post by techgrl on 2010-09-13
Several of these:

[http://www.everymac.com/systems/apple/mac_server_g3/stats/macserver_g3_350_bl.html](http://www.everymac.com/systems/apple/mac_server_g3/stats/macserver_g3_350_bl.html)


Several of these:

[http://www.everymac.com/systems/apple/mac_server_g4/stats/macserver_g4_400.html](http://www.everymac.com/systems/apple/mac_server_g4/stats/macserver_g4_400.html)

And several of these:

[http://www.everymac.com/systems/apple/imac/stats/imac_ab.html](http://www.everymac.com/systems/apple/imac/stats/imac_ab.html)

I am not having luck on the PwrMacs, getting a good xorg.conf  I finally made my way in and added lines to allow for HorizSync and VertRefresh and the like...and I still get no display.

---

### Post by linuxopjemac on 2010-09-14
If you are familiar with the xorg.conf concept, you might want to have a look [here]("http://mac.linux.be/content/xorgconf-files").

---

### Post by techgrl on 2010-09-14
Yes, in fact, I will say that last night I had the light bulb of all light bulbs shine in my brain. At some point I made it into xorg.conf.new, edited it and rebooted. Still the same outcome.

BUT <insert aforementioned light bulb here> at one point, I was re-reading some documentation and was stumped as to why I would find this xorg.conf.new in /root, but not is /etc/X11 as the documentation suggests. It occurred to me that if I opened/edited xorg.conf.new and gave it a new name, I could then mv it to the /etc/X11 directory where the POST (or whatever linux calls it) was expecting to find it.

It did so and instead of the pixelated screen I got a nice blue box alerting me that my xorg was not configured properly.

Hey- that is progress to me!

This morning I am now trying new combos of the xorg.conf to see if I can get my GUI to finally appear.

---

