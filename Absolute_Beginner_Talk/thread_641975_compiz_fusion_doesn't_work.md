---
title: "compiz fusion doesn't work"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-12-16
i had broken package so i reinstalled feisty fawn but my compiz fusion doesn't work now.. it always worked on my comp.. i dont know whats wrong.. i tried to all kinda tutorial.. it doesn't work.. i cant even load ccsm .. can anyone help me ?

in case you guys need it 
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)

```

---

### Post by HunkieChan on 2007-12-16
please can anyone help me ?

---

### Post by HunkieChan on 2007-12-17
ugh.. please someone !!

---

### Post by vikramsharma on 2007-12-17
Have you installed xserver-xgl, you can do that using apt-get install or using the Synaptic Package Manager.  You might want to install the components of compizconfigsettingsmanager too.  You can have a look at the Synaptic Package Manager for packages concerning compiz, can also install emerald.  You can also have a look at the following links.

[http://ubuntuforums.org/showthread.php?t=630999](http://ubuntuforums.org/showthread.php?t=630999)

[http://ubuntuforums.org/showthread.php?t=627177](http://ubuntuforums.org/showthread.php?t=627177)

[http://ubuntuforums.org/showthread.php?t=595882](http://ubuntuforums.org/showthread.php?t=595882)

Hope this helps you out.

---

### Post by macogw on 2007-12-17
> **vikramsharma said:**
> Have you installed xserver-xgl, you can do that using apt-get install or using the Synaptic Package Manager.  You might want to install the components of compizconfigsettingsmanager too.  You can have a look at the Synaptic Package Manager for packages concerning compiz, can also install emerald.  You can also have a look at the following links.

[http://ubuntuforums.org/showthread.php?t=630999](http://ubuntuforums.org/showthread.php?t=630999)

[http://ubuntuforums.org/showthread.php?t=627177](http://ubuntuforums.org/showthread.php?t=627177)

[http://ubuntuforums.org/showthread.php?t=595882](http://ubuntuforums.org/showthread.php?t=595882)

Hope this helps you out.

XGL is just for ATI.  He has Nvidia.

---

### Post by vikramsharma on 2007-12-17
> **macogw said:**
> XGL is just for ATI.  He has Nvidia.

Sorry about jumping the gun.

---

### Post by vikramsharma on 2007-12-17
> **HunkieChan said:**
> i had broken package so i reinstalled feisty fawn but my compiz fusion doesn't work now.. it always worked on my comp.. i dont know whats wrong.. i tried to all kinda tutorial.. it doesn't work.. i cant even load ccsm .. can anyone help me ?

in case you guys need it 
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)

```

what error do you get trying to run ccsm through the Terminal, please print the error so we can have a better understanding of it.

---

### Post by HunkieChan on 2007-12-17
> **vikramsharma said:**
> what error do you get trying to run ccsm through the Terminal, please print the error so we can have a better understanding of it.

i get this error.. when i put ccsm
```

Traceback (most recent call last):
File "/usr/bin/ccsm", line 45, in <module>
  idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

```

and when i put compiz --replace 

```

/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libccp.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'ccp'

```

---

### Post by vikramsharma on 2007-12-17
I had a similar error once, I think reinstalling compiz with the components might solve the problems also installing python might help.  To me looks like an error relating to python.  Compiz is not launching.  There is a thread thats relating to this particular error.

[http://ubuntuforums.org/showthread.php?t=534341&page=3](http://ubuntuforums.org/showthread.php?t=534341&page=3)

do check out the reply of fornax01, that could solve your problem.  In case that doesn't solve your problem please go through the complete thread.  I will also try and look for answer to your problem.

---

### Post by HunkieChan on 2007-12-17
> **vikramsharma said:**
> I had a similar error once, I think reinstalling compiz with the components might solve the problems also installing python might help.  To me looks like an error relating to python.  Compiz is not launching.  There is a thread thats relating to this particular error.

[http://ubuntuforums.org/showthread.php?t=534341&page=3](http://ubuntuforums.org/showthread.php?t=534341&page=3)

do check out the reply of fornax01, that could solve your problem.  In case that doesn't solve your problem please go through the complete thread.  I will also try and look for answer to your problem.

it says to downgrade ccsm .. he doesn't say how to.. how do i downgrade it ? beside ccsm, compiz doesn't work for me either. do you think downgrading ccsm will fix compiz too ?

---

### Post by vikramsharma on 2007-12-18
I am not an expert in this but removing the concerning repository (Trevino's repositories) mentioned in the forum would enable you to install stable version of compiz and ccsm.  My suggestion would be to completely remove compiz and compiz components and reinstall compiz along with ccsm.  You can remove compiz, ccsm and vcarious other compiz realted components through Synaptic Package Manager.  In case there is some one else going through this thread, your advice is appreciated.  Thanks.

---

### Post by HunkieChan on 2007-12-18
how do i trevino's respositories ? i mean.. i know how to remove em but i dont know which one is that.. . plus if i do it .. will it still be in synaptic ?

---

### Post by vikramsharma on 2007-12-18
Yes check for repositories in Synaptic Package Manager or you can edit your repositories through 'Software Sources'.  You can go to Software Sources through System_>Administration_>Software Sources.  There in look for Trevinos deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb).  I am linking another thread, hope it would clear some of your doubts.  [http://ubuntuforums.org/showthread.php?t=580063](http://ubuntuforums.org/showthread.php?t=580063)

---

### Post by HunkieChan on 2007-12-18
thanks alot bro that helped .. thanks alot

---

### Post by vikramsharma on 2007-12-18
You are welcome Sir. I am glad to have helped you out.

---

