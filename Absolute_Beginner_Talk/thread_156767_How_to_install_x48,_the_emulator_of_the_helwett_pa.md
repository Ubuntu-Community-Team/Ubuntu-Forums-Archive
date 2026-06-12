---
title: "How to install x48, the emulator of the helwett packart HP48GX ?"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-04-07
Hi, 

===
In order to install the HP48 on your Linux box, I can give you a easy script that can maybe help some of you:
  
```

cd /tmp
wget -N http://patrick295767.sitesled.com/miniram/installation-x48.sh
sudo sh /tmp/installation-x48.sh

``` ([script]("http://patrick295767.sitesled.com/miniram/installation-x48.sh"))

You just need to dump the rom, from the HP48 machine you bought and own !!, and copy it into your ~/.hp48/rom
(illegal rom dump are illicit)

Greetings
  
===
Screenshots:
[http://www.area48.com/](http://www.area48.com/)
[http://www.geocities.com/SiliconValley/Bay/9540/emul48.html](http://www.geocities.com/SiliconValley/Bay/9540/emul48.html)
ref:
[http://developer.berlios.de/projects/x48/](http://developer.berlios.de/projects/x48/)

---

### Post by trent dillman on 2006-04-07
Is it in the repos? If so, use Synaptic.

If not, d/l the source and read the README and INSTALL files.

---

### Post by patrick295767 on 2006-04-07
not in repos...


1/ i dowload the bin of x86

2/ i copied to /usr/local/bin
 
3/ i got the rom 

4/ and made the chmod 

to get the x86: [http://membres.lycos.fr/patrick295767/linux/data/HP48GX/x48-041f.tar.gz](http://membres.lycos.fr/patrick295767/linux/data/HP48GX/x48-041f.tar.gz)
to get the rom : [http://membres.lycos.fr/patrick295767/linux/data/HP48GX/x48-gxrom-r.tar.gz](http://membres.lycos.fr/patrick295767/linux/data/HP48GX/x48-gxrom-r.tar.gz)



I did this but it keeps saying that x86 cannot be runned


[QUOTE=trent dillman]Is it in the repos? If so, use Synaptic.

If not, d/l the source and read the README and INSTALL files.[/QUOTE]
  
```
Installation Notes:

   1. Obtain x48-gxrom-r.tar.gz or x48-sxrom-e.tar.gz and extract into your home directory (usually /home/zaurus).  E.g.:

      cd ~
      tar zxvf x48-gxrom-r.tar.gz
       
   2. Download the x48 binary and save in /usr/local/bin (or any other directory in your PATH).
   3. Fix permissions:  chmod 755 x48
   4. To run type:  x48 -geometry +0+0
```

---

### Post by trent dillman on 2006-04-07
You untarred in your ~ directory, right?

I've never used this, btw, just trying to help...

---

### Post by patrick295767 on 2006-04-07
[QUOTE=trent dillman]You untarred in your ~ directory, right?

I've never used this, btw, just trying to help...[/QUOTE]
  
I untarred in my directory and copied the bin files into the /usr/local/bin/x86 
/usr/local/bin/x86 
/usr/local/bin/ .... and other files ... 
  
You have an hotmail accoutn btw msn messenger ??
  cos i see you replied very fast !
  
Cheers !

---

### Post by trent dillman on 2006-04-07
Nope, no hotmail anymore. I discontinued all M$ usage.

Try running with the full path instead of the command name. (?)

---

### Post by patrick295767 on 2006-04-07
[http://www.area48.com/](http://www.area48.com/)
is cool website about HP48...
  
You figured out how to install it ??

---

### Post by patrick295767 on 2006-04-07
the x86, looks like this [http://dev.gentoo.org/~taviso/screenshots/march06a-fvwm.png](http://dev.gentoo.org/~taviso/screenshots/march06a-fvwm.png)
  
I hope we'll make it !!

===========
> Try running with the full path instead of the command name. (?)
  
I started it from the folder /usr/local/bin
with the rom into it ... 
  
./x86 
sh -c x86
sh x86
not working

---

### Post by trent dillman on 2006-04-07
What's the exact message?

---

### Post by patrick295767 on 2006-04-07
```
 ls /usr/local/bin   gives
checkrom         hp48   mkcard  sane-config        send  x86
dump2rom         INDEX  ram     sane-find-scanner  x48
gamma4scanimage  kget   rom     scanimage          x48f
   
then,
:/usr/local/bin$ x48
bash: /usr/local/bin/x48: cannot execute binary file

```




should [http://xqt.sourceforge.jp/download.html](http://xqt.sourceforge.jp/download.html) be installed ??

---

### Post by trent dillman on 2006-04-07
[http://www.hpcalc.org/hp48/pc/emulators/](http://www.hpcalc.org/hp48/pc/emulators/)

---

### Post by patrick295767 on 2006-04-07
[QUOTE=trent dillman][http://www.hpcalc.org/hp48/pc/emulators/](http://www.hpcalc.org/hp48/pc/emulators/)[/QUOTE]
  
I went there already but couldnt find the solution, the treasure to make x48 workign ... :-(
  
Thank you !

---

### Post by patrick295767 on 2006-04-08
==

---

### Post by patrick295767 on 2006-07-31
(back !)
 
Hi, 
  
I made today an extensive use of my HP48 for maths problem stuffs.
I can update my oooold post...

===
In order to install the HP48 on your Linux box, I can give you a easy script that can maybe help some of you:
  
```

cd /tmp
wget -N http://patrick295767.sitesled.com/miniram/installation-x48.sh
sudo sh /tmp/installation-x48.sh

``` ([script]("http://patrick295767.sitesled.com/miniram/installation-x48.sh"))

You just need to dump the rom, from the HP48 machine you bought and own !!, and copy it into your ~/.hp48/rom

Greetings
  
===
Screenshots:
[http://www.area48.com/](http://www.area48.com/)
[http://www.geocities.com/SiliconValley/Bay/9540/emul48.html](http://www.geocities.com/SiliconValley/Bay/9540/emul48.html)
ref:
[http://developer.berlios.de/projects/x48/](http://developer.berlios.de/projects/x48/)

---

### Post by brazzmonkey on 2006-12-14
didn't work here... i get :```
 /usr/bin/hp48gx: line 2: x48: command not found

```
indeed, no x48 in /usr/bin
what's wrong ? have i misunderstood anything ?

---

### Post by brazzmonkey on 2006-12-15
ok, don't bother, i installed emu48 under wine. i'm tired about spending hours to fix things...

---

### Post by patrick295767 on 2006-12-18
> **brazzmonkey said:**
> ok, don't bother, i installed emu48 under wine. i'm tired about spending hours to fix things...

Thank you for the information, 
I  deleted one required from my server for space needs, 
I am putting back up the file ...

Done & working again ! 

Greetings

---

### Post by brazzmonkey on 2006-12-19
you mean  i should try again ?

---

### Post by patrick295767 on 2006-12-23
not really 
time consuming mb
 
 
Now, x48 are in repos; maybe just :
apt-get -f -y install x48 
will be enough 

See ya' 
Enjopy HP

---

### Post by brazzmonkey on 2007-01-09
i cannot find it in repos. your script works fine now, though. many thanks patrick !

---

### Post by Webwil on 2007-03-07
> **brazzmonkey said:**
> i cannot find it in repos. your script works fine now, though. many thanks patrick !

Just add the folowing depot to your reposteries

deb http://schurger.org/breezy ./

Then you will find X48 in synaptic

It worked fine for me (installed it a few minutes ago.
Don't forget to dowload 
[http://www.linuxfocus.org/common/src/article319/x48-gxrom-r.tar.gz](http://www.linuxfocus.org/common/src/article319/x48-gxrom-r.tar.gz)
or
[http://www.linuxfocus.org/common/src/article319/x48-sxrom-e.tar.gz](http://www.linuxfocus.org/common/src/article319/x48-sxrom-e.tar.gz)
for the rom image.

---

