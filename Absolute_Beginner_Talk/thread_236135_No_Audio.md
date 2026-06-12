---
title: "No Audio"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by Chad_C on 2006-08-14
Recently, I installed Ubuntu on a Toshiba laptop 1955-s803. Everything is running smooth as silk with the exception of audio.
I need someone to hold my hand here -- how do install a tar file?? I know this is probably a very basic accomplishment, but I am having NO luck. I need a step by step walkthrough. ANY help is greatly apprecieted.

---

### Post by %hMa@?b&lt;C on 2006-08-14
```
sudo aptitude install build-essential
```
then untar your tar file to a place on your desktop
open terminal
```
cd ~/Desktop/werethefilewasextracted
```
then
```
./configure
```
```
make
```
```
sudo make install
```

---

