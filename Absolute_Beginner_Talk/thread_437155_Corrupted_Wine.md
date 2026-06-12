---
title: "Corrupted Wine"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by mevets on 2007-05-08
I did a bad thing. I wanted to completly remove a piece of software installed through wine. The uninstaller did not get rid of it, so I delted it in the fake c drive. Now none of Wine works. I tried to 'Completly remove' wine in synaptic and then reinstall but it did not help. Is there a way I can run a repair? Or completely remove wine so I can reinstall correctly?

---

### Post by H.E. Pennypacker on 2007-05-08
Since installing Wine is easily done, I'd suggest you re-install Wine.  To install Wine, I recommend you use Automatix.  Check Automatix out at [www.getautomatix.com](www.getautomatix.com).

For more information on Wine, please see the wiki.ubuntu.com.  Here's the direct link:

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

It is very useful.

---

### Post by NeoLithium on 2007-05-08
After you tried to reinstall, did you try to run this in terminal:
winecfg

---

### Post by mevets on 2007-05-08
Automatix ran winecfg for me. Now I get:
```
fixme:ntdll:NtQuerySecurityObject (0x78,0x00000007,0x5217c8,0x0000f000,0x33e71c) stub!
```

---

### Post by NeoLithium on 2007-05-08
I don't encourage automatix use; cause it has been known to cause problems with users.  I'd just as soon suggest you remove wine completely, and install it from the repositories, just run winecfg on your own after the install is complete.

---

### Post by mevets on 2007-05-08
I keep the error. The installer im running under wine also The file C:\windows\temp\GLFe24.tml could not be opened. Please check that your disk is not fill and that you have access to the desination directory. Access denied.

---

### Post by H.E. Pennypacker on 2007-05-08
Please start Synaptic, and uninstall everything related to Wine.  Then please download Automatix, and install Wine using Automatix.  I suggest you DO use Automatix.

If you are having a problem with a specific Windows application, try uninstalling it properly.  Follow these instructions:

[https://help.ubuntu.com/community/Wine#head-41221272a5a61a8bbcbb36d2c8d9ef28ccc07ed9](https://help.ubuntu.com/community/Wine#head-41221272a5a61a8bbcbb36d2c8d9ef28ccc07ed9)

NeoLithium, it is wrong to debate the merits or faults of Automatix in a thread like this.  Please use a thread dedicated to that purpose.

---

### Post by mevets on 2007-05-08
I tried running the livecd and installing wine. It worked as it should. After reinstalling ubuntu after the live cd test, it will not install! I get the same error. Is there a reason it cant free up this temp file?

---

### Post by H.E. Pennypacker on 2007-05-08
Do me a favor.  Uninstall Wine completely, and remove the .wine folder from your home folder.  The .wine folder may be causing problems.  Any folders beginning with a period are HIDDEN.   Press CTRL-H to view hidden folders.

Then install Wine using Automatix, not the repositories.

---

### Post by mevets on 2007-05-08
I did so and still a no go. I have finally got it to work, I cheated though. I reinstalled and installed under a fresh install. I plan to experiment somemore under vmware. Ill report back at a later date.

---

