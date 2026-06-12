---
title: "unable to watch videos"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by wiachy on 2007-11-05
when on youtube i can watch the video but the pause/play button and the volume control are all screwed up.  also with some other videos nothing can play and theres just numbers in the bottom right corner of the video.  do i need plug ins or something else? if so where do i get them from?  Thanks!

---

### Post by HokeyFry on 2007-11-05
which version of flash are you using? to find out right click the flash applet and it should say "About Flash X..."


if its not flash 9, install "flashplugin-nonfree" from the repos

---

### Post by daimaru on 2007-11-05
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by wiachy on 2007-11-05
> **daimaru said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```

just did that, it had me load the ubuntu 7.10 cd in, which i did and it loaded a bunch of stuff and still doesnt work :(



> which version of flash are you using? to find out right click the flash applet and it should say "About Flash X..."


if its not flash 9, install "flashplugin-nonfree" from the repos

i don't know where the flash applet would be (im noob to ubuntu) would you please explain a little more?

thanks for the quick replies!

---

### Post by SunnyRabbiera on 2007-11-05
you could give automatix a shot too.

---

### Post by daimaru on 2007-11-05
ok the sudo apt-get install ubuntu-restricted-extras would not solve your youtube flash problems , but i should have installed the other codecs to watch videos. 

just in case go here [http://www.medibuntu.org]("http://www.medibuntu.org") 
click "repository howto" and in terminal as it says on page type 

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
then type:
```
sudo apt-get install w32codecs
```

or just follow the stuff on the page including libdvdcss if you want to watch commercial dvds. 
i thought that the w32codecs where included in the ubuntu-restricted-extras, but just in case they are not do the stuff above. 
this should enable you to watch all the videos you want. if not try installing VLC media player just search for it in synaptic. the best player after mplayer maybe in my opinion.

for your flash problem i can just suggest to resinstall flash player by deleting the plugin
open terminal and type this
```
rm ~/.mozilla/plugins/libflashplayer.so
```
then just go to any flash page (youtube for example) and when firefox asks you to install needed plugins to display page content say yes. 

hope it works

---

### Post by barkej on 2007-11-05
> **wiachy said:**
> just did that, it had me load the ubuntu 7.10 cd in, which i did and it loaded a bunch of stuff and still doesnt work :(





i don't know where the flash applet would be (im noob to ubuntu) would you please explain a little more?

thanks for the quick replies!
Go [here]("http://www.adobe.com/shockwave/welcome/") and roll over the about button.

On another note [Automatix]("http://getautomatix.com") is a lifesaver if you are new to Ubuntu.

---

### Post by daimaru on 2007-11-05
@wiachy
just in case you are annoyed of having to insert your ubuntu cd, and assuming you have a fast internet connection. 
go to system->admin->software sources and uncheck your cd-rom at the bottom where it says "installable from cdrom/dvd"

---

### Post by Flying caveman on 2007-11-05
It just "seems" difficult because you haven't done it before.  Don't make me get in my truck and drive up the hill and do it for you.:)

---

### Post by Ituxlinux on 2007-11-06
Hi there;

I had the same problem and after following this, my firefox just crash when I try to open any youtube video.

Any idea what maybe wrong?

---

### Post by rudeboyskunk on 2007-11-06
> **Ituxlinux said:**
> Hi there;

I had the same problem and after following this, my firefox just crash when I try to open any youtube video.

Any idea what maybe wrong?

Type "firefox" into a terminal, go to youtube, wait for the browser to crash, then copy and paste what the terminal says into the forum.  That way we can see exactly what's happening.

---

### Post by Ituxlinux on 2007-11-06
itux@ubuntu704laptop:~$ firefox
Segmentation fault (core dumped)
itux@ubuntu704laptop:~$

---

