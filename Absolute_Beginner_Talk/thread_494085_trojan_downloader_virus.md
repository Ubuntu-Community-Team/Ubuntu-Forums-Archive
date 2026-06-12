---
title: "trojan downloader virus"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by urvaksh on 2007-07-06
I'm using Windows XP and Ubuntu on my laptop.
When I scan Windows with Nod32, Ad-aware and Spydoctor, my system comes up virus and malware clean.
However, when I boot via Linux and run a virus scan using Avast, it alerts me to the Win 32: Delf-XQ [TR] virus in pagefile.sys. I googled it and I think it's a trojan downloader.
I think the scanner scans all the windows files too, even though I'm in Linux.
Avast asks if I want to remove the virus and I delete it each time, yet it comes back.
I had the same problem with a virus in the hiberfil.sys folder, but after I disabled hibernation, that warning disappeared.
I wiped out the pagefile in Windows and reset it. But then, when I booted into Ubuntu and ran the Avast scanner, I was alerted to another Win32 trojan downloader.
I don't know if these are false positives. In the host file directory in ubuntu I see a pagefile folder. Should I delete that? Could that be where the virus is?
Thanks a ton.

---

### Post by waggygee on 2007-07-06
Does you windows behave unusual or show any of the symptoms of the win32 trojan downloader? and ensure that your NOD32 is up to date. try remove your internet connection then run the virus scan and remove the 'virus' again. Does it still come back?
A friend of mine has a program call Trojan remover he said its real good against trojan viruses (its a windows program)

---

### Post by reset3x on 2007-07-06
> **urvaksh said:**
> I'm using Windows XP and Ubuntu on my laptop.
When I scan Windows with Nod32, Ad-aware and Spydoctor, my system comes up virus and malware clean.
However, when I boot via Linux and run a virus scan using Avast, it alerts me to the Win 32: Delf-XQ [TR] virus in pagefile.sys. I googled it and I think it's a trojan downloader.
I think the scanner scans all the windows files too, even though I'm in Linux.
Avast asks if I want to remove the virus and I delete it each time, yet it comes back.
I had the same problem with a virus in the hiberfil.sys folder, but after I disabled hibernation, that warning disappeared.
I wiped out the pagefile in Windows and reset it. But then, when I booted into Ubuntu and ran the Avast scanner, I was alerted to another Win32 trojan downloader.
I don't know if these are false positives. In the host file directory in ubuntu I see a pagefile folder. Should I delete that? Could that be where the virus is?
Thanks a ton.
 
pagefile.sys is your windows swap file..... Try  turning of your page file  , reboot and scan your system again.. Then turn on your pagefile again... and do a another scan...

---

