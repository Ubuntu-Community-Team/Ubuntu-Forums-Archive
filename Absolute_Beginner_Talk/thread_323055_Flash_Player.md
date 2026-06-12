---
title: "Flash Player"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by Mac70 on 2006-12-21
I know theres been plenty posts on numerous forums about this but I just cant install it. Ive tried different things but the closest I got was a message saying it didnt work in my "x86/64bit environment".
Anyone got a foolproof method?

---

### Post by pissedoffdude on 2006-12-21
It works in 64-bit environments its just that you need to use it with a 32-bit browser.  If you install a 32-bit firefox you will be able to use flash without any problems.

---

### Post by Mac70 on 2006-12-21
Which would mean uninstalling Firefox and re-installing another version?](*,)

---

### Post by pissedoffdude on 2006-12-21
> **Mac70 said:**
> Which would mean uninstalling Firefox and re-installing another version?](*,)

Yes, you can go here [http://www.mozilla.com/en-US/firefox/]("http://www.mozilla.com/en-US/firefox/") and download the newest version.  Then extract it.  Then you can open up a terminal and do a sudo nautilus.  Place the extracted firefox into /usr/lib.  Then to get ur flash player to work, place the flash plugin in the /usr/lib/firefox/plugins

---

### Post by Mac70 on 2006-12-21
Im on Windows at the moment so Ill need to do it later but to be sure I do this right, is it Firefox 2 linux i686 that I want?
And how do I uninstall the old version or is that automatically done?

---

### Post by pissedoffdude on 2006-12-21
> **Mac70 said:**
> Im on Windows at the moment so Ill need to do it later but to be sure I do this right, is it Firefox 2 linux i686 that I want?
And how do I uninstall the old version or is that automatically done?

Yes i686 is the one that you want.  Just be sure to place the extracted folder in your /usr/lib folder.  If you would rather have this done automatically you can install swiftfox and swiftfox plugins via automatix.  Automatix will install a 32-bit swiftfox and 32-bit plugins including flash and java.

---

### Post by Mac70 on 2006-12-21
When you mentioned swiftfox I realised I had installed that today. And yes I have flash.Thanks.:D

---

