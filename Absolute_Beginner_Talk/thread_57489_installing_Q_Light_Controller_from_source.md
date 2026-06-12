---
title: "installing Q Light Controller from source"
date: 2005-08-16
forum: Absolute Beginner Talk
---

### Post by themadhippy on 2005-08-16
Anyone help a very confused hippy out with the installation of a piece of [software](http://qlc.sourceforge.net/).i've tryed sevral ways (including rtfm) all without any luck.Below is the message i got on my last attempt.Can anyone help (in very basic terms) please.

> 
hippy@ubuntu:~/Desktop/qlc2$ make
cd buildtools ; make
make[1]: Entering directory `/home/hippy/Desktop/qlc2/buildtools'
chmod +x *.sh
make[1]: Leaving directory `/home/hippy/Desktop/qlc2/buildtools'
cd libs ; make
make[1]: Entering directory `/home/hippy/Desktop/qlc2/libs'
cd common ; make
make[2]: Entering directory `/home/hippy/Desktop/qlc2/libs/common'
Makefile:24: uichfiles: No such file or directory
Makefile:25: uicofiles: No such file or directory
Makefile:26: mocuicofiles: No such file or directory
Makefile:27: mocofiles: No such file or directory
Makefile:28: objfiles: No such file or directory
Makefile:78: Makefile.dep: No such file or directory
rm -f Makefile.dep
touch Makefile.dep
makedepend -fMakefile.dep -Y *.h *.cpp &> /dev/null
../../buildtools/create_objects.sh
ls: *.ui: No such file or directory
No UI definitions found. Creating dummy files to satisfy make.
Create a list of regular object files from .cpp files
Create a list of moc_ files from .h files
../../buildtools/create_objects.sh
ls: *.ui: No such file or directory
No UI definitions found. Creating dummy files to satisfy make.
Create a list of regular object files from .cpp files
Create a list of moc_ files from .h files
../../buildtools/create_objects.sh
ls: *.ui: No such file or directory
No UI definitions found. Creating dummy files to satisfy make.
Create a list of regular object files from .cpp files
Create a list of moc_ files from .h files
../../buildtools/create_objects.sh
ls: *.ui: No such file or directory
No UI definitions found. Creating dummy files to satisfy make.
Create a list of regular object files from .cpp files
Create a list of moc_ files from .h files
../../buildtools/create_objects.sh
ls: *.ui: No such file or directory
No UI definitions found. Creating dummy files to satisfy make.
Create a list of regular object files from .cpp files
Create a list of moc_ files from .h files
make[2]: Leaving directory `/home/hippy/Desktop/qlc2/libs/common'
make[2]: Entering directory `/home/hippy/Desktop/qlc2/libs/common'
----------------- Building QLC 2 Common Library -----------------
../../buildtools/create_objects.sh
ls: *.ui: No such file or directory
No UI definitions found. Creating dummy files to satisfy make.
Create a list of regular object files from .cpp files
Create a list of moc_ files from .h files
/bin/moc filehandler.h -o moc_filehandler.cpp
make[2]: /bin/moc: Command not found
make[2]: *** [moc_filehandler.cpp] Error 127
make[2]: Leaving directory `/home/hippy/Desktop/qlc2/libs/common'
make[1]: *** [sources] Error 2
make[1]: Leaving directory `/home/hippy/Desktop/qlc2/libs'
make: *** [all] Error 2


---

### Post by Juergen on 2005-08-16
What 'fm' did you read?

If it is a 'standard' source-package you have to run './configure' first. Did you do that?
You might get error-messages that have to be handled before you can run 'make'

Normal procedure is
```
./configure --help
# look for options that you might want to activate, then:
./configure [options, if you want some]
make 
sudo make install
```

---

### Post by themadhippy on 2005-08-16
According to the fm "qlc doesn't require any configuration"  there is a config.make file,ive tried copying that into the terminal,but it throws up even more errors ](*,)

---

### Post by aysiu on 2005-08-16
[QUOTE=themadhippy]Anyone help a very confused hippy out with the installation of a piece of [software](http://qlc.sourceforge.net/).i've tryed sevral ways (including rtfm) all without any luck.Below is the message i got on my last attempt.Can anyone help (in very basic terms) please.[/QUOTE] Are you absolutely sure QLC is not in the Ubuntu repositories?

Never mind. It's not there. Maybe you're missing a dependency.

I'm not sure what this means, but the ReadMe file says:
[i]Requirements
------------
* QT/X11 3.1.1 or newer
* /dev/rtc (Real-time clock, usually enabled by default)
* Recommended: dmx4linux 2.4[/i]

Does anyone know if a default Ubuntu install would have these?

---

### Post by themadhippy on 2005-08-17
> Requirements
------------
* QT/X11 3.1.1 or newer
* /dev/rtc (Real-time clock, usually enabled by default)
* Recommended: dmx4linux 2.4 
i think ive got everything i need,Is there a way of finding out for certain?

---

### Post by ewaldgroup on 2005-10-17
I'd love to install this too, but on PPC hardware...

---

### Post by ewaldgroup on 2005-11-24
bump...

---

### Post by aysiu on 2005-11-24
[QUOTE=themadhippy]i think ive got everything i need,Is there a way of finding out for certain?[/QUOTE] Unless you installed this yourself, Ubuntu doesn't come with *dmx4linux 2.4* installed, and it's not in the repositories either.

---

### Post by aysiu on 2005-11-24
[QUOTE=ewaldgroup]I'd love to install this too, but on PPC hardware...[/QUOTE] If it's installed from source, it should be the same process.

---

### Post by marytgras on 2006-08-27
Okay, I figured it out! Make sure you have build-essential installed, first off.  What you also need is automake and autoconf, plus the autotools-dev, libclutils0c2, libclutils0-dev, libguile-ltdl-1, libltdl3, libltdl3-dev, and libtool packages that are readily available in the repositories. Do this in synaptic, it'll pop up a few other dependencies as well.  For anyone that wants to install this program (Q Light Controller) make sure you have what I mentioned, and follow the the directions in the readme file to the letter from inside your qlc2 folder. ie,:

./bootstrap

./configure

make

sudo make install

It might take a while in between these steps, just be patient.

the bins end up in usr/local/bin

double click or set up a launcher and you're good to go.

---

### Post by albesan on 2006-12-08
> **marytgras said:**
> Okay, I figured it out! Make sure you have build-essential installed, first off.  What you also need is automake and autoconf, plus the autotools-dev, libclutils0c2, libclutils0-dev, libguile-ltdl-1, libltdl3, libltdl3-dev, and libtool packages that are readily available in the repositories. Do this in synaptic, it'll pop up a few other dependencies as well.  For anyone that wants to install this program (Q Light Controller) make sure you have what I mentioned, and follow the the directions in the readme file to the letter from inside your qlc2 folder. ie,:

./bootstrap

./configure

make

sudo make install

It might take a while in between these steps, just be patient.

the bins end up in usr/local/bin

double click or set up a launcher and you're good to go.
hello team,

I did all of what the instrucctions and other postings required but even though the installation seem to go well and there seem to be nothing missing I'm getting this output:

~$ sudo qlc
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
vitut
ioctl: Invalid argument


anybody came across that before?? thanks

a.

---

### Post by albesan on 2006-12-09
bump

---

### Post by chalex on 2006-12-09
Why are you doing "sudo qlc".  How about just regular "qlc &"?

---

### Post by albesan on 2006-12-10
hey, thanks for the reply,
Are you sure you mean "qlc &"?
Anyway, this is the out put of that:

$ qlc &
[1] 4452
alberto@copitux:~$ X Error: BadDevice, invalid or uninitialized input device 166  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
vitut
ioctl: Invalid argument


and qlc:

qlc
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
vitut
ioctl: Invalid argument
[1]+  Exit 22                 qlc


any ideas? anybody?

thanks.

a.

---

### Post by jamsden on 2007-01-11
I'm gonna bump this cause I'm stuck at the same part. The X error can be solved by going into the xorg.conf. But I need help with the ioctl. I'm guessing it hhas something to do with usb io.

---

