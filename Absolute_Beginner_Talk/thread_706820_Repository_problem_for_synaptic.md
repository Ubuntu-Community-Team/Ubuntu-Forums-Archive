---
title: "Repository problem for synaptic"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by aborigine on 2008-02-24
I have a CDROM drive (cdrom0 in the hardware database) and a DVDROM drive (cdrom1) on the same machine - its to do with the age of the machine...
My problem is this I want to install some of the kit on Ubuntu Studio (DVD) synaptic has recognized its existence BUT insists that it should be in what I suppose is its default drive, the CD drive.
My machine is offline so I cannot use internet repositories.
Either I need to know what to tell the repository register so it goes and looks in the DVD drive instead or change the default drive of synaptic so it goes looking for everything in the DVD drive

Another thought - is synaptic working through some sort of server ? If so what is the linux version of [http://localhost](http://localhost)... (I only know this from using XAMPP in windows)?

I am an ABSOLUTE beginner so its no good getting too geeky !! -

---

### Post by warbird on 2008-02-24
you should be able to add it using this command:
apt-cdrom -d /dvddrive/mount/path add

edit: this should be run in the terminal (applications -> accessories -> terminal)

---

### Post by seventhc on 2008-02-24
If I understand you correctly, you want to add your cd drive to the repositories.
If thats the case go to
System>Administration>Software Sources
put a check where it says cd...look on the lower part, you should see it there. :)
Hope that helps.
Let me know if it works for you.

---

### Post by warbird on 2008-02-24
> **seventhc said:**
> If I understand you correctly, you want to add your cd drive to the repositories.
If thats the case go to
System>Administration>Software Sources
put a check where it says cd...look on the lower part, you should see it there. :)
Hope that helps.
Let me know if it works for you.

thats only from the official install cd, i think. he needs to add a new source (see my post)

---

### Post by seventhc on 2008-02-24
I thought the dvd was official, they sell sets like that for people with no connection, wouldn't that be the same??
I think it's like 6 dvd's with the full repositories included.
Edit: But after rereading both posts, my way won't work..looks like it's looking in the wrong place regardless of the fact if it's official or not.
so your way looks like it would be the way to go.

---

### Post by warbird on 2008-02-24
> **seventhc said:**
> I thought the dvd was official, they sell sets like that for people with no connection, wouldn't that be the same??
I think it's like 6 dvd's with the full repositories included.
Edit: But after rereading both posts, my way won't work..looks like it's looking in the wrong place regardless of the fact if it's official or not.
so your way looks like it would be the way to go.

I meant its only the original install CD/DVD thats listed there. He can't add new ones through that interface (afaik)

---

### Post by aborigine on 2008-02-25
There seems to be a question about the sources of the cds... They are downloaded images which ARE recognized by synaptic - the problem is that Synaptic won't recognize the DVD player as a legitimate source for the data.
Thanks everyone for the help so far !

---

### Post by seventhc on 2008-02-25
Here is something you might want to try, go back into the *Software Sources*, choose *Third Party Software* (second tab) on the bottom there is a button to *Add CD-ROM*

---

### Post by aborigine on 2008-02-25
I've done that. 
As I said the problem is not *recognizing* the existance of the dvd, its getting the thing to understand that I have two drives (dvds didn't exist when I got the machine so it was added later...) 
Synaptic says that Ubuntu Studio is on the system - the packages are in its database as available for installation, **_but _**when I go to install software it tells me to put the dvd in the cdrom drive, where it will not be possible to read it. If I leave it in the dvd drive it tells me it can't find it ... and so on !
I've thought of copying the whole thing to hard drive, but then again I'm not sure how to configure synaptic to go looking for it. The problem is that, as far as I can see, either you put in a web address or a CD, there is nothing in the documentation for local, offline repositories - and yes, allright, I have a hardware configuration which shouldn't happen !!

---

### Post by seventhc on 2008-02-25
OK, I didn't know you tried the third party tab, could you post the output of this command, just to see what it says there.
```
cat /etc/apt/sources.list
```
also have you tried the way posted above by **warbird**?

---

### Post by aborigine on 2008-03-04
I've tried all the suggestions here... - and I downloaded the Debian how to file. For some reason apt refuses to accept the second drive. So I'm laboriously copying the files into a local directory and will try building a local repository that way...
Thanks for trying !!

---

### Post by plucky on 2008-03-04
aborigine,

How are you with hardware? Try making the DVD drive the master drive and the CD drive the slave drive by changing the jumpers on the back of the drives.Especially if the jumpers are set as cable select.

Good luck.

---

### Post by anewguy on 2008-03-04
Just for grins, tried this myself.  I have the CD-RW drive as the master and the DVD drive as the slave.  When I put even just a distribution CD in the DVD drive, it is not recognized.  Additionally, as you mentioned, I can't "add" the DVD drive - it just wants a CD drive.  I'm running Gutsy.  I'll be watching this thread for a solution!  :)

---

### Post by aborigine on 2008-03-06
That is exactly the configuration I have - and I was told when I installed the DVD that the CD-RW had to be master to function properly...
Now there are two of us watching ... and waiting... !!

---

### Post by plucky on 2008-03-06
aborigine,

I meant for **you** to try it to see if it fixes your problem with using the Ubuntu Ultimate DVD as a repository.


Goodluck.

---

### Post by seventhc on 2008-03-06
you might try opening a terminal and putting this in
```

apt-cdrom
```
Then you will see a list of option, one of which is add...mount point, etc.
Not sure if this will help or not, but I don't think you've tried it yet.

---

### Post by aborigine on 2008-03-10
I've tried all the solutions so far proposed without luck
However someone told me that it is possible to copy an image of the cd into a directory and from there mount a virtual drive - he didn't tell me how to do it...
Anyone know [LIST=1]
[*]What does this mean ?
[*]How you do it ?
[*]Would it work?
[/LIST]
Or should I start another thread ?

---

### Post by aborigine on 2008-03-17
It works !!
It doesn't cure the problem of getting synaptic to recognize 2 cd drives but it DOES give you a highly efficient work round (except it eats your memory) - there is a nice little package that gives you a visual frontend for the code, but you can do it in the console. I can't find the link, but I will come back and post when I do.

---

### Post by aborigine on 2008-03-18
Now I have the links !
Go here [http://packages.ubuntu.com/gutsy/utils/gmountiso]("http://packages.ubuntu.com/gutsy/utils/gmountiso") to get the packet "GmountISO" and here [http://tuxenclave.wordpress.com/2007/12/01/gmount-iso-virtual-drive-for-linux/ ]("http://tuxenclave.wordpress.com/2007/12/01/gmount-iso-virtual-drive-for-linux/")to see what it looks like. Dpendencies, if not installed, are on the Ubuntu disk.
In the first field you point the system at the image file, the second you click browse and it will show available hardware emulations : choose "cdrom". Click "Mount" and you're in.
As long as the application is running, you can mount and unmount to your hearts content...

---

