---
title: "Driver for canon printer BJC-85"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by tyboon on 2007-03-29
Does anybody knows how i could make my old printer work?
In the official site there are no drivers for linux..anybody knows anything..?

---

### Post by coolclassic on 2007-03-29
Have a look here:

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

---

### Post by tyboon on 2007-03-29
thanx..i downloaded the driver and installed it...still i realy dont know how is my printer connected..it should be parallel but its not responding...any ideas?

---

### Post by coolclassic on 2007-03-30
Have you run turboprint setup? This can be run from the turboprint-setup icon on your desk top, if that is not there use "xtpsetup" in your shell this should detect your printer and setup your drivers.

---

### Post by anaconda on 2007-03-30
here:
[http://openprinting.org/show_printer.cgi?recnum=Canon-BJC-85](http://openprinting.org/show_printer.cgi?recnum=Canon-BJC-85)

---

### Post by tyboon on 2007-05-03
I tried several times to install my printer..Its a BJC-85  canon...I followed the instruction from anaconda..downloaded the driver as an rpm but i cant convert it to deb package ...Alien cant find the package..
I even tried using the BJC-600 driver that is included during the printig setup..That fails to...:( :confused: 
May be i am doing something wrong...?I dont know...
But i would really like to use my printer in ubuntu..
I hate logining in to windows..
Can anybody help...
Thanx .....

---

### Post by Sef on 2007-05-03
> downloaded the driver as an rpm but i cant convert it to deb package ...Alien cant find the package..

Did you switch to the directory where the deb package is?

---

### Post by tyboon on 2007-05-04
No...how can i do that...
Could you help me out please...?

---

### Post by aidanr on 2007-05-04
in a terminal copy
```
cd ~/Desktop && wget http://openprinting.org/download/printdriver/RPMS/i486/gutenprint-5.0.0.99.1-3lsb3.1.i486.rpm && sudo alien gutenprint-5.0.0.99.1-3lsb3.1.i486.rpm && sudo aptitude update && sudo aptitude upgrade && sudo aptitude install lsb && sudo dpkg -i *.deb
```

---

### Post by tyboon on 2007-05-04
Thanx Bro...i typed the command and i got this...

100%[====================================>] 13,031,820    59.12K/s    ETA 00:00

05:00:34 (35.17 KB/s) - `gutenprint-5.0.0.99.1-3lsb3.1.i486.rpm' saved [13031820/13031820]

Password:
Warning: Skipping conversion of scripts in package gutenprint: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.


so......... what now....
give me the insight bro...
you RULE.....:guitar:

---

### Post by tyboon on 2007-05-04
Everything worked out just fine...
Really man you rock...:guitar: 
I really appreciate it...
Though the terminal tried to download the new version of Beryl 0.21...i use an 0.20 with xgl-gnome and that would probably mess everything up...just in case check this out to...
Thanx again bro ...Thanx....if i get any problems more i ll send you a message..

):P

---

### Post by aidanr on 2007-05-04
no problem, it tried to update beryl because of the "sudo aptitude upgrade" part and there was an update available

:)

---

### Post by tyboon on 2007-05-05
i Had to downgrade beryl cause it wont work on my desktop otherwise...
With tha printer issue tough luck..again it wont print...:( 
I am stil stucked with windows on that thing..
but thanx bro...

---

### Post by t2000kw on 2007-05-05
First, if you have Feisty installed, I would go to the system menu, then administration, then printers. Click new printer. If yours was detected you should see a lot of Canon drivers in the next screen or so, and your printer is in there. Mine was not, so I had to use the apt-get command, found that there was a dependency on another program or file (it needed it and refused to install without it), so I searched for that program, found it on a Linux web site, and instaleld it. Then it allowed me to install the driver. You probably won't have to do that. BUt just in case, I'll post some web links to information you might find useful.

Have you tried these sources? I'm new to this also but found a driver for mine that wasn't supported in Ubuntu. 

[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-BJC-85](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-BJC-85)

[http://osdir.com/ml/printing.cups.general/2004-03/msg00411.html](http://osdir.com/ml/printing.cups.general/2004-03/msg00411.html)

---

### Post by tomdkat on 2007-07-27
Are you using a USB connection or a parallel connection to the printer?  I'm currently fighting with a Canon BJC-80 connected via parallel cable.

Peace...

---

