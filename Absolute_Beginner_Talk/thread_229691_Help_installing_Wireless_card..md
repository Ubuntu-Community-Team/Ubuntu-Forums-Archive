---
title: "Help installing Wireless card."
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by bitdefuser on 2006-08-04
Ok.
I have the files: bcmwl5a and bcmwl5.

How do I set this up?
I read other guides but, I want to hear from you. :p
______________
BCM94306MPLNA
I searched for BCM94306 and I found a couple.
Can you help me pick out one from [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) ?

---

### Post by FizDev on 2006-08-04
First, you need to install ndiswrapper so... type this in the terminal
```
sudo apt-get update
```
```
sudo apt-get install ndiswrapper-utils
```
Then go to the directory where your drivers are and type (to install the driver)
```
sudo ndiswrapper -i bcmwl5a.inf
```
Now check if it's installed (you should see a "Hardware present" or something like that)
```
sudo ndiswrapper -l
```
Hmm.. now that it's installed, check if it works
```
sudo modprobe ndiswrapper
```
Then add it to boot automatically
```
sudo ndiswrapper -h
```

PS. I'm not sure of theses steps, simply doing it from memory =S

---

### Post by bitdefuser on 2006-08-04
Can you please go into detail? I'm a noob. :D 


This is my laptop: hp compaq nx6110

My broadcom wirless model:
BCM94306MPLNA

---

### Post by FizDev on 2006-08-04
Hmm... try following this howto ;)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Its pretty much what I told you but in more details... and probably more accurate :)

---

### Post by bitdefuser on 2006-08-05
BCM94306MPLNA
I searched for BCM94306 and I found a couple.
Can you help me pick out one from [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) ?

---

### Post by bitdefuser on 2006-08-05
Don't know if the laptop model matters but, it's a Compaq nx6100.

---

### Post by Titus A Duxass on 2006-08-05
Did you try following the steps provided by FizDev?

---

### Post by bitdefuser on 2006-08-05
Yes but, I found about like 5 drivers on that website.
I'm not sure which one to download.

---

### Post by Titus A Duxass on 2006-08-05
You have two driver files already.
Use ndiswrapper -i with one file first and then do ndiswrapper -l that will tell you if you have the correct driver or not.

ndiswrapper -r will remove the installed driver so that you can repeat the exercise with the other driver.

When you can the message: hardware present driver present you have success.

---

### Post by bitdefuser on 2006-08-05
How stupid of me. Sorry.

---

### Post by Titus A Duxass on 2006-08-05
No worries, just keep us informed of your progress. I'm here all night tonight.

---

### Post by bitdefuser on 2006-08-05
I installed both of the drivers but, I try to activate the wirless thing and it doesnt work.
Nothing happens.
Help?

Model: BCM43006
Pcii: 0000:02:04:0 0280:14e4:4320
or it might be: 0280:14e4:4320 0000:02:04:0
One of those two ways.

I tried using wine but, it gave me this error: Dependencies is not satisfied libartsc0

Please help! Again; my laptop model is nx6100 and it requires me to click that wirless wifi blue button thing (which won't work.)

---

### Post by bitdefuser on 2006-08-05
Bumpie.

---

