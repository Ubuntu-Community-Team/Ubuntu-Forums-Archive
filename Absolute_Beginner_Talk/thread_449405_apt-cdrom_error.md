---
title: "apt-cdrom error"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by meatus on 2007-05-20
For some reason I can't add the cd to the repositories. When i perform sudo apt-cdrom add it asks me to insert the disk, even though it's inserted and recognised by ubuntu elsewhere. 

Does anyone know what could be causing this? It is preventing me from installing build-essential, which I need to compile ndiswrapper, to get on the internet, hence I need the cd.

Thanks in advance,

---

### Post by AlexenderReez on 2007-05-20
for me aptoncd works fine....

---

### Post by Outrunner on 2007-05-20
I'm not sure if this will solve your problem, but try ejecting and reinserting the CD. This is assuming you haven't tried this already.

---

### Post by meatus on 2007-05-20
> **Outrunner said:**
> I'm not sure if this will solve your problem, but try ejecting and reinserting the CD. This is assuming you haven't tried this already.
Yeah I've tried this, and I tried taking the disc out until it asks for it, then putting it in, to no avail.

---

### Post by meatus on 2007-05-20
Also, when i was trying to compile dpkg from source, when i ran ./configure it was all fine except the last output, which said the GNU C compiler cannot create executables, how can I remedy this?

---

### Post by seshomaru samma on 2007-05-20
just a wild suggestion
maybe you can browse the CD with nautilus and look for the package yourslef
not sure if it is there as a deb.

---

### Post by taurus on 2007-05-20
> **meatus said:**
> Also, when i was trying to compile dpkg from source, when i ran ./configure it was all fine except the last output, which said the GNU C compiler cannot create executables, how can I remedy this?

Is your machine connected to the internet?  And are you sure you insert the same CD that you used to install it?

---

### Post by abhishek456 on 2007-05-20
Yes the packages are available in .deb format

Built essentail packages are available in > /media/cdrom0/pool/main/b/build-essential replace cdrom0 with ur cdrom1 if ur using second cd/dvd rom.

Best of luck

---

### Post by meatus on 2007-05-20
Yeah the deb is on the CD, but it says it has dependencies on libc6-dev and libc6, which won't install through apt-get, for a variety of reasons. 

> **taurus said:**
> Is your machine connected to the internet?  And are you sure you insert the same CD that you used to install it?

No it's not connected to the internet, and no the disk is different, as I used [wubi](http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html) to install it, so should I use the alternate image that wubi uses to install?

---

### Post by meatus on 2007-05-20
Bump :(

---

### Post by abhishek456 on 2007-05-20
search  libc6 on the Cd drive or 

why don't you download those to the system you are presently using(from which ur posting) and transfer over there

---

### Post by meatus on 2007-05-20
> **abhishek456 said:**
> search  libc6 on the Cd drive or 

why don't you download those to the system you are presently using(from which ur posting) and transfer over there

libc6-dev isn't on the cd, and I couldn't compile it because of the error i stated earlier about the compiler not being able to create executables.

---

### Post by taurus on 2007-05-20
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by meatus on 2007-05-20
> **taurus said:**
> Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

not until i boot back into ubuntu tomorrow, but it is as standard, except i removed the #'s from in front of the CD, but in the synaptec manager and in the terminal it says that the CD cannot be added with apt-get. 

Does it make a difference that my ubuntu was installed with the alternate image, and I'm using the regular cd for the apt-cdrom command? I will burn the alternate image and see if it makes a difference.

---

### Post by meatus on 2007-05-20
How do you all get files from linux to windows? USB pen?

---

### Post by seshomaru samma on 2007-05-22
yes

---

