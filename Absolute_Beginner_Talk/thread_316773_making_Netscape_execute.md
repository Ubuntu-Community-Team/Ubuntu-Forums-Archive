---
title: "making Netscape execute"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by luvinit on 2006-12-11
I have installed the following old Netscape navigator distribution 

navigator-v48-us.x86-unknown-linux2.2.tar.gz

from

[http://sillydog.org/narchive/](http://sillydog.org/narchive/)

It has an install script which it recommends using, so I did as I was told. It seems to have installed ok, by default it puts everything to opt/netscape

there is an executable "netscape" there, but it doesn't run if I try to execute it, nothing happens. There is no script in there to run it instead of using it directly.Any ideas why? 
I have noticed in my short time as an ubuntu user that it is common for executable files to be run from a script, not directly. Why is that? sometimes you can run them directly, others not. I am sure there is a perfectly good explanation for this, but I don't know it.

---

### Post by taurus on 2006-12-11
You need to add that directory to your path so you can run it anywhere!!!  You can do that in ~/.bashrc

```
PATH=$PATH:/opt/netscape/bin
export PATH
```

---

### Post by rbprogrammer on 2006-12-11
not sure if the solution is as easy as making sure that the file is in fact an executable file....

i do this quite often, i forget that some files are not executable right after an installation.  

do something like:
```

cd /path/to/the/file
sudo chmod +x filename

```
this is assuming you want all users to execute the file

---

### Post by luvinit on 2006-12-11
Hi thanks, all, but none of that has any effect. Did I understand correctly, you are saying to edit the .bashrc file that is my home directory and put those lines in it? I have done that I get "command not found" if I go from the command line, regardless or where I am e.g. if i run the command from inside the opt/netscape directory or in my home directory. It isn't a permission problem I believe because it is accessible by all groups and is set to executable. Howver, I do know little about Ubuntu. :p

---

### Post by taurus on 2006-12-11
What's the output of this command?

```
ls -la /opt/netscape
```

---

### Post by luvinit on 2006-12-11
here it is

mark@mark-desktop:~$ ls -la /opt/netscape
total 13788
drwxr-xr-x 5 root root    4096 2006-12-11 14:55 .
drwxr-xr-x 3 root root    4096 2006-12-09 12:48 ..
-r--r--r-- 1 8482 uucp    4524 2002-07-22 13:17 bookmark.htm
drwxr-xr-x 3 8482 uucp    4096 2002-07-22 13:17 java
-r-xr-xr-x 1 8482 uucp   14940 2002-07-22 13:17 libnullplugin-dynMotif.so
-r--r--r-- 1 8482 uucp   16934 2002-07-22 13:09 LICENSE
drwxr-xr-x 3 8482 uucp    4096 2002-07-22 13:16 nethelp
-r-xr-xr-x 1 8482 uucp 7758308 2002-07-22 13:17 netscape
-r--r--r-- 1 8482 uucp  324029 2002-07-22 13:09 Netscape.ad
-r-xr-xr-x 1 8482 uucp 5867692 2002-07-22 13:17 netscape-dynMotif
-rwxr-xr-x 1 mark mark      14 2006-12-11 14:55 nt
-rw-r--r-- 1 mark mark      13 2006-12-11 14:53 nt~
drwxr-xr-x 2 root root    4096 2006-12-09 12:48 plugins
-r--r--r-- 1 8482 uucp   16728 2002-07-22 13:16 README
-rw-r--r-- 1 root root    2405 2006-12-09 12:48 registry
-rwxr-xr-x 1 mark mark   22008 2002-07-22 16:05 vreg
-r--r--r-- 1 8482 uucp    4674 1994-10-18 07:54 XKeysymDB

---

### Post by taurus on 2006-12-11
In that case, add these two lines to ~/.bahsrc...

```
PATH=$PATH:/opt/netscape
export PATH
```
Save it and source it...

```
source ~/.bashrc
netscape
```

---

### Post by luvinit on 2006-12-11
ok looks like some kind of action now, here is the output i got when netscape command was run

netscape: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

---

### Post by taurus on 2006-12-11
Use synaptic and search for that package, libstdc++-libc6.  Otherwise, what's the output of this command, regarding all the share library for that old version of netscape?

```
ldd /opt/netscape/netscape
```

---

### Post by luvinit on 2006-12-11
synatpic can't find anything. the output is here

linux-gate.so.1 =>  (0xffffe000)
        libBrokenLocale.so.1 => /lib/tls/i686/cmov/libBrokenLocale.so.1 (0xb7f12000)
        libXt.so.6 => /usr/lib/libXt.so.6 (0xb7ec4000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0xb7ebb000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0xb7ea2000)
        libXmu.so.6 => /usr/lib/libXmu.so.6 (0xb7e8d000)
        libXpm.so.4 => /usr/lib/libXpm.so.4 (0xb7e7d000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7e70000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7da7000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7da3000)
        libstdc++-libc6.1-1.so.2 => not found
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7d7c000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7c48000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7c45000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7c40000)
        /lib/ld-linux.so.2 (0xb7f26000)

i appreciate the time you're taking over this. some people might wonder why i am bothering but i like to test websites in older browsers because I don't like to make things inaccessible to users just cus they have an old rig

---

### Post by taurus on 2006-12-11
I won't be in the office until later today but try to search for libstdc, stdc, or libc6.  And if you find something, make sure you install the right version that it needs, libstdc++-libc6.1-1.so.2.

---

### Post by luvinit on 2006-12-11
will do, thanks

---

### Post by luvinit on 2006-12-11
Ok there are versions of libstdc++-libc6.1-1.so.2. around but not for ubuntu so I have avoided them for now.
Alternatives I have found are people who have had the same problem installing other software, who have fixed the problem by sym linking to other libstdc repositories. These haven't worked for me. examples are 

[http://support.nusphere.com/viewtopic.php?t=1823](http://support.nusphere.com/viewtopic.php?t=1823)

[http://ubuntuforums.org/showthread.php?p=1864802](http://ubuntuforums.org/showthread.php?p=1864802)

[http://icculus.org/~jcspray/maple9_debian.html](http://icculus.org/~jcspray/maple9_debian.html)

error i get now is 

segmentation fault core dumped

before that I was getting another error, but i cant remember what it said, something to do with a symbol I think! :D 

a screen did flash up for a second but not anymore

I sit a good idea to try another linux release version of the repository? I'm inclined to think that i might be a good idea to give up at this point. Thanks for your help.

---

### Post by taurus on 2006-12-11
Try to run it from a terminal so you can see the exact error message instead of opening and closing of the app from X!

---

### Post by luvinit on 2006-12-11
when i run from the terminal exact error is

Segmentation fault (core dumped)

---

### Post by kerry_s on 2006-12-11
If you don't mind me asking, but why do you want a old buggy web browser version? Have you looked at seamonkey? It offers the same thing, just newer.-> [http://www.mozilla.org/projects/seamonkey/](http://www.mozilla.org/projects/seamonkey/)
I was using it for a while and it is very fast. Adding this extension & it's even better-> [http://multizilla.mozdev.org/](http://multizilla.mozdev.org/)
Here's the theme i was using-> [http://www.tom-cat.com/mozilla/seamonkey.html](http://www.tom-cat.com/mozilla/seamonkey.html)

---

### Post by luvinit on 2006-12-11
Well I didn't realise it was going to be so difficult. :-D  It is because I like to make websites accessible to old machines, so it is handy to have something older to test it with. You are correct, but Netscape died off because people tended to take the mentality that it if it worked with IE you should just switch, whereas I always made my stuff work better in Netscape. Luckily the mozilla project has given us some great alternatives, but what if it had died in 1999-2000 never to return? The first time I used some Microsoft software to edit pages it outputted them in format that no longer showed correctly in Netscape, so I stopped using it. Most people just switched. For a laugh I tend to put in irritating dynamic stuff that only shows up in IE. :D Knowing them, they probably think it is really cool, but it annoys the hell out of me.

---

