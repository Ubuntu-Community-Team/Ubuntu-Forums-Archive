---
title: "Mp3, CD's and DVD's"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by LennyBerm on 2007-03-08
I installed Ubuntu 6.10 on my computer but it tells me I need plugins to play Mp3, DVD's, or even play CD's. Where do I get these and how do I install them?
Thanks,
Len

---

### Post by Ek0nomik on 2007-03-08
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

That should help you get under way!

Cheers!

---

### Post by LennyBerm on 2007-03-08
I went to the page and downloaded some files for xine but I cant figure out how to install them. It seems to be very different than Windows.
Thank you,
Len

---

### Post by mikewhatever on 2007-03-08
You have not mentioned Xine in the innitial post. What are you trying to do? In case you are trying to install Xine, it should be as simple as
> sudo apt-get install xine-ui libxine-extracodecs

---

### Post by Ek0nomik on 2007-03-08
What couldn't you get to work?

MP3, DVD...?

The MP3 one I know is easy, I did it recently myself.

---

### Post by LennyBerm on 2007-03-08
I am only interested in Mp3 and maybe CD. I appreciate your help.
Thanks,
Len
San Diego, CA USA

---

### Post by mekkah on 2007-03-08
I'm pretty new to Ubuntu, but this i know a smooth solution to: Install [EasyUbuntu]("http://easyubuntu.freecontrib.org/"). It's a since script that allow you to easily install support for all those goodies we can't live without: MP3, DivX/XviD, Flash, Rar-archives, Nvidia Drivers and so on.

---

### Post by GranpaDan on 2007-03-08
Following the directions on the following link helped me.

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/codecs.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/codecs.html)

---

### Post by champenoise on 2007-03-09
You can install EasyUbuntu and still not be able to play MP3's if, like me, you haven't checked the appropriate *repositories* in Synaptic Package Manager. I don't think EasyUbuntu contains plugins, it just tries to download them for you, and apparently doesn't complain much when it can't. For MP3 codecs, I think you need the repository labeled 'multiverse'. Once I checked that, EasyUbuntu successfully downloaded and installed the MP3 codecs.

---

### Post by LennyBerm on 2007-03-09
Where do I run command line stuff? I cant find the command line prompt?
Len

---

### Post by Ek0nomik on 2007-03-09
Accessories/Terminal

Cheers!

---

### Post by LennyBerm on 2007-03-09
Thanks again.
Len

---

