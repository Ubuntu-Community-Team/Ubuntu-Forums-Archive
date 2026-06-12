---
title: "Games Are Slow in Linux"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2006-12-06
Why do games run so much slower in Linux? I use Wine, and it just makes the game unplayably slow :(

---

### Post by Tomosaur on 2006-12-06
Could be a number of reasons:

1) You may need to install the correct graphics drivers for your card. Ubuntu only installs 'basic' drivers by default, just to get things going.

2) Wine may not support your game properly.

---

### Post by Captain Kirk76 on 2006-12-06
I heard there was a list of games it can and can't play, where can i find that?

Also, i am using the Ubuntu basic drivers. my card is an nVidia GeForce 6

---

### Post by Biggus on 2006-12-06
Could it be becuase you are running an aplication in an emulator which is itself running on a third platform?

---

### Post by Captain Kirk76 on 2006-12-06
I don't understand that?
I am trying to run a Windows game (Locomotion) on Linux, using Wine, the game loads, but is a bit slow playing, it runs normal speed on Windows, so my system does run it OK.

---

### Post by tophatandy on 2006-12-06
I got wine from the repos and I think I have it.. it says i do... anyway..

you should be expecting some kind of lag when you are emulating an os within an os..

kinda alot of processing that is going on there.

---

### Post by Sefrin on 2006-12-06
Check to see if your app is in the wine database with the search tool here: [Wine App Database]("http://appdb.winehq.org/")

You should probably update to the specific nvidia driver.

I'm not sure how Wine works for sure, but I know of some applications needing certain dll files in the system32 directory.

---

### Post by theratster on 2006-12-06
but WINE Wine isn't an emulator!

it "should" run close to normal speed, because all the APIs are present to run it directly. Its not running in a virtual environment.

I'd say it depends on the game. More often than not, the display drivers that are included with Ubuntu don't allow full functionality of all the video cards. If it really bugs you, try to get the propietary driver, that should speed things up.

---

### Post by Captain Kirk76 on 2006-12-07
I have got the Linux driver, but how do i install it...

---

### Post by Adramelech on 2006-12-07
[http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")

---

