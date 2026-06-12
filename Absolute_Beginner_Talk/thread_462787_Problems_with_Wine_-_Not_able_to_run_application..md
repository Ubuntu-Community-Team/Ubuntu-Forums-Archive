---
title: "Problems with Wine - Not able to run application."
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by sibot on 2007-06-03
I finally installed wine and wanted to test out the most majorly needed application by me. There is this voip software, webcalldirect. That is my first and foremost need. Anyway so I installed wine and installed the software. The file name was setupWebcalldirect.exe.

anyway so moving on, i tried to run the software by:-

" wine webcalldirect.exe " and i got this error 
> 
wine: could not load L"c:\\windows\\system32\\webcalldirect.exe": Module not found


So moving on, i access the wine file manager with winefile, and tried to double click the application to make it work, which was btw present under /Program Files/Webcalldirect/Webcalldirect.exe 

and i got this error

> 
err:module:import_dll Library pdh.dll (which is needed by L"Z:\\home\\digvijoy\\.wine\\drive_c\\Program Files\\WebCallDirect.com\\WebCallDirect\\WebCallDirect.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\digvijoy\\.wine\\drive_c\\Program Files\\WebCallDirect.com\\WebCallDirect\\WebCallDirect.exe" failed, status c0000135


Can anyone please help me out. I really need this software and i really dont want to install xp, just to use this software. If theres anyway i can make it work, please do help me out.

If someone could spare sometime and check out the software by installing it on their machines to see if works, it would be really nice of them. 

Thanks in advance

---

### Post by YokoZar on 2007-06-03
What happens if you use a terminal window to navigate to the file and run it using wine webcalldirect.exe ?

---

### Post by david_kt on 2007-06-03
Download pdh.dll from

```
http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/P/pdh.dll
```

and then put it in:

```
~/.wine/drive_c/windows/system32
```

and then try to run it again.

DK

---

