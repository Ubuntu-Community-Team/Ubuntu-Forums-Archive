---
title: "Ubuntu as a server with a GUI?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by !GN!T!ON on 2007-01-11
hi,

im new to linux and have always used windows but now ive got an extra pc wich a want to use as an dedicated server, wich will have the tasks
-DHCP server
-FTP Server
-Web Server
-Teamspeak/Ventrillo Server
and sometimes a game Server for games like America's Army or Call of Duty.

Ive been running windows server 2003 and kerio winroute firewall on it before but i didnt like it really much and my trails expired [-( 

now i downloaded the dapper drake server release and found that it had no GUI and i couldnt really understand the Command line interface. now i dont really have a problem learning the command line interface but i was wondering of i could also use the ubuntu desktop version as a server, because it has an GUI and i can make the switch to the command line more gradually and get my server going :KS 

My Server spec's are

AMD AthlonXP 1ghz
768mb of RAM
40gb HDD
2x Realteak Ethernet NIC's
Nvidia Geforce 2 32mb
Cd-rom drive
Floppy drive

:rolleyes: 

if any could help me get on my way I would be very thankfull :D 

Thanks in advance,

!GN!T!ON

---

### Post by jvc26 on 2007-01-11
You could install the server release then run:
```

sudo apt-get install xubuntu desktop

```
For a lightweight GUI desktop. That works (If it throws up anything about problems with dependencies use:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)
Then do the above command.
Il

---

### Post by Pixilarion on 2007-01-11
Sure you can use the graphic way... With those specs your computer should be able to manage...
Setting up all those services might prove rahter difficult, but keep trying, you'll get there. I'm only saying that it won't be easy...

---

### Post by Pixilarion on 2007-01-11
> **Illuvator said:**
> You could install the server release then run:
```

sudo apt-get install xubuntu desktop

```
For a lightweight GUI desktop. That works (If it throws up anything about problems with dependencies use:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)
Then do the above command.
Il

acutally it is xubuntu-desktop...
```

sudo apt-get install xubuntu-desktop

```

---

### Post by jvc26 on 2007-01-11
yeah - so it is - apologies, a typo :)
Il

---

### Post by Pixilarion on 2007-01-11
> **Illuvator said:**
> yeah - so it is - apologies, a typo :)
Il

No problem: only wanted to avoid disappointment and "Hey! It doesn't work!!!!" ;)

---

