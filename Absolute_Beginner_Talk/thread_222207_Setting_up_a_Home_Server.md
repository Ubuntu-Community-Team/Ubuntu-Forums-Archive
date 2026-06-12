---
title: "Setting up a Home Server"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by itKiwi on 2006-07-24
Am I biting off more than I can chew ?

I am thinking of setting up a Ubuntu Server.  Purpose is to provide common storage of family photos, etc., backup of all work files from a couple of computers, and as an internal web server with apache, php and mysql, for web development.  (I have a separate Belkin firewall/router for my internet access, and want to keep this separate.) Workstations are running XP.

I have been using Windows for years, and before that, DOS, but zero Linux (apart from a failed install 18 months ago). 

I ask again; Am I biting off more than I can chew ?

Thanks.:-k

---

### Post by A2A on 2006-07-24
HI there, ubuntu server is completely text based.  The desktop version on the other hand is graphical, and will allow you a terminal window for text commands, if you wish to use them.  
You can install the desktop version, and then addon apache, mysql, php and all the mods you need.  Yo make your computer accessable by the windows machines as a file server, you would need to install samba.
All this is not hard to accomplish, 'cos there is help files and readme files available, and then you could always post your questions here as well :-)
Hope this helps, any more questions, just fire back.

A2A

---

### Post by Jagot on 2006-07-24
Here's a nice server setup guide:

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

In all liklihood you won't need everything detailed here but it's quite useful anyway.

---

### Post by Nalum on 2006-07-24
> **Jagot said:**
> Here's a nice server setup guide:

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

In all liklihood you won't need everything detailed here but it's quite useful anyway.

Thank you very much Jagot, this is exactly what i need.

---

### Post by richbarna on 2006-07-24
Take a look at this :-
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

EDIT: Looks like we posted at the same time :)

---

### Post by itKiwi on 2006-07-24
Thanks for all your very positive comments.  I had a quick look at the “perfect set up”.  Text based, which I was expecting, but some of the commands are very, very long.  I can't envisage “cut and paste” in this text based new installation environment.  So, I assume it really is typing into the command line, or have I missed something ?

Another beginners question (and the answer for sure is in the docs); What does LTS stand for (as in LTS Server) ? 

Thanks again.

---

### Post by Jagot on 2006-07-24
LTS = Long Term Support

And yes, you will have to type all commands - no copying and pasting.

---

### Post by itKiwi on 2006-07-24
Thanks Jagot.
Not surprised about the typing. I'll start later in the week.
Bed time.
Thanks once again everyone.

---

### Post by az on 2006-07-24
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

### Post by itKiwi on 2006-07-29
[FONT="Verdana"]OK, so far, so good, following the "Perfect Setup" instructions.  Or almost.  After a quick course on vi . . . :smile: 

Got down to para 5 “Configure the network”.  My Belkin ADSL 4port gateway router set itself up as 192.168.2.1.  THE DHCP server in the router uses addresses 192.168.2.2 to 192.168.2.100.  So the other PCs are all in this group.  The router also sets a local domain name of “Belkin” by default, and I haven't changed this.  My hostname is the default “ubuntu1”   I setup this new server to the address 192.168.2.101   I edited the first two lines of the “hosts” file to read [/FONT]

[FONT="Courier New"]127.0.0.1   localhost.Belkin   localhost
192.168.2.101  ubuntu1.Belkin   ubuntu1[/FONT]

[FONT="Verdana"]Is this correct ?  I ask this because when I run hosts and hosts-f, I get [/FONT]

[FONT="Courier New"]hostname ubuntu1
hostname-f  ubuntu1.Belkin[/FONT]

[FONT="Verdana"]The “Perfect” instructions say that these should both be the same.

Second problem.  Carrying on, despite the above, para 7 “Install some software”.  I was told that the packages ncftp and zlibg-dev “Couldn't be found”.  Will this cause problems later ?  Where can I find these ?

Thanks for your ongoing help and encouragement.[/FONT];-)

---

### Post by itKiwi on 2006-07-29
> **itKiwi said:**
> [FONT="Verdana"]OK, so far, so good, following the "Perfect Setup" instructions.  Or almost.  After a quick course on vi . . . :smile: 

Got down to para 5 “Configure the network”.  My Belkin ADSL 4port gateway router set itself up as 192.168.2.1.  THE DHCP server in the router uses addresses 192.168.2.2 to 192.168.2.100.  So the other PCs are all in this group.  The router also sets a local domain name of “Belkin” by default, and I haven't changed this.  My hostname is the default “ubuntu1”   I edited the first two lines of the “hosts” file to read [/FONT]

[FONT="Courier New"]127.0.0.1   localhost.Belkin   localhost
192.168.2.101  ubuntu1.Belkin   ubuntu1[/FONT]

[FONT="Verdana"]Is this correct ?  I ask this because when I run hosts and hosts-f, I get [/FONT]

[FONT="Courier New"]hostname ubuntu1
hostname-f  ubuntu1.Belkin[/FONT]

[FONT="Verdana"]The “Perfect” instructions say that these should both be the same.

Second problem.  Carrying on, despite the above, para 7 “Install some software”.  I was told that the packages ncftp and zlibg-dev “Couldn't be found”.  Will this cause problems later ?  Where can I find these ?

Thanks for your ongoing help and encouragement.[/FONT];-)
I forgot to say that I set up this new server with the address 192.168.2.101.

---

### Post by itKiwi on 2006-07-30
Second problem solved.  
I'll repost the first problem in the networking foum.

---

