---
title: "[SOLVED] Sound doesn't work in Flash"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by rollerrat on 2007-07-07
Hi! I installed Ubuntu a few days ago, and I'm still quite new to Linux. This far everything has worked out pretty well - the internet connection works, I can listen to music without trouble and everything looks pretty.

However, I can't get any sound from Flash. In sites like Youtube I can only see the video but can't hear anything. I think this is a problem in Firefox or in the Flash-plugin, since I can play video and music files without any trouble. I've searched the forums and other parts of the web for solutions but nothing has worked.

I've tried installing alsa-oss and setting "FIREFOX_DSP" in /etc/firefox/firefoxrc to "aoss", "none" and other values, but it didn't have any effect. I've also tried creating a symbolic link from /usr/lib/libesd.so.0 to /usr/lib/libesd.so.1 and from /tmp/.esd-1000 to /tmp/.esd, but that didn't do anything either.

I'm using the 32bit version of Ubuntu 7.04 on AMD64 computer and Mozilla Firefox 2.0.0.4 with Shockwave Flash 9.0.

Could someone help me out with this?

---

### Post by finer recliner on 2007-07-08
this is a common problem with flash and linux. make sure you have the latest flash player installed from adobe's website

---

### Post by deepclutch on 2007-07-08
> **rollerrat said:**
> Hi! I installed Ubuntu a few days ago, and I'm still quite new to Linux. This far everything has worked out pretty well - the internet connection works, I can listen to music without trouble and everything looks pretty.

However, I can't get any sound from Flash. In sites like Youtube I can only see the video but can't hear anything. I think this is a problem in Firefox or in the Flash-plugin, since I can play video and music files without any trouble. I've searched the forums and other parts of the web for solutions but nothing has worked.

I've tried installing alsa-oss and setting "FIREFOX_DSP" in /etc/firefox/firefoxrc to "aoss", "none" and other values, but it didn't have any effect. I've also tried creating a symbolic link from /usr/lib/libesd.so.0 to /usr/lib/libesd.so.1 and from /tmp/.esd-1000 to /tmp/.esd, but that didn't do anything either.

I'm using the 32bit version of Ubuntu 7.04 on AMD64 computer and Mozilla Firefox 2.0.0.4 with Shockwave Flash 9.0.

Could someone help me out with this?
yes.u need to set "aoss" in iceweasel(firefox)rc file.
for firefox or iceweasel or epiphany,enable esd(enlightened sound daemon) from menu System>pref>Sound>enable sound,esd etc.
then apt-get install alsa-oss,restart alsa.that's it.
Also,with latest version of flash,native gtk is supported(is better!) and u can download it into ur /usr/lib/mozilla/plugins removing earlier versions.

---

### Post by Hallvor on 2007-07-08
[http://ubuntuforums.org/showthread.php?t=204022](http://ubuntuforums.org/showthread.php?t=204022)

Edit: Too slow.

---

### Post by rollerrat on 2007-07-08
Thanks for your help! I still can't get the sound to work though. :(

I have the following line in /etc/firefox/firefoxrc:
```
FIREFOX_DSP="aoss"
```

I also have the latest versions of alsa-oss (1.0.12-1) and Flash (9.0.31.0.2), and I have checked the "Enable software sound mixing (ESD)" box in System > Preferences > Sound. This doesn't seem to have any effect.

I've tried the method described in [http://ubuntuforums.org/showthread.php?t=204022]("http://ubuntuforums.org/showthread.php?t=204022"):
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket
```

But it didn't work either. Sound works in videos and music as before, but I still can't hear anything from Flash.

Is there anything else I could try?

---

### Post by deepclutch on 2007-07-08
did u enable Enlightened Sound daemon in menu system>preferrences>Sound ?

---

### Post by Hallvor on 2007-07-08
Just in case, you have to restart Firefox.

---

### Post by rollerrat on 2007-07-09
It turns out that the problem wasn't in Flash at all. I have two soundcards, one onboard for my speakers (which I use very rarely) and an external one for my headset. I had set everything in Sound Preferences to use USB Audio so that sound would go to my headset instead of the muted speakers, but apparently Firefox was still somehow using the onboard soundcard. I unmuted the speakers, and yup, I got sound from Flash and from other plugins. :)

Anyway, I got the problem solved by setting the external soundcard as the default device by modifying /etc/modprobe.d/alsa-base. I followed the advice from this thread: [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449").

Sound and Flash work great now. Thanks for all the help! :)

---

### Post by sharperguy on 2007-08-04
I was wondering, exactly how did you set the default sound device by editing that file?

Ive looked at the thread and it dosnt seem to give any clues.

I've look at the file and its just confusing

---

### Post by PrivatePickle on 2007-08-05
I used the following part from his guide and it worked for me without editing a file.  I re-arranged the text a little so that it made more sense.

> Here's an alternate solution posted in launchpad Here.

    * In a terminal type: 

```
sudo asoundconf list
```

    * If you have more than one sound card, you should see several entries (You need to know which card produces sound. If you don't know then try the next step for all the entries)
    * Now type this in a terminal: 

sudo asoundconf set-default-card ENTER_NAME_OF_CARD_HERE

For example, this is what I did: 
codeslicer@ubuntu:~$ sudo asoundconf list 

Names of available sound cards: 
rev20 
AudioPCI 
codeslicer@ubuntu:~$ sudo asoundconf set-default-card AudioPCI 
codeslicer@ubuntu:~$

    * You might have to try that several times. Luckily it worked for me from the first try. Note that if you're using a media player to test your sound, you will have to close it first, then run the command, and then open it again. It won't just start working all of a sudden in the middle of a song. HTH! 

You will also need to restart firefox to test sound in flashplayer also.  Hope this helps.

---

### Post by emartinez13 on 2007-09-02
You are the MAN!!!!! After countless hours and trying all sorts of things I finally got my USB sound card to work with this. Thank you!!!! I have to have my Youtube fix

---

