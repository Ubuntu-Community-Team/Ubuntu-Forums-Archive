---
title: "Getting frustrated"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by big_bad_brad on 2006-08-28
So far I have really enjoyed Ubuntu with the exception of the Flashplyer plugin. I've been trying to install it for days. Posted 1 thread, read everything I could find, used easyubuntu, synaptic, both of which looks like it is installed, and still nada. I can't download the .tar file from the adobe site and was wondering if this was my problem. Is it a repository thing or something in Firefox that I need to change? I am running out of ideas(not that I had many to begin with). Any help would be much appreciated.  Thanks.

---

### Post by Bachstelze on 2006-08-28
Which browser are you using ?

---

### Post by big_bad_brad on 2006-08-28
Mozilla Firefox 1.5.0.5

---

### Post by rattlerviper on 2006-08-28
Automatix is a easy way to fix the problem in all likelyhood:)  I uasually don't use it, but if your frustrated it should help out quick.

---

### Post by rattlerviper on 2006-08-28
oh sorry here is a link to the website [http://www.getautomatix.com/]("http://www.getautomatix.com/")

---

### Post by xyz on 2006-08-28
From the UbuntuDapper Guide:
> sudo apt-get install flashplugin-nonfree
sudo update-flashplugin

    * Restart Mozilla Firefox 

Note: if sound doesn't work in Flash Player (for example on YouTube):

sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

Change:

FIREFOX_DSP=""

To:

FIREFOX_DSP="aoss"


Also have you got the necessary repos? multiverse,universe..?
Hope it works...let us know!

---

### Post by big_bad_brad on 2006-08-28
automatix gives me this 'automatic installation failed due to network problems or upstream changes'

---

### Post by big_bad_brad on 2006-08-28
and the other code

brad@brad-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
brad@brad-desktop:~$ sudo update-flashplugin
automatic installation failed due to network problems or upstream changes
brad@brad-desktop:~$

---

### Post by Bachstelze on 2006-08-28
Really weird, installing flashplugin-nonfree worked like a charm here, without theed for update... Are you running the default Firefox or the one from mozilla.com ?

---

### Post by xyz on 2006-08-28
Does anyone know if "due to network problems or upstream changes" has anything to do with internet connection breaking down just long enough to make it all fail?

---

### Post by big_bad_brad on 2006-08-28
I am running the one that came with ubuntu.  If that's what you mean.

---

### Post by rattlerviper on 2006-08-28
> **big_bad_brad said:**
> automatix gives me this 'automatic installation failed due to network problems or upstream changes'

try using automatix to install Swiftfox and swiftfox plugins...If that does not do it I'm out of answers.  Swiftfox will be under the internet tab on your menu.

---

### Post by xyz on 2006-08-28
I found this [http://www.ubuntuforums.org/showthread.php?t=164521&page=7](http://www.ubuntuforums.org/showthread.php?t=164521&page=7)

It's quite a long thread; I have not read it all but you might give it a try.

---

### Post by big_bad_brad on 2006-08-28
Installed swiftfox, but flashplayer still doesn't work. I thought I saw the same 'failed due to ...upstream changes' fly by during the installation process.  If I go to the Adobe Flashplayer Download Center and click 'download now' I get :
Unable to connect
Firefox can't establish a connection to the server at fpdownload.macromedia.com.
*   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Swiftfox is permitted to access the Web.

Could Adobe be having problems? I would guess no or more people would be posting.

---

### Post by big_bad_brad on 2006-08-28
Should I reinstall ubuntu?  Would that help? If I should do that will it mess up my other partitions? What is the best way to go about it?

Thanks

---

### Post by rattlerviper on 2006-08-29
> **big_bad_brad said:**
> Should I reinstall ubuntu?  Would that help? If I should do that will it mess up my other partitions? What is the best way to go about it?

Thanks

I wouldn't give up just yet.  I would hate to tell you to reinstall and you end up in the same situation.  Someone may come around with the answer tommorow:) it's just that this doesn't seem to be a "easy" problem to fix.  Was this a "fresh" isntsll that is acting this way?  If you do do a fresh install go straight to Automatix...EasyUbuntu has been acting up for me lately and stalling out which is why I switched to Automatix(doing dev work so I reinstall very frequently).  Anyways you should NOT mess up your partitions if you know what you are doing...but it's really hard to tell you what to do especially without knowing your partition setup.  I'll check back in tommorow, hopefully one of us can find a answer for you.











h

---

### Post by big_bad_brad on 2006-08-29
Thanks.  I'll keep fishin' and checking here in case someone comes up with something.

---

### Post by tmadsen on 2006-09-13
Hi, I had the same problem. First I installed via automatix, but without getting it to work. Then I tried it with synaptic, no luck either.

Then I fetched the install package from adobe's website [http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash]("http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash")

And followed the instructions, that got it to work.

---

