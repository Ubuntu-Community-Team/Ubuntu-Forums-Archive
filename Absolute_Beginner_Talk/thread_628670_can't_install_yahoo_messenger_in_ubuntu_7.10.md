---
title: "can't install yahoo messenger in ubuntu 7.10"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by cromohawk on 2007-12-01
hi ,
i can't install yahoo messenger on my ubuntu 7.10

i have downloaded the package, but when i type 'sude dpkg -i yahoomessenger.db' it doesn't install at all...please help.am still new to ubuntu..

things was a litle easier in redhat...

---

### Post by Delvien on 2007-12-01
> **cromohawk said:**
> hi ,
i can't install yahoo messenger on my ubuntu 7.10

i have downloaded the package, but when i type 'sude dpkg -i yahoomessenger.db' it doesn't install at all...please help.am still new to ubuntu..

things was a litle easier in redhat...

A willingness to learn is what makes it easier :)

Redhat uses a diff install method.

Can you paste its error messages when you run the following command when in the folder the .deb is located?

```
 sudo dpkg -i yahoomessenger.deb
```

---

### Post by Majorix on 2007-12-01
Do you desperately need the Yahoo! Messenger? Why don't you have a look at Pidgin or Kopete?

---

### Post by Delvien on 2007-12-01
this is a quote from a post on these forums.

> In a terminal window enter: (leave the quotes out)

"wget [http://download.yahoo.com/dl/unix/ymessenger_1.0.4](http://download.yahoo.com/dl/unix/ymessenger_1.0.4) _1_i386.deb"

After it finishes downloading enter:

sudo apt-get install libssl0.9.6 (this library was needed)

sudo dpkg -i ymessenger_1.0.4_1_i386.deb

After these packages are installed you can run Yahoo messenger from the terminal by entering:

/usr/bin/ymessenger

---

### Post by PhoenixP3K on 2007-12-01
> **cromohawk said:**
> hi ,
i can't install yahoo messenger on my ubuntu 7.10

i have downloaded the package, but when i type 'sude dpkg -i yahoomessenger.db' it doesn't install at all...please help.am still new to ubuntu..

things was a litle easier in redhat...

I would really recommand using Pidgin but If you really want to use the Unix version of the Yahoo Messeger download the deb file to your desktop [http://us.dl1.yimg.com/download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb](http://us.dl1.yimg.com/download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb) and than the debi installer should run it (double click = easy :D )

---

### Post by SunnyRabbiera on 2007-12-01
pidgin will most likely do you fine.

---

### Post by cromohawk on 2007-12-02
hi guys...
thanks for the reply,
i have found out the first error which was the missing libssl0.9.6 file,
i have installed it,now the installer says "xlibs" is missing...so i wanted to update all the packages in my box by making an apt-get update...and i got this error message 

===================================================
cromohawk@warhead:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
===================================================

how can i install xlibs ?
i need yahoo messenger badly to communicate with my classmates in the university campus.PLEASE HELP...thanks...

---

### Post by monte48lowes on 2007-12-02
apt-get must be done using sudo...

```
sudo apt-get update
```

Mike

---

### Post by hamzamusa on 2007-12-23
> **SunnyRabbiera said:**
> pidgin will most likely do you fine.

Pidgin with No Cam Or Voice for Yahoo , MSN , and GTALK !!!

---

### Post by philinux on 2007-12-23
Kopete does webcams.

---

### Post by Sef on 2007-12-23
For yahoo, get [GyachE Improved]("http://gyachi.sourceforge.net/").  It does cam and voice.

---

### Post by Feisty-Fox on 2008-01-16
Gaim is nice to use if you are on broadband or even on dial-up. However, Gaim takes ages to connect if you are on an extremely slow internet connection (GRPS through mobile phone, for instance) and it is here that you would be better off with Yahoo Messenger.

I have a Mandrake 10.0 system on one of the partitions on my machine.  I had installed the RPM version of Yahoo messenger (rh9.ymessenger-1.0.4-1.i386.rpm) on that partition and the messenger client was working without any issues.  However, an installation of the client on my Ubuntu Feisty Fawn(7.04) system using a debian installer (ymessenger_1.0.4_1_i386.deb) failed due to unsatisfied dependancies.  So, I copied over the entire installation including the sub-directories available under /opt of the Mandrake system to /opt of my Ubuntu Feisty Fawn system and created a shortcut on my desktop to  /opt/ymessenger/bin/ymessenger. Also copied was the .ymessenger directory from the home directory of the Mandrake system to the home directory of Ubuntu Feisty Fawn.  I have since been using this set up without any issues. You could try this method if you have a Mandrake 10.0 system on one of your partitions.  As an aside, you may have to set your locale to "English (United States of America)" or you will find Yahoo Messenger's menu missing!

---

### Post by shadowtroopers on 2008-01-17
i prefer using gyachE for yahoo chat etc. You can find that under sourceforge.net

---

### Post by coolbrook on 2008-01-29
I'm trying to install the official version as well. I just need to get xlibs installed first.

---

### Post by sports fan Matt on 2008-01-29
maybe its me..im not sure..but im having trouble understanding why one would absolutely dire need YM.  Like others have said there are suiitable replacements out there, and I wouldnt mind using other tools...

Not a rant but asking why (it sometimes seems like more people NEED X or Y and im trying to understand why when in some cases the alternative is much better in support and supported better for an OS...Am i crazy in my thinking?

---

### Post by coolbrook on 2008-01-29
I found [this thread]("http://ubuntuforums.org/showthread.php?p=2307236#post2307236") through another.  It's not worth the trouble.

---

### Post by coolbrook on 2008-01-29
> **sox fan Matt said:**
> maybe its me..im not sure..but im having trouble understanding why one would absolutely dire need YM.

For arguments sake....Familiarity.  If you are the expert wanting to convert someone from Windows and they want Yahoo Messenger to look like Yahoo Messenger 
(on Ubuntu) then you'll wanna give it a go.

---

### Post by sports fan Matt on 2008-01-29
Yeah, i took a look at that thread and it looks downright awful..it seems to even try it for a newbie maybe complete hell and so not worth the trouble..but thats just me::)

---

### Post by tungpham42 on 2008-02-10
Why don't you choose [GYACHI](http://gyachi.sourceforge.net/index.shtml) because you can use conference, webcam, and transfer file.

---

### Post by crjackson on 2008-02-11
Well I can understand the desire myself.  I can't get Pidgin or Kopete to connect to my yahoo account.  GYACHI - Well I downloaded it and tried to compile but had no luck.

BTW  Pidgin connects fine to my MSN account.  I'm using 64-Bit Gutsy.  Is there a 64-bit deb somewhere or do I need to install the 32-bit deb?

Well nevermind.  I found that Pidgin works just fine on my desktop systems.  It's only my laptop that it won't.  I may be in for a fresh install of Ubuntu if I can't figure it out.  NOTHING from my laptop will connect to Yahoo, but it connects just fine on my other computers.

---

