---
title: "Easy Swiftfox 2.0 Install"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by NewDisciple on 2006-12-18
After trying every listed method of installing Firefox 2.0 and failing I found this.  Go to [URL="http://getswiftfox.com/releases.htm"].
Pick your processor and click Debian at the top of the page.
Instructions for installing with apt-get:
Add the repository to your sources.list file: 
deb http://getswiftfox.com/builds/debian unstable non-free
1.Install from a terminal window as root using the correct package name: 
apt-get update && apt-get install swiftfox-athlon-xp
or: swiftfox-athlon
swiftfox-athlon-xp
swiftfox-athlon64
swiftfox-k6-2
swiftfox-pentium-m
swiftfox-pentium2
swiftfox-pentium3
swiftfox-pentium3m
swiftfox-pentium4
swiftfox-prescott
Whatever your processor is.
This worked like a charm and took only about a minute to do.  Go to applications/internet/swiftfox browser to start 2.0 and that is all there is to it.

---

### Post by ain't_dunit on 2006-12-18
Hi ,that's how I installed also. 
It's also listed in automatix2 as an install option.

---

### Post by raul_ on 2006-12-18
I just went to the site and downloaded the .sh file :) But that's neat

---

### Post by padre999 on 2006-12-18
Haven't tried swiftfox for a while. Installed it as you described and I am pleasantly surprised :) 

Finally nice font rendering (that always kept me from using swiftfox) and much faster than the standard firefox.

thanks

---

### Post by Kalibur on 2007-03-08
I put this line in my reposition list (synaptic) 

"deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free"

Reloaded the list 
Then looked for Swiftfox and it showed me only what I needed to install thus swiftfox-anthlon64 in my case.  So if unsure about what sort of processor you have just add the repo to your install manager (synaptic in my case) and it will automatically pick just the one you need for you system.:-({|=

---

### Post by J11Gyro on 2007-03-08
Worked nice, thank you now I can use it instead of firefox 1.05

---

