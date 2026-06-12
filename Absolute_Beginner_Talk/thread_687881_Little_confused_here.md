---
title: "Little confused here"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Mosod on 2008-02-04
```
joel@joel-desktop:~$ cd ~/opt/eclipse
joel@joel-desktop:~/opt/eclipse$ ls
about_files  configuration  eclipse.ini   features  libcairo-swt.so  plugins
about.html   eclipse        epl-v10.html  icon.xpm  notice.html      readme
joel@joel-desktop:~/opt/eclipse$ ~/opt/eclipse/eclipse
bash: /home/joel/opt/eclipse/eclipse: No such file or directory
joel@joel-desktop:~/opt/eclipse$
```

I'm super confused here.  I probably just typed something wrong and can't see it, but why the heck my system telling me a file is there and then telling me it isnt when I try and run it?

---

### Post by spiderbatdad on 2008-02-04
well...just typing the name of a file doesnt do anything. Are you trying to view the contents of the file? It doesn't look like a program ie. eclipse.sh...but if it were ./eclipse

Also you are already in ~/opt/eclipse...so the next path would be only /eclipse

---

### Post by jken146 on 2008-02-04
Why don't you just install eclipse from the repositories?

---

### Post by jan quark on 2008-02-04
go to system > administration > synaptic 
and search for the package eclipse

it will be downloaded and installed automatically with all needed dependencies

then it should be displayed in the applications menu

---

### Post by Mosod on 2008-02-04
The eclipse in the repositories is an older version.  I want the latest.  Also, I followed the instructions found [here]("https://help.ubuntu.com/community/EclipseIDE") (the user installation section) but have run into the problem I am inquiring about.

---

### Post by spiderbatdad on 2008-02-04
in your op. your pwd was  ~/opt/eclipse and you entered ~ /opt/eclipse/eclipse...do you see the problem?

---

### Post by Mosod on 2008-02-04
> **spiderbatdad said:**
> in your op. your pwd was $ ~/opt/eclipse and you entered ~ /opt/eclipse/eclipse...do you see the problem?

No thats what I wanted to do.  I want to execute the file eclipse found in the ~/opt/eclipse folder.  That was the point of the ls, to show that the system tells me there is a file named eclipse in the ~/opt/eclipse directory but if I try ~/opt/eclipse/eclipse to run it, it says there is no such file or directory.

---

### Post by emarkd on 2008-02-04
So what happens if you do 

```
$ cd ~/opt/eclipse
$ ./eclipse
```

---

### Post by Mosod on 2008-02-04
I get the same thing.

```
joel@joel-desktop:~$ cd ~/opt/eclipse
joel@joel-desktop:~/opt/eclipse$ ./eclipse
bash: ./eclipse: No such file or directory
joel@joel-desktop:~/opt/eclipse$ ls
about_files  configuration  eclipse.ini   features  libcairo-swt.so  plugins
about.html   eclipse        epl-v10.html  icon.xpm  notice.html      readme
joel@joel-desktop:~/opt/eclipse$ 

```

ls is there again just to show that the file is (supposedly) there.

---

### Post by spiderbatdad on 2008-02-04
the eclipse file as you have it does not look like a launchable script. It should be called eclipse.sh ( I'm assuming) It should also be executable```
chmod a+x eclipse.sh
```(assuming you are still in pwd ~/opt/eclipse. Then```
./eclipse.sh
```

---

### Post by Mosod on 2008-02-05
That doesn't seem to be the problem.  I tried adding the .sh extension without any luck.  The file is listed as an executable if I bring up the file properties (MIME type executable/x-something or other).  Also the directions I linked to earlier in the thread mentions nothing about changing extensions.

---

### Post by emarkd on 2008-02-05
It's not the extension that matters, it's the permissions.  Try running

```
ls -l
```

in the directory containing the file in question and lets see if it has the execute bits set.

---

### Post by Trail on 2008-02-05
By the way, the file command might come in handy as to see what sort of file that is, as in:

file eclipse

---

### Post by Mosod on 2008-02-06
I've been working on this and I've come across some new info:

```
joel@joel-desktop:~/opt/eclipse$ ls -l
total 376
drwxr-xr-x 2 joel joel   4096 2007-11-03 13:40 about_files
-rw-r--r-- 1 joel joel  13852 2007-11-03 13:40 about.html
drwxr-xr-x 2 joel joel   4096 2007-11-03 13:40 configuration
-rwxr-xr-x 1 joel joel  21118 2007-11-03 13:40 eclipse
-rw-r--r-- 1 joel joel     92 2007-11-03 13:40 eclipse.ini
-rw-r--r-- 1 joel joel  16536 2007-11-03 13:40 epl-v10.html
drwxr-xr-x 6 joel joel   4096 2007-11-03 13:40 features
-rw-r--r-- 1 joel joel   9022 2007-11-03 13:40 icon.xpm
-rwxr-xr-x 1 joel joel 266168 2007-11-03 13:40 libcairo-swt.so
-rw-r--r-- 1 joel joel   6506 2007-11-03 13:40 notice.html
drwxr-xr-x 9 joel joel  12288 2007-11-03 13:40 plugins
drwxr-xr-x 2 joel joel   4096 2007-11-03 13:40 readme
joel@joel-desktop:~/opt/eclipse$ file ./eclipse
./eclipse: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), not stripped
joel@joel-desktop:~/opt/eclipse$ ldd ./eclipse
        not a dynamic executable
joel@joel-desktop:~/opt/eclipse$ 

```

So as someone suggested I verified the permissions are set to allow the file to be executed.  More interesting (to me anyway) is the results of the file and ldd commands.  file says eclipse is "dynamically linked" but ldd says eclipse is not a dynamic executable.  The results may not have anything to do with one another but they seem to be at odds.

---

### Post by zabien1970 on 2008-02-06
did you try eclipse without the  ./

---

### Post by Mosod on 2008-02-06
I have solved the problem ([and another one I posted about earlier]("http://ubuntuforums.org/showthread.php?t=684989").).  Apparently the download I got off the eclipse page (the version with the c/c++ IDE) was actually a 32 bit version despite being clearly labeled as the 64 bit version.  Once I installed a 32 bit version of java I started getting the error from the thread I linked to.  Once I configured eclipse to look for the newly downloaded 32 bit java, everything started working.

---

