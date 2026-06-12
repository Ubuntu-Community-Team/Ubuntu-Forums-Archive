---
title: "LimeWire 4.10"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by FinePix on 2006-05-15
I have downloaded LimWireLinux.rpm from LimeWire.com. I dont know how to install. 

Any help

---

### Post by Perfect Storm on 2006-05-15
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install alien
sudo alien -i XXXXXXXXX.rpm

```

---

### Post by richbarna on 2006-05-15
If you are a "Newbie" and you download an .RPM to your desktop and you get a "file not found" message, try copying it to your home folder;)

---

### Post by FinePix on 2006-05-16
[QUOTE=Artificial Intelligence]```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install alien
sudo alien -i XXXXXXXXX.rpm

```[/QUOTE]
It works. Thanks. 

One more question. is alien a program to run *.rpm files ? and do i have to use "sudo alien -i XXXXXXXXX.rpm" every time to install rpm files.

---

### Post by manicka on 2006-05-16
You might find frostwire a better option than limewire

[http://www.frostwire.com/](http://www.frostwire.com/)

---

### Post by barbarian on 2006-05-16
> You might find frostwire a better option than limewire

[http://www.frostwire.com/](http://www.frostwire.com/)

why frostwire better?

---

### Post by manicka on 2006-05-16
[QUOTE=barbarian]why frostwire better?[/QUOTE]

the site speaks for itself

---

### Post by tc10b on 2006-05-16
I'm having a problem with Frostwire, I can't get it to run when I install it, I've installed it from the website and with Automatix and still it just won't run. It gives me this error message in the terminal:

tc10b@tc10b-175-75:/usr/bin$ frostwire
: command not found:
: No such file or directory
: command not found:
: command not found3:
'unFrost.sh: line 24: syntax error near unexpected token `
'unFrost.sh: line 24: `look_for_java()

---

### Post by manicka on 2006-05-16
Do you have java installed?

[https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249](https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249)

---

### Post by Perfect Storm on 2006-05-16
[QUOTE=FinePix]It works. Thanks. 

One more question. is alien a program to run *.rpm files ? and do i have to use "sudo alien -i XXXXXXXXX.rpm" every time to install rpm files.[/QUOTE]

Yep. But I'll advise you to use .deb and/or compile stuff instead. There's no gurantee when converting a .rpm to .deb it will work.

---

### Post by FinePix on 2006-05-17
[QUOTE=Artificial Intelligence]Yep. But I'll advise you to use .deb and/or compile stuff instead. There's no gurantee when converting a .rpm to .deb it will work.[/QUOTE]
i dont know how to install .deb file. 

As in the topic im very new to linux and im a beginner

---

### Post by joshrobinson on 2006-05-17
[QUOTE=FinePix]i dont know how to install .deb file. 

As in the topic im very new to linux and im a beginner[/QUOTE]

frostwire was packaged wrong in the tar file

```
sudo apt-get install sysutils 
sudo dos2unix /usr/lib/frostwire/runFrost.sh
```

assuming that frostwire is in /usr/lib/frostwire

change the directory if you have to to point to where it needs to go
it should work now if java is installed

as for installing debs you can just double click them and put your password in and click install package

---

### Post by Perfect Storm on 2006-05-17
[QUOTE=FinePix]i dont know how to install .deb file. 

As in the topic im very new to linux and im a beginner[/QUOTE]

Firstly check if the application is available via apt-get/synaptic package manager (always a good idea before hunting for a .deb)

If you find a .deb you want to install:

```
sudo dpkg -i XXXXXXXXXXXX.deb
```

---

### Post by FinePix on 2006-05-17
got it. thanks for the help.

---

### Post by tc10b on 2006-05-23
[QUOTE=manicka]Do you have java installed?

[https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249](https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249)[/QUOTE]

Yeah I already installed it with Automatix, I tried again though and it says that the package is the newest version.

---

