---
title: "Instalation app in Wine"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by slusar_o2 on 2007-07-28
Hi. I treid to use wine. Firstly i started Synaptic, typed in search "wine" and downolad all package.
Them i configure wine using some polish "HowTo" threat.
Them I wanted install InfanView. I downloaded it.

when i typed in terminal ```
wine /home/slusar/Download/kGet/infa.exe
```
I saw

```
slusar@slusar-desktop:~$ wine /home/slusar/Download/kGet/infa.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\slusar\\Download\\kGet\\infa.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\slusar\\Download\\kGet\\infa.exe" failed, status c0000135
slusar@slusar-desktop:~$
```

I had download taht missing MFC42.DLL  file, put it into stystem32 directory and tried install InfanView once again

After i typed again that installation "order" i saw a wine deskop for a moment them it disappear. Nothing more had happened : (

What can be wrong?

---

### Post by andyho on 2007-07-28
Is it showing up in your list of programs if you type in winecfg in the terminal?

---

### Post by yogo on 2007-07-28
> **andyho said:**
> Is it showing up in your list of programs if you type in winecfg in the terminal?



I do not have one single program listed, is this because they are installed in Windows and I need to also install them on Linux?


TIA

---

### Post by slusar_o2 on 2007-07-28
> **andyho said:**
> Is it showing up in your list of programs if you type in winecfg in the terminal?

no.
[http://www.mangacars.pl/upload/images/5874omg.png](http://www.mangacars.pl/upload/images/5874omg.png)

And I should add that installation file into that winecfg?

---

### Post by andyho on 2007-07-28
when I had to install a prog with wine I had to install the actual "install" .exe file and then go back in and install the program .exe file. worked fine after that!

---

### Post by MrFSL on 2007-07-28
There are huge differences between different versions of mfc42.dll. Where did you download it from? If you downloaded it from "dll files" odds are you will have problems.

---

### Post by slusar_o2 on 2007-07-28
> **andyho said:**
> when I had to install a prog with wine I had to install the actual "install" .exe file and then go back in and install the program .exe file. worked fine after that!

nach. That's not work : (

And i have downolad dll from here 
[http://www.dll-files.com/dllindex/dll-files.shtml?mfc42](http://www.dll-files.com/dllindex/dll-files.shtml?mfc42)

---

### Post by MrFSL on 2007-07-28
Download it from somewhere else:

I found this in google:
[http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mfc42.dll/6.0.400/download.html](http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mfc42.dll/6.0.400/download.html)

---

### Post by slusar_o2 on 2007-07-28
LoL its working : D
thanks man : )

---

### Post by MrFSL on 2007-07-28
No problem anytime. The real problem comes when you have several MFC42.dll files and you have to remember which one works with which application.

;)

---

