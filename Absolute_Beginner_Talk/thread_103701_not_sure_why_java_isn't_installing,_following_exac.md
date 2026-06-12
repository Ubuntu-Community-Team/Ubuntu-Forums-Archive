---
title: "not sure why java isn't installing, following exact same steps?"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by Il_Tuo_Nome on 2005-12-14
On the past couple of installations, I had absolutely no problem installing J2SE Runtime Environment. As I have with past installs, I followed the directions given within the help file "lifebuoy" as seen here:

```
Java

1.&#8195;

How do I install the J2SE Runtime Environment (JRE) 5 (1.5) with Firefox plugin?

       1.

          Make sure the multiverse repository is enabled. (See How do I add Universe and Multiverse?)
       2.

          Go to http://java.sun.com/j2se/1.5.0/download.jsp and click on “Download JRE 5.0 Update 4”. Ensure you do not choose the link with the NetBeans bundle.

          At the time of this writing J2SE is at version 5.0 Update 4. This is subject to change. If you do not see this version on Sun's website, download the newest version displayed.
       3.

          You must first accept the licence, then click on “Linux self-extracting file” (jre-1_5_0_04-linux-i586.bin). Save this file to your hard drive.
       4.

          Install the java-package package with Synaptic (See How do I use Synaptic to install packages?)

          Miscellaneous - Text Based (multiverse) > java-package
       5.

          Make the downloaded file executable. At the command line, change to the directory where you downloaded the file, and type

chmod +x jre-1_5_0_04-linux-i586.bin

       6.

          To install JRE, run the downloaded file. Type

fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin

       7.

dpkg -i sun-j2re1.5_1.5.0+update04_i386.deb


```, as I did step 6., I received the following:

```
rosso@Gianuntu:~/Java$ ls
jre-1_5_0_06-linux-i586.bin
rosso@Gianuntu:~/Java$ chmod +x jre-1_5_0_06-linux-i586.bin
rosso@Gianuntu:~/Java$ ls
jre-1_5_0_06-linux-i586.bin
rosso@Gianuntu:~/Java$ fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
/usr/bin/fakeroot: line 150: make-jpkg: command not found
rosso@Gianuntu:~/Java$ sudo fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
/usr/bin/fakeroot: line 150: make-jpkg: command not found

```. 

I went in to gedit, and could find nothing pertaining to line 150. I updated my repositories as well as updated everything before this happened, so now I'm at a loss. Please, can someone help me out with this?

Thank you

---

### Post by Rackerz on 2005-12-14
Here are the instructions i usually use when installing Java; 

[http://www.ubuntuforums.org/showthread.php?t=76702&highlight=installing+java](http://www.ubuntuforums.org/showthread.php?t=76702&highlight=installing+java)

---

### Post by carlosqueso on 2005-12-14
try without the fakeroot....I don't think I used it.

---

### Post by NotJustANewbie on 2005-12-14
My reply:

[http://ubuntuforums.org/showthread.php?p=574231&posted=1#post574231](http://ubuntuforums.org/showthread.php?p=574231&posted=1#post574231)

---

### Post by Il_Tuo_Nome on 2005-12-14
TY Rackerz,

I followed that link. Apparently I was lacking the 'sudo apt-get install fakeroot java-package java-common' command, which must of been added before when I updated. The rest was the same.


TY for your help :)

---

### Post by Rackerz on 2005-12-14
Not a problem, if you ever need help again, im here and happy to contribute :).

---

