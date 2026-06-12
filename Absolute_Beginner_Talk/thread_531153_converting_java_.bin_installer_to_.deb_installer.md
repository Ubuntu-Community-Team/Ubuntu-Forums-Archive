---
title: "converting java .bin installer to .deb installer"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2007-08-21
i have downloaded sun java 6 development kit from java.sun. it is .bin installer which does not configure my system for java and jadk. i want to convert this bin installer to deb installer.

i tried following 
> sudo apt-get install fakeroot java-package java-common
then to convert .bin to .deb i did this and got the result
> ejaz@ejaz-desktop:~/java$ fakeroot make-jpkg  jdk-6u2-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.RiLRpO8060
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

Detected Debian build architecture: i386
Detected Debian GNU type: i486-linux-gnu

No matching plugin was found.
Removing temporary directory: done
ejaz@ejaz-desktop:~/java$        

can anybody help me in solving this?
i do not want to install java from repo because it is not always uptodate .
plz don't suggest installing from repository

---

### Post by testube_babies on 2007-08-21
You could try installing it the even-less-official way, without fakeroot/java-package:

[http://www.daveshuck.com/blog/index.cfm/2007/2/7/Installing-Java-6-16-in-Linux](http://www.daveshuck.com/blog/index.cfm/2007/2/7/Installing-Java-6-16-in-Linux)


EDIT:  There's a more up-to-date version of this method here:
[http://ubuntuforums.org/showthread.php?t=332674](http://ubuntuforums.org/showthread.php?t=332674)

---

### Post by u04f061 on 2007-08-21
thanks for this.
I used 2nd link. it has installed java runtime environment. so java command is available, but javac command for jdk is not there

---

### Post by flargen on 2007-08-21
Maybe you installed the JRE instead of the JDK. [Here]("https://sdlc1b.sun.com/ECom/EComActionServlet;jsessionid=5774D979AC43D8EB0C5D9D697ED4D328")

---

### Post by u04f061 on 2007-08-21
No! I installed JDK1.6_02 .Netbeans can locate jdk and it compiles files successfully but terminal can't find javac command

---

### Post by testube_babies on 2007-08-22
You can find the javac program by doing ```
sudo updatedb
locate javac
```

And then to use it```
sudo update-alternatives --install /usr/bin/javac javac */path/to/javac* 300
sudo update-alternatives --config javac
```


You might want to do this with the other java commands too:  javah, javaws, javadoc, javap, etc.

---

