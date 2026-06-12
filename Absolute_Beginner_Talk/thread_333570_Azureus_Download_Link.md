---
title: "Azureus Download Link"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by PiggiePaul on 2007-01-07
Simple Request from a Linux/Ubuntu newbie.

Could anyone give me a simple download link to the latest/best version of Azureus for Ubuntu?

Thanks

---

### Post by taurus on 2007-01-07
[http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)

---

### Post by PiggiePaul on 2007-01-07
> **taurus said:**
> [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)

Thanks. I did look there earlier, but unsure what I actually needed to download.

Is it the JAR file I need?

Sorry, but this is day 1 on my Ubuntu/Linux learning curve.

---

### Post by madmetal on 2007-01-07
since you are new i suggest deluge..
open synaptic ( system >> management >> synaptic ) search it and install it..
simple and good..

---

### Post by PiggiePaul on 2007-01-07
> **madmetal said:**
> since you are new i suggest deluge..
open synaptic ( system >> management >> synaptic ) search it and install it..
simple and good..

Thanks.
I just need to make sure I download the right file in the 1st place.

Is it the JAR file I need?

---

### Post by taurus on 2007-01-07
There are two versions for Linux:  Linux & Linux AMD64.  You want the Linux which is a .tar.bz2 so you just have to unpack it where you want to install it.

[http://prdownloads.sourceforge.net/azureus/Azureus_2.5.0.0_linux.tar.bz2?download](http://prdownloads.sourceforge.net/azureus/Azureus_2.5.0.0_linux.tar.bz2?download)

---

### Post by PiggiePaul on 2007-01-07
> **taurus said:**
> There are two versions for Linux:  Linux & Linux AMD64.  You want the Linux which is a .tar.bz2 so you just have to unpack it where you want to install it.

[http://prdownloads.sourceforge.net/azureus/Azureus_2.5.0.0_linux.tar.bz2?download](http://prdownloads.sourceforge.net/azureus/Azureus_2.5.0.0_linux.tar.bz2?download)

Thanks.
Yes, I just downloaded that file you mentioned.

I unpacked it into a folder.
I was just wondering is you need to "Install it" as it were.

You know, like with Windows apps, you get the installer which installs the program for you.

That "Synaptic" thing just seems to browse my CD.

---

### Post by Frak on 2007-01-07
you try removing the CD from your sources.lst?

---

### Post by taurus on 2007-01-07
After you unpack it with 

```
tar xvjf Azurues_2.5.0.0_linux.tar.bz2
```
you will see a new directory called azureus.  Change to that directory and run it with

```
cd azureus
./azureus
```

p.s.  Make sure you have a working java first because if you don't, it will exit with error message.

```
java -version
```

---

### Post by PiggiePaul on 2007-01-07
> **taurus said:**
> After you unpack it with 

```
tar xvjf Azurues_2.5.0.0_linux.tar.bz2
```
you will see a new directory called azureus.  Change to that directory and run it with

```
cd azureus
./azureus
```

p.s.  Make sure you have a working java first because if you don't, it will exit with error message.

```
java -version
```


Thanks, I managed to upack it to a folder of my choise just using the Ubuntu windows front end.

Coming from Windows (where you put programs in a folder called "Program Files"

On Linux, which folder/directory should you put programs into?

---

### Post by Frak on 2007-01-07
should go into Applications->Internet or if its not there, go to the Terminal and type azureus

---

### Post by taurus on 2007-01-07
Anywhere in your $HOME directory but I usually put the binaries/programs (for personal use) in ~/bin.

```
mkdir ~/bin
```

---

### Post by PiggiePaul on 2007-01-07
> **taurus said:**
> Anywhere in your $HOME directory but I usually put the binaries/programs (for personal use) in ~/bin.

```
mkdir ~/bin
```

Thanks.

---

