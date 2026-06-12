---
title: "Wine: Nothing happens after clicking on an .exe-file."
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by TheFly on 2007-11-19
Well, I'm having trouble opening a setup.exe file by using Wine (the newest version, installed from SynapticPM).
At first I got an error-message which told me to get the newest JScript.dll file. I downloaded the .dll file and pasted it into the system32 folder. The error disappeared, but when I click on the setup.exe (photoshop cs3), nothing happens!
I have tried to open an other .exe file and that worked without any problems.

What is wrong?

As I am totally new to Ubuntu and Wine, I would appreciate some help!

Thanks!

---

### Post by Phesto on 2007-11-19
have you tried running wine from the terminal?
wine ../location/setup.exe

Then post the output or error message here.

---

### Post by TheFly on 2007-11-19
Here is what I got from the Terminal:

```
fixme:console:AttachConsole stub ffffffff
Begin Adobe Setup
UI mode: Full GUI
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x12f1bc 0x12f1c8 (nil) (nil)
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
fixme:msxml:domelem_getAttributeNode 
End Adobe Setup.  Exit code: 4
fixme:msxml:DllCanUnloadNow 
fixme:msxml:DllCanUnloadNow 

```

---

### Post by duruttye on 2007-11-19
I'm not sure Photoshop CS3 works with wine, last time I checked, about 2-3 weeks ago, only photoshop 7 seemed to work.

Correct me if I'm wrong.

---

### Post by TheFly on 2007-11-19
Damn, how can I open and process my RAW-files then?

---

### Post by blithen on 2007-11-19
Can't Gimp do that? If not try Krita, it's in the repos.

---

### Post by TheFly on 2007-11-19
I tried out Krita, but I don't think that it can compare to PS at all. The program lacks of opportunities which I need when I'm editing my photos.

Any other programs?

---

### Post by duruttye on 2007-11-19
Gimp?

---

### Post by TheFly on 2007-11-19
No, it doesn't support CR2-files (RAW)

---

### Post by TheFly on 2007-11-19
Okay, I have figured out that I might have a copy of the PS7-version at work. WIll bring the CD home tomorrow and try to install it using Wine.

---

### Post by blithen on 2007-11-19
Alright good luck!

---

### Post by Abild on 2007-11-19
There are actually a few plug-ins availible for the gimp which enables it to open RAW files. One of them is availible from [http://ufraw.sourceforge.net/]("http://ufraw.sourceforge.net/") (i think it's in the repositories also)  and if you google "gimp raw" you will probably locate the rest quite easily.

If you insist on using photoshop people seems to be having success in running photoshop CS2 with wine. CS3, however, seems to be a no-go for the time being.

Finally since Wine improves so quickly i would recommend insatlling the version provided by the official wine repositories rather than relying on the outdated version provided by Ubuntu. Instructions are availible at the [wine website]("http://www.winehq.org/site/download")

---

