---
title: "Microphone troubles..."
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by hippz-420 on 2007-10-21
My Dell Inspiron B120 Laptop has a line in/mic jack, and whenever I plugged in a mic when I had windows, it automatically recognized it and asked if it was a line in or a mic. With Ubuntu, it doesn't recognize anything. I cant even get Sound Recorder open because it gives me the following error message:
[I][B]
Your audio capture settings are invalid. Please correct them in the Multimedia settings.
[/B][/I]
So, I go into the mixer and f*** with the settings for a bit, and I get this error message when I try to test my "Sound capture" input from "Sound Preferences," which is located in "System -> Preferences."

[I][B]gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.

[/B][/I]I am getting really frustrated with this thing and I need some help!

Thanks,
             Chris

---

### Post by linuxwizard on 2007-10-21
Look over these

[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

[http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone](http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone)

---

### Post by hippz-420 on 2007-10-22
I have already tried everything both of those links tell me to do, but that just didn't cut it. Could it possibly be my sound card? I was looking through my Hardware Information (System > Preferences > Hardware Information) and found this...

[I][B]82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller

[/B][/I]I am not totally sure whether or not that it my sound card, but I'm thinking it is. There is more stuff to do with audio though...

[I][B]82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1

82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4

82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller

[/B][/I]I am just guessing that the Express ports are my line in and my headphone jacks on the side of my laptop (Dell Inspiron B120). Maybe it could be because there is a shiny Windows sticker on my laptop, meaning that the hardware doesn't support Linux or something, or maybe I just have some crappy stuff in there. Further in-depth help would me ***much*** appreciated.

Thanks again,
                      Chris

---

### Post by hippz-420 on 2007-10-22
I have also just added a poll to find out how many people actually have this problem, so that someone in power over how Ubuntu works can do something about it. Hey, maybe even Ubuntu 7.14 Hasty Hobbit? (I just made that up off the top of my head, nothing with too much thought behind it. :))

Chris

---

### Post by Rinulin on 2007-10-22
I'm having the same issue. Different onboard sound card, but the same issue. I'll try and check tonight which onboard sound card I'm using.

---

### Post by hippz-420 on 2007-10-22
I'm not totally sure if it's the microphone itself or the sound card. I'm stumped on this one.

---

### Post by Stunts on 2007-10-23
Hi, this is my 1st post on this forum (and on any other as for that matter!) and, well, I just got the exact same problem...
My soundcard is a "VT8233/A/8235/8237 AC97 Audio Controller" and the mic's been working just fine on Windows...
I have also tried the suggestions posted above, to no result... Hope someone can help with this... Thanks in advance.

Edit - browsing more threads I found that it is a bug and that it has apparently been reported... Guess all we can do now is wait for the fix.

---

