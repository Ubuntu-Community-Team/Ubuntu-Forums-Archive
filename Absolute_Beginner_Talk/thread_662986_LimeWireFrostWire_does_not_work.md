---
title: "LimeWire/FrostWire does not work"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2008-01-09
I have been using LimeWire for a few months but recently, after reading about how much better FrostWire is on these forums, I installed the latter. Now when I try and open Frostwire from Applications nothing happens. When I open Limewire, it loads up and afte displaying the "upgrade to Pro" pop-up it just doesn't load and the window remains blank. On top of that, in order to forcibly quit it I have to kill the limewire and the java processes with system monitor.

---

### Post by taseedorf on 2008-01-09
hm, did you try to open frostwire in a terminal so you can see if there are any errors?

If I remember right, when I first installed it, there was some sort of error, where I needed to change a file's name specific to my system, or install some sort of libs or something.  

Try going into terminal, and typing frostwire and checking out the results...something in there helped me (infact, i just checked and I still get some errors, but frostwire works.)    Post them up here if you don't get it figured out

---

### Post by intense.ego on 2008-01-13
I tried running frostwire from the terminal and got this:
```
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com

```

---

### Post by thamood on 2008-01-13
**You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)**

or go to System->Admin->Synaptic Package Manager

look for Java there should be a JRE package install it or upgrade it

---

### Post by Majorix on 2008-01-13
Java How-to [here]("https://help.ubuntu.com/community/Java").

---

### Post by intense.ego on 2008-01-13
According to Synaptic Package Manager, I have installed sun java 6 jre, bin, etc. I reinstalled them but I got the same error message as above.

---

### Post by taurus on 2008-01-13
What's the output of this command from a terminal?

```
java -version
```
Maybe you need to configure so your system would use the latest Sun java version instead of the gij one.

```
sudo update-alternatives --configure java
```

---

### Post by Sbarton on 2008-01-13
If you have'nt done this try it. System/Admin/Synaptic Manager, scroll to Frostwire RIGHT click it and see if there are any other suggestions to be installed (can be 2 or 3), if so install them.
regards

---

### Post by intense.ego on 2008-01-13
The output of ```
 java -version 
``` was
```
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

> **Sbarton said:**
> If you have'nt done this try it. System/Admin/Synaptic Manager, scroll to Frostwire RIGHT click it and see if there are any other suggestions to be installed (can be 2 or 3), if so install them.
regards
I'm not sure what you mean. I checked the dependencies and they all appeared to be installed.

---

### Post by Sbarton on 2008-01-14
Just to explain further, go to system/admin/synaptic manager, scroll to Frostwire right click it and look at the bottom of the dialogue box and see if there are any entries below 'Properties', such as 
'Mark suggested for installation' or 'Mark reccommended for installation'. If these are available to install then do so. If they are greyed out I assume you have them installed.
Hope this explains my post a little better.
regards

---

### Post by intense.ego on 2008-01-14
The two entries you mentioned are grey and cannot be clicked. Should I try installing an older version of java too or would that just be detrimental?

---

### Post by some_guy on 2008-01-14
I'll give this a shot.  Since it sounds like you've already installed Sun Java...

Try:

```
sudo update-alternatives --config java
```

You should see something like:

```
There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:
``` 

Pick the one from Sun.  If you don't see something like this,  post the output of the command and we'll go from there.  Best of luck.

---

### Post by gn2 on 2008-01-14
If you are using 64-bit Ubuntu this is the cure: [http://ubuntuforums.org/showpost.php?p=3458033&postcount=9](http://ubuntuforums.org/showpost.php?p=3458033&postcount=9)

---

### Post by Azraelthe7th on 2008-01-16
> **gn2 said:**
> If you are using 64-bit Ubuntu this is the cure: [http://ubuntuforums.org/showpost.php?p=3458033&postcount=9](http://ubuntuforums.org/showpost.php?p=3458033&postcount=9)

Is there a way to automate the switching?  I don't much enjoy having to go into the terminal everytime I want to start Frostwire or Tuxguitar.

---

### Post by ubuntu27 on 2008-01-16
> **intense.ego said:**
> The output of ```
 java -version 
``` was
```
**java version "1.4.2"**
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```


I'm not sure what you mean. I checked the dependencies and they all appeared to be installed.

You have an old version of Java. The version you need is at least 1.5.0.

What version of Ubuntu are you using?

---

### Post by gn2 on 2008-01-16
> **Azraelthe7th said:**
> Is there a way to automate the switching? 

What do you have to switch? 

After I installed ```
sudo apt-get install ia32-sun-java6-bin
```
on my 64-bit Xubuntu PC, and then ran ```
sudo update-alternatives --config java
```
and picked the ia32, Frostwire opens every time.

---

### Post by intense.ego on 2008-01-16
I fixed it (with your help, of course)! The default java config was gcj and all i had to do was switch to sun 6. Are there any important differences i should know about?

---

### Post by gn2 on 2008-01-18
> **intense.ego said:**
> Are there any important differences i should know about?

Not as far as I'm aware.

---

### Post by z-itou16 on 2008-01-19
mmmm interesting. not that i have that issue but it can help with mandriva...well ill check thanks

---

### Post by (((X))) on 2008-01-19
I turned off visual effects, and limewire works again
I have Java installed too, ubuntu did that for me:P

---

### Post by Azraelthe7th on 2008-01-19
> **gn2 said:**
> What do you have to switch? 

Tux Guitar doesn't work with the 32-bit Java driver (I guess I should have mentioned I use the 64-bit version of Gutsy), and having to constantly switch Java versions for each program is a bit tedious, so I was wondering if there was a way for me to make Frostwire go directly to the 32-bit Java instead of searching for it.

---

