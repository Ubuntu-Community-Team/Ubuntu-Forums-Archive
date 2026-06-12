---
title: "High quality text to speech"
date: 2013-02-01
forum: Assistive Technology &amp; Accessibility
---

### Post by ebenfarnworth on 2013-02-01
I have been trying to find a good solution to TTS on Linux for about 8 months now and have done quite a bit of reading around. I have decided to post information on what I have found already as it may be useful to someone out there… However the question I’m trying to answer really is how to get a high quality voice like the ones from **Cepstral** working in Ubuntu or any other linux distribution? [www.cepstral.com](www.cepstral.com) a closed source program costing around $40. I can get it running fine in the command line but can’t find a suitable interface using it on a day to day bases.

I require a tts program to help me proofread nearly everything I write as without it I almost always have to many mistakes. There is not only good tts for Windows and Mac but for Android and ISO, so it should not be beyond the realms of possibility to have a working solution on linux.

First for the Linux one tts, festival, its very impressive that all this work has been done both free and open source. I have tried out some of the different voices, the ones people say are the best but they are still not good enough. Someone also wrote a nice simple bash script to use with festival and xsel. Then you can set a keyboard command to trigger it you have a very nice tts system. The script is from: [http://hak5.org/episodes/haktip-51](http://hak5.org/episodes/haktip-51) & [http://www.ghacks.net/2010/10/09/linux-text-to-speech-with-festival/](http://www.ghacks.net/2010/10/09/linux-text-to-speech-with-festival/)

```
#!/bin/bash

xsel | festival –tts –pipe
```

Now if we could find a way to use the cepstral swift engine in the same way, for me it would for fill all my needs.

Here is a forum post on how to make festival use better voices, but they were still not as good as the cepstral ones: [http://ubuntuforums.org/showthread.php?t=751169](http://ubuntuforums.org/showthread.php?t=751169)

Then there are screen readers like orca, which maybe grate for their intended use to read the whole screen for blind people and must stay running in the back ground all the time. However orca to me is not easy to use and I have not found a way to set it up to read only what I highlight or copy to the clipboard. But it has built in drivers for both cepstral swift, festival and espeak.

**KDE 3** seems to have had the perfect solution, with its ktts that could be used as a front end for festival, cepstral, espeak, and others. But in KDE 4 its been replaced with Jovie which in its current state of development can only connect to espeak. I also cannot find any information if its possible to run kde 3 apps on **KDE 4** and also no where to download the old ktts. Here is a grate tutorial on how to set up ktts but as ktts is now obsolete its useless: [http://awesomelinux.blogspot.jp/2009/04/text-to-speech-in-linux.html](http://awesomelinux.blogspot.jp/2009/04/text-to-speech-in-linux.html)

**Gespeaker** can be used as a front end to some speech engines (espeak and other voices) but dose not proved good enough quality results. Also with some of the talkers it’s not possible to stop them once they have started reading.

This is a company (**Digital Future** ® [http://www.digitalfuturesoft.com](http://www.digitalfuturesoft.com)) who have a linux front end for cepstral which they say they can sell for $99.

“[I]Dear customer
The version is experimental and it needs to be built and recompiled for ur version of Linux.
We can provide it for $99. Let us know if you agree and we will send you the secure payment link.
The adaptation process may take up to 2 weeks.
Let us know.
SupportDigital Future ® Team
[http://www.digitalfuturesoft.com](http://www.digitalfuturesoft.com)[/I]”.

I’m not shore about spending $99 on a program which is experimental and only dose what comes built into windows, mac and iso.

[http://www.wizzardsoftware.com](http://www.wizzardsoftware.com) lso have high quality voices for Linux but out of my budget.

**SVOX pico2wave** [https://launchpad.net/ubuntu/precise/+source/svox/](https://launchpad.net/ubuntu/precise/+source/svox/) have a very light wait system which is quite customisable and can create many different voices. But not really suitable for reading back lots of text at a time it seems to crash and was not clear enough for my purposes. Here is the recommended bash script:

```
#!/bin/bash
pico2wave -l=de-DE -w=/tmp/test.wav "$1"
aplay /tmp/test.wav
rm /tmp/test.wav
```

The **google chrome** extension speakit uses tts from an online server to convert text to speech however this is also not a good solution for an expat living in China working over very slow internet connections: [https://chrome.google.com/webstore/detail/speakit/pgeolalilifpodheeocdmbhehgnkkbak?utm_source=chrome-ntp-icon](https://chrome.google.com/webstore/detail/speakit/pgeolalilifpodheeocdmbhehgnkkbak?utm_source=chrome-ntp-icon).

**ispeech** is similar and to me also unusable solution: [http://www.ispeech.org/free.text.to.speech.tts.software](http://www.ispeech.org/free.text.to.speech.tts.software).

**JSpeak** is a newer tts with a nice simple gui, but still lacks the quality I’m looking for. 

So thats most of the relevant research I have done so far. I’m shore I have mist stuff out!… Please post any other solutions you have found below; all idea's are welcome. 
I’m most interested in a bash scrip to pipe text into cepstral swift or if anyone has brought the Digital Future software before, was it worth it?

Thanks in advance, Eben

---

### Post by frytek on 2013-02-02
It is also possible to install SAPI server on wine and use a SAPI voice. Tested to work with Ivona ([http://www.ivona.com/us/](http://www.ivona.com/us/) ) and Acapela ([http://www.acapela-group.com/text-to-speech-interactive-demo.html](http://www.acapela-group.com/text-to-speech-interactive-demo.html)) voices.
Demo voices from acapela work for one hour, then you have to reboot the wine SAPI server.
Demo voices from Ivona work as long as you don't turn your computer off, you have to run the installation/configuration script after each reboot. Registered versions should work infinitely. 

Let me know if you want to know the details, because this solution has also no GUI. 

Basically, you have to add this ppa:

deb [http://ppa.launchpad.net/ethanak/milena/ubuntu](http://ppa.launchpad.net/ethanak/milena/ubuntu) precise main

and install sapi4linux, libivolektor1, libsapilektor, libsapilektor-utils. Then check the README file in /usr/lib/sapi4linux/ on how to download and run demo voices within a *separate* wine environment. That guarantees 1. it will work 2. it will not interfere with your other wine programs, if any. 

You need a command line to read a file aloud or to produce wav/mp3.  

It is possible to choose one of installed voices, speed, pauses length and so on. 

The results are quite nice: 
 
[https://dl.dropbox.com/u/187581/test_lucy.mp3](https://dl.dropbox.com/u/187581/test_lucy.mp3)
[https://dl.dropbox.com/u/187581/test_heather1.mp3](https://dl.dropbox.com/u/187581/test_heather1.mp3)
[https://dl.dropbox.com/u/187581/test_salli_ivona.mp3](https://dl.dropbox.com/u/187581/test_salli_ivona.mp3)
[https://dl.dropbox.com/u/187581/test_amy_ivona.mp3](https://dl.dropbox.com/u/187581/test_amy_ivona.mp3)

A typical command line for making a file would be something like: 
sapilektor -a -r -s 1.3 -v salli test.txt - | lame --preset voice -r -m m -s 22050 - test_salli_ivona.mp3

To listen to a file use: 
sapilektor -s 1.3 -v Amy -o test.txt

---

### Post by ebenfarnworth on 2013-02-06
Thanks for the information. Yes I'm more looking for a gui solution for a native linux product like Cepstral. Cepstral works grate in the command line but I'm looking for a way to run in it gui or with a bash script like the one above, piping selected text with xsel to Cepstral swift.
Thanks again for your reply.

---

### Post by gaetanlord on 2013-05-08
Hi

Having some issue to implement.
I did install the sapilektor, and coud run it with your command mentionned with voice like Mike and Sam

I did download ivona voice (2), but can't seem to get ot work
The file I have in my ivoina_voice are
chantal.dat
eric.dat
control.dat

Not sure if they are the one I should expect, README mention 2 small files and many big (voice). I only have one small.

They are both in the ivona_voice directory under the sapi4linux directory

How could I use them, I did reinstall sapi4linux and force erasing the files. I do get a message that ivona voices are installed but when running your command It fail.
 
sapilektor -a -r -s 1.3 -v chantal meteo - | lame --preset voice -r -m m -s 22050 - meteo.mp3  

also sapiconfig -n  only return mike, sam and Mary]

Thank for any help

---

### Post by bobbiescap on 2013-05-19
Top post, thanks for the information and the effort you put in.

---

### Post by pc-athome on 2013-08-02
Ultimate Edition (can't pinpoint it in my collection - yet) used a closed source application for voices but it is 'free' - [http://www.mbrola.com/](http://www.mbrola.com/)

I understand the issue with using this pack is that recompiling the kernel has to be done in order for it to still work after kernel updates - can't remember where I read it.

---

### Post by frytek on 2013-09-11
I am starting a new thread on High quality text to speech GUI.
[http://ubuntuforums.org/showthread.php?t=2173822&p=12785866#post12785866](http://ubuntuforums.org/showthread.php?t=2173822&p=12785866#post12785866)

---

### Post by pushkarajthorat on 2014-01-17
> **frytek said:**
> It is also possible to install SAPI server on wine and use a SAPI voice. Tested to work with Ivona ([http://www.ivona.com/us/](http://www.ivona.com/us/) ) and Acapela ([http://www.acapela-group.com/text-to-speech-interactive-demo.html](http://www.acapela-group.com/text-to-speech-interactive-demo.html)) voices.
Demo voices from acapela work for one hour, then you have to reboot the wine SAPI server.
Demo voices from Ivona work as long as you don't turn your computer off, you have to run the installation/configuration script after each reboot. Registered 


Hi Frytek,

As Ivona 3 voices not available and acapela 's voices for only french language is available. Hence these steps are no longer functional.

Could you please upload the installables you have (with which you 've created those mp3 files) so that it could be used.

Thanks,

---

### Post by Bucky Ball on 2014-01-17
*Thread closed.*

See post #7.

---

