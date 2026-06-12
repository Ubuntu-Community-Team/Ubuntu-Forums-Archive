---
title: "yet another noob needing wifi help (broadcom 4318, AMD 64)"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by codyduncan on 2008-01-29
I've read the wiki's, followed some instructions elsewhere, but to no avail.
al
In the case of [https://help.ubuntu.com/community/WifiDocs/NdiswrapperOnAMD64](https://help.ubuntu.com/community/WifiDocs/NdiswrapperOnAMD64) , I am too inexperienced to even make sense of some of the instructions, and in other cases, either the sites seem sketchy (I don't want to follow their directions potentially damaging my system) or they just haven't worked.

So, as in the topic, I am running a Broadcom 4813 wifi card on an HPzv6000 notebook, with an AMD 64 processor.  I should also add, I am using Gutsy.

I am guessing that I am going to have to go the route of ndiswrapper, but I am fuzzy about how to go about that.

Something that seems to make this problem a little more strange is that I can't seem to find "device manager" under system->administration (as in, it's not there).

I realize this problem is very common and annoying, so thanks in advance

---

### Post by mikeyphi on 2008-01-29
I believe that this is the guide you should be using: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

Ask if you have problems with any of the instructions

---

### Post by codyduncan on 2008-01-29
Those instructions only apply to the fwcutter method of dealing with my problem, and I am trying to avoid that particular solution, as even though I had marginal success (my card was able to recognize networks, and my system recognized my card working) I was not able to get past the WEP security of my router, so it was basically worthless.

I found amongst the archives, a huge post [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102) (practically a forum in itself) based around just this problem, but I have yet to get any results from it.

---

### Post by mikeyphi on 2008-01-29
> **codyduncan said:**
> Those instructions only apply to the fwcutter method of dealing with my problem, and I am trying to avoid that particular solution, as even though I had marginal success (my card was able to recognize networks, and my system recognized my card working) I was not able to get past the WEP security of my router, so it was basically worthless.

I found amongst the archives, a huge post [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102) (practically a forum in itself) based around just this problem, but I have yet to get any results from it.

That guide is based on the one I posted - and might be easier to follow!
Unfortunately for you, there is no easy option - you've just got to plough through the process.

Good luck - ask if you need further explanation on any of the instructions.

---

### Post by stump138 on 2008-01-29
I've gotten that combination to work, but unfortunately only when running regular i386 (32 bit) ubuntu. If you're willing to run 32 bit, it could be a possibility for you.

---

### Post by codyduncan on 2008-01-29
I've been looking at this wiki: [https://help.ubuntu.com/community/WifiDocs/NdiswrapperOnAMD64](https://help.ubuntu.com/community/WifiDocs/NdiswrapperOnAMD64)

but the instructions there are beyond my comprehension

---

### Post by codyduncan on 2008-01-29
also, is it strange that there is no device manager under administration?

---

