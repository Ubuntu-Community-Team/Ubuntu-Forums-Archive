---
title: "Updating Java"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by gustasonfrever on 2007-04-08
I am trying to install frostwire but in the process of booting frostwire from terminal I received this prompt;
gustason@gustason-laptop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
gustason@gustason-laptop:~$ 
 I went to java.com and downloaded 1.5 but now I'm not sure what commands to use to update the current 1.4 I have right now. Any help will be appreciated, thanks in advance.

---

### Post by alkat on 2007-04-08
Java is now included in the official Ubuntu repositories so there is no need to go and look for it on [www.java.com](www.java.com). Which Ubuntu version are you running? It seems that the Java version in the Ubuntu repositories fits Frostwire requirements:
[http://tinyurl.com/2zox62](http://tinyurl.com/2zox62)

I you want to go ahead and install Java directly from java.com, you can do so by followig this tutorial:
[http://www.debian-administration.org/articles/142](http://www.debian-administration.org/articles/142)

Remember to completely uninstall the version you now have before installing the new one (i believe that the two could live together with a little tweaking, bt it could be tricky to tell Frostwire which version to use).

Ale.

---

### Post by gustasonfrever on 2007-04-08
Alright thank you for your help. How do I completely uninstall the old one?

---

### Post by alkat on 2007-04-08
How did you install it in the first place? If it came preinstalled on your system or if you installed it from a .deb package, you can remove it via Synaptic: just launch the program and look for Sun java.

.a.

---

### Post by gustasonfrever on 2007-04-08
I have no idea how I instaled it in the first place. The guide that Alkat linked to is not working, terminal is not recognizing the commands (I'm running 6.10)

---

### Post by alkat on 2007-04-08
> **gustasonfrever said:**
> I have no idea how I instaled it in the first place. The guide that Alkat linked to is not working, terminal is not recognizing the commands (I'm running 6.10)


I've used that guide several times before Debian/Ubuntu accepted Java into official repositories so I'm quite sure it works. Can you tell us which commands are not recognized? Maybe you just need to install something.

Try to launch Synaptic and search for Java: if a JRE is listed there, it means that it was installed via apt-get or aptitude and therefore can be removed from Synaptic.

If you're running Edgy, you can just install an up-to-date version of the Java JRE from the official repositories (again, using Synaptic).

---

### Post by mahiyar on 2007-04-08
If you want java just for frost free then install jre1.5 (no matter if it is already installed) from this link [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp) this is the second file on the list: Linux (self-extracting file). 
Then make a new directory >>sudo mkdir /usr/java. 
Copy the bin file downloaded  to the new dir >>sudo cp jre-1_5_0_11-linux-i586.bin /usr/java . 
Make it executable and accessable to all >>sudo chmod a+x /usr/java/jre-1_5_0_11-linux-i586.bin
Run it >>sudo /usr/java/jre-1_5_0_11-linux-i586.bin

Now run frostwire, hopefully it should start. When frostwire starts one the places it looks for to get java is /usr/java, and that is exactly where we are putting java.

---

### Post by zvacet on 2007-04-08
If all your repositories are open you can install Java 1.6 with synaptic.To remove old version
```
 sudo apt-get remove --purge correct_name _of_your_program
```

---

### Post by gustasonfrever on 2007-04-08
How do I make a new directory and where do I create this directory? The reason I'm in the absolute beginner forum is because I really have no idea what I am doing. 

Well I typed your commands into terminal and this is what I got, tell me what I'm doing wrong

gustason@gustason-laptop:~$ sudo mkdir /usr/java
Password:
gustason@gustason-laptop:~$ sudo cp jre-1_5_0_11-linux-i586.bin /usr/java
Password:
cp: cannot stat `jre-1_5_0_11-linux-i586.bin': No such file or directory
gustason@gustason-laptop:~$

---

### Post by happymellon on 2007-04-08
> **gustasonfrever said:**
> How do I make a new directory and where do I create this directory? The reason I'm in the absolute beginner forum is because I really have no idea what I am doing.

In your in a terminal the command "mkdir" makes a directory

If your in Nautilus (the file manager) right click will give you create new folder option.

As for where it has to be, that's in /usr
The catch is that since it is outside of your home directory, you don't own it so you have to run sudo to make it. This gives you temporary administrator privileges to perform these duties.

so the full command would be

sudo mkdir /usr/java

Another way which might be easier in the long run if you want to keep everything in the GUI is to get a program called Automatix, this installs a bunch of software (you can pick which ones though) and one of them gives you a right click Root Nautilus Here option so you can perform all these things from the GUI rather than the command prompt.

This does seem strange since Java is part of the Ubuntu installation, have you tried running:
sudo apt-get upgrade
to get the newest version of Java?

---

### Post by gustasonfrever on 2007-04-08
Well Automatix2 is not working for me, everything I try and download has the same error, I've tried 10 programs and everyone gave me an error. 

I did what you said and this is what I got

gustason@gustason-laptop:~$ sudo mkdir /usr/java
Password:
gustason@gustason-laptop:~$ sudo cp jre-1_5_0_11-linux-i586.bin /usr/java
Password:
cp: cannot stat `jre-1_5_0_11-linux-i586.bin': No such file or directory
gustason@gustason-laptop:~$ 
Then I tried again and got this
gustason@gustason-laptop:~$ sudo mkdir /usr/java
mkdir: cannot create directory `/usr/java': File exists
gustason@gustason-laptop:~$ 

If I was typing in the upgrade command do I need to do anything so that the computer nows what program I want to update?
And what program were you teling me about that lets you download stuff from a GUI?

---

### Post by mahiyar on 2007-04-09
Hopefully you should have downloaded the jre file. If you know where the file is, then you are supposed to cd to that directory e.g if you can see the jre file on the desktop then before using the cp command (copy) first do this >>cd ~/Desktop . The ~ isign is short form for /home/"user name" directory and Desktop folder path is /home/"user name"/Desktop
This link gives a good overview of filesystems and linux in general [http://www.tldp.org/LDP/gs/node5.html](http://www.tldp.org/LDP/gs/node5.html) . Of course since the directory is already created the second time you enter the command it will say that the directory is present.

---

