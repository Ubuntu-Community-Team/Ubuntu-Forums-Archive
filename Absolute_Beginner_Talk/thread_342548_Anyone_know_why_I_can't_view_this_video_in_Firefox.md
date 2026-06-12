---
title: "Anyone know why I can't view this video in Firefox?"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by kliljedahl on 2007-01-20
I get the message that I need the Macromedia Flash Player (which I have). It's the only one I've found that won't play. It's no biggie because it opens in Opera, but I'd like an understanding of why, if possible: [http://www.nytimes.com/packages/khtml/2007/01/18/obituaries/20070118_BUCHWALD_FEATURE.html]("http://www.nytimes.com/packages/khtml/2007/01/18/obituaries/20070118_BUCHWALD_FEATURE.html")

---

### Post by ChadMMc on 2007-01-20
Hi, I just viewed it and my flash player works fine. Are you sure you have the newest version of the flash player (flash 9, released yesterday or 2 days ago)
You can get it here. [http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4](http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4)

---

### Post by kliljedahl on 2007-01-20
I thought I did, but apparently I don't. I downloaded and opened on the desktop. What is the best procedure for installing? I'm clueless now, but intend to learn.

---

### Post by Tmi on 2007-01-20
If I remember correctly there is a readme file included in the downloaded file (which probably will autoopen if you click it in your desktop environment).

---

### Post by deadgobby on 2007-01-20
Here is how you can install the newest version of flash.
[http://www.ubuntuforums.org/showthread.php?t=279990](http://www.ubuntuforums.org/showthread.php?t=279990)
GObby

---

### Post by petersjm on 2007-01-20
Extract the downloaded tar (right-click "extract here") then in the terminal, navigate to the new folder (cd /path/to/folder - you can drag the folder into the terminal and it will fill in its location for you). Hit enter. Now you're in the folder. Type "./flashplayer-installer" (without the quotes). Bingo, it's done.

---

### Post by kliljedahl on 2007-01-20
> **deadgobby said:**
> Here is how you can install the newest version of flash.
[http://www.ubuntuforums.org/showthread.php?t=279990](http://www.ubuntuforums.org/showthread.php?t=279990)
GObby

Just did that and I still get the same message. I didn't realize Flash 9 had gone out of beta though.

---

### Post by kliljedahl on 2007-01-20
Now I get the message: NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.
and it still won't play that video.

---

### Post by Malta paul on 2007-01-20
To remove XPT.DAT    Go to: Places>Home Folder>View>Show hidden folders>    then Find .Mozilla-Thunderbird (icon) Inside you will find the Xpti.dat file, then move to trash.
Hope tis is of help :)

---

### Post by ComplexNumber on 2007-01-20
> **kliljedahl said:**
> I get the message that I need the Macromedia Flash Player (which I have). It's the only one I've found that won't play. It's no biggie because it opens in Opera, but I'd like an understanding of why, if possible: [http://www.nytimes.com/packages/khtml/2007/01/18/obituaries/20070118_BUCHWALD_FEATURE.html](http://www.nytimes.com/packages/khtml/2007/01/18/obituaries/20070118_BUCHWALD_FEATURE.html)
go to */usr/lib/mozilla-firefox/plugins *and* /home/>your-username>/.mozilla/plugins, a*nd tell me what you have installed. i have my flash 9 installed in my home directory, and i have provided a screenshot of what is in those 2 directories above so that you can see if you have flash installed. the 1st screenshot shows /usr/lib/mozilla-firefox/plugins and the 2nd shows the contents of /home/>your-username>/.mozilla/plugins

---

### Post by kliljedahl on 2007-01-20
libflashplayer.so in both, and I'm still being told on that page that I need it.

---

### Post by kliljedahl on 2007-01-20
Also, Firefox has crashed twice opening that page.

---

### Post by ComplexNumber on 2007-01-20
> **kliljedahl said:**
> libflashplayer.so in both, and I'm still being told on that page that I need it.
you mean in **both(ie in /usr/lib and in your home directory) directories**? if so, i would suggest that you *may* have different versions of flashplayer in each of them and that they are clashing.  
as a test, will you create a temporary directory in your home directory and call it something like 'flash-backup', then move the flashplugin in the mozilla directory in your home directory to the 'flash-backup' directory. then restart firefox and tell me if it still crashes.

---

### Post by kliljedahl on 2007-01-20
I see what it did now. It only  installed in the Home folder, not the /usr/lib~ folder
When I went to the response telling linking to how to uninstall the old and reinstall the new, the message was it couldn't uninstall because it was not installed. Yet the libflashplayer.so was in the home plugins folder the usr/lib/mozilla/plugins folder and the usr/lib/mozilla-firefox/plugins folder. This is perplexing.

---

