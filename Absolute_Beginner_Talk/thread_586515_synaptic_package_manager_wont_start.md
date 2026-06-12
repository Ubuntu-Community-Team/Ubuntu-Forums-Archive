---
title: "synaptic package manager wont start"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Malice007 on 2007-10-22
Sun-java froze had to reboot nwo when I open it I get this:


Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first


How do I fix?

---

### Post by overdrank on 2007-10-22
> **Malice007 said:**
> Sun-java froze had to reboot nwo when I open it I get this:


Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first


How do I fix?

HI you can try the command in the terminal
```
sudo apt-get install -f

```

---

### Post by realvz on 2007-10-22
wait for 15mins and then try again....

perhaps its just refreshing the repositories

---

### Post by Malice007 on 2007-10-22
I typed that and now I get this


malice@malice-laptop:~$ sudo apt-get install -f
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
malice@malice-laptop:~$

---

### Post by realvz on 2007-10-22
wait for 15mins and then try again....

---

### Post by Malice007 on 2007-10-22
ok I rebooted the computer all is good it told me to fix it to type a command and now when I try to install sun java I get this:

malice@malice-laptop:~$ sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-bin is already the newest version.
sun-java6-plugin is already the newest version.
sun-java6-fonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up sun-java6-doc (6-00-2ubuntu2) ...
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


I tried to reintall the jdk-6-doc and I get the same thing...I hit enter several times and then typed no to stop

---

### Post by Papa-san on 2007-10-22
If you have any program open that has administrative rights, your system will keep telling you this.

This is a safeguard to keep you from opening your 'synaptic package manager' while you have like 'update manager' running. As to which programs are going to cause this, you will learn them as you use Ubuntu for longer. 

I used to try to run a few different operations in Windoze at the same time to save time. In win that works... In Ubuntu, it's one at a time.

Can you imagine what it would be like for windows users to get this kind of error when some hacker was acting as admin? Prolly wake them up to how insecure the windows OS's really are.

---

### Post by Papa-san on 2007-10-22
Apt-get, which is admin, is still running. That's why you are getting the error. Try running your synaptic package manager first, and then try the apt-get operations once you are done.

(FYI, though, 'sudo aptitude' has it's own error-checking capabilities, and will grab dependencies that 'sudo apt-get' won't try to resolve.)
Try:```
malice@malice-laptop:~$ sudo aptitude install sun-java6-jre
```and see if it makes a difference.

I do offer this disclaimer: I use the Long Term Support version: Ubuntu Dapper 6.10 LTS, so some things may be different in your version...

---

### Post by Malice007 on 2007-10-22
ok I waited opened up synaptic yet again it told me to type a command in terminal, I did this... then I opened it up again it went into it.. and then I typed what you told me.. and I get this....

I had nothing else open just terminal..


malice@malice-laptop:~$ sudo dpkg --configure -aPassword:
Setting up sun-java6-doc (6-00-2ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of JDK documentation
dpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-doc
malice@malice-laptop:~$ sudo aptitude install sun-java6-jreReading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up sun-java6-doc (6-00-2ubuntu2) ...
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

### Post by Malice007 on 2007-10-22
Also this all started when it all locked up on me when install sun-java and I had to reboot...noe of the things I selected intalled correctly I believe

---

### Post by Malice007 on 2007-10-22
reinstall ubuntu again? Everytime I run into problems I call up dell and they tell me to reintall... I dont think that is a fix

---

### Post by Papa-san on 2007-10-22
Hmmmm....

It does sound as though you might have found a version specific issue, It shouldn't have tried to do anything with your password...

I really don't know enough to work this through. 

Though we do know that you couldn't get into synaptic because apt-get hung on ya. (and hence, the stuff you were trying to install was mussed up by the re-boot.)

Try to search specifically for "install+sun" and see what kinds of threads you find.

---

### Post by Malice007 on 2007-10-22
Ok,

I fixed the problem. I went into synaptic searched for all sun-java.. did a complete uninstall rebooted.

Went into terminal typed: sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin sun-java6-fonts

all is good now..

---

### Post by 1/0 on 2007-11-14
I got that a wile back. Its these freekin GUI:s people want that causes this. Java needs an EULA agreement, the regular installation prompts for an OK but the GUI hides it (unless you choose to see the details). Naturally most people assume the install has crashed, when it is actually awaiting an agreement. 

I can't remember if I solved it by removing the packages and the reinstalling them or if it was by:

```

sudo dpkg --configure -a
sudo apt-get update

```

If you have further problems, the above has shown useful for me.

---

