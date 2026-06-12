---
title: "problem with sound"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by darkeale on 2007-04-10
i recently put in a new soundcard in my computer except with kguitar. when i try and play a song it says "error opening midi device". and theres no midi device listed in the configuration. anyone know why? do i have to setup my new soundcard as the default or something somewhere?

---

### Post by bodhi.zazen on 2007-04-10
You forgot to post your soundcard, version of Ubuntu, and CPU

---

### Post by darkeale on 2007-04-10
i did didnt i. i have a amd duron 1600+ and am running ubuntu 6.06. and the sound card is a c-media cmi8738

---

### Post by bodhi.zazen on 2007-04-10
Try Open your sound mixer and change to the cmi card.

If it is not recognized, try loading the driver with :
```
sudo modprobe snd-cmipci
```

---

### Post by darkeale on 2007-04-10
hmmm no that hasnt done it. it only appears to be with kguitar. midi and sound works with all other programs so im guessing its just a problem with that, anyone know?

---

### Post by bodhi.zazen on 2007-04-10
Well, if sound is working then yes the problem is with kguitar.

I thought your problem was that the sound card was not working ...

I have no idea 'bout kguitar

---

