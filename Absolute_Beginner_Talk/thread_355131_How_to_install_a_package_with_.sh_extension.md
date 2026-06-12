---
title: "How to install a package with .sh extension ?"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by rofarmer on 2007-02-06
I downloaded the SETI tool, which is delivered in a .sh format.  I tried using the Terminal function, and **sh boinc-etc-etc.sh**  to unpack it.  It says it can't open the boinc file.  I added **/desktop/** in front of the boinc file name, and it still does not work.  I am sure there is something simple I am not doing here, but I can't find what it is.

---

### Post by taurus on 2007-02-06
```
cd ~/Desktop
chmod 755 **filename.sh**
./**filename.sh**
-or-
sudo ./**filename.sh**
```

---

### Post by ComplexNumber on 2007-02-06
> **rofarmer said:**
> I downloaded the SETI tool, which is delivered in a .sh format.  I tried using the Terminal function, and **sh boinc-etc-etc.sh**  to unpack it.  It says it can't open the boinc file.  I added **/desktop/** in front of the boinc file name, and it still does not work.  I am sure there is something simple I am not doing here, but I can't find what it is.
is the ".sh" file meant to be an executable? right click on the ".sh" file, select 'properties', then select 'permissions'. click on the execute tickbox.

EDIT: ahhh heck, taurus, you've got there before me :D

---

### Post by taurus on 2007-02-06
> **ComplexNumber said:**
> 
EDIT: ahhh heck, taurus, you've got there before me :D

Hello ComplexNumber.  ):P

---

### Post by rofarmer on 2007-02-06
Thanks for the prompt response, but neither of these worked.  The .sh seems to mean it is a sort of self-unzipping file.  I tried the **cd ~/desktop** and the bash says no such file or directory.  I tried the permissions thing and nothing happened after I chose HOW I wanted the file handled.  I must be doing something really dumb.  It is very frustrating to have been a technical person in the PC world for almost 20 years, only to find Linux is so cryptic I can't even do the simplest things, OR, that Linux is so not-ready-for-prime-time that it took me an entire day to get my internet working, and it still doesn't understand how to use a floppy drive.

---

### Post by ComplexNumber on 2007-02-06
**rofarmer**
can you give me a link to where you downloaded the file from? then i can have a look at it myself so i can advise. btw there neeed to be a dot before the /file, so that it reads: **.**/filename

**taurus**
):P

---

### Post by fenian on 2007-02-06
Desktop need to start with a capital 'D'.

---

### Post by kevinlyfellow on 2007-02-06
> **rofarmer said:**
> It is very frustrating to have been a technical person in the PC world for almost 20 years, only to find Linux is so cryptic I can't even do the simplest things, OR, that Linux is so not-ready-for-prime-time that it took me an entire day to get my internet working, and it still doesn't understand how to use a floppy drive.

Don't be so frustrated... its one of those things where the more experience you have with another os, the harder it is to change gears.  Give yourself some time, you'll get the hang of it!  I grew up with dos, but I switched to linux, and now I find dos so cryptic that its unusable (just using dosbox gives me a headache now!)  

anyways, .sh stands for shell (shell script, kinda like old batch files that have a set of instructions that you can use in your shell).    Open it up with a text editor (vi, nano, or gedit) and take a look at what's inside even if you don't understand anything, but do look for some commands you know.   Sometimes they have binary in them, so if you can't open it up, don't worry.  [edit: I checked this out and it is indeed in binary]

You need to change the permissions of the file before it will allow you to run the set of commands.  This is a security feature.  To change them, you can use the terminal and do the chmod (change modifiers) thing, or you can do it graphically.  

Well, I know I didn't help solve the problem, but hopefully I provided some insight as to your situation.  Don't expect to learn everything right off the bat, but once you do learn it, you will love it!

[edit]  I tried it out for myself, and this is what happened
```

kevinly@ubuntu:~$ chmod 755 Desktop/boinc_5.4.11_i686-pc-linux-gnu.sh
kevinly@ubuntu:~$ ./Desktop/boinc_5.4.11_i686-pc-linux-gnu.sh
now run /home/kevinly/BOINC/run_client to run the client and /home/kevinly/BOINC/run_manager to run the GUI
kevinly@ubuntu:~$ cd /home/kevinly/BOINC/
kevinly@ubuntu:~/BOINC$ ./run_client
2007-02-06 19:23:42 [---] Starting BOINC client version 5.4.11 for i686-pc-linux-gnu
2007-02-06 19:23:42 [---] libcurl/7.16.0 OpenSSL/0.9.8d zlib/1.2.3
2007-02-06 19:23:42 [---] Data directory: /home/kevinly/BOINC
2007-02-06 19:23:42 [---] Processor: 2 GenuineIntel Genuine Intel(R) CPU    T2300  @ 1.66GHz
2007-02-06 19:23:42 [---] Memory: 1002.28 MB physical, 854.98 MB virtual
2007-02-06 19:23:42 [---] Disk: 54.19 GB total, 36.72 GB free
2007-02-06 19:23:42 [---] No general preferences found - using BOINC defaults
2007-02-06 19:23:42 [---] Local control only allowed
2007-02-06 19:23:42 [---] Listening on port 31416
2007-02-06 19:23:42 [---] This computer is not attached to any projects
2007-02-06 19:23:42 [---] Visit http://boinc.berkeley.edu for instructions

```

---

### Post by rofarmer on 2007-02-06
You can get the package from setiathome.berkeley.edu

I changed it to Desktop, and the sh command DID something. but now it tells me to do something else

run /home/myname/Desktop/BOINC/run_client

I changed to that directory, but how to "run" the run_client escapes me.

---

### Post by rofarmer on 2007-02-06
Another intuitive command.  I added the dot-slash and the run_client now operated, but gave a long list of **GUI RPC bind failed**.

---

### Post by ComplexNumber on 2007-02-06
> **rofarmer said:**
> You can get the package from setiathome.berkeley.edu

I changed it to Desktop, and the sh command DID something. but now it tells me to do something else

run /home/myname/Desktop/BOINC/run_client

I changed to that directory, but how to "run" the run_client escapes me.
ok, here's what i did after downloading the file, firing up the terminal, then cd-ing to where the downloaded file(ie boinc_5.4.11_i686-pc-linux-gnu.sh)  is:
-i right clicked on the file and set the execute tickbox that i mentioned about earlier.
-i then entered: **./boin*   **(NOTE: you can use wildcards so you don't have to type the whole name out)
-in the same directory where the file is, a new directory was created by the application after running it called 'BOINC'
-i then cd'd into that directory.
-i double clicked on run_client. it brought up a dialogue. select 'run'. it then created some new files.
-i then double clicked on run_manager. after that, you will see the following in the screenshot.

---

### Post by kevinlyfellow on 2007-02-07
> **rofarmer said:**
> Another intuitive command.  I added the dot-slash and the run_client now operated, but gave a long list of **GUI RPC bind failed**.

[http://boinc.berkeley.edu/dev/forum_thread.php?id=1333](http://boinc.berkeley.edu/dev/forum_thread.php?id=1333)
Your not the only one with this problem... unfortunatly I couldn't find a solution.  One thing that you can try is to enable your universe repos and install it through synaptic.

btw, another way to run files is by using the command
```
sh program
```

---

### Post by Feenix3k on 2007-04-07
> **kevinlyfellow said:**
> Don't be so frustrated... its one of those things where the more experience you have with another os, the harder it is to change gears.  Give yourself some time, you'll get the hang of it!  I grew up with dos, but I switched to linux, and now I find dos so cryptic that its unusable (just using dosbox gives me a headache now!)  

anyways, .sh stands for shell (shell script, kinda like old batch files that have a set of instructions that you can use in your shell).    Open it up with a text editor (vi, nano, or gedit) and take a look at what's inside even if you don't understand anything, but do look for some commands you know.   Sometimes they have binary in them, so if you can't open it up, don't worry.  [edit: I checked this out and it is indeed in binary]

You need to change the permissions of the file before it will allow you to run the set of commands.  This is a security feature.  To change them, you can use the terminal and do the chmod (change modifiers) thing, or you can do it graphically.  

Well, I know I didn't help solve the problem, but hopefully I provided some insight as to your situation.  Don't expect to learn everything right off the bat, but once you do learn it, you will love it!

[edit]  I tried it out for myself, and this is what happened
```

kevinly@ubuntu:~$ chmod 755 Desktop/boinc_5.4.11_i686-pc-linux-gnu.sh
kevinly@ubuntu:~$ ./Desktop/boinc_5.4.11_i686-pc-linux-gnu.sh
now run /home/kevinly/BOINC/run_client to run the client and /home/kevinly/BOINC/run_manager to run the GUI
kevinly@ubuntu:~$ cd /home/kevinly/BOINC/
kevinly@ubuntu:~/BOINC$ ./run_client
2007-02-06 19:23:42 [---] Starting BOINC client version 5.4.11 for i686-pc-linux-gnu
2007-02-06 19:23:42 [---] libcurl/7.16.0 OpenSSL/0.9.8d zlib/1.2.3
2007-02-06 19:23:42 [---] Data directory: /home/kevinly/BOINC
2007-02-06 19:23:42 [---] Processor: 2 GenuineIntel Genuine Intel(R) CPU    T2300  @ 1.66GHz
2007-02-06 19:23:42 [---] Memory: 1002.28 MB physical, 854.98 MB virtual
2007-02-06 19:23:42 [---] Disk: 54.19 GB total, 36.72 GB free
2007-02-06 19:23:42 [---] No general preferences found - using BOINC defaults
2007-02-06 19:23:42 [---] Local control only allowed
2007-02-06 19:23:42 [---] Listening on port 31416
2007-02-06 19:23:42 [---] This computer is not attached to any projects
2007-02-06 19:23:42 [---] Visit http://boinc.berkeley.edu for instructions

```



The above works fine, but I got an error saying I neede GLIBC_2.4. What is it?

feenix@James-Laptop:~$ cd ~/Desktop
feenix@James-Laptop:~/Desktop$ chmod 755 boinc_5.4.11_i686-pc-linux-gnu.sh
feenix@James-Laptop:~/Desktop$ ./boinc_5.4.11_i686-pc-linux-gnu.sh
now run /home/feenix/Desktop/BOINC/run_client to run the client and /home/feenix /Desktop/BOINC/run_manager to run the GUI
feenix@James-Laptop:~/Desktop$ cd /home/feenix/BOINC
feenix@James-Laptop:~/BOINC$ ./run_client
./boinc: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required b y ./boinc)
feenix@James-Laptop:~/BOINC$

---

