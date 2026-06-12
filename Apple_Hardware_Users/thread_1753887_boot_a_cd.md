---
title: "boot a cd"
date: 2011-05-09
forum: Apple Hardware Users
---

### Post by martine.ginette on 2011-05-09
Hello,

Following [http://www.google.com/url?q=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FMactelSupportTeam%2FAppleIntelInstallation%23Single-Boot%3A%2520Ubuntu%2520Only&sa=D&sntz=1&usg=AFQjCNFkuf3JIfgRRiqcrYcFnvH0qdRmEA](http://www.google.com/url?q=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FMactelSupportTeam%2FAppleIntelInstallation%23Single-Boot%3A%2520Ubuntu%2520Only&sa=D&sntz=1&usg=AFQjCNFkuf3JIfgRRiqcrYcFnvH0qdRmEA) I have removed OSX from my MacBookPro 7,1 —those SSD are so small!— and then installed Natty on it.

However, now I can't boot any CD: I have tried with "C" and "option" keys, but the laptop always ends up booting on the HD. I will definitely have to boot a CD someday (e.g. to reinstall OSX when I have to give the laptop back), so I need to fix this. Any idea? Thanks in advance.

Cheers,
Martin.

---

### Post by Silmathoron on 2011-05-09
Just press Alt immediately before or when the gray screen appears

---

### Post by martine.ginette on 2011-05-18
Hi Silmathoron,

Many thanks for your reply. When I press the C key, I have a screen with only one option: "Windows", which obviously leads to Linux. But I never happen to boot the CD. It's a huge problem. Does somebody have an idea?

Martin.

---

### Post by martine.ginette on 2011-05-18
Sorry, I meant: when I press the "option" key. When I press the "C", the computer boots linux as usual.

---

### Post by martine.ginette on 2011-05-19
nobody?

---

### Post by snafu006 on 2011-05-20
does the computer read any disk? like when ubuntu is running and the disk is in do you see it?

---

### Post by martine.ginette on 2011-05-20
Yes it does!

I am wondering if it is related to the fact that I have totally removed OSX from the computer (following [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Single-Boot:%20Ubuntu%20Only](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Single-Boot:%20Ubuntu%20Only))...

And I am wondering if there is a way to undo this...

Thanks for your help anyway.

Martin.

---

### Post by snafu006 on 2011-05-20
**Resetting PRAM and NVRAM**

 
[LIST=1]
[*]Shut down the computer.
[*]Locate the following keys on the keyboard: Command, Option, P,  and R. You will need to hold these keys down simultaneously in step 4.
[*]Turn on the computer.
[*]Press and hold the Command-Option-P-R keys. You must press this key combination before the gray screen appears.
[*]Hold the keys down until the computer restarts and you hear the startup sound for the second time.
[*]Release the keys.
[/LIST]
 Your computer's PRAM and the NVRAM are reset to the default values.  The clock settings may be reset to a default date on some models. 



Use the link and reset 

**Resetting NVRAM in Open Firmware**

 If your computer is Open Firmware-based (Power PC) and you are unable  to reset NVRAM as described above, you may alternatively reset the  NVRAM and Open Firmware settings using the steps in the Solution section  of [         Message “To continue booting, type 'mac-boot' and press return”]("http://www.info.apple.com/kbnum/n42642").
 In some cases, an Open Firmware-based computer may not respond to the  keyboard commands noted above, and may not allow starting up into Open  Firmware by pressing and holding the Command, Option, O, and F keys  during startup.  If you are unable to get to an Open Firmware prompt  (and your computer supports doing so), try powering on the computer with  the power button held down continuously—as if you were doing a firmware  update.  This should force the computer into Open Firmware, allowing  the steps in the article noted above to be used.


[http://support.apple.com/kb/HT1431?viewlocale=en_US](http://support.apple.com/kb/HT1431?viewlocale=en_US)

---

### Post by martine.ginette on 2011-05-20
Many thanks for your help.

And sorry for the stupid question: how is it going to solve my problem? Thanks in advance.

Martin.

---

### Post by snafu006 on 2011-05-20
if your computer is able to read a disk when ubuntu or macos is running then its not the ubuntu or osx that is the problem its you pram or nvram just reset them to see if it helps

---

### Post by snafu006 on 2011-05-20
PRAM stores certain system and device settings in a location that Mac  OS X can access quickly. Exactly which settings are stored in the  computer's PRAM varies depending on the type of computer as well as the  types of devices and drives connected to the computer. Parameter RAM is a  small area of non-volatile RAM (NVRAM).
 Some information stored in PRAM includes:
 
[LIST]
[*]Display and video settings such as refresh rate, screen resolution, number of colors
[*]Startup volume choice
[*]Speaker volume
[*]Recent kernel panic information, if any
[*]DVD region setting     **Note: **Mac OS X stores your preselected DVD region choice  in PRAM for easy access. Resetting PRAM does not allow you to change the  DVD region.
[/LIST]
 Unlike prior versions of the Mac OS, Mac OS X does not store network  settings in PRAM. If you experience a network issue, resetting PRAM will  not help.
 If PRAM is reset, you may need to verify your time zone, startup  volume, and volume settings using System Preferences. Certain firmware  updates may reset PRAM as a normal part of their installation process.

---

### Post by martine.ginette on 2011-05-20
Thanks very much.

I recognize I'm a bit scared. Are you sure I'll be able to boot normally at least my linux partition after that? Anyway, I'll do some backup before trying. I'll keep you posted.

Martin.

---

### Post by snafu006 on 2011-05-20
yes you will be ok i have to do it sometimes

---

### Post by martine.ginette on 2011-07-11
OMG...IT WORKS!

Sorry for the late notice, but I was kind of scared the computer won't boot at all after that, so I wait until I have another computer running.

Anyway, you saved my computer, man! Thanks so much! Now I can boot from a CD, so I can reinstall Linux if there is a problem, and reinstall OSX when I have to give the computer back (it's a professional laptop). That's perfect!

Now I just have to figure out how to get rid of this stupid startup noise. I guess I'll be OK.

Thanks again!
Martin.

---

