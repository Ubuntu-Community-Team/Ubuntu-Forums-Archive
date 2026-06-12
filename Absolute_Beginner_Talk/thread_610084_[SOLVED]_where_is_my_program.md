---
title: "[SOLVED] where is my program?"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Da King on 2007-11-11
I installed an alien software " NETOP sys"..which was for linux and acording to the terminal...everything well..now i cant see the program i installed..where do i get it?

---

### Post by Pumalite on 2007-11-11
In Terminal:

locate <file>

---

### Post by Da King on 2007-11-11
i did, it located the installation files on  the desktop folder rather..it was an rpm so i dont know if after installing the program name is going to change or remain the same..i need it to be able to see the desktops and control the pc's of my students moro.

---

### Post by kwacka on 2007-11-11
1. try typing NETOP in a terminal & see if it starts up (or press ALT +F2 and type NETOP in the box).

2. type 'locate NETOP' in a terminal and it will show you where all files/directories have the name NETOP.

3. type 'man NETOP' in a teminal and see what comes up.

I've used google to look for an application called 'netop' but found nothing. Could it be 'nettop'?

If it is nettop  take a look at jNettop, its in the Ubuntu universe repository, will this do what you want?

---

### Post by Da King on 2007-11-11
i tried all the above and yet no luck... actually the file i download had a name like this ```
NetOpGuest-8.00-2005.062.i386.rpm
``` and installed it with the "install alien command.

if this doesnt help how do i set up remote desktop and control the other pc's on my LAN (they r on windows ) or is there any software in place of this [http://www.netop.com/netop-13.htm]("http://www.netop.com/netop-13.htm")

---

### Post by kwacka on 2007-11-11
Try 'locate NetpOpGuest'

I looked at the netop site, I assume 'guest' is their trial. You mentioned students, so I made the assumption that you wanted netop school - the requirements for this (teacher & student) are Windows machines.

If you can tell us exactly what you are after, maybe we can sort somthing out between us. e.g. vnc?

---

### Post by Da King on 2007-11-11
> **kwacka said:**
> Try 'locate NetpOpGuest'

I looked at the netop site, I assume 'guest' is their trial. You mentioned students, so I made the assumption that you wanted netop school - the requirements for this (teacher & student) are Windows machines.

If you can tell us exactly what you are after, maybe we can sort somthing out between us. e.g. vnc?

I am looking for the REMOTE CONTROL..that one works better..i have the host installed on network pc's so i need the GUEST to control them..i download the linux edition which came in the UK.tar form..i extracted the files to my desktop and had the files on my desktop..so i used the terminal to 

```
sudo apt-get alien
cd desktop
sudo apt-get install alien -i NetOpGuest-8.00-2005.062.i386.rpm
```

everything went through and now i cant find where it installed it.

---

### Post by whitewizardcoder on 2007-11-11
Try opening the rpm file with file-roller (the archive manager).  Traverse the directories inside of file-roller until you find a binary file.  The folder that it's in in file-roller is the directory where the binary file is on your filesystem.  Use the terminal to cd to that directory and execute the program using
```
./<program_name>
```

where <program_name> is the name of the file that you found inside the rpm file.

Hope this helps!

---

### Post by Da King on 2007-11-11
> **whitewizardcoder said:**
> Try opening the rpm file with file-roller (the archive manager).  Traverse the directories inside of file-roller until you find a binary file.  The folder that it's in in file-roller is the directory where the binary file is on your filesystem.  Use the terminal to cd to that directory and execute the program using
```
./<program_name>
```

where <program_name> is the name of the file that you found inside the rpm file.

Hope this helps!

ok i did what u said..the rpm was in a forlder with a folder (usr & bin) so i went in the system folder and into the bin..i found it in the bin..i double click and nothing happens..i tried the ALT+F2 and run it,,when typing it give u the correct name as it shod appear (NetOpGuest)  bt when i run it nothing happens. 

or shod i adapt to VMware? is it a good choice cose PCANYWHERE is sold and i alreay have the keys of the NetOp so reinstalling in windows wont worry. is VM very big...i donno bt it seems i have installed soo many stuffs cos of this dependencies especially trying to get compiz work on my intel 82815 graphic :(

---

### Post by whitewizardcoder on 2007-11-11
> **Da King said:**
> ok i did what u said..the rpm was in a forlder with a folder (usr & bin) so i went in the system folder and into the bin..i found it in the bin..i double click and nothing happens..i tried the ALT+F2 and run it,,when typing it give u the correct name as it shod appear (NetOpGuest)  bt when i run it nothing happens. 

or shod i adapt to VMware? is it a good choice cose PCANYWHERE is sold and i alreay have the keys of the NetOp so reinstalling in windows wont worry. is VM very big...i donno bt it seems i have installed soo many stuffs cos of this dependencies especially trying to get compiz work on my intel 82815 graphic :(

Try running the program in the terminal to see if you get any output from it and to make sure it runs.  If any error messages appear in the terminal, post them here.  If the program doesn't run, make sure it is flagged as executable.  To do this:
```
sudo chmod +x /usr/bin/NetOpGuest
```
and try it again.

Hope this helps!

---

### Post by Da King on 2007-11-12
Well i tried i got this error message
```

king@King:~$ NetOpGuest
NetOpGuest: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open 
shared object file: No such file or directory
king@King:~$
```
i run it in the run manager(ALT+F2) and nothing happends.

---

### Post by whitewizardcoder on 2007-11-12
> **Da King said:**
> Well i tried i got this error message
```

king@King:~$ NetOpGuest
NetOpGuest: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open 
shared object file: No such file or directory
king@King:~$
```
i run it in the run manager(ALT+F2) and nothing happends.

You're missing a dependency.  To fix this, run
```
sudo apt-get install libstdc++2.10-glibc2.2
```

This will install the necessary library file.  Hopefully your program should run now!

---

### Post by Da King on 2007-11-12
Thanks very much..its fixed now..u think my windows lincense will work on their linux endition?

---

### Post by whitewizardcoder on 2007-11-12
> **Da King said:**
> Thanks very much..its fixed now..u think my windows lincense will work on their linux endition?

Glad I could help out!  As for the license, i'm not familiar with the program so I don't know how their licensing works.  If your Windows license doesn't work I would contact the producers of the software and see if they can supply you with one that works, seeing as you already have a valid license.

---

### Post by Da King on 2007-11-13
well it someway took the lincense not knowing its a version 9 and the one on linux is an 8 version..well im still searching for a version 8 host for my windows pc's otherwise its a "COS-90" job:lolflag:... am suffering about this progam becos i donno if remote access will work on my windows from my linux desktop. or does ubuntu have a remote control program which can control my other window pc's? 

Yet still thanks soo much for your help.

---

### Post by kwacka on 2007-11-13
Does NX from 'NoMachine' look to be of any use?

[http://www.nomachine.com/](http://www.nomachine.com/)

---

### Post by Da King on 2007-11-13
> **kwacka said:**
> Does NX from 'NoMachine' look to be of any use?

[http://www.nomachine.com/](http://www.nomachine.com/)

Oh thanks soo much..im downloading it now..hope it works great on my windows..all the same thanks for been there for me \\:D/

---

### Post by whitewizardcoder on 2007-11-13
> **Da King said:**
> or does ubuntu have a remote control program which can control my other window pc's?

Ubuntu has a remote desktop client built in, but it's kinda hard to find if you don't know where to look.  Press Alt-F2 and run "tsclient".  You can connect to a remote computer using several different protocols, including VNC and RDP (the one used by Windows Remote Desktop).

---

### Post by Da King on 2007-11-13
i did download the NX..bt when i try to install i get this message
```
Error:Dependency is not satisfiable:nxclient
``` what does that mean?

---

### Post by Da King on 2007-11-13
> **whitewizardcoder said:**
> Ubuntu has a remote desktop client built in, but it's kinda hard to find if you don't know where to look.  Press Alt-F2 and run "tsclient".  You can connect to a remote computer using several different protocols, including VNC and RDP (the one used by Windows Remote Desktop).

yea i think urs might work cos i tried the remote connection and it got the windows screen login just had an error about account restriction....will have to try and find out more about it..if NX machines fail me i will have to use the Terminal client. Thanks a lot tho for ur help..i really appreciate it.

---

### Post by Da King on 2007-11-14
Thanks soo much everyone for your timing and dedication to my post..now i dont need to get VMware to use these...TSCLIENT worked amazingly. hey i got the beer's just bring the :popcorn: and lets have some:guitar:


:lolflag:1luv man!!

---

