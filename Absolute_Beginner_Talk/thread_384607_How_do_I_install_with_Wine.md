---
title: "How do I install with Wine?"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Nigel Hewlett on 2007-03-14
I am trying to use Wine to install Memory Map (ordnance survey maps of the British Isles which I use for hill walking).  It includes an Installation Disk so I want to put that in the CD drive and try to get Wine to configure it.

At some point I think I accidentally deleted a drive mapping.  Now when I type winnecfg in the terminal I get the following message:

nhewlett@hopeful:~$ winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
err:winecfg:load_drives GetVolumeInformation() for 'C:\' failed, setting serial to 0

I tried reinstalling Wine but that didn't change the message.  

My questions are:
How do I repair what I have done to the drive mapping?
How do I then go about getting Wine to apply itself to installing this software (Memory Map)?  
(I would prefer to stay in the Terminal if possible.  Clicking away in the Winecfg window was how I came to grief last time.)

I would be really grateful for any advice anyone could give me.  This is really the only bit of software I still need Windows for so if I could get it running in Linux I would be fully liberated!

Nigel Hewlett

---

### Post by jem7v on 2007-03-14
Once you get Wine to work, you basically go to the directory the install exe is in and type
```
wine setup.exe
```
or whatever the file is named.  [http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine) explains it a little more in depth.

As for fixing wine and the likes, though, I'm not sure what to do!  Have you searched snippets of that error message on Google?

---

### Post by siciliancasanova on 2007-03-14
Sounds like he has some permission problems, I am not an expert though.

---

### Post by Nigel Hewlett on 2007-03-14
Thanks for the tip about Googling.  Several other people have run into this problem it seems.  But not found a solution yet.  For example I get (following one suggested solution):
nhewlett@hopeful:~$ sudo apt-get install winetksetup
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package winetksetup
nhewlett@hopeful:~$ winesetup
bash: winesetup: command not found

---

### Post by Nigel Hewlett on 2007-03-17
Still working on this! I have tried various things in the last couple of days and read some previous threads on using Wine.  I always get a message that L"c\\windows" and L"c:\\windows\\system32" are inaccessible.  Howevre, I am pretty sure I am in the same directory as the target software now (it's on CD) and I get a longer feedback message now.  I have found a setup.exe file, which I asume is the one I need Wine to apply to.  It is in a folder called setup.  This is what I get when I try to apply Wine to it: 

nhewlett@hopeful:~$ wine /cdrom/setup/setup.exe
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
fixme:msi:MsiInstallProductW L"C:\\setup\\Setup.msi" L" WISE_SETUP_EXE_PATH=C:\\setup\\setup.exe"
err:msi:copy_package_to_temp failed to copy package to temp path L"C:\\windows\\temp\\MSI614.tmp"
err:msi:ACTION_CallDllFunction Unable to load library
err:msi:ACTION_CallDllFunction Unable to load library
err:msi:ITERATE_Actions Execution halted, action L"LaunchConditions" returned 1627
nhewlett@hopeful:~$

Does anyone know what these messages mean?

Nigel Hewlett

---

