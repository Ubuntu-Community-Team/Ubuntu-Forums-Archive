---
title: "Ti4200 doesnt work?"
date: 2005-07-23
forum: Absolute Beginner Talk
---

### Post by dumbomustflyy on 2005-07-23
new to ubuntu/linux.. i think im having problems with the nvidia ti4200, everytime it loads up and i play around with stuff it just freezes up. ive searched the forums and found this howto [https://wiki.ubuntu.com//BinaryDriverHowto](https://wiki.ubuntu.com//BinaryDriverHowto) but im still getting freezes, anyone know what else i could try? gettin desperate   :|  tried Suse before unbuntu and had the same problem

---

### Post by pmj on 2005-07-23
Why do you think it's a video card problem? Have you tried another OS that did not freeze?

---

### Post by poofyhairguy on 2005-07-23
[QUOTE=dumbomustflyy]new to ubuntu/linux.. i think im having problems with the nvidia ti4200, everytime it loads up and i play around with stuff it just freezes up. ive searched the forums and found this howto [https://wiki.ubuntu.com//BinaryDriverHowto](https://wiki.ubuntu.com//BinaryDriverHowto) but im still getting freezes, anyone know what else i could try? gettin desperate   :|  tried Suse before unbuntu and had the same problem[/QUOTE]

Sounds like more you have a bad RAM stick then you have a bad video card. Do you get the Nvidia logo when it boots?

---

### Post by dumbomustflyy on 2005-07-23
havent tried any other linux OS besides ubuntu and suse, they both froze.
card works fine on winxp sp2 though.

and i dont think its a bad stick of ram cause it works on windows fine?
 
and yes i did get the nvidia logo when it boots up

---

### Post by Synt4x_3rr0r on 2005-07-23
I have a Ti4200 as well, but mine works just as it should.

---

### Post by pmj on 2005-07-23
This is a longshot, but I had a problem with the computer freezing when playing certain games like Bloodlines and Riddick. It turned out that the CPU was running a bit hot. The strange thing was that I could play many other CPU intensive games like Doom 3 for hours, at just as high temperatures, without any freezes.

Cleaning out the fan and heatsink fixed the problem for me.

---

### Post by poofyhairguy on 2005-07-23
[QUOTE=dumbomustflyy]havent tried any other linux OS besides ubuntu and suse, they both froze.
card works fine on winxp sp2 though.

and i dont think its a bad stick of ram cause it works on windows fine?
 [/QUOTE]


My Ubuntu machine is a little more picky with RAM than the Windows side is. I had to return a stick once because it kept crashing in Ubuntu....but my Windows partition worked fine.

Apples are the same way.

The problem might be an app. Is there a particular app that might cause this (Firefox is pretty buggy for me sometimes)?

---

### Post by dumbomustflyy on 2005-07-25
i keep my computer case open and i keep it pretty clean, so i dont think dust or CPU overheating is the problem.

and for the ram, hmm might be tricky, i have mushkin pc3200 if anyoen else with the same ram is reading this thread

---

### Post by maruchan on 2005-07-25
Maybe you're just experiencing the famous Xorg freeze?

[http://ubuntuforums.org/showthread.php?t=39819](http://ubuntuforums.org/showthread.php?t=39819)

There's a lot of help with this issue here on the forum. I was able to fix it on my system, so you'll probably be fine.

Edit: The specific tip that solved my lockups was this one:

[http://ubuntuforums.org/showpost.php?p=232712&postcount=14](http://ubuntuforums.org/showpost.php?p=232712&postcount=14)

---

