---
title: "Microphone Issues (not just skype)"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by markyb86 on 2007-12-03
I thought skype would "just work" but when i test it, I get no input. When i goto my sound properties and hit test I get this error message:

[IMG]http://www.7thyear.com/dci/media/c33%201196642154%20Screenshot-gnome-sound-properties.png[/IMG]

it just doesnt seem to work for me. sound playback is fine however.

this is the nvidia chipset on the dell dimension c521 amd sempron 3400+ 1gb ram 160gb hd nvidia geforce 6150 le

---

### Post by markyb86 on 2007-12-04
bump :-(

---

### Post by markyb86 on 2007-12-04
nothing?

---

### Post by smithareen on 2007-12-07
I solved it for me...found this on another forum.

Have you tried to double click on volume control
click on Capture
remove X from microphone?

I double clicked on volume control and did that. I also fiddled around with the new settings available after turning capture on.

Hope that helps.

It was here... [http://ubuntuforums.org/showthread.php?t=352424](http://ubuntuforums.org/showthread.php?t=352424)

---

### Post by khurrum1990 on 2007-12-07
> **markyb86 said:**
> I thought skype would "just work" but when i test it, I get no input. When i goto my sound properties and hit test I get this error message:

[IMG]http://www.7thyear.com/dci/media/c33%201196642154%20Screenshot-gnome-sound-properties.png[/IMG]

it just doesnt seem to work for me. sound playback is fine however.

this is the nvidia chipset on the dell dimension c521 amd sempron 3400+ 1gb ram 160gb hd nvidia geforce 6150 le
Hi, this is a bug in Ubuntu 7.10 I read some where. Its not present in Ubuntu 7.04 though. I know cause on one of my Linux computers has this bug. I am using Kubuntu 7.10 on this one without any problems. You will have to wait for the bug to get solved I think.

---

### Post by mdsmedia on 2007-12-07
It can depend on the type of MIC you're using. I initially used a headset with twin jacks (plug in microphone and headphones jack to their respective inputs, and it just worked.

I then bought a USB headset when I sat on and broke the old headset.

This was a little more problematic. In SYSTEM PREFERENCES SOUND in the menus you then need to set the default sound card to the headset you're using. This worked for me. But if you unplug the USB headset and then re-plug it you'll probably need to set it again.

I'm using a notebook so this was a little different for me. I can't have a MIC plugged in all the time.

If you're using a Desktop with permanent MIC, I'm not sure why it wouldn't pick that up and use it "out of the box".

---

### Post by markyb86 on 2007-12-07
Im using one of those cheapo headset microphones. 

smithareen  - I cant find capture? when i double click on volume control.

Thanks for the responses ill keep toying with it!

---

### Post by markyb86 on 2007-12-07
Im a retard. InMux is the wrong thing. InVol is the right thing.......... Works now

THANKS FELLOW UBUNTU-ERS!!

---

### Post by Benzaa on 2007-12-11
InMux? InVol??
Where do I find those parameters?

Im also stuck with the microphone and I cannt make it work. Do you mind telling me what you did?

---

### Post by markyb86 on 2007-12-11
when i double clicked on the volume control, you get an options or preferences menu where you can select to add them in, and then a recording tab appears that you can adjust the levels with

---

### Post by philinux on 2007-12-11
I've got my headphone mic working just fine but that error still pops up if I press test so thats a bug.

The only thing I cant crack is my webcam mic :confused:

---

