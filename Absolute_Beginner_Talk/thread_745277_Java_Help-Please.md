---
title: "Java Help-Please"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Ellaine on 2008-04-04
I screwed up thru Add/Remove programs and tried to install everything for Sun Java. During the downloads it locked up on java6.doc, and wouldn't finish the download. I rebooted and now can't open Synaptic Package Manager to correct the problem. Get the following error and have no idea what to do with this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried in Add/Remove to remove Synaptic Package Manager and reinstall, but it said I can't except thru Synaptic Package Manager which won't open because of error. Is there some way to fix this or revert to yesterday? Please any help would be great!

PS: Running Ubuntu 7.10 with nearly all additional programs from stchman.com.:(

---

### Post by GOROSSI on 2008-04-04
Hello Ellaine

Go to Applications, then Accessories, open "Terminal" and type dpkg --configure -a , Press the enter key.

this will fix the synaptic not opening issue As I recall the process should run automatically with no user input needed.

Hope this helps:)

---

### Post by bumanie on 2008-04-04
'dpkg --configure -a' means that the download was interrupted. This command gets it restart where it left off.

---

### Post by Ellaine on 2008-04-04
I tried this but terminal says "requested operation requires superuser privilage". I put in password says command not found. Who the hell is superuser? If it's Bill Gates I'll reload from scratch!

---

### Post by FuturePilot on 2008-04-04
You need to use sudo
```
sudo dpkg --configure -a
```
or else you'll get the error you mentioned above.

---

### Post by Ellaine on 2008-04-04
This didn't ask for superuser, but gave me this:

Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

---

### Post by bumanie on 2008-04-04
An easier way may be to go to terminal 
> sudo apt-get install sun-java6-plugin and install java this way.

---

### Post by Ellaine on 2008-04-04
Trie this and got:  

dick@dick-desktop:~$ sudo apt-get install sun-java6-plugin
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
dick@dick-desktop:~$ dick471
bash: dick471: command not found
dick@dick-desktop:~$ 

Is ther some way to use Sudo and remove all Sun Java. If so then what version would be correct for use in Opera, since i don't use firefox?

---

### Post by philinux on 2008-04-04
Ellaine,

Just run this first.

sudo dpkg --configure -a

---

### Post by Ellaine on 2008-04-04
Now receive this:

dick@dick-desktop:~$ sudo apt-get install sun-java6-plugin
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
dick@dick-desktop:~$ dick471
bash: dick471: command not found
dick@dick-desktop:~$ sudo dpkg --configure -a
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

---

### Post by Ellaine on 2008-04-04
Solved: I don't know what I did but put in "no" + RETURN three times and now Synaptic Package Manager opens without error message.  THANKS for all the help. I just hope java works in Opera 9.25 after all this trouble.

Thanks to everyone!

---

### Post by GOROSSI on 2008-04-04
> **Ellaine said:**
> Now receive this:

dick@dick-desktop:~$ sudo apt-get install sun-java6-plugin
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
dick@dick-desktop:~$ dick471
bash: dick471: command not found
dick@dick-desktop:~$ sudo dpkg --configure -a
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

I would suggest Go into Synaptic It should work if now you ran that command sorry about missing Sudo Off
then search and install the following packages 

Sun-java6-bin
sun-java6-jdk
sun-java6-jre
sun-java6-plugin

these are what I am running and I also use Opera, though as a secondary browser but java works.

---

