---
title: "Another Airport extreme card question"
date: 2007-07-05
forum: Apple PPC Users
---

### Post by Redneo on 2007-07-05
I've read the guides and I'm a little confuse about the getting the card to start. it's says to get the bcm43xx-fwcutter to get the the firmware and i got that. I'm using an Apple powerbook G4 so  I don't use the ndiswrapper tool cause of it being a real apple g4 correct? So when I use the fwcutter tool and bring up the list of the firmware do I type bcm43xx-fwcutter <filename> <version> <md5checksum> or just the file name

---

### Post by pbarthelemy on 2007-07-06
Hello,

true, ndiswrapper is for MacIntel only.

this blog entry is in French, but the command to type are easy to 'translate'

give a look at [http://blog.effraie.org/index.php/post/2006/10/20/Wifi-sous-ubuntu-ppc-avec-la-carte-Airport-extrem]("http://blog.effraie.org/index.php/post/2006/10/20/Wifi-sous-ubuntu-ppc-avec-la-carte-Airport-extrem")

--p

---

### Post by tcrroadie on 2007-07-06
Yes you are on the correct track.  For PowerPC you use bcm43xx-fwcutter to extract the firmware for your wireless card either from your OS X installation or from the install DVD.  

You can easily install bcm43xx-fwcutter using apt or Synaptic. 

```
sudo apt-get install bcm43xx-fwcutter
```

In may case, when I installed bcm43xx-fwcutter, the package automatically extracted the firmware for my Airport Extreme card from my OS X installation since I had the partition OS X is installed on mounted. 

Syntax for manual firmware extraction would look something like this.  Assuming your OS X installation is mounted on /media/macosx  
```

bcm43xx-fwcutter -w /lib/firmware/ /media/macosx/System/Library/Extensions/AppleAirPort2.kext/Contents/MacOS/AppleAirPort2
```

More information on how to extract the Broadcom firmware, can be found[ here.]("http://www.terrasoftsolutions.com/support/solutions/ydl_5.0/airport-extreme.shtml")

---

### Post by Redneo on 2007-07-11
I've try to get the the driver from the cd but says that it can't mount the volume. So what's do i do to get the drive

---

### Post by pxwpxw on 2007-07-11
> **Redneo said:**
> I've try to get the the driver from the cd but says that it can't mount the volume. So what's do i do to get the drive

If you install the bcm43xx-fwcutter package using the procedure in the PowerPCFAQ  Section 4.1 (see sticky at the top of this forum) and have an internet connection, the whole process is automatic with ubuntu feisty release and most current applemac G4,G5.

---

