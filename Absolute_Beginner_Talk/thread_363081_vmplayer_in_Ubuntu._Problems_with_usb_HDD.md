---
title: "vmplayer in Ubuntu. Problems with usb HDD"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2007-02-16
I'm using vmplayer to run Windows XP as a Guest OS over Ubuntu host.
This works very well and dramatically facilitates changing from Ubuntu to Windows compared to the dual boot situation.

However, there is just one annoying problem. This is that my virtual Windows doesn't always recognise my usb external HDD (where I have all my music and photos).
Nevertheless, about 20% of the time it DOES recognise it and everything works fine until and I shut down and start up again.

I understand that this is a known problem in vmware for usb devices in general. However, I did try this "fix" ([http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=3862823&sliceId=SAL_Public&dialogID=10535760&stateId=0%2](http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=3862823&sliceId=SAL_Public&dialogID=10535760&stateId=0%2)) but found that it made absolutely no difference to whether or not my usb HDD was recognised or not.

Note that my usb HDD is hooked up to a usb 1.1 port as I believe vmware has problems with usb 2.0

I would be interested to hear others experiences particularly if a resolution is available.

Thanks
Paul

---

### Post by Richard Kut on 2007-02-16
Maybe try using VMware Server instead of the player?

---

### Post by PaulFXH on 2007-02-16
Yes, that is an option particularly as the server is also free.
However, vmplayer really is working so unexpectedly well, that it would be a pity to give up until I know there just is no way to resolve my usb hdd problem.

Has anybody out there been able to get Windows XP (as guest OS) to ALWAYS recognise the external HDD?

---

### Post by flossgeek on 2007-02-16
You could dump VMWare, I have tried it at work so I have GNU/Linux on my desktop as well, its awfully slow. Now I know all virtual machines are slow but VMWare just seems painful. Have you tried VirtualBox? Give it a go:-

[http://www.virtualbox.org/](http://www.virtualbox.org/)

Not sure how it will respond to your USB HDD though, thats for you to find out...

---

### Post by PaulFXH on 2007-02-16
Thanks for the suggestion but for me vmplayer is definitely NOT slow.
Indeed my virtual Windows XP is at least as fast, if not faster than my "real" WinXP.
Now, if only I could get the usb HDD to always work.......................

---

