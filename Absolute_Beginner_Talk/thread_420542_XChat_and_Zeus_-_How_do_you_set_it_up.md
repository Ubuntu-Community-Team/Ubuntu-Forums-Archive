---
title: "XChat and Zeus - How do you set it up?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by pimpaulogy on 2007-04-23
Sorry, still a newbie to Linux, but one of the reasons I still have a Windows box is because I use MIRC with Autoget.  I have seemed to find the Linux alternative: XChat and Zeus, but I can't get it to work.

Does anybody know the step by step instructions for setting it up from scratch, including all the addition required components.

Thanks for the help.

---

### Post by mrvertigo on 2007-04-26
well, are you running ubuntu, kubuntu, xubuntu?

within these do you use the add remove programs icon on your menu? or synaptic? adept manager? 

or do you have it installed but cant bring it up?

---

### Post by pimpaulogy on 2007-04-27
I am running Ubuntu 6.10 Edgy Eft.
XChat was installed via Automatix2
Zeus is downloaded via their website ([http://sourceforge.net/projects/zeus-autoget/](http://sourceforge.net/projects/zeus-autoget/))

There is a readme with the Zeus download, but it only covers setting up Zeus.  It says there are other requirements, which they list, but they don't describe how to install those.  I tried to install the requirements via Synaptic and searching google.  Maybe I have all the requirements or maybe I don't.

Following the readme, I get to the point where it says to launch XChat and load the plugin.  When I load the plugin, I get this error message in XChat:

Error loading '/home/paul/apps/zeus-0.4a/zeus.pl':
 Can't locate Zeus_DB.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 .) at (eval 3) line 3.
 BEGIN failed--compilation aborted at (eval 3) line 3.

I am assuming I am setting it up wrong or are still missing some of the requirements.  Like I said, I still consider myself a newbie so I need the hand holding of a HowTo.

---

### Post by ljcasey on 2007-04-27
mirc works pretty well from WINE. Although I prefer Xchat (the proper xchat) alot better.

---

### Post by pimpaulogy on 2007-04-27
I got MIRC working through WINE, but the AutoGet addon for MIRC doesn't work well with WINE.  That is why I have been trying to track down a Linux equivalent to the MIRC/Omen AutoGet combination for Windows.  The only one I have found is Zeus with XChat, but I can't get past the error message.

Right now, the only reason why I use my Windows box is for the MIRC/Omen AutoGet combination.  I wish I didn't have to use it because I would like to convert that box into a mail server.

---

### Post by mrvertigo on 2007-04-27
i havent had this problem, sorry i couldn't be of more help, all i can say is enable all repositories and try synaptic again, if you have universe or restricted repositories commented you may be missing something important

---

### Post by pimpaulogy on 2007-04-27
Yeah, unfortunately, Zeus isn't available in the repositories so you have to download it and build it yourself, including all the prerequisites.

Thanks for the advice none the less.

---

### Post by mrvertigo on 2007-04-27
maybe google for a .deb file that shouls ease things for ya

---

### Post by pimpaulogy on 2007-04-27
Have yet to be able to find one.

---

### Post by papercut on 2007-09-26
I don't know if you still need these, but here are the required perl modules.


perl-tk
```
sudo apt-get install perl-tk
```

mp3::info
[http://search.cpan.org/~daniel/MP3-Info-1.20/Info.pm](http://search.cpan.org/~daniel/MP3-Info-1.20/Info.pm)

DBI
[http://search.cpan.org/~timb/DBI/lib/Bundle/DBI.pm](http://search.cpan.org/~timb/DBI/lib/Bundle/DBI.pm)

DBD::SQLite
[http://search.cpan.org/~msergeant/DBD-SQLite-1.14/lib/DBD/SQLite.pm](http://search.cpan.org/~msergeant/DBD-SQLite-1.14/lib/DBD/SQLite.pm)


Unpack the archives, enter them and

```

perl Makefile.pl

make

make test

sudo make install

```


I could get the gui to work from the command line, but was getting errors from within xchat.  Also, I couldn't figure out how to use it even with the gui open.

Hope you have better luck.

---

