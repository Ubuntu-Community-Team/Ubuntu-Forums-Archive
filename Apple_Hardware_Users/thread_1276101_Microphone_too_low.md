---
title: "Microphone too low"
date: 2009-09-26
forum: Apple Hardware Users
---

### Post by WindPower on 2009-09-26
Hi, I have a MacBook Pro that I bought about three weeks ago. Since it was very recent, I assumed all the while that it was a MacBookPro5,5 and followed the [MacBookPro5,5/Jaunty instructions](https://help.ubuntu.com/community/MacBookPro5-5/Jaunty) instructions on the Wiki, and they have worked flawlessly. Yet, out of curiosity, one day I ran "sudo dmidecode -s system-product-name" just out of curiosity and it said "MacBookPro5,3"! Does that mean I did not buy the latest MacBook Pro model? I ordered it from Apple...

Anyway, sound was not working out of the box, so I followed the sound instructions on the MacBookPro5,5 page, which made both the sound and the microphone work. However, the microphone volume is extremely low. I have to shout very loudly in order to hear anything out of the recording. That, and I get a very noticeable (~500ms) audio lag in Windows apps running in Wine with the alsa driver, though that is a secondary problem.

Time passed and then I ran "sudo dmidecode -s system-product-name" to find out that I didn't follow the correct instructions page. So I thought that my audio would work if I followed the audio instructions on the MacBookPro5,3, but it turns out that the code to execute is exactly the same between the two pages, so this wasn't the problem.
So now I still have my microphone problem :(

Here's alsamixer -V all:
```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.18 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA NVidia                                                                             &#9474;
&#9474; Chip: Cirrus Logic CS4206                                                                    &#9474;
&#9474; View:  Playback  Capture [All]                                                               &#9474;
&#9474; Item: Master [dB gain=0.00]                                                                  &#9474;
&#9474;                                                                                              &#9474;
&#9474;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;                &#9484;&#9472;&#9472;&#9488;                          &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;                          &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;                          &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;                          &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;                          &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;                          &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;                          &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;                          &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;                          &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;                          &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;                          &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;                          &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;                          &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;      &#9492;&#9472;&#9472;&#9496;      &#9500;&#9472;&#9472;&#9508;      &#9484;&#9472;&#9472;&#9488;      &#9492;&#9472;&#9472;&#9496;      &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;      &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;     &#9474;OO&#9474;      &#9474;OO&#9474;                &#9474;OO&#9474;      &#9474;OO&#9474;                &#9474;OO&#9474;      &#9474;OO&#9474;               &#9474;
&#9474;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;                &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;                &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     L    R    &#9474;
&#9474;                                                                                    CAPTUR    &#9474;
&#9474;      100    100<>100  100<>100  100<>100            100<>100                      100<>100   &#9474;
&#9474;  < Master > Headphon    PCM     Front Sp  Surround  Surround   IEC958   IEC958 D  Capture    &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```
As you can see, I just turned everything to the maximum and my microphone is still way too low.
All my apps are using ALSA and there is no pulseaudio/esound/whatever daemon running, it's all pure ALSA.

I read about a "Microphone boost" option in alsamixer, but I can't seem to see it. Perhaps it is the solution to my problem, but how to enable it?

Running Kubuntu 9.04 64-bit with KDE 4.3 and kernel 2.6.28-15-generic.

---

### Post by crocowhile on 2009-09-27
[http://ubuntuforums.org/showpost.php?p=7959332&postcount=169](http://ubuntuforums.org/showpost.php?p=7959332&postcount=169)

---

### Post by WindPower on 2009-09-27
> **crocowhile said:**
> [http://ubuntuforums.org/showpost.php?p=7959332&postcount=169](http://ubuntuforums.org/showpost.php?p=7959332&postcount=169)I do not use PulseAudio, I am on Kubuntu which uses ALSA :(

---

### Post by WindPower on 2009-10-27
I caved in and installed PulseAudio, but still couldn't set the volume to 150% in any sound mixer, or check a "Microphone boost" checkbox anywhere in alsamixer or KMix or whatever. I solved it by following this: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275998/comments/109](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275998/comments/109)
Basically, it creates an extra audio interface which can be software-amplified up to +50 dB (After following the instructions, you have to go to alsamixer and increase the volume of the input device that was just created).

Not sure if I should mark this as solved though, because this is really a hack, not a solution... I think?

---

### Post by proycon on 2009-10-29
Crocowhile's instruction worked perfectly for me and seems a bit less intrusive than adding a boost device. I had to select "Internal Audio Analog Stereo" on my MacBook Pro 5,3 (alsa_input.pci-0000_00_08.0.analog-stereo). You may need to apt-get install paman .

But I suppose the setting will be lost at reboot again? Is there an easy way to make it stick?

---

### Post by WindPower on 2009-10-29
> **proycon said:**
> Crocowhile's instruction worked perfectly for me and seems a bit less intrusive than adding a boost device. I had to select "Internal Audio Analog Stereo" on my MacBook Pro 5,3 (alsa_input.pci-0000_00_08.0.analog-stereo). You may need to apt-get install paman .

But I suppose the setting will be lost at reboot again? Is there an easy way to make it stick?

That's pretty cool, never saw you could increase the volume using this. :D

---

