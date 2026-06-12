---
title: "low Screen resolution comparing to windows! plz help"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by ke3pup on 2006-06-09
hi guys

i have an Acer TravelMate 4060 with Intel Graphics Media Accelerator 900. on windwos i get 1280 * 1024 resolution but on Ubuntu it can only archive 1024 * 768! it's rather small screen space to browse internet for long.

can anyone please tell me what steps i can take (ideally HowTo cause i dont know much about linux) to get a higher resoultion? thanx 

P.S. i tried "sudo dpkg-reconfigure xserver-xorg" and after following the wizard i ended up having the same resolution as befroe.

---

### Post by _simon_ on 2006-06-09
Hi,

Please take a look here, hopefully one of the suggestions will work for you.

[https://wiki.ubuntu.com/FixVideoResolutionHowto?highlight=%28resolution%29](https://wiki.ubuntu.com/FixVideoResolutionHowto?highlight=%28resolution%29)

---

### Post by ke3pup on 2006-06-10
thanx for the link, i tried all the suggestions there but im still on 1024x768! i've followed "sudo dpkg-reconfigure xserver-xorg" and choose ONLY 12800x768 which i know is supported by my display (Acer TravelMate 4060) but still in the "Screen Resolution" i only have 1024x768, 800x600 and lower! 

i tried many diffrent combinations and resolutions to see what happens but nothing changes! please help guys, what am i doing wrong? here's my "xorg.conf" file, all of it , i dont see any 1024x768 in that file yet that's what i get!

---

### Post by IYY on 2006-06-10
First, for the obvious solution: did you restart the X server after making the change? Ctrl+Alt+Backspace to kill it.

Second, here is the section of the xorg.conf file you specified that deals with the resolutions:

```

        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1280x960" "1280x768"
        EndSubSection

```

So, 1280x768 is on there, but it's not the one it should choose by default. It would appear it tries to load 1280x1024, but fails, so falls back to 1280x768. It's possible that your HorizSync and VertRefresh are wrong (check in your monitor's manual. I don't think that's the problem, but having the correct values is better anyway). Also, try switching to the vesa driver, just to check if that helps.

---

