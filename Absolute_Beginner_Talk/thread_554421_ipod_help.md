---
title: "ipod help"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by cattyb on 2007-09-19
I understand that other people have asked about help on ipods but I can't find the information I require - I'm an absolute beginner at all this so please bear with me! I've installed both Banshee and gtk pod - the latter shows my ipod as being unplugged, even when it shows up on Places and is clearly plugged in. Banshee has supposedly synched my music - it certainly shows up when the ipod is mounted, but as soon as I take the ipod out, there is nothing on it at all. Now, maybe I haven't ever formatted the ipod correctly? But how to do this on ubuntu? I've downloaded itunes from the net but should that work? I'm completely new to ipods and ubuntu so have compounded my problems, perhaps. Help! Really really easy language would be appreciated - I'm a writer and know v. little about computers. What I can say is that the under both rhythmbox and gtk up pops a message saying plug in failed and when I try to create media directory in gtk it pops up saying that it isn't mounted in media - but no info as to how to do this. Very confusing and frustrating!
catty

---

### Post by AlexKeaton on 2007-09-19
Clearly the problem is that you have a bad USB port. You can buy a new USB card at an average computer store for approximately $30.

---

### Post by sunexplodes on 2007-09-19
Okay, a few things to try:

- sudo nautilus /media, then create a folder called "ipod". 

- try Amarok, it's the only app we ever used for my roomate's ipod, and it worked wonders. 

- use itunes to Restore the ipod's firmware, as it may be incorrectly formatted.

---

### Post by laidback on 2007-09-19
Suggest you install Amarok..works with ipods for me.
Once installed:-
Settings>Configure Amarok>Media Devices choose plugin ipod from the drop down at the top of the page, now press Auto-detect Devices, when finished press OK.  Your  ipod is in the USB socket throughout.

Back at the main screen choose Devices from the tabs on the LHS, you'll see what's on your ipod listed there. Note the Connnect, Disconnect and Transfer buttons just under the main menu at the top of the window. You can use these. After adding a load of tunes (drag and drop to lower part of Devices tab) remember to Tansfer them over (e.g. write to the ipod ). You can also delete items from the ipod and generally sort things out. I've transferred music and the spoken word, never used it with video as my ipod doesn't do this.

Treat the ipod like any other memory stick, don't remove until you have Unmounted it. You can do this in Amarok or from the desktop icon that appears when you plug your ipod into the usb socket.

---

### Post by cattyb on 2007-09-24
Hi - thanks for the detailed instructions on the use of Amorak - I tried this and it just doesn't configure my ipod. It's there in the drop down menu on the right hand side - but it won't auto detect and I still can't see any of the music when I unmount the ipod. This is v. frustrating! I've also tried gtkpod and that worked once, until my son attempted to organise the songs - which just went into a great heap, no artist or album organisation - and wiped them all off! We retraced our steps on that one, but no banana. This is a brand new ipod nano 4gb. I can use it on my pc which runs windows xp and I can copy music through the network, of course, but i want to be able to use my laptop and I want to be able to use Ubuntu which I do like! (Though I'm not a computer person at all, so discovering steep learning curves.) Any other suggestions? It is not the usb port - they are fine!
Catty

---

