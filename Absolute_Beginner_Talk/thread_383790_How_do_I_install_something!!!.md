---
title: "How do I install something?!?!?!"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by HebrewHammer on 2007-03-13
I am brand new to Ubuntu and Linux, I have installed it on my laptop where I need to use my wireless network card. I did some research and found that madwifi drivers will make my card work, so I downloaded it and......How do install the dam thing?!?!?! Theres a "install" file but it just opens like text, and the same think with a file called "make." I give up, i need help. Thanx

---

### Post by taurus on 2007-03-13
What is the output of this command in the directory that you just downloaded a driver for your wireless card?

```
ls -la
```

---

### Post by benfindlay on 2007-03-13
If you click on Sysem>>Admininstration>>Synaptic Package Manager it will launch a GUI installer for packages. It is worth reading up on this program and "repositories" as it makes life much easier than manually installing downloaded packages

But to directly answer your question:

If the file is source type the following lines into a terminal-
```
cd [folder where file is saved, eg Desktop]
sudo tar -xfvz [filename].tar.gz
cd [filename] (leave off tar.gz
./configure
make
make install

```

If the file is a .deb file-
```
cd [folder where file is saved]
sudo dpkg -i [filename]
```

---

### Post by HebrewHammer on 2007-03-13
when i cd into directory where the files are and type "ls -la" it looks like it prints out all the files and folders in the folder

---

### Post by noob_saioke45601 on 2007-03-13
here's a great tutorial on how to install stuff if its in source form.

[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html)

---

### Post by HebrewHammer on 2007-03-13
Also, when I do "make" in that directory, it first prints out "Checking requirements.......OK" then "Checking kernal configuration......OK" but then it prints out a crap load of errors. I extracted the archive on the desktop and I'm running it from there, is that ok?

---

### Post by HebrewHammer on 2007-03-13
hmmmmm, when i try copying the folder in the usr/local/src directory a window pops up and says "Error while copying to "usr/local/src" You do not have permissions to write to this folder" I just installed Ubuntu on my laptop an hour ago. I thought my accounr was admin?!

---

### Post by noob_saioke45601 on 2007-03-13
yea i get the same error. im searhing for a solution and when i find it ill post it.

---

### Post by HebrewHammer on 2007-03-13
Also, when i type "./configure" it says that that there is no such file or directory

---

### Post by HebrewHammer on 2007-03-13
Here is whhat happns when I ues "make":
```
hebrewhammer@laptop:~$ cd Desktop/madwifi-0.9.2.1
hebrewhammer@laptop:~/Desktop/madwifi-0.9.2.1$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/hebrewhammer/Desktop/madwifi-0.9.2.1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  HOSTCC  /home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:27:19: error: errno.h: No such file or directory
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:29:20: error: string.h: No such file or directory
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c: In function 'uudecode_usage':
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c: At top level:
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:40: error: expected ')' before '*' token
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:70: error: expected ')' before '*' token
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c: In function 'main':
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:121: error: for each function it appears in.)
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:188: warning: implicit declaration of function 'open'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath/uudecode] Error 1
make[2]: *** [/home/hebrewhammer/Desktop/madwifi-0.9.2.1/ath] Error 2
make[1]: *** [_module_/home/hebrewhammer/Desktop/madwifi-0.9.2.1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [modules] Error 2

```

---

### Post by HebrewHammer on 2007-03-14
*bump* help *bump* srry, but i can't do jack w/o internet on my laptop

---

### Post by undertakingyou on 2007-03-14
Try ```
sudo make
``` it will ask for your password. 
After it does the make file do ```
 sudo make install
```

---

### Post by silhouette on 2007-03-14
First, you need to install build-essential to compile software. Try this first:

```
sudo apt-get install build-essential
```

Second, you should not have to put files in /usr/local/src. Some people may do this but to me it's extra work. Just extract the .tar.gz to some directory, then navigate to that directory, and run

```
./configure
make
sudo make install
```

Third, notice that you do not have to run sudo along with "./configure" and "make". You **do**, however, have to run sudo with "make install", because that moves files to /usr/src or /usr/local/src, which are write-protected for non-root users.

When you installed Ubuntu and set up a user account, Ubuntu made all directories that were not in your home folder write-protected for security reasons. This is why you must prepend commands that perform operations outside of that folder with "sudo".

HTH!

---

### Post by undertakingyou on 2007-03-14
> **silhouette said:**
> First, you need to install build-essential to compile software. Try this first:

```
sudo apt-get install build-essential
```

Second, you should not have to put files in /usr/local/src. Some people may do this but to me it's extra work. Just extract the .tar.gz to some directory, then navigate to that directory, and run

```
./configure
make
sudo make install
```

Third, notice that you do not have to run sudo along with "./configure" and "make". You **do**, however, have to run sudo with "make install", because that moves files to /usr/src or /usr/local/src, which are write-protected for non-root users.

When you installed Ubuntu and set up a user account, Ubuntu made all directories that were not in your home folder write-protected for security reasons. This is why you must prepend commands that perform operations outside of that folder with "sudo".

HTH!

Thanks for clarifying me.

---

### Post by HebrewHammer on 2007-03-14
well, freakin awesome b/c that worked!!!! But, how do i get my wireess card to work now???? I just want to connect to my wireless network!!!

---

### Post by undertakingyou on 2007-03-14
Go to SYSTEM =>ADMINISTRATION =>NETWORKING.  Make sure it is enabled and then put in your information such as SSID etc.  Also, there is a program called network manager that is supposed to be easy to use to search for nearby networks.  Haven't ever used it myself though.

---

### Post by HebrewHammer on 2007-03-14
Wow, i cannot tell you guys how much i love u!!!!!!!!!! I have tried a million times to use Ubuntu on my laptop but always gave up b/c i couldn't get the wifi card to work. THANK YOU GUYS SOOOOOOOOOOOOO MUCH!!!!!!!!!!!!!!

---

### Post by hyper_ch on 2007-03-14
Good to know it worked. Next time just buy hardware that will natively supported... that gives much less headache :)

---

### Post by benfindlay on 2007-03-14
I would also recommend installing wifi-radar onto your computer. It adds scanning function to your computer as well as allowing you to have multiple wireless network configurations on your machine at once.

It runs in a GUI and you simply click connect to connect to the wireless network you want to use. Really useful for people that actually take their laptops out of the house!

---

