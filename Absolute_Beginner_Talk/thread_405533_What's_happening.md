---
title: "What's happening?"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by David Oxland on 2007-04-09
This machine has dapper only installed as OS.  My Wife was surfing on Firefox and told me to "come look" and a clickthrough or bunch of popups were going with no prompting except to click no and try to close windows.  This cast itself as a Firefox problem and " would you like to install Systemdoctor to check your registery?"  I Googled it a bit and there was mention of a malware but all pretaining to Microsoft.

My question is;  Are Linux /Ubuntu users immune? Any action required?
My only actiion was to shutdown Firefox when I saw it happening
Thanks

---

### Post by Tsen on 2007-04-09
It was probably just a site that spammed popups, and not an actual infection in your Ubuntu installation.
I'd recommend you go to the Firefox addons page, install "Adblock Plus" and "Adblock Filterset G Updater".  With those two extensions installed, you shouldn't see any ads at all while browsing the internet.
Also, check your popup settings (Edit->Preferences->Content->"Block Popups", I think) to make sure they're turned on.

---

### Post by chalex on 2007-04-09
You shouldn't worry.  Whatever malware it was, it probably tried to get you to run a Windows executable or something like an ActiveX control, none of which works on your Linux machine.

---

### Post by aysiu on 2007-04-09
Get NoScript:
[https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)

---

### Post by ComplexNumber on 2007-04-09
> **David Oxland said:**
> This machine has dapper only installed as OS.  My Wife was surfing on Firefox and told me to "come look" and a clickthrough or bunch of popups were going with no prompting except to click no and try to close windows.  This cast itself as a Firefox problem and " would you like to install Systemdoctor to check your registery?"  I Googled it a bit and there was mention of a malware but all pretaining to Microsoft.

My question is;  Are Linux /Ubuntu users immune? Any action required?
My only actiion was to shutdown Firefox when I saw it happening
Thanks
system doctor? isn't that malware itself....similar to winfix? it won't affect linux, but will affect windows.

no operating system is immune, whatever people may have you believe. linux is naturally more secure than windows because of its better security model, but even linux has some viruses...however rare and unlikely to become infected. even with vista, despite microsofts focus on security, the windows OS was never meant as a multiuser system for the internet. thats not to bash microsoft or windows, but it is indeed true. when windows was first developed, it was intended for single user and non-networked. bill gates dismissed the internet as a fad, and so didn't incorporate features that would be useful for  a networked OS. to be fuly seccessful, microsoft would need to go back to the drawing board and resdesign the system from the ground up. however, thats never likely to happen because a) too much time and effort, and b) preserving backwards compatibility, especially because most of the worlds users and businesses use windows.
if you're running a server for winodows machines, an antivirus is necessary then. otherwise, only a firewall is really necessary for linux, as it is for all OS's.

---

### Post by gmos on 2007-05-18
I also had a recent encounter with the Systemdoctor popup which really caused me to worry a bit. 

I was browsing for Simcity Linux info on FireFox (with popups blocked) when went to a site and was immediately prompted to install and run it. This took me by surprise, firstly because _FireFox normally blocks popups and tells me when it has blocked them_, and secondly, _because it looked exactly like a system generated dialogue box_. The FireFox status bar was indicating that data was being transferred from systemdoctor - I quickly closed the popup/dialogue box. It reappeared again as soon as I hit the 'back' button to get away from the website, and again I quickly closed the dialogue box/popup. 

My concern was twofold:
1. Why wasn't it blocked by Firefox?
2. What was being downloaded, and how? (ie Was there something running?)

Did a quick search of forums and found some info on this malware (all windows forums). Did a search of my filesystem for 'systemdoctor' and 'vundo', and luckily found nothing.

Perhaps I've been a bit naive, but I didn't think this type of thing would happen with Linux and Firefox. It may not have been able to do anything - but it *looked* as if it was!

---

### Post by carlosqueso on 2007-05-18
Some websites have figured out ways around popup blockers.  It's just a particularly tricky one the firefox folks haven't figured out a way to block. 

Nothing was being downloaded and no programs were run.  I've seen this kind of thing occasionally.  The adblock suggestions above definitely help.

---

