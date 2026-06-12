---
title: "swiftfox?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-06-19
i was looking through Automatix and decided to install Swiftfox.

I am running on an Intel Core 2...
Automatix says Swiftfox is not built for my PC Architecture.

is this true?

---

### Post by walkerk on 2007-06-19
goto getswiftfox.com and download the install script for your achitecture. there is core solo/core duo...

---

### Post by skymera on 2007-06-19
i notice that Core 2 is the same as Prescott.... :S

---

### Post by Rui Pais on 2007-06-19
[swiftweasel?]("http://swiftweasel.sourceforge.net/") ;)

---

### Post by Nessa on 2007-06-19
Isn't swiftfox optimized for amd rigs?

---

### Post by skymera on 2007-06-19
its AMD and Intel

---

### Post by dptxp on 2007-06-19
Which is better, Swiftfox or swiftweasel ?

---

### Post by Rui Pais on 2007-06-19
Swiftfox is "kinda" close. 
The author of it [don't make public]("http://getswiftfox.org/") what it does and you must believe on him that he don't change code for nothing (not even to spy you when you home banking ;)) 


Swiftweasel is completely open, and all optimization and flags used are available. And no license restrictions too.

---

### Post by dptxp on 2007-06-19
I have installed swiftfox, how do I take it out ?

---

### Post by Stirling on 2007-06-19
> **Rui Pais said:**
> Swiftfox is "kinda" close. 
The author of it [don't make public]("http://getswiftfox.org/") what it does and you must believe on him that he don't change code for nothing (not even to spy you when you home banking ;)) 


Swiftweasel is completely open, and all optimization and flags used are available. And no license restrictions too.
You are not correct.  Source code is available.  The only thing that isn't is the branding.  I am sure you understand what branding is.  Even with an app that has all source available that only protects you if you inspect all the code and build it yourself.  There is nothing to say the author of swiftweasel doesn't distribute the source and then when doing builds adds other code to spy on you.  I am not saying this is the case with swiftweasel, just using it for an example since you mentioned it.  In the end you have to trust people and do your research.  If an app has been around a while and no one has reported any ill behavior then you are most likely safe.

---

### Post by Rui Pais on 2007-06-19
it depends the way you have done it... if you use a deb with apt-get (but then you wouldn't probabily ask...)
if you uses a compressed file just remove the uncompressed folder.

If you use some script you need to read the script to check which way it was installed.

---

### Post by dptxp on 2007-06-19
I clicked on the file at their site to install, if my memory is right.

---

### Post by Rui Pais on 2007-06-19
> **Stirling said:**
> You are not correct.  Source code is available.  The only thing that isn't is the branding.  I am sure you understand what branding is.  Even with an app that has all source available that only protects you if you inspect all the code and build it yourself.  There is nothing to say the author of swiftweasel doesn't distribute the source and then when doing builds adds other code to spy on you.  I am not saying this is the case with swiftweasel, just using it for an example since you mentioned it.  In the end you have to trust people and do your research.  If an app has been around a while and no one has reported any ill behavior then you are most likely safe.

Glad you quote my "kinda" ;)

Check swiftfox site. You got a patch file that it's suppose to act uppon firefox (public) code and you got binaries. 
I believe they are made exactly the way they say they made with nothing more on it. I don't believe its a bad mean thing. I'm not such suspicious or paranoid.
Just don't like the branding, precisely, and the license.

I've used and advised swiftfox a lot in the past. 
But now there is swiftweasel, don't see the point in still using it. :)

---

### Post by Rui Pais on 2007-06-19
> **dptxp said:**
> I clicked on the file at their site to install, if my memory is right.

the problem is that site have debs, tar.bz2 and sh script :(

try first: apt-get remove swiftfox
if it fails do a search to see where is located the binary and remove the folder (usually is /usr/local/lib/swiftfox)

---

### Post by dptxp on 2007-06-19
I used these instructions given at their site  

 1.  Download the installer to your home directory
   2. Open a terminal window
   3. Run the installer by typing the following:
      sh install-swiftfox.sh
   4. Launch Swiftfox by selecting it from the menu

They have an uninstaller too. I think i have to replace install with uninstall in the command line.

---

### Post by Rui Pais on 2007-06-19
> **dptxp said:**
> I used these instructions given at their site  

 1.  Download the installer to your home directory
   2. Open a terminal window
   3. Run the installer by typing the following:
      sh install-swiftfox.sh
   4. Launch Swiftfox by selecting it from the menu

They have an uninstaller too. I think i have to replace install with uninstall in the command line.

i read the script, now.
It installs on /opt/swiftfox (ls /opt should show it)

I don't see an uninstall options...

---

### Post by Stirling on 2007-06-19
> **dptxp said:**
> I used these instructions given at their site  

 1.  Download the installer to your home directory
   2. Open a terminal window
   3. Run the installer by typing the following:
      sh install-swiftfox.sh
   4. Launch Swiftfox by selecting it from the menu

They have an uninstaller too. I think i have to replace install with uninstall in the command line.

Link to the uninstaller is on the site.  The direct link for you though is:

[http://getswiftfox.com/builds/installer/uninstall-swiftfox.sh](http://getswiftfox.com/builds/installer/uninstall-swiftfox.sh)

---

