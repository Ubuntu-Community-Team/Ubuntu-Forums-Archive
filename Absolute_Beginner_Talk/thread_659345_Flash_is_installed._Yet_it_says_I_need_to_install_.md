---
title: "Flash is installed. Yet it says I need to install it..."
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Roasted on 2008-01-05
Synaptic says it's installed. However, whenever I go to a site using flash, it prompts me to install it. So I do, each time, getting no errors. And it says installed. Yet... whenever I go back to the site... I get prompted to install it yet again.

I've rebooted several times.

---

### Post by jan quark on 2008-01-05
try to install it manually, go to the adobe site download the tar file and unzip it to the desktop

than run the terminal, navigate to the unziped file and type   ./flashplayer-install somethining like that...

---

### Post by SOULRiDER on 2008-01-05
From IRC
> **The Flash plugin installation is currently broken. This is due to Adobe changing the tar file that the package downloads. See [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397) if you need to fix this immediately, but it's recommended to wait for an official fix.**

---

### Post by eolson on 2008-01-05
This is what worked for me ....

I went to the weather channel page
clicked on the radar scrolled down and found the install flash button clicked it and flash installed.
Why?  I dunno.

---

### Post by Roasted on 2008-01-06
So... I downloaded the tar.gz

I did the tar -zxvf (flash file)

Yet when I CD'd into the DIR and ran a ./configure... it said command not found. 


Uhhhh??

---

### Post by JoshuaRL on 2008-01-06
Try:

```

sudo aptitude install flashplugin-nonfree

```

That should work.

---

### Post by mdpalow on 2008-01-07
unless something has been fixed recently, the above command won't work.

You say you installed it and there are no errors, but if you look closely, you'll see that it actually didn't install. That's because the download is currently broke.

Click the link in my signature below and my script will install it for you.

Good luck...

---

### Post by Roasted on 2008-01-08
When I click on that link it takes me to a new backup solution...

---

### Post by philinux on 2008-01-08
There's a known error with the nonfree flash in synaptic the md5sum is wrong.

Follow option 1 from adobe.
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

---

### Post by Roasted on 2008-01-09
> **philinux said:**
> There's a known error with the nonfree flash in synaptic the md5sum is wrong.

Follow option 1 from adobe.
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

See post 5 of this thread. 

:(

---

### Post by RomeReactor on 2008-01-09
> **Roasted said:**
> See post 5 of this thread. 

:(

Hi. See [this]("http://ubuntuforums.org/showpost.php?p=4101050&postcount=5") for the easiest way to fix it. Otherwise, if you still want to use your downloaded .tar.gz, extract it and from the terminal, go into the extracted directory, then:
```
sudo ./flashplayer-installer
```

---

### Post by mdpalow on 2008-01-09
> **Roasted said:**
> When I click on that link it takes me to a new backup solution...

READ all of the link I sent you.  :)

---

### Post by Roasted on 2008-01-10
> **RomeReactor said:**
> Hi. See [this]("http://ubuntuforums.org/showpost.php?p=4101050&postcount=5") for the easiest way to fix it. Otherwise, if you still want to use your downloaded .tar.gz, extract it and from the terminal, go into the extracted directory, then:
```
sudo ./flashplayer-installer
```

That worked. Thanks.

---

### Post by Roasted on 2008-01-10
> **mdpalow said:**
> READ all of the link I sent you.  :)

My bad. I don't even remember looking at your link. I think I was dead-tired-about-to-pass-out when I clicked it and posted here. 

Note to self - staying up all hours of the night to fix minor issues sometimes won't get you anywhere. ;)

---

### Post by ubuntu-freak on 2008-01-10
Download it here [http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466")

Save it to your home folder, then open the terminal and paste this: 

sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb


Nathan

---

