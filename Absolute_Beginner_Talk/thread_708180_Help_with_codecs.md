---
title: "Help with codecs"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Miss Karen on 2008-02-26
Okay guys, hi I'm new, and I know you've probably had a dozen posts on this topic before, but I'm in an awkward situation here.


I need my multimedia codecs, videos and whatnots, but I don't have my computer hooked up to the internet. Basically what I want is to be able to download the codecs to USB, then install them on my computer. I'm running basic Ubuntu on an Acer Aspire notebook.

Anyone able to help?

---

### Post by oedha on 2008-02-26
can you just connect that laptop to net ?
since ubuntu will lost its fun without internet
if you can connect :==> sudo apt-get install ubuntu-restricted-extras
from terminal.......
if you can't connect.......you will have to find many packages to install one by one :)

---

### Post by sayakb on 2008-02-26
> **Miss Karen said:**
> Okay guys, hi I'm new, and I know you've probably had a dozen posts on this topic before, but I'm in an awkward situation here.


I need my multimedia codecs, videos and whatnots, but I don't have my computer hooked up to the internet. Basically what I want is to be able to download the codecs to USB, then install them on my computer. I'm running basic Ubuntu on an Acer Aspire notebook.

Anyone able to help?

Just note the exact package names of all the gstreamer plugins, log on to the internet from wherever it's feasible, google the exact package name, download it to your USB.
Please note: DO NOT download from debian package sources. Go for sources from packages.ubuntu.com or ubuntu archives etc.
Also, do take care of your architecture. Say, if you have a 32-bit OS, download and install the i386 or i686 package only.

---

### Post by Miss Karen on 2008-02-26
Ummmm...hate to feel stupid, but can you guys please explain in plain english and elaborate a little? Thanks!

---

### Post by oedha on 2008-02-26
> **LinuxIsInnovation said:**
> Just note the exact package names of all the gstreamer plugins, log on to the internet from wherever it's feasible, google the exact package name, download it to your USB.
Please note: DO NOT download from debian package sources. Go for sources from packages.ubuntu.com or ubuntu archives etc.
Also, do take care of your architecture. Say, if you have a 32-bit OS, download and install the i386 or i686 package only.

- go to [http://packages.ubuntu.com](http://packages.ubuntu.com)
- search for gstreamer
- download them together with the dependencies
- put them on your USB
- install it one by one ( there will be 37 packages if i am not mistaken )

i have a link for you to install this gstreamer  manually :-->
[http://oedha.blogspot.com/2007/11/edubuntu-offline-installation.html](http://oedha.blogspot.com/2007/11/edubuntu-offline-installation.html)

---

### Post by Miss Karen on 2008-02-26
thankyouthankyouthankyou

---

### Post by oedha on 2008-02-26
you're welcome....i hope it work....
last time...a friend from pakistan has the same problem like yours....
and he/she can play the media now......:)

---

### Post by ellalan on 2008-02-28
Hi oedha
I am a newbee and I was unable to play VCD and I have been searching everywhere and I found your post, it did the magic for me.
"apt-get install ubuntu-restricted-extras"  entry made VCD work.
I do really appreciate your contribution and Thank you.

---

### Post by stchman on 2008-02-28
> **Miss Karen said:**
> Okay guys, hi I'm new, and I know you've probably had a dozen posts on this topic before, but I'm in an awkward situation here.


I need my multimedia codecs, videos and whatnots, but I don't have my computer hooked up to the internet. Basically what I want is to be able to download the codecs to USB, then install them on my computer. I'm running basic Ubuntu on an Acer Aspire notebook.

Anyone able to help?

Yes, I agree with the 2nd poster.  If you can take your laptop to say a Bread Company and use their WiFi and use the following procedures.

[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)
[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

This will get your system playing and ripping CDs, DVDs, MP3s, Mpeg2, Mpeg4, etc.

---

### Post by oedha on 2008-02-28
> **ellalan said:**
> Hi oedha
I am a newbee and I was unable to play VCD and I have been searching everywhere and I found your post, it did the magic for me.
"apt-get install ubuntu-restricted-extras"  entry made VCD work.
I do really appreciate your contribution and Thank you.

Hi ellalan;
you're welcome....!! :)
that package not only for vcd......you can find out later on....

---

### Post by Nythain on 2008-02-28
> **stchman said:**
> If you can take your laptop to say a Bread Company and use their WiFi
hehe... thats the greatest thing i've read all nite

---

