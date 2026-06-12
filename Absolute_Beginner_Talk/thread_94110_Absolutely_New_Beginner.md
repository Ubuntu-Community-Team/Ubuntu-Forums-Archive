---
title: "Absolutely New Beginner"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by mishranurag on 2005-11-23
Hi!
I just switched to Ubuntu few days back. I have had a few troubles with setting up and understanding the new system. Now, I have been trying to install a few programs on my systems and had troubles in executing "make" command. I don know if I need to have any specific patch or something else installed or do any tweak in the system.
Switching from Windows to Ubuntu was a nice experience to realize so may open source programs but it was a difficult experience to make many things working :(. I hope I will learn in future, but looks like this sytstem is still for geeks only.
Anurag

---

### Post by endersshadow on 2005-11-23
Generally, use Synaptic for installing software, but here's how to get the make command to work:

Run the following in the terminal:
```
sudo apt-get install make
```

---

### Post by Kapre on 2005-11-23
[QUOTE=mishranurag]Hi!
I just switched to Ubuntu few days back. I have had a few troubles with setting up and understanding the new system. Now, I have been trying to install a few programs on my systems and had troubles in executing "make" command. I don know if I need to have any specific patch or something else installed or do any tweak in the system.
Switching from Windows to Ubuntu was a nice experience to realize so may open source programs but it was a difficult experience to make many things working :(. I hope I will learn in future, but looks like this sytstem is still for geeks only.
Anurag[/QUOTE]

mishanurag - what apps or programs are you trying to install? Are you aware of the synaptic package manager? If not, SPM is the repository of all apps that is available. Maybe you dont need to execute "make" as the apps that you maybe trying to install is already available in the SPM. Try it by going to System-----Adminnistration------Synaptic Package Manager.

K

---

### Post by az on 2005-11-23
[QUOTE=mishranurag]Hi!
I just switched to Ubuntu few days back. I have had a few troubles with setting up and understanding the new system. Now, I have been trying to install a few programs on my systems and had troubles in executing "make" command. I don know if I need to have any specific patch or something else installed or do any tweak in the system.
Switching from Windows to Ubuntu was a nice experience to realize so may open source programs but it was a difficult experience to make many things working :(. I hope I will learn in future, but looks like this sytstem is still for geeks only.
Anurag[/QUOTE]
Ubuntu tries to provide everything you need out-of-the-box.  You don't need to compile anything, usually.

If you really need to compile something from source, install the build-essential package, which is on your install cd.  You will also need to install the -dev libraries that go with whatever you want to compile (Read the README in the tarball).

What are you trying to compile?

---

### Post by aysiu on 2005-11-23
[A guide to all the ways of installing software in Ubuntu](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by darknuala on 2005-11-23
Breezy also has a windows like front-end to install software for synaptic, called Add Applications.  Its basically the same as synaptic, but shows the most common apps to install.

---

### Post by mishranurag on 2005-11-23
After  sudo apt-get install make the make application is working now :)
Thanks for the replies. I will post more questions as and when they come across.
Thanks again.
Anurag

---

### Post by mishranurag on 2005-11-23
I was installing a software HSPEXP ( a water quality calibration softare available at [http://water.usgs.gov/software/hspexp.html](http://water.usgs.gov/software/hspexp.html) )
I was getting the following error when I used the make command. Can anybody help me?
Anurag



[quote=endersshadow]Generally, use Synaptic for installing software, but here's how to get the make command to work:

Run the following in the terminal:
```
sudo apt-get install make
```[/quote]

---

### Post by mishranurag on 2005-11-25
Hi!
Sorry for not sending the right error which I got in the last message. Her it is. I get this error after make command. Please help me.
Anurag

root@anmishra:/usr/opt/wrdapp/hspexp2.3/src# make
Created directory ../bin
Created directory ../bin_data
f77 -C -u   -c -o hspexp.o hspexp.f
make: f77: Command not found
make: *** [hspexp.o] Error 127


[quote=mishranurag]I was installing a software HSPEXP ( a water quality calibration softare available at [http://water.usgs.gov/software/hspexp.html]("http://water.usgs.gov/software/hspexp.html") )
I was getting the following error when I used the make command. Can anybody help me?
Anurag[/quote]

---

### Post by ssam on 2005-11-25
f77 looks like fortran to me. i think gcc may include the f77 compiler. do a search for it in synaptic and you should find something.

---

### Post by mishranurag on 2005-11-25
I got the following details in the readme file of the software. Will that help?

1.  The values for the indicated variables in the following hspexp2.3 files
    may need to be modified (see the file hspexp2.3/doc/versions.doc for
    more details):

                               may need to be modified
                           -------------------------------
                            version     compiler
    file name              variables  flags  name  library
    ---------------------  ---------  -----------  -------
    src/Makefile           WrdA       FFLAGS  F77    LGks
        fhsxms.inc         WDNAME
    msg/wdimex.sh          WrdA
    test/test.sh           WrdA 

[quote=ssam]f77 looks like fortran to me. i think gcc may include the f77 compiler. do a search for it in synaptic and you should find something.[/quote]

---

