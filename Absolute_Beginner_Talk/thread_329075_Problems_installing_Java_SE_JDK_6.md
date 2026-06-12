---
title: "Problems installing Java SE JDK 6"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by andrew222 on 2006-12-31
I downloaded Java SE JDK 6 from the Sun website. I executed the binary file and I received this:

Initializing InstallShield Wizard........
Extracting Installation Archive.
andrew@ubuntuOne:~$


It ceased to do any more actions after this...I hoping to get a full installation. Any advice on what is wrong is greatly appreciated...

Andrew

---

### Post by MkfIbK7a on 2006-12-31
do you have wine? because installshield wizard is a windows program.

---

### Post by steve.horsley on 2007-01-01
I second that question - what was the filename you downloaded? When I installed it, the file I downloaded was **jdk-6-linux-i586.bin** I installed it with a series of commands rather like this:
> sudo su
cd /opt
chmod +x jdk-6-linux-i586.bin
jdk-6-linux-i586.bin
which created the install directory in /opt. Then I had to fix up the symlink to java in /etc/alternatives to point to the new install.

---

### Post by taurus on 2007-01-01
I think he downloaded the Windows version instead of the Linux version!

---

### Post by andrew222 on 2007-01-01
To Steve.Horsley:

I decided to follow your lead and I got the exact file you named  'jdk-6-linux-i586.bin' and I followed your steps...I ran into a problem at the last line which tries to execute the file.  Here is what I ran into...

andrew@ubuntuOne:~$ sudo mv /home/andrew/Desktop/jdk-6-linux-i586.bin /opt/
andrew@ubuntuOne:~$ sudo su
root@ubuntuOne:/home/andrew# cd /opt
root@ubuntuOne:/opt# chmod +x jdk-6-linux-i586.bin
root@ubuntuOne:/opt# jdk-6-linux-i586.bin
bash: jdk-6-linux-i586.bin: command not found



I also have another thread going right now about some problems I have downloading updates and downloading from synaptic package manager,  so I think I may have a very corrupted Ubuntu installation right now,  and that is really troubling me at the moment...

Any advice and help is welcome,  

Andrew

---

### Post by taurus on 2007-01-01
Try

```
./jdk-6-linux-i586.bin
```

Look at your thread and post your /etc/apt/sources.list!!!

---

### Post by Olli on 2007-01-01
> **andrew222 said:**
> To Steve.Horsley:

I decided to follow your lead and I got the exact file you named  'jdk-6-linux-i586.bin' and I followed your steps...I ran into a problem at the last line which tries to execute the file.  Here is what I ran into...

andrew@ubuntuOne:~$ sudo mv /home/andrew/Desktop/jdk-6-linux-i586.bin /opt/
andrew@ubuntuOne:~$ sudo su
root@ubuntuOne:/home/andrew# cd /opt
root@ubuntuOne:/opt# chmod +x jdk-6-linux-i586.bin
root@ubuntuOne:/opt# jdk-6-linux-i586.bin
bash: jdk-6-linux-i586.bin: command not found



I also have another thread going right now about some problems I have downloading updates and downloading from synaptic package manager,  so I think I may have a very corrupted Ubuntu installation right now,  and that is really troubling me at the moment...

Any advice and help is welcome,  

Andrew

I think you should use
chmod +ax jdk-6-linux-i586.bin
./jdk-6-linux-i586.bin

---

### Post by andrew222 on 2007-01-01
Thank You for the replies...

taurus:

Thank You again...I have responded to your inquiry on my other existing thread and look forward to hearing from you...



Olli:

I should have remembered that... I do know that the '  ./  '  is required but rushed and forgot...

I need to get off the anxious seat and start solving these problems with a clear mind  :-)

---

### Post by steve.horsley on 2007-01-01
Oops. Yes it should have said ./jdk-6-linux-i586.bin. Oh well, at least you found it.

Once java was working, I also made a symlink from my firefox plugins directory to the java 6 plugin. > steve@StevesPC:~$ ls -l /opt/firefox/plugins/
total 20
lrwxrwxrwx 1 root root    54 2006-12-01 20:53 libjavaplugin_oji.so -> /opt/jdk1.6.0/jre/plugin/i386/ns7/libjavaplugin_oji.so
-rwxr-xr-x 1 root root 19160 2006-10-17 18:45 libnullplugin.so


You can make symlinks with the command:
**sudo ln -s realFileName symlinkFileName**
or if you prefer, **gksudo nautilus**, open a second window, then drag the target file from one window to the other window at the place you want to link it from using the **middle** mouse button.

---

