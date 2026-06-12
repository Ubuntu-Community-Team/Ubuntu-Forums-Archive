---
title: "Gutsy update error msg."
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by rosswmcgee on 2007-10-23
I have 9 updates to instlall, but get this message. E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

when i try to run dpkg -configure -a in terminal i get this msg. dpkg --configure -a
dpkg: requested operation requires superuser privilege


This i a clean install.:)

---

### Post by offroad64 on 2007-10-23
Try "sudo dpkg -configure -a"

---

### Post by rosswmcgee on 2007-10-23
Then I get this.

dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or

---

### Post by offroad64 on 2007-10-23
Sorry Typo try sudo dpkg --configure -a

---

### Post by rosswmcgee on 2007-10-23
Then I get this msg. It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first. so after I run the terminal command I am stalled as shown below, I find no way to accept the terms.





Operating System Distributor License for Java v1.1 (DLJ)                  &#8593;  
 &#9474;                                                                           &#9646;  
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618;  
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618;  
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618;  
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618;  
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618;  
 &#9474; TERMS OF THE AGREEMENT.                                                   &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618;  
 &#9474;     form, any other machine readable materials including, but not         &#9618;  
 &#9474;     limited to, libraries, source files, header files, and data files),   &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                                        
 &#9474;

---

### Post by offroad64 on 2007-10-23
Try space bar or right arrow can't remember which

---

### Post by ItsMitsHere on 2007-10-23
dear rosswmcgee,

i think there is no harm in typing all of the keys of the keboard to trigger the yes, however try with up, down, left, right, o, y and some combinations there of also try hitting enter and so on you will do it at last...

If you can't get through even after this, you may try **sudo apt-get --fix-missing** first, then **sudo apt-get update** and finally update manager (graphical) to update!

let me know if you still have problems!!!

---

### Post by rosswmcgee on 2007-10-23
Gotter done! and thank you! Ross

---

### Post by ItsMitsHere on 2007-10-23
> **rosswmcgee said:**
> Gotter done! and thank you! Ross

is this thanks for me? this is first 'thanx' i've received if its for me!!! :) :( :confused: else any ways 'every-buddy' is welcome here!!!:guitar:

---

### Post by rosswmcgee on 2007-10-23
yep

---

