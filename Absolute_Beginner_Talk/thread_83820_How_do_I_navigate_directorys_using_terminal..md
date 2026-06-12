---
title: "How do I navigate directorys using terminal."
date: 2005-10-29
forum: Absolute Beginner Talk
---

### Post by brutaldrummer on 2005-10-29
I'm trying to learn how to install tar.gz files with the terminal but when I CD I can never get the directory. This is what I type

cd desktop/downloads/

now in my mind that would take me there, but I'm typing it wrong can someone give me an example of how to get somewhere?

---

### Post by Kapre on 2005-10-29
[QUOTE=brutaldrummer]I'm trying to learn how to install tar.gz files with the terminal but when I CD I can never get the directory. This is what I type

cd desktop/downloads/

now in my mind that would take me there, but I'm typing it wrong can someone give me an example of how to get somewhere?[/QUOTE]

Pls change it to cd /Desktop/downloads......please make sure that your downloads directory doesnt start with a capital letter.

K

---

### Post by Sionide on 2005-10-29
Ubuntu and Linux in general is case-sensative.

/home/user/Desktop is a different directory to /home/user/desktop

Also, try using tab - type the first few letters of "downloads" and press tab, it'll complete the rest of the directory name for you, or give you a list of all the things which start with those letters.

---

### Post by brutaldrummer on 2005-10-29
new question... how do I move backwards... from oh lets say... desktop to home.

---

### Post by NewWithoutClue on 2005-10-29
cd ..
to go back ;)

---

### Post by cwaldbieser on 2005-10-29
[QUOTE=brutaldrummer]new question... how do I move backwards... from oh lets say... desktop to home.[/QUOTE]
"cd" by itself to go to your home, directory is another shortcut.

---

### Post by cowlip on 2005-10-29
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)

This will help you with hte terminal

---

### Post by orbishek on 2005-10-30
how do i navigate to my windows partitions, i have a dual os with xp installed in d:\  ,how do  i access the files in it via linux

---

### Post by xmastree on 2005-10-30
[QUOTE=orbishek]how do i navigate to my windows partitions, i have a dual os with xp installed in d:\  ,how do  i access the files in it via linux[/QUOTE]Is the drive mounted?
[http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)
then:
```
cd /media/windows/
```To get to its root directory.

---

### Post by Mustard on 2005-10-30
Just thought I would mention that on Breezy you can go to System>>Administration>>Disks to mount drives.

As your drive is using ntfs you will only be able to mount it as read only.

---

### Post by Boca on 2005-11-19
Having the same problem here (can't navigate to a file I want).

[I]boca@linubuntu:~$ cd /desktop
bash: cd: /desktop: No such file or directory
boca@linubuntu:~$ cd /Desktop
bash: cd: /Desktop: No such file or directory
boca@linubuntu:~$ cd /Desktop/downloads
bash: cd: /Desktop/downloads: No such file or directory
boca@linubuntu:~$[/I]


What am I missing?

---

### Post by spartas on 2005-11-19
Leave out the forward slash.  The / tells it to go to the very root of the drive.  Your home folder is located in /home/[your_user_name_here].

---

### Post by Boca on 2005-11-19
[QUOTE=spartas]Leave out the forward slash.  The / tells it to go to the very root of the drive.  Your home folder is located in /home/[your_user_name_here].[/QUOTE]
So what exactly would the command(s) be to reach this file?

/home/boca/Desktop/downloads/bjfilter-pixusip3100-2.50-2.i386.rpm

I'm trying to install a printer driver.

-------------------------------
EDIT: I got closer but says permission was denied.

boca@linubuntu:~/Desktop$ /home/boca/Desktop/downloads/bjfilter-pixusip3100-2.50-2.i386.rpm
bash: /home/boca/Desktop/downloads/bjfilter-pixusip3100-2.50-2.i386.rpm: Permission denied


root@linubuntu:~# /home/boca/Desktop/downloads/bjfilter-pixusip3100-2.50-2.i386.rpm
-bash: /home/boca/Desktop/downloads/bjfilter-pixusip3100-2.50-2.i386.rpm: Permission denied
root@linubuntu:~#

---

### Post by spartas on 2005-11-19
First, get into the correct directory with:

```

cd ~/Desktop/downloads

```

Note: the ~ is a shortcut for your home directory.

Secondly, you need that file to be executable

```

chmod +x bjfilter-pixusip3100-2.50-2.i386.rpm

```

Now you can use it.  With rpm files, we use alien to convert them.  Install alien and run 
```

man alien

```
to find out more about that tool.

Edit: it should be chmod, not chomd.

---

### Post by Boca on 2005-11-19
I finally got there this way.
> 
boca@linubuntu:~$ cd
boca@linubuntu:~$ Desktop/downloads
bash: Desktop/downloads: is a directory

boca@linubuntu:~$ sudo alien Desktop/downloads/bjfilter-pixusip3100-2.50-2.i386.rpm
bjfilter-pixusip3100_2.50-3_i386.deb generated

boca@linubuntu:~$ sudo alien Desktop/downloads/bjfilter-pixusip3100-3.50-2.i386.rpm
bjfilter-pixusip3100_2.50-3_i386.deb generated

boca@linubuntu:~$ sudo alien 
Desktop/downloads/bjfilter-pixusip3100-lprng-2.50-2.i386.rpm
bjfilter-pixusip3100-lprng_2.50-3_i386.deb generated

*cd ~/Desktop/downloads* is much shorter and faster :) Thx!

---

