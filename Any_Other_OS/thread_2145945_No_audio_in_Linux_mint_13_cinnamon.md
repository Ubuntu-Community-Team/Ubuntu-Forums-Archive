---
title: "No audio in Linux mint 13 cinnamon"
date: 2013-05-17
forum: Any Other OS
---

### Post by snowlizard31 on 2013-05-17
I've install linux on my computer and I can't any audio. I've just build my system and installed realtek audio drivers for linux but that didn't work. also my motherboard AsRock pro3 came with onboard audio so I haven't bought an audio card is that it or do I need to download Asrock audio drivers or something?

---

### Post by UltimateCat on 2013-05-22
If (and I'm pretty sure) that your As Rock mobo came with an on-board audio card.
Try finding out what on-board audio card you have and install the driver for your card.
Run this cmd in the terminal and it should provide you with your sound card info.-

```
lspci | grep -i audio

```
If not your book that came with your motherboard should tell you which card you have on-board.
If not there should be a PDF online for your specific mobo. I know; I found the PDF for my MSI:-

Not sure if Linux Mint's 'default sound' is alasamixer but I know it is for Ubuntu and Debian--

Open the terminal and type:
```
alsamixer

```

Upon doing so you will be greeted with a black/grey background and you will see columns across the screen.
Raise up the PCM and Master and all the rest of the columns all the way. Do a sound test. The test is file named "noise.wav
Enusure that the colums are not muted.  At the bottom of each column is a [ ] with text in it.
This means muted=[mm]....this means un-muted [00] which is what you want.
Close the alsamixer and terminal when done.

Everyone's system is a little different so your file may not be like mine but this gives you an idea at least:
> /etc/init.d/alsa-utils/usr/share/sounds/alsa



I'm not 100% sure if you need the driver for your audio card but if you follow the alsamixer instructions first and still have no sound than most likely
you need the driver for the on-board card.
Make sure you have the **'Linux Sound Architectue Driver'**

Hope this helps

---

### Post by gordintoronto on 2013-05-22
99% of the time no audio means the sound is muted somewhere along the line. What application are you using? Have you run Sound Settings? Have you plugged the speakers/earphones (which?) into the back of the computer or the front? Many headphones also have a volume control which might be turned all the way down.

---

