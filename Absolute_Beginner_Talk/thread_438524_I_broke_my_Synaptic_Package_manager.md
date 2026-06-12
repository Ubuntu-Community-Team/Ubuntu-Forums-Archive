---
title: "I broke my Synaptic Package manager"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by VampiricuS on 2007-05-09
Hello and thanks for reading.
   I was trying to add a repository and apparently i added it wrong. as the following:

deb [http://medibuntu.sos-sts.com/repo/pool/feisty/free/](http://medibuntu.sos-sts.com/repo/pool/feisty/free/) main

when i hit reload i got an error and it closed. Now whenever I try to open the manager i get this error:

E: Malformed line 45 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

and then the manager closes.

I was trying to follow a tutorial on how to play dvd's basically. 
Please can someone guide me to fix my manager. thank you

btw i was trying to follow this tutorial:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by icechen1 on 2007-05-09
Try remove the new source from the source list,is it fixed now?

---

### Post by BHelts on 2007-05-09
```
gksudo gedit /etc/apt/sources.list
```
and either comment out using # at the front of each line or delete each line that refers to medibuntu.
Give that a whirl

---

### Post by Iokua on 2007-05-09
Open a terminal window and type:

```
gksudo gedit /etc/apt/sources.list

```

Then delete the wrong entry. Save the file. And try Synaptic again.

---

### Post by VampiricuS on 2007-05-09
how do i know what is the wrong entry?

total newb here when it comes to editing linux files

---

### Post by VampiricuS on 2007-05-09
i deleted 

deb [http://medibuntu.sos-sts.com/repo/pool/feisty/free](http://medibuntu.sos-sts.com/repo/pool/feisty/free) main

which was the last line. thank you very much, wasnt as bad as i thought. i hope all my problems are that easy ;)


now if i can only get my dvd's playing. minus the breaking stuff :P

---

### Post by opus on 2007-05-09
Try changing that line to this:
```
deb http://medibuntu.sos-sts.com/repo/pool/feisty/free/ feisty main
```

Use the "sudo gedit /etc/apt/sources.list" or edit it from Synaptic.

Aaron Throckmorton

---

### Post by VampiricuS on 2007-05-10
what will that do for me? I have already removed the line.

---

### Post by opus on 2007-05-10
If you need that repository for a software package you installed/want to install then you can use that modified line.  Otherwise you can leave it out.  Either way.  :)

Aaron

---

### Post by Iokua on 2007-05-10
You know, I think it's kind of silly that Synaptic doesn't have a failsafe mechanism for a corrupted sources.list file. In making Ubuntu more user friendly, there should definitely be a way to get Synaptic up and running without having to manually edit files. Is anyone aware of such a proposal for future releases?

---

