---
title: "Ubuntu-Server edition has no desktop?"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by Aximilli on 2006-06-19
Hi all. I installed server edition on a computer at work that I hope to make into a web server. Having LAMP installed and configged (for the most part) is nice, but no help to me if all i get is a terminal. I did apt-get install ubuntu-desktop, which got me gnome, but cost me everything else. And apt-get install gnome doesn't work. Any ideas guys?

---

### Post by uzi09 on 2006-06-19
what do you mean by "cost me everything else"? did you lose something? what?

check this out:
[http://www.psychocats.net/ubuntu/nox.php](http://www.psychocats.net/ubuntu/nox.php)

---

### Post by Aximilli on 2006-06-19
[QUOTE=uzi09]what do you mean by "cost me everything else"? did you lose something? what?

check this out:
[http://www.psychocats.net/ubuntu/nox.php](http://www.psychocats.net/ubuntu/nox.php)[/QUOTE]

It installed the regular ubuntu setup, and I lost LAMP. I think, because I never acutally got to use it in the first place.

---

### Post by uzi09 on 2006-06-19
u might want to take a look at this then:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

---

### Post by Aximilli on 2006-06-19
[QUOTE=uzi09]u might want to take a look at this then:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)[/QUOTE]

I'v seen that giude before. That shows how to install server apps onto ubuntu desktop. Whereas I have Ubuntu-Server Edition and I'd like to install a desktop environment onto it.

---

### Post by Aximilli on 2006-06-19
well I'v installed xserver-xorg. but no desktop environment, and I'm still stuck in the terminal. Anyone?

---

### Post by Kilz on 2006-06-19
[QUOTE=Aximilli]I'v seen that giude before. That shows how to install server apps onto ubuntu desktop. Whereas I have Ubuntu-Server Edition and I'd like to install a desktop environment onto it.[/QUOTE]
The command apt-get install ubuntu-desktop installs the Ubuntu desktop with everything that comes in a standerd Ubuntu install to my knowlage. Gnome is the standerd Ubuntu desktop. If you need other things installed, or think something is missing you can use apt-get or synaptic to install them.
If the server no longer works, you can install any missing pieces with [this howto]("https://help.ubuntu.com/community/ApacheMySQLPHP"). I created the server and installed a desktop just like you, and the server still functioned. If there is a /var/www folder place a web page in it to test. But if its giving you problems, install the standerd Ubuntu package, then follow the howto above.

---

### Post by Perfect Storm on 2006-06-19
Well, which one of the DE do you want to install?

---

### Post by Aximilli on 2006-06-19
[QUOTE=Artificial Intelligence]Well, which one of the DE do you want to install?[/QUOTE]

GNOME I suppose.

---

### Post by az on 2006-06-19
[QUOTE=Aximilli]It installed the regular ubuntu setup, and I lost LAMP. I think, because I never acutally got to use it in the first place.[/QUOTE]
I think you are expecting there to be a graphical frontend to Apache and Mysql.  There are not.  You installed the turn-key LAMP server adn then installed ubuntu-desktop on top of that.  Had you tried to access that box from another machine, you would have gotten the default apache page.

Apache is a deamon.  It runs in the background.  So does mysql.  

[https://help.ubuntu.com/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/ubuntu/serverguide/C/index.html)

---

### Post by skirkpatrick on 2006-06-19
Look for and install webadmin in the repositories.  It will give you a nice graphical front-end to manage your server via a web browser.

---

### Post by NeoGreen on 2006-06-19
I was having the same problem thanks for the info.:D

---

### Post by Aximilli on 2006-06-19
So does that mean the only way I access and modify it is through the .conf files? Confused me because when in windows apache has an executable in the system tray.

---

### Post by Aximilli on 2006-06-19
[QUOTE=Kilz]... the server still functioned. If there is a /var/www folder place a web page in it to test.[/QUOTE]

I installed ubuntu-desktop and now there is no www in /var

---

### Post by az on 2006-06-20
[QUOTE=Aximilli]I installed ubuntu-desktop and now there is no www in /var[/QUOTE]
That is not because of anything involved with the installation of ubuntu-desktop or any other desktop packages.

---

### Post by houstonbofh on 2006-06-21
[QUOTE=Aximilli]I installed ubuntu-desktop and now there is no www in /var[/QUOTE]
You just got bit by the poor terminology.  After installing a LAMP server, from the command line type *sudo apt-get install ubuntu-desktop* to install the desktop onto the server.  If you booted the desktop cd and installed it, you overwrote the LAMP server.

---

### Post by Roxydogg28 on 2007-11-10
Hello all,  I've run into the same issue, wouldn't really call it a problem.  I would prefer to have some gui interface on my server install, but I am getting errors when trying the sudo apt-get....
Specifically E: Couldn't find package ubuntu-desktop

How can I install those??  And it seems like this would be somewhere on the system based on the fact that everyone seems to just suggest running the command not installing anything(package, etc.)

Any help would be great, I've still got the server install cd as well as the desktop install cd.

Thanks,

Matt

---

### Post by Tux.Ice on 2007-11-10
Ive got a question how do you host a website on ubuntu 7.10 desktop so you upload like index.html to /var/www but then how do you access it, by going to your ip (for ex.99.99.99.99)

---

### Post by Perfect Storm on 2007-11-10
> **Roxydogg28 said:**
> Hello all,  I've run into the same issue, wouldn't really call it a problem.  I would prefer to have some gui interface on my server install, but I am getting errors when trying the sudo apt-get....
Specifically E: Couldn't find package ubuntu-desktop

How can I install those??  And it seems like this would be somewhere on the system based on the fact that everyone seems to just suggest running the command not installing anything(package, etc.)

Any help would be great, I've still got the server install cd as well as the desktop install cd.

Thanks,

Matt

Might be there aren't any internet connection or the sourcelist isn't correctly set.

```
sudo nano /etc/apt/sources.list
```
to check/modify it
afterwards;
```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install ubuntu-desktop
```

---

### Post by Roxydogg28 on 2007-11-10
no internet connection....

So how do I get around the issue without having an internet connection???

Thanks for your quick response.

Matt

---

### Post by Perfect Storm on 2007-11-10
Well, you need to download Ubuntu Desktop CD or better use Xubuntu if it's a server you want.

---

### Post by Roxydogg28 on 2007-11-10
Ok, so are you suggesting a fresh install of xbuntu, then adding LAMP?
Or does it come with that setup like the server edition?
If it isn't obvious I'm a bit of a newbie, using a windows machine to burn my images.  With that said, I don't have anything that will burn, hold info(packages etc) in a file format suitable for linux(non fat32 etc.)

I'll take any suggestions on the best approach.  I'll do what I need to, i.e. fresh install etc.

.....If I knew how to get the machine "online" using the xterm(command line) I would then be able to run the commands suggested above.

I have a working cable modem hooked up to my windows machine, that I have no problem unhooking and hooking up to the ubuntu machine....though I do have a wireless router between the cable modem and the lan port, should I bypass this to try and get online(that is if that is a viable solution to get past this issue.)

Thanks again all,

Matt

---

### Post by Roxydogg28 on 2007-11-11
Ok, I thought I might be able to try something a bit off the wall.  I found a knoppix disc laying around.....

Knoppix came right up on the machine.

I was able to mount the hard drive as it is already formatted from the server install.

Plugged in my network cable from my cable modem, but couldn't get the connection working....Thought if I did that, and sudo'd in as root on the machine I might be able to run the commands to install the app.

Was my approach even possible, or was that too far fetched??

Thanks again,

Matt

---

### Post by Roxydogg28 on 2007-11-11
here's another off the wall option that I'm not sure could work.

Is it at all possible to connect my Ubuntu server machine into my router, then ssh(or something similar) into via my windows machine and add packages that way??

Thanks,

Matt

---

### Post by steveneddy on 2007-11-11
I have Ubuntu Server LTS 6.06 installed and shortly after installation I installed Ububtu-Desktop and it works well for me. The only reason I dod this is so I can plug my USB drive into the machine and move pics for my web page, music for my music server app and surf occasionally when I leave the lappie in the car.

I didn't loose anything that belonged to the server portion and I turn off X when I log off by doing in terminal:

```
sudo /etc/init.d/gdm stop
```

When I need a GUI, I just turn on the monitor and type in terminal:

```
sudo /etc/init.d/gdm start
```

and Gnome starts up.

To get to the "terminal" from Gnome, do a **ctrl+alt+F1** and log in, enter your commands, log off or whatever you need to do.

Typical session for me when I need a GUI.

Turn on monitor, type in terminal my log on info, then

```
sudo /etc/init.d/gdm start
```

I then give my log in info, again.....

Do whatever I need to do with a GUI and then do a **ctrl+alt+F1** to get back to the terminal screen, then in terminal

```
sudo /etc/init.d/gdm stop
```

This way I can have a GUI if I need it and it isn't sucking up system resources when I don't.

BTW, I boots in about 12 seconds or less and I have uptime of over 2 months without a restart.

---

### Post by Roxydogg28 on 2007-11-11
That's most likely what I will be doing but....I still cannot get online to get the desktop installed.......the more I think about it, the more I would probably like the using a live cd that doesn't actually install anything.  Once again, can't get online either way though.

Thanks again,

Matt

---

### Post by Roxydogg28 on 2007-11-12
Ok, I guess I'll deal without having a desktop.
I think I'll just use a live cd when I really need a gui.

Can anyone point me in the direction of a good source of information for configuring ubuntu server.

I've been looking around on ubuntus site, these forums, and other forums and haven't found too much "starter" info.  I have been finding good tid bits here and there though.

Thanks,

Matt

---

