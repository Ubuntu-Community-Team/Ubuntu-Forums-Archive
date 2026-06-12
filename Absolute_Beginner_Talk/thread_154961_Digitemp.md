---
title: "Digitemp"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by ntaba on 2006-04-04
I tried to install DIGITEMP using Synaptic. It seems that the installation went through whithout any problems. When I give the command digitemp in the console it gives the reply  bash: digitemp: command not found"

What have I done wrong?

---

### Post by Stealth on 2006-04-04
Ok, according to its description: 
> Digitemp is a program that reads data coming from a 1-Wire network using a passive adapter (DS9097) or the newer active adapter (DS9097U), connected to a serial port. It also supports reading from USB adaptors like the DS2490.

Those numbers are the main thing, looking at the list of files installed, 3 Digitemp files are installed in /usr/bin/ (that's where the exectuable is) so you have to launch it by one of the following commands: 

digitemp_DS2490					    
digitemp_DS9097					    
digitemp_DS9097U

I guess accordingly to what type of adapter you have :)

---

### Post by ntaba on 2006-04-04
If I launch digitemp_DS9097 from the console, what will be the result? Maybe a very stupid question but I'm a beginner!

---

### Post by ntaba on 2006-04-04
In the documenattion this can be read:
Installation of the Software
The software is available as a tar archive, it can be installed with the command:

 tar -xvzf digitemp-1.3.tar.gz

In the newly installed directory digitemp1-3 we find the source code, documentation and some Perl scripts, but also the binaries digitemp, which can be used as they are.

The command

digitemp -i -s/dev/ttyS0

accomplishes that, in this case the interface circuit is connected to the first serial interface. 
The software detects the sensors, a message similar to this appears:

DigiTemp v1.3 Copyright 1997-99 by Nexus Computing

ROM #0 : 1032724700080086
ROM #1 : 1092214400080089

The problem is that I don't have any digitemp binary!!

---

### Post by Stealth on 2006-04-04
Maybe try doing it like:

digitemp_DS2490 -i -s/dev/ttyS0 ?

I've never used it to be sure, but seeing as how you installed it in synaptic already, I can tell you those 3 files I mentioned above are the executables that you would launch.

---

### Post by ntaba on 2006-04-04
Ok, I'll try that later tonight. Thanks.

---

