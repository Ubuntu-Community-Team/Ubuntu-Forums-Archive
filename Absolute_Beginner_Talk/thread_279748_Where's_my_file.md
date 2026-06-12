---
title: "Where's my file?"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by Risotto on 2006-10-18
Sorry for being really dumb but what am I doing wrong here please?  (I was really pleased to have converted it using alien!)

```
mike@ubuntu-mike:~/Desktop$ sudo dpkg -i quasar-client_1.4.7_GPL-2_i386.deb
Password:
(Reading database ... 117839 files and directories currently installed.)
Preparing to replace quasar-client 1.4.7_GPL-2 (using quasar-client_1.4.7_GPL-2_i386.deb) ...
Unpacking replacement quasar-client ...
Setting up quasar-client (1.4.7_GPL-2) ...
mike@ubuntu-mike:~/Desktop$ ./quasar-client
bash: ./quasar-client: No such file or directory
```

---

### Post by Anonii on 2006-10-18
Since you installed the program using APT, it will run with its command. That ./* you did, would open an executable file in your current directory. 
Try using the command, **quasar** or **quasar-client** in the terminal.
Or **qua** and then hitting TAB for auto-completion.

Good luck , and if you make it, report back.

---

### Post by taurus on 2006-10-18
It's probably installed in /bin, not ./ (which is current directory).  Therefore, try to run it as 

```
quasar-client
```
or search for it with

```
whereis quasar-client
```

---

### Post by Risotto on 2006-10-18
Thanks for this, I found the file...

```
mike@ubuntu-mike:~/Desktop$ whereis quasar-client
quasar-client:
mike@ubuntu-mike:~/Desktop$ whereis quasar
quasar: /opt/quasar/bin/quasar
```

But...

```
mike@ubuntu-mike:/opt/quasar/bin$ ls -l
total 10976
-rwxr-xr-x 1 root root 8622088 2005-07-04 21:03 quasar
-rwxr-xr-x 1 root root 2589992 2005-07-04 21:03 quasar_setup
mike@ubuntu-mike:/opt/quasar/bin$ quasar_setup
bash: quasar_setup: command not found
mike@ubuntu-mike:/opt/quasar/bin$ ./quasar_setup
./quasar_setup: error while loading shared libraries: libtcl8.4.so: cannot open shared object file: No such file or directory
mike@ubuntu-mike:/opt/quasar/bin$ quasar
bash: quasar: command not found
mike@ubuntu-mike:/opt/quasar/bin$ ./quasar
./quasar: error while loading shared libraries: libtcl8.4.so: cannot open shared object file: No such file or directory
```

I assume this means that I am missing a dependency somewhere?  However, I can't see libtcl in Synaptic.  What should I do now please?

Many thanks
Mike

---

### Post by raul_ on 2006-10-18
install tcl and tk in synaptic, i think that should do it

---

### Post by Risotto on 2006-10-19
Thanks Raul_, I found that adding tcl and tk and the -dev version of each has pushed it further forward - i.e. I'm getting a new dependency now:

```
mike@ubuntu-mike:/opt/quasar/bin$ ./quasar_setup
./quasar_setup: error while loading shared libraries: libicuuc.so.32: cannot open shared object file: No such file or directory
mike@ubuntu-mike:/opt/quasar/bin$ ./quasar
./quasar: error while loading shared libraries: libicuuc.so.32: cannot open shared object file: No such file or directory
```

But I can't find anything that seems to get me past this.  Any ideas please?

Thanks
Mike

---

### Post by raul_ on 2006-10-19
Aren't those libs on synaptic?

---

### Post by Risotto on 2006-10-19
libicu34 and libicu34-dev are, but they don't seem to make any difference.  I can't see anything else that might be of use.

---

### Post by Ben Sprinkle on 2006-10-19
Your trying to execute it in the home directory. I believe all packages go to like /var/tmp/cache or something. Search for cache and you will find all the packages you ever got via aptitude or synaptic. It might not be /var/tmp/cache. I am not on my linux comp.
Afteryou find just double click it and the deb installer will come up. :)

---

### Post by Risotto on 2006-10-19
No, I was trying to run it in /opt/quasar/bin/ as suggested by Taurus.  I used the whereis command to find the file.

---

### Post by Ben Sprinkle on 2006-10-19
```

sudo su
cd /opt/quasar/bin
ls
./exefile

```
Try that?

---

### Post by Risotto on 2006-10-19
Thanks Goat Spirit but it's still coming back with the same problem...

```
root@ubuntu-mike:/opt/quasar/bin# ls
quasar  quasar_setup
root@ubuntu-mike:/opt/quasar/bin# ./quasar_setup
./quasar_setup: error while loading shared libraries: libicuuc.so.32: cannot open shared object file: No such file or directory
root@ubuntu-mike:/opt/quasar/bin# ./quasar
./quasar: error while loading shared libraries: libicuuc.so.32: cannot open shared object file: No such file or directory

```

Any other suggestions?  I'm stumped!

---

### Post by raul_ on 2006-10-19
you don't need the "./" but that's not the problem...it's like it's searching for the libs in the wrong path..maybe with a symlink but honestly i don't know what files to link. Maybe another guy who reads this can make something up

---

### Post by raul_ on 2006-10-19
see if this rings any bell (found it on a website):

> The CPSC 324 Renderer requires several libraries which are not available in the standard location on the lab machines. This can be addressed by telling your environment where to find them; the easiest solution is to modify your .bashrc file so this environment setup is done each time you start up a terminal window. To do this:

   1. Open the file .bashrc (yes, the filename starts with a dot) file in your home directory. You should have such a file, but if you don't, a new file can be created. If you are using a graphical tool to locate and open the file, you may need to tell it to show hidden files.
   2. Add the following two lines at the end of the file:

      LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/classes/s06/cs324/lib
      export LD_LIBRARY_PATH

   3. Save the file. 

Things should now be set properly in any new terminal windows that you open. **If you get error messages about "error while loading shared libraries" when you try to start the renderer or about libicuuc.so.32, libicudata.so.32, and undefined references in libxerces-c.so when you compile, then your environment is not properly set.** See me if you need help modifying your .bashrc, or if you tried to make the changes but are getting these error messages. 

---

### Post by Risotto on 2006-10-20
Thanks Raul_.  I have done exactly what you suggest - I did have a .bashrc file - but it's still giving me the same response. :(

---

### Post by Ben Sprinkle on 2006-10-20
It's me goat. I ditched that account.
Actually you do need ./ for extracting archives with the executable property.

---

### Post by toxygen on 2006-10-20
> **Risotto said:**
> Thanks Raul_, I found that adding tcl and tk and the -dev version of each has pushed it further forward - i.e. I'm getting a new dependency now:

```
mike@ubuntu-mike:/opt/quasar/bin$ ./quasar_setup
./quasar_setup: error while loading shared libraries: libicuuc.so.32: cannot open shared object file: No such file or directory
mike@ubuntu-mike:/opt/quasar/bin$ ./quasar
./quasar: error while loading shared libraries: libicuuc.so.32: cannot open shared object file: No such file or directory
```

But I can't find anything that seems to get me past this.  Any ideas please?

Thanks
Mike

1) have you installed libicu34-dev and libicu34?
2) have you checked whether libicuuc.so.32 exists in your system?
```
updatedb
```
wait until it ends and then
```
locate libicuuc.so
```

if you get something like 
```
/usr/lib/libicuuc.so
``` and nothing else, then what you need to do is
```
sudo ln -s  /usr/lib/libicuuc.so /usr/lib/libicuuc.so.32
```

hope this help

---

### Post by snares on 2007-12-27
A little late to the party but thought I should post a solution. I had the same problem. Same Program in fact. I created the sym-link but that brought up a differnet error. What I did to solve this problem it go [libicu-3.2-3.i586.rpm]("http://rpm.pbone.net/index.php3/stat/4/idpl/3272463/com/libicu-3.2-3.i586.rpm.html")
and convert it to .deb w/ alien.(I used the --scripts option also not sure if it will make a difference. I always use it. I don't use alien that often but it works when I need it.) Then just install the new deb and it created all the shared libs I needed. 

cheers

---

