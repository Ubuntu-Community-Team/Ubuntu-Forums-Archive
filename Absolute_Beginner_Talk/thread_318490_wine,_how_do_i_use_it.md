---
title: "wine, how do i use it?"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2006-12-14
i have been searching the forums and trying commands but i just dont seem to be able to get wine to do anything.
it is in my home folder and looks to be ok.
i have just bought a new phone and woulkd like to load the program that comes with it if i can.
so i was wondering what commands do i give to get the exe. to install ,
or even the command to see if it is working properly.
thanks

---

### Post by hyper_ch on 2006-12-14
If you have installed wine, then first execute:

```

winecfg

```

This will add some stuff in your ~/.wine dir.

After that just start the install exe with   wine /path/to/install.exe

---

### Post by STREETURCHINE on 2006-12-14
hi i have done wine config .
it is in my dvd/cd drive so does that make the path ...wine /desktop/L.Ginstall.exe,
it is the paths i am not good at never get them right

---

### Post by STREETURCHINE on 2006-12-14
ok i tried and copied it in to my home folder and typed in this

rex@Linux:~$ wine /home/rex/LG_PC_Sync.iso
wine: could not load L"Z:\\home\\rex\\LG_PC_Sync.iso": Bad EXE format for
rex@Linux:~$

i dont know if it is of any help

---

### Post by hyper_ch on 2006-12-14
Well, a ISO is not an windows executable file. You first need to mount the iso somewhere and the issue the wine command to an .exe file

---

### Post by rich.bradshaw on 2006-12-14
The easiest way to get it to work is to try and open an .exe file in Nautilus, choose to open with wine, and then they will be associated and everything works.

He's right, and iso file is a disk image, so you need to mount that first.

---

### Post by Jussi01 on 2006-12-14
> **STREETURCHINE said:**
> hi i have done wine config .
it is in my dvd/cd drive so does that make the path ...wine /desktop/L.Ginstall.exe,
it is the paths i am not good at never get them right


 as far as I understand it you need to be in the dvd directory when you give that wine command. so go to the DVD directory for example (might be different on your system):

In terminal: 

```
cd media

cd cdrom0

cd [directory on cd]

wine /desktop/L.Ginstall.exe
```

Thats my understanding anyway... (if Im wrong correct me)

---

### Post by STREETURCHINE on 2006-12-14
> **sjau said:**
> Well, a ISO is not an windows executable file. You first need to mount the iso somewhere and the issue the wine command to an .exe file

no i know this but i was just trying something differant while i was waiting.

cd media

cd cdrom0

cd [directory on cd]

wine /desktop/L.Ginstall.exe

none of these worked.
i have tried nautilus it dont happen there either
something has to be not config right but i have no idea what

---

### Post by 3rdalbum on 2006-12-14
If you've cd'ed to the directory that contains the program, then just:

```
wine "L.Ginstall.exe"
```

should do the trick.

---

### Post by STREETURCHINE on 2006-12-14
> **3rdalbum said:**
> If you've cd'ed to the directory that contains the program, then just:

```
wine "L.Ginstall.exe"
```

should do the trick.

rex@Linux:~$ cd media
bash: cd: media: No such file or directory
rex@Linux:~$ cd cdrom0
bash: cd: cdrom0: No such file or directory
rex@Linux:~$ cd [directory on cd]
bash: cd: [directory: No such file or directory
rex@Linux:~$ wine /desktop/L.Ginstall.exe
wine: cannot find '/desktop/L.Ginstall.exe'
rex@Linux:~$


this is what i get.

rex@Linux:~$ wine "L.Ginstall.exe"
wine: could not load L"c:\\windows\\system32\\L.Ginstall.exe": Module not found
rex@Linux:~$

---

### Post by kimusabi on 2006-12-14
When "cd"ing out of you're home dir, you need to add the forward slash (/) otherwise linux gets confused and throws errors in you're face like a bad monkey.

A method I tend to use when feeling lazy is just type "wine" (without the quotes) into the terminal, and drag and drop the exe into the terminal then press return. Works wonders.

---

### Post by STREETURCHINE on 2006-12-14
> **kimusabi said:**
> When "cd"ing out of you're home dir, you need to add the forward slash (/) otherwise linux gets confused and throws errors in you're face like a bad monkey.

A method I tend to use when feeling lazy is just type "wine" (without the quotes) into the terminal, and drag and drop the exe into the terminal then press return. Works wonders.

ok gave that a go as well.

rex@Linux:~$ wine /media/cdrom0/LGInstaller.exe

but got an error message in a popup window could not open etc etc etc blah blah 

i am starting to think this is going to be like tring to get a printer working,damn impossible
i am just going to have to keep running two computers and switch back and forward between them when i need stuff or to print

---

### Post by md5 on 2006-12-14
[SIZE=2]Put your installer on Linux Desktop. When write [/SIZE]```
sudo wine /home/user/Desktop/Installer.exe
```

---

### Post by STREETURCHINE on 2006-12-14
> **md5 said:**
> [SIZE=2]Put your installer on Linux Desktop. When write [/SIZE]```
sudo wine /home/user/Desktop/Installer.exe
```

hi. gave that a go as well still no luck

rex@Linux:~$ sudo wine /home/user/Desktop/Installer.exe
Password:
wine: cannot find '/home/user/Desktop/Installer.exe'
rex@Linux:~$  sudo wine /home/user/Desktop/Installer.exe
wine: cannot find '/home/user/Desktop/Installer.exe'
rex@Linux:~$ sudo wine /home/user/desktop/L.Ginstaller.exe
wine: cannot find '/home/user/desktop/L.Ginstaller.exe'
rex@Linux:~$

thanks for trying:o

---

### Post by md5 on 2006-12-14
You didn't put the installer on the Desktop. That's the mistake.

---

### Post by STREETURCHINE on 2006-12-14
> **md5 said:**
> You didn't put the installer on the Desktop. That's the mistake.

i clicked and draged it to the desktop ,or do i do it some outher way.
as to my computr knowledge i am still in kindergaten(preprimary)

---

### Post by md5 on 2006-12-14
sudo wine /home/user/desktop/L.Ginstaller.exe --> That's wrong
sudo wine /home/enter_your_username/Desktop/L.Ginstaller.exe --> That's good

---

### Post by cytutchi on 2006-12-14
you need to put: / befor you type a directory outside of your home directory....

therefore..

cd /media

or cd /....

---

### Post by cytutchi on 2006-12-14
sorry for that reply guys... mistake of mine..plz ignore since repleid for the last thread of page one...and that has already been answered!!!

---

### Post by STREETURCHINE on 2006-12-14
rex@Linux:~$ sudo wine /home/rex/desktop/L.Ginstaller.exe
Password:
wine: cannot find '/home/rex/desktop/L.Ginstaller.exe'
rex@Linux:~$ sudo wine /home/rex/Desktop/L.Ginstaller.exe
wine: cannot find '/home/rex/Desktop/L.Ginstaller.exe'
rex@Linux:~$

no no .not want to work :)

---

