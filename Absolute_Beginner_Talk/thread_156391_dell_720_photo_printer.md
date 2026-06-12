---
title: "dell 720 photo printer"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by wolfee on 2006-04-06
Ubuntu sees it but It wont print. I looked everywhere on ubuntu forum to find answers and found out that this is a really bad area for ubuntu and dapper. Most people don't have the answers and can't get their printer working eather, or they just plug it in and it works. I found this statement to my surprise. However It is no help.
[B][U]
Ubuntu Harvester
 
Join Date: Oct 2004
Location: Canada
Dapper Drake Testing/ User
Beans: 892
Send a message via MSN to Burgundavia
	
Default Re: Setting up Printers - help needed[/U][/B]
Generally printing is a mess in Linux, both the backend and the frontend. The work for dapper can be found here:

[https://wiki.ubuntu.com/AutomaticPrinterConfiguration](https://wiki.ubuntu.com/AutomaticPrinterConfiguration)

It also appears that we have no clear wiki page on printing. I shall try and rectify this in the next week or so.

Corey

---

### Post by htinn on 2006-04-06
Printers have tons of models, and they are very lax about providing drivers. Here's a good place to start if you are looking to get printing working:

[http://www.linuxprinting.org/suggested.html](http://www.linuxprinting.org/suggested.html)

---

### Post by wolfee on 2006-04-07
This is what the HELP file said. 
In general, to install Z600 CUPS Printer Driver, you run
    the following command:
      - sh z600cups-1.0-1.tar.gz.sh
I got this 
 make install - sh z600cups-1.0-1.tar.gz.shmake: *** No rule to make target `install'.  Stop.
Maybe I typed make install 1 step too soon. Can someone give me a step by step breakdown of how to install tar gz files?

---

### Post by trent dillman on 2006-04-07
usually to install from tar.gz:

```

./configure
make
sudo make install

```

I'd try looking for a README or INSTALL file and opening it in your favorite text editor as well.

---

### Post by wolfee on 2006-04-07
[QUOTE=trent dillman]usually to install from tar.gz:

```

./configure
make
sudo make install

```

I'd try looking for a README or INSTALL file and opening it in your favorite text editor as well.[/QUOTE]
 I tried ......maybe the package is bogess sigh......i feel so stupid sometimes

---

### Post by Sef on 2006-04-09
> i feel so stupid sometimes

You aren't stupid.  Lexmark (which makes Dell printers) does not support Linux very well.

---

### Post by wolfee on 2006-04-09
[QUOTE=Sef]You aren't stupid.  Lexmark (which makes Dell printers) does not support Linux very well.[/QUOTE]
Ok so thats why it's not working. I don't understand why Ubuntu can "see" my printer but won't print.:confused:

---

### Post by Sef on 2006-04-10
check out this threadto get your lexmark working (I hope):

[http://www.ubuntuforums.org/showthread.php?t=56631&highlight=dell+720]("http://www.ubuntuforums.org/showthread.php?t=56631&highlight=dell+720")

---

