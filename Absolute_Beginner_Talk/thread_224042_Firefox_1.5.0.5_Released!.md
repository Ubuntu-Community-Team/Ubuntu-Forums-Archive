---
title: "Firefox 1.5.0.5 Released!"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by bierpullen on 2006-07-27
Firefox 1.5.0.5 Released!

Mozilla has released the official version of the newest firefox.
[http://www.mozilla.org/firefox/](http://www.mozilla.org/firefox/)



-----------------------------------------


Acer laptop 1522, 528mb, AMD 64 3000, 64mb Nvidia.
[http://www.antarctica-rbak.nl/ubuntu/acer_aspire.php](http://www.antarctica-rbak.nl/ubuntu/acer_aspire.php)

---

### Post by x64Jimbo on 2006-07-27
Just saw this last night. Hooray Firefox! Now can someone tell me if they've fixed that stupid memory leak yet?

---

### Post by aysiu on 2006-07-27
> **x64Jimbo said:**
> Just saw this last night. Hooray Firefox! Now can someone tell me if they've fixed that stupid memory leak yet?
Here's what got fixed: [quote=Mozilla's Website]Fixed in Firefox 1.5.0.5
MFSA 2006-56 chrome: scheme loading remote content
MFSA 2006-55 Crashes with evidence of memory corruption (rv:1.8.0.5)
MFSA 2006-54 XSS with XPCNativeWrapper(window).Function(...)
MFSA 2006-53 UniversalBrowserRead privilege escalation
MFSA 2006-52 PAC privilege escalation using Function.prototype.call
MFSA 2006-51 Privilege escalation using named-functions and redefined "new Object()"
MFSA 2006-50 JavaScript engine vulnerabilities
MFSA 2006-48 JavaScript new Function race condition
MFSA 2006-47 Native DOM methods can be hijacked across domains
MFSA 2006-46 Memory corruption with simultaneous events
MFSA 2006-45 Javascript navigator Object Vulnerability
MFSA 2006-44 Code execution through deleted frame reference[/quote]

---

### Post by x64Jimbo on 2006-07-27
Several mentions of "Memory" in there. Hopefully it's fixed now... Heh. Only one way to find out...
/me opens firefox and walks away for a couple days...

---

### Post by easyease on 2006-07-27
i just downloaded firefox2-alpha off the klik site, thats proper release is due for autumn but it seems very fast and efficient but the downside is a lot of the old extensions dont work on it......

---

### Post by Kurt` on 2006-07-27
> **x64Jimbo said:**
> Several mentions of "Memory" in there. Hopefully it's fixed now... Heh. Only one way to find out...
/me opens firefox and walks away for a couple days...

*Notes 1.5 gigs of ram usage* ;)

---

### Post by TheRingmaster on 2006-07-27
when will this release hit ubuntu?

---

### Post by aysiu on 2006-07-27
> **jpazindustries said:**
> when will this release hit ubuntu?
Probably in about a week. That's how long it took the devs to package 1.5.0.4 after it came out.

If you're in a hurry, get the Mozilla (not Ubuntu) version of Firefox--it's self-updating.

---

### Post by x64Jimbo on 2006-07-27
> **easyease said:**
> i just downloaded firefox2-alpha off the klik site, thats proper release is due for autumn but it seems very fast and efficient but the downside is a lot of the old extensions dont work on it......
Solution:
Nightly Tester Tools extension
[http://users.blueprintit.co.uk/~dave/web/firefox/nightly/index.html](http://users.blueprintit.co.uk/~dave/web/firefox/nightly/index.html)

---

### Post by easyease on 2006-07-27
wahey nice one Jimbo! thanks!

---

### Post by x64Jimbo on 2006-07-27
You're welcome. I've been using that extension since before 1.0 came out. It made things very simple and I've almost always been running versions of firefox that exceed the current release without having to worry about extension compatibility.

---

### Post by SonicTempest on 2006-07-27
> **x64Jimbo said:**
> Just saw this last night. Hooray Firefox! Now can someone tell me if they've fixed that stupid memory leak yet?

IIRC, the major memory leaks are only due to be fixed in Firefox 3.0 (due early next year). The incremental 1.5xx patches are only to fix security holes and other bugs, I believe.

---

### Post by x64Jimbo on 2006-07-27
> **SonicTempest said:**
> IIRC, the major memory leaks are only due to be fixed in Firefox 3.0 (due early next year). The incremental 1.5xx patches are only to fix security holes and other bugs, I believe.
The release notes mentioned stability, so that's why I wondered.

---

### Post by lime4x4 on 2006-07-27
it's in the repositories now..
From terminal

sudo apt-get update
sudo apt-get upgrade

---

### Post by Rich3077 on 2006-07-27
If I update using apt-get will I loose the cool original firefox logo?

---

### Post by TheRingmaster on 2006-07-27
> **lime4x4 said:**
> it's in the repositories now..
From terminal

sudo apt-get update
sudo apt-get upgrade

Thanks for telling me about that! :)

---

### Post by waffen on 2006-07-28
Hi,

I updated my system via update manager, and its installing the new FF version, but when I click the FF icon its open the old 1.5.0.4, its a bug?:confused:

---

### Post by mlind on 2006-07-28
> **waffen said:**
> Hi,

I updated my system via update manager, and its installing the new FF version, but when I click the FF icon its open the old 1.5.0.4, its a bug?:confused:

try *killall firefox* and then start it again. Version should be 1.5.0.5.

---

### Post by waffen on 2006-07-28
I try this but not found....

---

### Post by Sef on 2006-07-28
> I updated my system via update manager, and its installing the new FF version, but when I click the FF icon its open the old 1.5.0.4, its a bug?

Not a bug. My update went fine. Just used the updater when it said I had some updates to install.

---

### Post by waffen on 2006-07-28
OK, I remember then the only way to update my FF its via this:

[https://help.ubuntu.com/community/FirefoxNewVersion#head-a9caf32d1e839c9c8cf0b9db6f834937aad86df2]("https://help.ubuntu.com/community/FirefoxNewVersion#head-a9caf32d1e839c9c8cf0b9db6f834937aad86df2")

because I update from Brezy to Dapper my entire Ubuntu and its the only way ti install the last version in Brezy.

Any idea how revert this?

Thansk!

---

### Post by mlind on 2006-07-28
> **waffen said:**
> OK, I remember then the only way to update my FF its via this:

[https://help.ubuntu.com/community/FirefoxNewVersion#head-a9caf32d1e839c9c8cf0b9db6f834937aad86df2]("https://help.ubuntu.com/community/FirefoxNewVersion#head-a9caf32d1e839c9c8cf0b9db6f834937aad86df2")

because I update from Brezy to Dapper my entire Ubuntu and its the only way ti install the last version in Brezy.

Any idea how revert this?

Thansk!

Have you used dpkg-divert on firefox binary or have you installed it locally?

---

### Post by waffen on 2006-07-28
No, I just follow the Instalation Guide [https://help.ubuntu.com/community/FirefoxNewVersion]("https://help.ubuntu.com/community/FirefoxNewVersion")

---

### Post by mlind on 2006-07-28
> **waffen said:**
> No, I just follow the Instalation Guide [https://help.ubuntu.com/community/FirefoxNewVersion]("https://help.ubuntu.com/community/FirefoxNewVersion")

That page also has "Removing" instructions, tried following those yet?

---

### Post by ozarkman on 2006-07-28
upgrade went smooth for me. except im back to the ugly IMO ubuntu icons how can I switch back. I tried the dapper fix 

[http://ubuntuforums.org/showthread.php?t=199193&highlight=replace+firefox+icon](http://ubuntuforums.org/showthread.php?t=199193&highlight=replace+firefox+icon)

but their still their. what next?

---

### Post by mostwanted on 2006-07-28
I have version 1.5.0.5 and I haven't done anything out of the ordinary to update it, came as an update from dapper-security.

---

### Post by harpo_the_whale on 2006-07-29
Just getting all of my machines updated to the latest Firefox 1.5.0.5 also. It looks like some of the stability issues have been resolved... definately better than 1.5.0.4 & 1.5.0.3. Thanks for letting me know guys & gals!

Harpo

---

### Post by domeili on 2006-07-29
i download the tar package from the mozilla/firefox officialsite ,when i issue the command /opt/firefox ,it shows me : Segment Fault,Cannot excute $prog

---

### Post by mlind on 2006-07-29
> **domeili said:**
> i download the tar package from the mozilla/firefox officialsite ,when i issue the command /opt/firefox ,it shows me : Segment Fault,Cannot excute $prog

Why don't you use Ubuntu repositories to get the update?

---

