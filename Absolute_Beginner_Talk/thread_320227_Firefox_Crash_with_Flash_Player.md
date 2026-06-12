---
title: "Firefox Crash with Flash Player"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by tc10b on 2006-12-16
Hi, I've recently put Xubuntu on my machine and it's been running great.
I only have one small problem. Firefox doesn't run very well. It keeps crashing when I try to view a page with flash on it, such as hotmail etc. This is since I installed the flash plugin. I don't really know how to fix it and would appreciate some help. ](*,) 

Cheers in advance.

Tom

---

### Post by taurus on 2006-12-16
Maybe the sites require flash 8 or above and you are using flash 7!  Start firefox and in the address field, see which flash plugin you have!

```
about:plugins
```

---

### Post by pay on 2006-12-17
I heard that this is a bug with flash and 16bit colour depth. You can change the colour depth to 24 with```
sudo nano /etc/X11/xorg.conf
```and changing the appropriate section.

---

### Post by tc10b on 2006-12-17
Hi thanks for the quick reply, I do have flash 7 but I don't think that's what's causing the problem.
I've tried changing the xorg.conf and am testing it.

---

### Post by tc10b on 2006-12-17
Hi thanks for the advice. Firefox doesn't crash anymore! :)

Thanks for the help

Tom

---

### Post by Preserved Killick on 2006-12-19
I have:
MIME Type 	                        Description 	            Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	       Yes
application/futuresplash 	   FutureSplash Player 	   spl 	          Yes

My X config is already at a depth of 24.

I also tried two other suggestions I saw that had worked for others.  One involved editing /etc/firefox/firefoxrc and the other was an edit of /usr/bin/firefox.  I didn't have success with either. 

Another suggestion was to uninstall a library, which, it turns out, was not installed on my system anyway.

I tried Konqueror, but can't seem to find a way to install Flash.  The directions for installing flash are all for Mozilla.

 ](*,) 

Is there a way forward here?  Is an update for this expected from Ubuntu or Mozilla or Adobe?

Thank you,

-- P. Killick

---

### Post by taurus on 2006-12-19
What version of flash do you have?

From firefox's address field:
```
about:plugins
```

---

### Post by Preserved Killick on 2006-12-19
I am using plugin 7.0 r61.

---

### Post by taurus on 2006-12-19
> **Preserved Killick said:**
> I am using plugin 7.0 r61.
Maybe the reason firefox crashes because those sites that you've visited require you to have at least flash 8!  Therefore, you need to install flash 9 plugin for firefox if you wish.  Automatix2 comes with flash 9 plugins so install automatix2 and use it to install flash 9 for your firefox then...

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by Preserved Killick on 2006-12-19
> **taurus said:**
> Maybe the reason firefox crashes because those sites that you've visited require you to have at least flash 8!  Therefore, you need to install flash 9 plugin for firefox if you wish.  Automatix2 comes with flash 9 plugins so install automatix2 and use it to install flash 9 for your firefox then...

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

Thanks for the suggestion, Taurus.  I'm trying to use YouTube and they only require Flash 7.  Here are the site req's:

    * Macromedia Flash Player 7.0+ plug-in
    * Windows 2000 or higher with latest updates installed
    * Mac OS X 10.3 or higher
    * Firefox 1.1+, Internet Explorer 5.0+, or Safari 1.0+
    * Broadband connection with 500+ Kbps
-----------------------

If I don't need any higher than Flash 7, should I move on to 9 anyway?  And do I have to use Automatix2 to get Flash 9?

Thank you!  :) 

-- Preserved Killick

---

### Post by megs on 2006-12-19
Preserved Killick,
You can get Flash 9 from [http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html) if you prefer.  I am on edgy - for me it was a case of downloading the tar file somewhere.  Then tar -xzf the file, to get out libflashplayer.so.  Then copying this to /usr/lib/firefox/plugins, probably overwriting the version that is in there currently.  Restarting firefox, and loading up about:plugins should then show something like :
    File name: libflashplayer.so
    Shockwave Flash 9.0 d78

I was having problems earlier on with the wrong colour depth (16) causing crashes.  Frustrating until I twigged as to why...
Cheers,
Chris

---

### Post by Preserved Killick on 2006-12-21
Thanks, Meg.  I downloaded Flash 9 and it's installed and working.  :) 

-- Killick

---

