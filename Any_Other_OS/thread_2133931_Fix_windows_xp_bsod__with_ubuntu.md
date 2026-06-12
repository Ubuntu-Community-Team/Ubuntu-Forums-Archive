---
title: "Fix windows xp bsod  with ubuntu"
date: 2013-04-09
forum: Any Other OS
---

### Post by BobbiPinz on 2013-04-09
Hi there, I hope I'm posting in the right place. I have been trying for a few weeks now to fix an unbootable windows xp. I get BSOD and I have no recovery cd. I have gone through numerous articles where ubuntu has rescued others but none of the solotiouns have worked for me... so... Here I am... Help me please!?!? 

I am currently online with said unit with ubuntu live and must say, once I get windows fixed ubuntu is going alongside.. but till then I would appreciate any assistance.

I have tried repairing the mbr but get told I have no permissions, I've tried installing lilo and ntfsfix but still no workie.

---

### Post by KnownSyntax on 2013-04-09
You can always make a CD from your manufacturer of your computer (since most-all have them online) that will basically re-install Windows XP for you to fix that issue. Have you also tried and looking to see if your computer has a "ghost" drive (hidden partition) that contains a backup on Windows XP from the factory?

You won't be able to contact Microsoft with any help since Windows XP is near (or at) it's end-life of support for everyone, so try either using Ubuntu or upgrade to a newer and better version of Windows.

---

### Post by nerdtron on 2013-04-09
> **BobbiPinz said:**
> Hi there, I hope I'm posting in the right place. I have been trying for a few weeks now to fix an unbootable windows xp. I get BSOD and I have no recovery cd. I have gone through numerous articles where ubuntu has rescued others but none of the solotiouns have worked for me... so... Here I am... Help me please!?!? 

I am currently online with said unit with ubuntu live and must say, once I get windows fixed ubuntu is going alongside.. but till then I would appreciate any assistance.

I have tried repairing the mbr but get told I have no permissions, I've tried installing lilo and ntfsfix but still no workie.

Does an error appears when you try to boot XP? Like NTLDR missing or something?
If your documents and files in the XP partiion are important to you, I suggest you backup them now to an external drive while you are in live mode. In the event you can't fix your XP, you're can just reinstall it.

---

### Post by leunam12 on 2013-04-09
Try Rescatux, it fixes windows MBR. I have used with XP and it works.

---

### Post by LostFarmer on 2013-04-09
Why do you think it is a MBR problem ?  It likely is not with a BSOD but could be.  What happens if you try safemode ? (tap F8 duing booting to get boot menu).  would agree with [**[COLOR=#000000]nerdtron[/COLOR]**]("http://ubuntuforums.org/member.php?u=895543") backing up important data and more infor on problem.

You may need to do a web search on how to make a Recovery Console cd.

---

### Post by BobbiPinz on 2013-04-10
It won't boot into safemode, lkgc, nothing. It doesn't say there is a problem other than error code 0xc000012f
I've tried recovery console and a number of other recovery systems (avira) etc. That's why I've resorted to ubuntu.
To try most others you have to at least be able to get into safemode

---

### Post by fantab on 2013-04-10
BSOD is generally caused by some malfunction in the XP itself. Or some bad install/update/upgrade in XP. 

If you have a XP repair CD or XP installation Disk then you can use that to repair that. You might be able to use Ubuntu to recover the "crash dump" File Location: %systemroot%; File extension: .DMP by mounting the XP C: partition, and perhaps be able to determine what went wrong. However, it may not be of any help if you are unable to boot into XP. Perhaps, REINSTALLING XP can be an option. When Using Windows ALWAYS CREATE A REPAIR DISK.

For more: [http://www.xpforums.com/search.php?searchid=26](http://www.xpforums.com/search.php?searchid=26)

---

### Post by lisati on 2013-04-10
*Thread moved to **Other OS/Distro Support**.*

---

### Post by leunam12 on 2013-04-11
> **LostFarmer said:**
> Why do you think it is a MBR problem ?  It likely is not with a BSOD but could be.  What happens if you try safemode ? (tap F8 duing booting to get boot menu).  would agree with [**[COLOR=#000000]nerdtron[/COLOR]**]("http://ubuntuforums.org/member.php?u=895543") backing up important data and more infor on problem.

You may need to do a web search on how to make a Recovery Console cd.Ok, I had a DUH! moment. BSOD blue screen of death, of course!

---

### Post by Habitual on 2013-04-11
> **BobbiPinz said:**
> It won't boot into safemode, lkgc, nothing. It doesn't say there is a problem other than error code 0xc000012f
I've tried recovery console and a number of other recovery systems (avira) etc. That's why I've resorted to ubuntu.
To try most others you have to at least be able to get into safemode Seen this?
[how to fix blue screen error c0000021a  status of 0xc000012f fatal system error?]("http://answers.microsoft.com/en-us/windows/forum/windows_xp-system/how-to-fix-blue-screen-error-c0000021a-status-of/d6deb640-9100-42df-9fc4-444b80937244")

---

### Post by BobbiPinz on 2013-04-11
Yes... Went through the whole process windows came preloaded with no disc

---

### Post by Habitual on 2013-04-11
> **BobbiPinz said:**
> Yes... Went through the whole process windows came preloaded with no discGet one. ;)

---

