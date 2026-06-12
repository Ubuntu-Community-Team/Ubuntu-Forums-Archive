---
title: "driver for sounds card"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by nivfeld on 2007-05-19
hello,

i just installed ubuntu for the first time, but the sound doesn't work.

it seems to me that the sound card is not installed. I only get sound from the speaker inside the computer tower.

i have an on board sound card: c-media AC97
i found this driver:

[http://www.opendrivers.com/freedownload/211126/c-media-9738-9739-ac97-codec-driver-v041-for-linux-download.html](http://www.opendrivers.com/freedownload/211126/c-media-9738-9739-ac97-codec-driver-v041-for-linux-download.html)

i don't know if it's the right one or even how to install it

i'll appreciate if someone can give me some ideas on what to do

thank you!

---

### Post by n8bounds on 2007-05-19
show us the output of 

lspci -vvv

from a terminal

what I am looking for is your audio card, and I'm going to compare it to this:

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-C-Media#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-C-Media#matrix)

---

