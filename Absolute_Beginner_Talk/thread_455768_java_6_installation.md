---
title: "java 6 installation"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by giulian on 2007-05-26
Trying to install java 6 through the terminal, something went wrong and now when I try again I got the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


Please help!

---

### Post by taurus on 2007-05-26
Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude update
```

---

### Post by giulian on 2007-05-26
thank you, now I am in front of a grey screen in the terminal and I have to agree to the license of sun:

                                                              
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-jre &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                  &#8593;  
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

How to agree??? Thank you !

---

### Post by taurus on 2007-05-26
Use the down arrow to scroll down to the end (or the space bar) when you can type in **yes** to except the license.

---

### Post by giulian on 2007-05-26
I scrolled down till the end of the agreement but there is no place where I can type yes

---

### Post by taurus on 2007-05-26
You can type it at the last line.  There should be a question in there with "yes or no?" thing at the end.

---

### Post by giulian on 2007-05-26
this is the end:

its subject matter.  It supersedes all prior or contemporaneous       &#8593;  
 &#9474;     oral or written communications, proposals, representations and        &#9618;  
 &#9474;     warranties and prevails over any conflicting or additional terms      &#9618;  
 &#9474;     of any quote, order, acknowledgment, or other communication           &#9618;  
 &#9474;     between the parties relating to its subject matter during the term    &#9618;  
 &#9474;     of this Agreement.  No modification of this Agreement will be         &#9618;  
 &#9474;     binding, unless in writing and signed by an authorized                &#9618;  
 &#9474;     representative of each party.                                         &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; For inquiries please contact: Sun Microsystems, Inc., 4150 Network        &#9618;  
 &#9474; Circle, Santa Clara, California 95054, U.S.A.                             &#9618;  
 &#9474;                                                                           &#9646;  
 &#9474; DLJ v1.1                                                  27APR2006ANS    &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>

---

### Post by taurus on 2007-05-26
Hit the Tab bar to highlight the <OK>.  Then hit the return key.  

Can you take a screenshot of your desktop with that license window?

---

### Post by giulian on 2007-05-27
Thank you very much for your patience, you are the best!

---

### Post by giulian on 2007-05-27
This is what I got at the end of the installation:

giuliano@giuliano-desktop:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

---

### Post by taurus on 2007-05-27
> **giulian said:**
> This is what I got at the end of the installation:

giuliano@giuliano-desktop:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

Well, you are running Java version 1.6 now.

---

