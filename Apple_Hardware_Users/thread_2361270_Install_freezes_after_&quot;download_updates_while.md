---
title: "Install freezes after &quot;download updates while installing&quot; screen (Gnome 17.04, USB)"
date: 2017-05-14
forum: Apple Hardware Users
---

### Post by thomashartmann on 2017-05-14
Hey! I'm having a little issue with installing Gnome on my 2012 Retina Macbook Pro. 

I have created a bootable USB drive with Gnome 17.04, and can "Try Ubuntu" with no issues, but when installing it, either from trial mode or straight from the installer, the process stops responding after the screen where you can choose whether to download updates while installing and whether you want to install the standard software pack, and later on freezes completely. I have tried ticking both, only one, and none of the options.

No error messages show up, and the rest of the system runs fine (well, until it freezes everything).

The issue appears to be similar this: [https://ubuntuforums.org/showthread.php?t=2277233](https://ubuntuforums.org/showthread.php?t=2277233), but I can't seem to find a clear solution in that thread.

I have followed[ this guide]("https://www.lifewire.com/dual-boot-linux-and-mac-os-4125733") for installation purposes, with the exception of using a downloaded ISO file, rather than UNetbootin's option to download it automatically. This was because I wanted to run Gnome rather than the standard Ubuntu. They guide specifies that using a downloaded ISO will not work, but seeing as the "Try Ubuntu" option works just fine, and the installer opens too, that doesn't appear to be the problem. As was mentioned by oldfred in the similarly themed thread:
"[COLOR=#000000]I believe one of the installers did not work with the new UEFI. But unetbootin has worked for most. A few have had issues and used other installers.[/COLOR]
[COLOR=#000000]And some flash drives have had issues.[/COLOR]
[COLOR=#000000]But in all those cases it would not start at all.[/COLOR]"

It might be worth mentioning that to get Wi-Fi up and running, manual installation of b43 is necessary (no ethernet cables), but it works fine after that, although it seems terribly slow most of the time (but I can't rule out the router as the culprit for that issue).

Anyway, any and all input on this would be much appreciated, and if there is any pertinent info I've left out, just let me know! In advance: cheers!

EDIT: Can confirm that the same thing happens using regular Ubuntu 17.04 downloaded by Unetbootin (e.g. as per the guide), as well as using the fallback installers.

---

