---
title: "[SOLVED] using the terminal to install a downloaded file"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by littletinman on 2008-02-15
ok, i'm trying to install Enemy Territoroy with the terminal. and trying to fallow these instructions.

To install go to Applications->System Tools->Root Terminal
Navigate to wherever you downloaded the file.
Simply run the file (./et-linux-2.56-2.x86.run)
and it should bring up a GUI to help you through the process. I pretty much kept everything as default


My file is "et-linux-2.60.x86.run" (without " of course) and it's located in my home folder. which in my case is called "philip".   So what do i need to put into the terminal so that it will run the file from there? It's got me a little confused.

---

### Post by akiratheoni on 2008-02-15
Try:
```
sudo bash ./et-linux-2.60.x86.run
```

It will prompt you for your password so type it in then it will install and you can continue the installation process.

---

### Post by littletinman on 2008-02-15
it started to work then i got this. 

philip@philip-laptop:~$ sudo bash ./et-linux-2.60.x86.run
[sudo] password for philip:
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install..............................................................................................................................................................................................................................................................................................................................
./setup.sh: 278: /home/philip/.setup12834: not found
./setup.sh: 289: /home/philip/.setup12834: not found
philip@philip-laptop:~$

---

### Post by akiratheoni on 2008-02-15
It's running the script fine I think --- now I think that might be a problem with the installer, not my command I gave you. You'll have to ask someone else. Sorry.

---

### Post by neurostu on 2008-02-15
Did you just pull the .run file out of the archive or did you un tar (unzip) the entire archive?

---

### Post by littletinman on 2008-02-15
Thanks anyways. So who else can help?

---

### Post by James Little on 2008-02-15
Try running
```
updatedb
locate .setup12834
```

to see if that file is somewhere else.

---

### Post by littletinman on 2008-02-15
i just ran it straight from the download. here is what your code got.

philip@philip-laptop:~$ updatedb
updatedb: fatal error: You are not authorized to create a default slocate database!
philip@philip-laptop:~$ locate .setup12834
philip@philip-laptop:~$

---

### Post by James Little on 2008-02-15
sorry, try 
```
sudo updatedb
```
and enter your password when prompted

---

### Post by neurostu on 2008-02-15
When you downloaded the file did it come in a tar.gz file or did you download a .run file?  If it came in a tar.gz did you remove just the .run file or everything?

if you didn't untar the file try:
```

$tar -xvzf <filename>.tar.gz

```
it will then create a directory named: <filename>

go into that directory and try sudo bash ./<run_me_file_name>.run

---

### Post by littletinman on 2008-02-15
since i had already entered the password it just blinked for a couple seconds then went back to the normal ~$ thing. I tryed installed again but no luck.

---

### Post by littletinman on 2008-02-15
I downloaded the .run file straight.

---

### Post by James Little on 2008-02-15
Sounds like you're missing a lot of files as someone else has mentioned. The .run file can't be the only file needed to install the game, it just runs the installation script, which will look for loads of other files. Did you download a large (probably hundreds of megs) archive?

---

### Post by littletinman on 2008-02-15
yes. i'm going to try a run file that is an earlier version that i have on a disk. The file is called "et-linux-2.55.x86.run" what should i put in the terminal for that?

---

### Post by James Little on 2008-02-15
change to the directory which contains the run file and type 
```
./et-linux-2.55.x86.run
```

Do you have the game on a cd/dvd?

---

### Post by littletinman on 2008-02-15
I tried with the old file and now get this.

philip@philip-laptop:~$ sudo bash ./et-linux-2.55.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
This installation doesn't support glibc-2.0 on Linux / unknown
(tried to run setup)
See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting
The setup program seems to have failed on unknown/glibc-2.0

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting
philip@philip-laptop:~$

---

### Post by littletinman on 2008-02-16
ok, never mind. It worked. Wierd. I triyed the second posters idea a couple hours later it's now up and running. With no sound though. i'm going to look at previous posts for that. thanks all.

---

