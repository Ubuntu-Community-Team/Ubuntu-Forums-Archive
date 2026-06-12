---
title: "Wine: SHGetFolderPathW Failed to create directory L&quot;Y:\\Desktop&quot;"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by GeneralHooHa on 2007-08-05
When using wine, I get this error message: 
```
nick@Private-Laptop:~$ sudo wine /media/cdrom0/install.exe
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
err:shell:SHGetFolderPathW Failed to create directory L"Y:\\Desktop".
err:shell:SHGetFileInfoW pidl is null!
err:shell:SHGetFolderPathW Failed to create directory L"Y:\\Desktop".

```

I also see this when running winecfg. It just closes the program. What is happening?

---

### Post by happyhamster on 2007-08-05
Perhaps you don't have the right permissions in some folders, but it's also likely that running wine as root (by using 'sudo') causes trouble. Basically, you should never run wine or winecfg as root, just run it as a regular user. So, first thing you can try is to remove wine completely (using Synaptic), including the hidden ".wine" folder in you home dir, then re-install it. Then run winecfg and wine (without 'sudo').

---

### Post by GeneralHooHa on 2007-08-05
I re-installed wine, and everything is working. I had to do a "locate wine" and manually delete all the files, but everything is peachy now.

---

