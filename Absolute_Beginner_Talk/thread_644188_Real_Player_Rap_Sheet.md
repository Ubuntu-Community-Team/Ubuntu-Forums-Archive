---
title: "Real Player Rap Sheet"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by discoade on 2007-12-18
i downloaded real player 10 from [COLOR=Blue][here]("http://forms.helixcommunity.org/helix/builds/?category=realplay-current")[/COLOR]
titled PLATFORMS
linux-2.2-libc6-i386 

name of the file 
     linux-2.2-libc6-gcc32-i586@rhel4 

I downloaded the bin version and the rpm version to my home folder as i wasn't 100% clear which one i wanted!

i converted the rpm to deb with alien which gave me this file
 
     realplayer_10.1.0.3821-20071217_i386.deb 

tried installing and got this!
   
```
 adrian@adrian-desktop:~$ sudo dpkg -i realplayer_10.1.0.3821-20071217_i386.deb
[sudo] password for adrian:
(Reading database ... 128002 files and directories currently installed.)
Preparing to replace realplayer 10.1.0.3821-20071217 (using realplayer_10.1.0.3821-20071217_i386.deb) ...
Unpacking replacement realplayer ...
Setting up realplayer (10.1.0.3821-20071217) ...
dpkg: error processing realplayer (--install):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing: realplayer
adrian@adrian-desktop:~$ 
```so what do you think guys?
its on about replacing real player yet i dont have real player! although i have got helix player which rp is based on! conflict?

the problem i have now is every time i install something else it tries to install real player as well but still gives the error..

```
   subprocess post-installation script returned error exit status 127
Errors were encountered while processing: realplayer
```Anyone any ideas how to stop it trying to install or better still to actually get it to install rp in the first place?

im in your hands! :)

---

### Post by daimaru on 2007-12-18
try the deb file here
[http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.1_i386.deb](http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.1_i386.deb)

```

wget -c http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.1_i386.deb
sudo dpkg -i realplayer_10.0.9-0.1_i386.deb

```this link may interest you
[http://howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon_p3](http://howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon_p3)
of course you can start at page 1, but thats all about installing, so you can skip to page 3

---

### Post by seventhc on 2007-12-18
I just installed it as a .bin file without converting it and that works...before i installed real player i installed helix to see if i got an error, I didnt. so there is no conflict.
if you need help installing bin files here is a good thread on it.
[http://ubuntuforums.org/showthread.php?p=2471799](http://ubuntuforums.org/showthread.php?p=2471799)

ps. before you go ahead with this, you can wait for my next post as it is still installing. I'll let you know the outcome, but so far it looks successful.

pss..never mind the post above looks easier. lol :)

pss. I think you will have to remove helix. so one or the other, not both.

---

### Post by discoade on 2007-12-18
By jove! sir your a genius! now if you can tell me how to install the plugin into firefox i would be forever in your debt!

---

### Post by daimaru on 2007-12-18
realplayer should already be the default in firefox if you used my link, but if you want to be sure and if you want to choose which players play what in firefox, install[ this extension]("https://addons.mozilla.org/en-US/firefox/addon/446") and durring setup choose realplayer as your default for rm files. 
hope this helps

---

### Post by discoade on 2007-12-18
real player up and running! :)

now i read some where that you need to install 2 files into 2 dirs in firefox! i cant find the article i read it in!  firefox is still not playing ram feeds!

---

### Post by daimaru on 2007-12-18
could you provide a link to a page where your trying to view a ram file so i can test if it works with my setup . 
thx

---

### Post by discoade on 2007-12-18
partial success 

stream wont play in firefox it says i need to install the real player plugin but if i click play in external player it works!

trying to listen to the live stream from [here]("http://www.bbc.co.uk/blackcountry/")

---

### Post by daimaru on 2007-12-18
yeah i see what you mean.. it launches external (realplayer) for me, but i don't even get sound... this sucks. guess i never came across a rm ram file before so i didnt realize that i had this problem too. :) 

real sorry cause i dont know the solution to it either. :(

---

### Post by discoade on 2007-12-18
Mines playing in the external rp 10 as we speak! just the firefox plugin not working! :confused:  i read it somewhere! you need to copy 2 files to a folder in firefox but can i heck as like find where i read it!! :mad::lolflag:

Perhaps i should write a strongly worded letter to the bbc!    Dear bbc! it has come to my attention that ..... blah blah blah  balh blah.... signed Annoyed from Warwickshire!

---

### Post by jamaas on 2007-12-19
Thanks Daimaru,

Apologies in advance.  Where does your script actually install the executable for realplayer?  I need it to reconfigure the extension you mention, must point to the realplayer executable using browse.

Thanks a bunch.

Jim

> **daimaru said:**
> realplayer should already be the default in firefox if you used my link, but if you want to be sure and if you want to choose which players play what in firefox, install[ this extension]("https://addons.mozilla.org/en-US/firefox/addon/446") and durring setup choose realplayer as your default for rm files. 
hope this helps

---

### Post by discoade on 2007-12-19
mines located in  

root / usr / lib / realplay-10.0.9 /

---

