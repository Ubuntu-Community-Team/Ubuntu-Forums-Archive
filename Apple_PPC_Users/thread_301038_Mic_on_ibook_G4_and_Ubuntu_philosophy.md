---
title: "Mic on ibook G4 and Ubuntu philosophy"
date: 2006-11-16
forum: Apple PPC Users
---

### Post by boccaccio on 2006-11-16
Hi people,

Ubuntu is a community based linux distribution. As such everybody of us should/could give (no matter how small) contribution.

Well maybe this is my turn. ;)

As a user of an ibook G4 and as an ubuntu-lover, I have downloaded the live version of edgy and tried it on my laptop.

At the beginning there were so many new good things that I was really impressed!

I think I have found two bugs.

1) On the live version my webcam (Logitech quickcam 3000, one of those supported by the linux driver) did not work under ekiga. I downloaded the latest driver (of the Philips webcams), compiled it under the live-distribution (!) and then the webcam was up and running.

2) The microphone. This is a little bit more tricky point. The built-in microphone did not work at first when I was using Ekiga... and I was really puzzled by it. Of course I could use the usb mic of my webcam (and that worked very well), but in my office (without the webcam) I could not use ekiga if the built-in mic was not working.

I thought deeply, tried many different things, but still nothing.   I noticed that the same sound card was recognized as "PowerMac" in Dapper and "SoundByLayout" by Edgy... things were getting complicated.

Finally, a few days ago, I have found that the built-in microphone CAN work :D . How? Well, that also is a bit weird...

The first thing I did is loading Gnome's SoundRecorder. I chose microphone as source, and... it worked... [Now this sounds trivial, but not having tried the mic under ekiga first]

After that the mic was working under Ekiga (during the wizard-sound process). In other words if I try the mic in Ekiga first it does not work, but if I try it after having tried the mic in SoundRecorder, it works. I hope I was clear.

Now I can use Ekiga without webcam with the built-in mic, and record my voice reading Boccaccio's Decameron.

All this to say, that in the end I learnt a lot about linux. All this process also convinced me that Ubuntu Edgy is a fantastic release (not perfect, but an improvement with respect to Dapper). In fact already the live version is a fantastic live-cd.

I know there might not be any other Ubuntu distribution in the future for my ibook, but the hope never dies. I'd be there to test my machine/hardware and report the possible problems to you guys who form the soul of Ubuntu.

-- Boccaccio

---

### Post by casfindad on 2006-11-27
> **boccaccio said:**
> Hi people,


2) The microphone. This is a little bit more tricky point. The built-in microphone did not work at first when I was using Ekiga... and I was really puzzled by it. Of course I could use the usb mic of my webcam (and that worked very well), but in my office (without the webcam) I could not use ekiga if the built-in mic was not working.



=D> Thank you! I was about to give up on getting Ekiga to work with my laptop's internal microphone, and now the built-in mic works great with it. I am currently running Edgy on a Powerbook G4.

Just a clarification for others who want to implement your fix:

In Sound Recorder, choose File > Open Volume Control. When the Volume Control window opens, select Edit > Preferences. Check the box for "Input Source" and click close. A new tab (titled "Options") will show up in the Volume Control window. Click on the Options tab, and select "Mic" in the input source drop-down menu. Close the Volume Control window, and test that everything works by making a short recording in Sound Recorder. The internal mike should now work.

You can now test Ekiga via the [echo test]("http://www.gnomemeeting.org/index.php?rub=3&pos=0&faqpage=x62.html#AEN87"). If you're lucky, all should now work.

Thank you Boccaccio, for your contribution!

casfindad

---

### Post by linuxopjemac on 2008-02-09
I will have a look if it works for my Pismo too....I will keep you updated...I use Feisty btw

---

### Post by stream303 on 2008-02-09
Great writeups!  Thanks guys, that is going into the scrapbook immediately.

---

