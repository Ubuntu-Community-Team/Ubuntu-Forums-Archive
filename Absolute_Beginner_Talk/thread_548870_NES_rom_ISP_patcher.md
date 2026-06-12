---
title: "NES rom ISP patcher"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by MS-DOS4 on 2007-09-11
Hello, I want to patch a mario bros NES rom so I can play the hack. I was wondering if anybody knew of a good NES rom patching software for linux.

---

### Post by nonewmsgs on 2007-09-12
it's ips, and im looking right now....

---

### Post by nonewmsgs on 2007-09-12
[http://os4depot.net/index.php?function=showfile&file=utility/filetool/uips.lha](http://os4depot.net/index.php?function=showfile&file=utility/filetool/uips.lha)

but you'll have to "make" it.

---

### Post by Zeikcied on 2007-10-01
> **nonewmsgs said:**
> [http://os4depot.net/index.php?function=showfile&file=utility/filetool/uips.lha](http://os4depot.net/index.php?function=showfile&file=utility/filetool/uips.lha)

but you'll have to "make" it.

I'm looking for an IPS patcher, as well.

I tried that, but I couldn't get it to work.  I followed the directions, but that got me nowhere.  If it actually compiled properly, it sure as heck didn't work.  Kubuntu kept telling me that the command doesn't exist, even after I moved the binary to /usr/bin.

Isn't there any other program that supports IPS?  I tried a few Windows-based IPS patchers in Wine, and they don't work properly.  They either don't run, or they crash during the patching process.

---

### Post by gilforsyth on 2008-06-07
This worked for me -- 

You will need to install some packages first:
```
sudo apt-get install gcc build-essentials lha
```

Now download [uips.lha]("http://os4depot.net/share/utility/filetool/uips.lha")

--

Go to the console and browse to your download directory or wherever you put uips.lha
```
lha e uips.lha
```
This command will extract all the files into the current directory

--

Now, browse to the "Source" folder in the console and compile uips.
```
gcc uips.c -o uips
```
I just named it uips for consistency but anything is ok.  
You'll probably get a warning or two but it's no biggie.  

--

Now, to use your new patcher
```
./uips game.nes patch.ips
```
This assumes that the patch and the rom are in the same folder as uips, if not, you'll have to put in the location of the rom and patch, i.e.
```
./uips /home/user/game.nes /home/user/patch.ips
```

Last, the patcher will irreversibly patch the rom, so make a copy first.  You won't get the original game back.  

Hope that helps.

---

