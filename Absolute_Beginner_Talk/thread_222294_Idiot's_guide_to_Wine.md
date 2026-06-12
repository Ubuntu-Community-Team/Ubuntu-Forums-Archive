---
title: "Idiot's guide to Wine?"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-07-24
I have been to the WineHQ, and looked at the FAQs,still I can't seem to find an actual guide of how to use Wine ! I have it installed and run winecfg from a terminal add an .exe from my windows partition, then what?............. :confused:  Thanks

---

### Post by Jagot on 2006-07-24
To open the file, from Terminal:

```
wine /location/of/file/filename.exe
```

---

### Post by Drakkor on 2006-07-24
drakkor@drakkor:~$ sudo wine /dev/hda1/Program Files/Skype/Phone/skype.exe
Password:
wine: cannot find '/dev/hda1/Program'
drakkor@drakkor:~$

---

### Post by Jagot on 2006-07-24
You can't leave spaces - it's recognising Program Files as two separate words.  It would need to be:

```
sudo wine /dev/hda1/Program\ Files/Skype/Phone/skype.exe
```

But you are aware there is a Linux version of Skype?

---

### Post by Drakkor on 2006-07-24
Yes I have the linux version already installed, I just wanted to try and run a windows program to check and see how wine works. Still having problems:
drakkor@drakkor:~$ sudo wine /dev/hda1/ProgramFiles/Skype/Phone/skype.exe
Password:
wine: cannot find '/dev/hda1/ProgramFiles/Skype/Phone/skype.exe'
drakkor@drakkor:~$ sudo wine /dev/hda1/Program/Files/Skype/Phone/skype.exe
wine: cannot find '/dev/hda1/Program/Files/Skype/Phone/skype.exe'
drakkor@drakkor:~$ sudo wine /dev/hda1/Program\ Files/Skype/Phone/skype.exe
wine: cannot find '/dev/hda1/Program Files/Skype/Phone/skype.exe'
drakkor@drakkor:~$ sudo wine /dev/hda1/Program\Files/Skype/Phone/skype.exe
wine: cannot find '/dev/hda1/ProgramFiles/Skype/Phone/skype.exe'
drakkor@drakkor:~$

I must say that the windows skype is on another partition and on another hard drive.

---

### Post by Kilz on 2006-07-24
> **Drakkor said:**
> Yes I have the linux version already installed, I just wanted to try and run a windows program to check and see how wine works. Still having problems:
drakkor@drakkor:~$ sudo wine /dev/hda1/ProgramFiles/Skype/Phone/skype.exe
Password:
wine: cannot find '/dev/hda1/ProgramFiles/Skype/Phone/skype.exe'
drakkor@drakkor:~$ sudo wine /dev/hda1/Program/Files/Skype/Phone/skype.exe
wine: cannot find '/dev/hda1/Program/Files/Skype/Phone/skype.exe'
drakkor@drakkor:~$ sudo wine /dev/hda1/Program\ Files/Skype/Phone/skype.exe
wine: cannot find '/dev/hda1/Program Files/Skype/Phone/skype.exe'
drakkor@drakkor:~$ sudo wine /dev/hda1/Program\Files/Skype/Phone/skype.exe
wine: cannot find '/dev/hda1/ProgramFiles/Skype/Phone/skype.exe'
drakkor@drakkor:~$

You may be better off testing something simple. Like say a notpad replacement. You also dont want to use sudo when running wine most of the time. Dose the command winecfg bring up the wine config?

---

### Post by CarpKing on 2006-07-24
If the name of the directory is "Program Files" you should type:

```
wine /dev/hda1/"Program Files"/Skype/Phone/skype.exe
```

You need the quotes to preserve the space.  Also, make sure that Program Files is really in /dev/hda1.  Normally it would be in /home/username/.wine/drive_c (hit ctrl+h to show hidden folders in nautilus).

---

### Post by Drakkor on 2006-07-24
I enter wincfg in the terminal and I can't type anything in "Look In"
Like I said,someone needs to make some sort of guide of how to use this program !!

---

### Post by orb9220 on 2006-07-24
when you run the winecfg click on the drives tab and autodetect drives to add 
them to wine.

To install xnview to my system i used this:
sudo wine /drives/hdd1/Ubuntu-Configs/XnView-win-full.exe
That is to install the windows version that I have on a fat32 drive.

It will start the normal windows install for xnview
when it is done it will install the program in a fake c:Programs  directory that it creates.

Next you have to add the program to winecfg  under default you should have 
already did the autodetect for drives earlier.  

Now click on add program you should see the c: Program foleder in the open dialog cruise into the program folders until you find the program.exe that 
you want to add double click Ok.

It now should be in the winecfg list select it. change to run as winxp click on drives click autodetect click apply and done.

Now you should be able to run it.

I am new to using wine to so that is about all the info I have.

---

### Post by orb9220 on 2006-07-24
The problem with the path problem is it a windows partition if it is move the 
installer program to somewhere on your linux partition.

I believe you do not have exec privaleges on a ntfs partition.

Here is my shortcut for xnview

wine "C:\Program Files\XnView\xnview.exe"

Hope this helps a bit

---

### Post by Drakkor on 2006-07-24
](*,)  Guess I just wasn't meant to use wine autodetect drives went :

drakkor@drakkor:~$ winecfg
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/media/data'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'F:', targetpath of '/windows'
err:winecfg:apply_drive_changes   unable to define devicename of 'G:', targetpath of '/windows2'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/windows3'
err:winecfg:apply_drive_changes   unable to define devicename of 'I:', targetpath of '/home/drakkor'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/media/data'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'F:', targetpath of '/windows'
err:winecfg:apply_drive_changes   unable to define devicename of 'G:', targetpath of '/windows2'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/windows3'
err:winecfg:apply_drive_changes   unable to define devicename of 'I:', targetpath of '/home/drakkor'
drakkor@drakkor:~$ wineserver: could not save registry branch to /home/drakkor/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/drakkor/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/drakkor/.wine/user.reg : Permission denied

---

