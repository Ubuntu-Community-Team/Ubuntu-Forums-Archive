---
title: "How To: Burn DMG to DVD-DL natively on Ubuntu"
date: 2014-03-07
forum: Apple Hardware Users
---

### Post by mole84 on 2014-03-07
I needed to burn a DMG to a DVD-DL disc without having access to a working Apple computer. Over the process of trial and error and found this to work pretty well.

**Required Items**
[LIST=1]
[*]dmg2img-1.6.5
[*]DMG Image
[*]DVD-DL burner
[*]Blank DVD-DL disc
[/LIST]

**Step 1: Manually build and install dmg2img-1.6.5**
You'll notice that if you use aptitude that the current version of dmg2img in the repository is 1.6.2. We need to install the updated version. I am researching ways to update the respository version.

Step 1.1: Download source code for dmg2img-1.6.5: [http://vu1tur.eu.org/tools/]("http://vu1tur.eu.org/tools/")
Step 1.2: Prepare build environment
```
sudo apt-get install build-essential gcc zlib1g zlib1g-dev libghc-zlib-dev libbz2-dev
```
Step 1.3: Extract archive, build source, install binary
```
cd ~
```
```
cd Downloads
```
```
tar -xf dmg2img-1.6.5.tar.gz
```
```
cd dmg2img-1.6.5
```
```
make
```
```
sudo cp dmg2img /usr/bin
```
Step 1.4: Verify correct version is installed by running dmg2img
```
dmg2img
```
dmg2img v1.6.5 (c) vu1tur (to@vu1tur.eu.org)

**Step 2: Convert DMG to IMG using dmg2img-1.6.5**
```
dmg2img in.dmg out.img
```
Here in.dmg is the name of the DMG that you need to convert
Following this process you should have out.img
Note: I tried to mount the img in various ways but it did not work. I still went ahead with the burn.

**Step 3: Burn IMG file to DVD--DL using K3b**
```
sudo apt-get install k3b
```
Start K3b: Sound & Video > K3b
Open the IMG file and burn!

---

