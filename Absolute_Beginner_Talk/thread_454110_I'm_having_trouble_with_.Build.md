---
title: "I'm having trouble with ./Build"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by powergod on 2007-05-25
I'm trying to start up my MUD but I'm having difficulties with ubuntu. I never had this problem when I started my MUD with Linux before-back when I ran a MUD remotely at betterbox - FYI.
This is what I see after I do ./build.MudOS

Trying out some stuff to see what works; ignore errors ...
./build.MudOS: 138: gmake: not found
make: Nothing to be done for `nothing'.
./build.MudOS: 149: xlc: not found
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
./build.MudOS: 193: clcc: not found
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
FATAL ERROR: Cannot find a C compiler

---

### Post by skug on 2007-05-25
```

Trying out some stuff to see what works; ignore errors ...
./build.MudOS: 138: gmake: not found
make: Nothing to be done for `nothing'.
./build.MudOS: 149: xlc: not found
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
./build.MudOS: 193: clcc: not found
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
FATAL ERROR: Cannot find a C compiler

```

Since Ubuntu does not have a compiler by default you have to install a C compiler to get it working. to this by installing build-essentials using:
System->Administration->Synaptic Package Manager. Then search for build-essentials package and any other package that might be useful i.e xlc. 

hope this helps...

---

### Post by powergod on 2007-05-25
I checked and Ubuntu does have a c compiler called 'GNU C Compiler'. I doin't know what to do at this point. Will someone please help me?

---

### Post by Seisen on 2007-05-25
That's because its part of build-essential just like skug was talking about. In Synaptic search for "build-essential"
or in a terminal type this

```
sudo apt-get install build-essential
```

---

### Post by powergod on 2007-05-25
Sorry to be off the subject but before I continue, can someone tell me how to signup for irc. I've looked everywhere and have had no luck.

---

