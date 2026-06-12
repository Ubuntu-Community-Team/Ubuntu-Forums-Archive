---
title: "Clam update error"
date: 2012-06-04
forum: Any Other OS
---

### Post by abnordude on 2012-06-04
I get this error when i type sudo freshclam in the terminal

ERROR: Please edit the example config file /etc/clamav/freshclam.conf
ERROR: Can't open/parse the config file /etc/clamav/freshclam.conf

---

### Post by abnordude on 2012-06-05
Anyone please help me.......

---

### Post by zhogan85 on 2012-06-05
Type the following

```
nano /path/to/freshclam.conf
```

and make sure Example is commented out.

---

### Post by abnordude on 2012-06-07
> **zhogan85 said:**
> Type the following

```
nano /path/to/freshclam.conf
```and make sure Example is commented out.

After doing that....when i type sudo freshclam, I get..

ERROR: Can't create temporary directory /var/lib/clamav/clamav-50a7a5f6dd45550766b7f45b49844073
Hint: The database directory must be writable for UID 64 or GID 64

---

### Post by zhogan85 on 2012-06-07
Try the code below, from the [ArchWiki]("https://wiki.archlinux.org/index.php/ClamAV")

```
chown 64:64 /var/lib/clamav & chmod 755 /var/lib/clamav 
```

---

### Post by abnordude on 2012-06-07
> **zhogan85 said:**
> Try the code below, from the [ArchWiki]("https://wiki.archlinux.org/index.php/ClamAV")

```
chown 64:64 /var/lib/clamav & chmod 755 /var/lib/clamav 
```

yes....thanks very much.....it worked.....but can you also tell me how to uptdate the clamav engine and GUI???????

---

### Post by zhogan85 on 2012-06-07
You're using Arch right? Then I would think, as long as you update your system regularly they should be up to date.

---

### Post by chamber on 2012-06-08
> **abnordude said:**
> yes....thanks very much.....it worked.....but can you also tell me how to uptdate the clamav engine and GUI???????

Have you infact read the wiki?

If you had did you notice [this?]("https://wiki.archlinux.org/index.php/ClamAV#Updating_database")

---

### Post by abnordude on 2012-06-08
> **zhogan85 said:**
> You're using Arch right? Then I would think, as long as you update your system regularly they should be up to date.


I'm using arch....i am talking about clamtk.....when i open that i can see that the GUI and the AV Engine is out of date.....I read the wiki (Had not read earlier)....But, in the wiki, I didn't see a method to update the GUI and the Engine.....

How can I do that?

---

### Post by chamber on 2012-06-08
You need to re read it as the answer is in there. It's actually the link I posted.

---

### Post by abnordude on 2012-06-08
> **chamber said:**
> You need to re read it as the answer is in there. It's actually the link I posted.

I can see that my engine is updated....GUI is showing some error.....
So, I downloaded the source files of the latest clamtk....
Can anyone tell me how to install it.....?

---

### Post by chamber on 2012-06-08
> **abnordude said:**
> I can see that my engine is updated....GUI is showing some error.....
So, I downloaded the source files of the latest clamtk....
Can anyone tell me how to install it.....?

Posting the error you get might be handy.

Screenshot perhaps?

---

### Post by abnordude on 2012-06-08
Also when I do 'check for update' in help option....

It says in 'GUI updates' that a newer version is available....

But it doesnt update....

What am i doing wrong???

---

### Post by abnordude on 2012-06-08
> **chamber said:**
> Posting the error you get might be handy.

Screenshot perhaps?


Sorry,.....It's not actually an error

But when I went to the clamav website....I saw that I have the latest engine and yet in my PC clamtk shows a somewhat a blue icon with an 'i'....That's what I was actually trying to convey........

---

### Post by chamber on 2012-06-08
The database files are located here,

/var/lib/clamav/daily.cvd
/var/lib/clamav/main.cvd

So in theory you could load your downloaded definitions into their.

I don't use any AV on my arch install so I do not have any experience with clam.

What does,

```
freshclam -v
``` 

do for you?

You have also not given any details about your setup.

WM? DE? Network Connections??????

Makes it kind of hard to troubleshoot.


EDIT|||||||||||||||

Also, 

post the result of 

```
pacman -Qi clamav
```

---

### Post by abnordude on 2012-06-09
pacman -Qi clamav gave.........


Name           : clamav
Version        : 0.97.4-2
URL            : [http://www.clamav.net/](http://www.clamav.net/)
Licenses       : GPL
Groups         : None
Provides       : None
Depends On     : bzip2  libltdl
Optional Deps  : None
Required By    : clamtk
Conflicts With : None
Replaces       : None
Installed Size : 11344.00 KiB
Packager       : Gaetan Bisson <bisson@archlinux.org>
Architecture   : x86_64
Build Date     : Thu 29 Mar 2012 12:08:01 AM IST
Install Date   : Fri 08 Jun 2012 04:58:06 PM IST
Install Reason : Explicitly installed
Install Script : Yes
Description    : Anti-virus toolkit for Unix

---

### Post by abnordude on 2012-06-09
sudo freshclam -v
Password: 
Current working dir is /var/lib/clamav
Max retries == 3
ClamAV update process started at Sat Jun  9 21:35:05 2012
Using IPv6 aware code
Querying current.cvd.clamav.net
TTL: 689
Software version from DNS: 0.97.4
main.cvd version from DNS: 54
main.cvd is up to date (version: 54, sigs: 1044387, f-level: 60, builder: sven)
daily.cvd version from DNS: 15023
Retrieving [http://database.clamav.net/daily-15020.cdiff](http://database.clamav.net/daily-15020.cdiff)
Trying to download [http://database.clamav.net/daily-15020.cdiff](http://database.clamav.net/daily-15020.cdiff) (IP: 219.94.128.99)
Downloading daily-15020.cdiff [100%]
cdiff_apply: Parsed 10 lines and executed 10 commands
Retrieving [http://database.clamav.net/daily-15021.cdiff](http://database.clamav.net/daily-15021.cdiff)
Trying to download [http://database.clamav.net/daily-15021.cdiff](http://database.clamav.net/daily-15021.cdiff) (IP: 219.94.128.99)
Downloading daily-15021.cdiff [100%]
cdiff_apply: Parsed 12 lines and executed 12 commands
Retrieving [http://database.clamav.net/daily-15022.cdiff](http://database.clamav.net/daily-15022.cdiff)
Trying to download [http://database.clamav.net/daily-15022.cdiff](http://database.clamav.net/daily-15022.cdiff) (IP: 219.94.128.99)
Downloading daily-15022.cdiff [100%]
cdiff_apply: Parsed 18 lines and executed 18 commands
Retrieving [http://database.clamav.net/daily-15023.cdiff](http://database.clamav.net/daily-15023.cdiff)
Trying to download [http://database.clamav.net/daily-15023.cdiff](http://database.clamav.net/daily-15023.cdiff) (IP: 219.94.128.99)
Downloading daily-15023.cdiff [100%]
cdiff_apply: Parsed 21 lines and executed 21 commands
Loading signatures from daily.cld
Properly loaded 217096 signatures from new daily.cld
daily.cld updated (version: 15023, sigs: 217096, f-level: 63, builder: mcichosz)
Querying daily.15023.64.1.0.219.94.128.99.ping.clamav.net
bytecode.cvd version from DNS: 185
bytecode.cvd is up to date (version: 185, sigs: 39, f-level: 63, builder: neo)
Database updated (1261522 signatures) from database.clamav.net (IP: 219.94.128.99)
ERROR: Please edit the example config file /etc/clamav/clamd.conf
ERROR: NotifyClamd: Can't find or parse configuration file /etc/clamav/clamd.conf

---

### Post by chamber on 2012-06-09
> ERROR: Please edit the example config file /etc/clamav/clamd.conf
ERROR: NotifyClamd: Can't find or parse configuration file /etc/clamav/clamd.conf

Do this.

[quote=ArchWiki]Configuration

Whether you are going to use clamav as a daemon or use it as a simple file checker you need to comment out the line that contains the word Example, usually it is found at the beginning of /etc/clamav/freshclam.conf and /etc/clamav/clamd.conf files. [/quote]

A simple google search about the GUI update sourced the answer.

[http://clamtk.sourceforge.net/faq.html#outdated_gui](http://clamtk.sourceforge.net/faq.html#outdated_gui)

The latest version is in the AUR.

[https://aur.archlinux.org/packages.php?ID=16810](https://aur.archlinux.org/packages.php?ID=16810)

---

### Post by abnordude on 2012-06-17
OOhhh....I forgot to add a thanks to all the people who helped me.....

Thanks all.....Big thanks to chamber......

---

