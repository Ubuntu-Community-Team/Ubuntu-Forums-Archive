---
title: "First INSTALL, NOW NEED Security"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by neewby on 2006-08-03
WHATS the SECURITY FOR ubuntu

Do I need to download IPTABLES for or something

I need something to watch all traffic

or other


Any rundowns on What I Security Measures I should be taking Before roaming the net and other things,
Or where I can Download Doc for linux security for beginners.

other then that UBUNTU is "THE MAC"8)

---

### Post by neewby on 2006-08-03
Also whats the CONTROL for UBUNTU 6.06 

As I mean Yast2 is to SUSE shittyLINUX

---

### Post by Mach1US on 2006-08-03
Linux is pretty stealthy system from the moment is installed but you can aditionally install firewall

---

### Post by T700 on 2006-08-03
Repeat after me:  "Linux is not Windows."  Say that 20 times.  :-)

1.  Keep updated.  Download and install all updates and patches that Ubuntu automatically sends you.

2.  By default, no ports are open, so a firewall is not needed.  If you like to wear pants and suspenders, go to the command line (terminal) and ```
type: sudo aptitude update
```
and then
```
sudo aptitude install firestarter
```
This will install a graphical frontend and wizard to configure IPtables.  Just go to the command line again and type ```
gksudo firestarter
``` and follow the wizard.

3.  Unless you are running a mail server that sends mail to Windows machines, you do not need an antivirus.  The only reason a mail server needs one is to avoid passing the viruses to Windows PC's.

4.  Don't run code or install programs unless you know and trust the source.

Have fun!
Paul

---

### Post by T700 on 2006-08-03
> **neewby said:**
> Also whats the CONTROL for UBUNTU 6.06 

As I mean Yast2 is to SUSE shittyLINUX

Huh?

Paul

---

### Post by neewby on 2006-08-03
Thanks DUDEs

Awesome support for such a powerful distribution

Or better yet an excellent execution

oh yeh and I found the security section LOL

I was about to download firestarter from the site

I better study on what UBUNTU includes first before all other nonsense 

and many thanks aganinanainins:KS
????????????????????????????????????????????????????????????????????????????????????????????/
I MEAN CONTROL PANEL for the system configuration????????????????????????????????????????

---

### Post by Mach1US on 2006-08-03
Another great think about ubuntu is that is based on debian wich packages can be made to install on Ubuntu , more over Ubuntu has its own greatsystem 
just go   System>Synaptics Package Manager   and you can find thousand of aplications there.

---

### Post by Jagot on 2006-08-03
> **neewby said:**
> Also whats the CONTROL for UBUNTU 6.06

Ubuntu does not have a centralised configuration utility like YaST.

---

### Post by neewby on 2006-08-03
>  ```
gksudo firestarter
``` and follow the wizard.

gksudo doesnt work???

---

### Post by neewby on 2006-08-03
Someone Point TO good bash lessons for newbies

so I can paruse my way around linux using the terminal I want to get good at understanding the TREE, BRANCHES, LEAFS streams roots bark etc...

---

### Post by Jagot on 2006-08-03
> **neewby said:**
> Someone Point TO good bash lessons for newbies

so I can paruse my way around linux using the terminal I want to get good at understanding the TREE, BRANCHES, LEAFS streams roots bark etc...

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by Mach1US on 2006-08-03
Someone Point TO good bash lessons for newbies

so I can paruse my way around linux using the terminal I want to get good at understanding the TREE, BRANCHES, LEAFS streams roots bark etc...
Reply With Quote

Try some O`Reilly books like "ubuntu hacks" and "shell scripting"

---

### Post by neewby on 2006-08-03
NEED to PLAY MP3 and WMA and all codecs

What I need to INSTALL:confused:

whats an Alternative for

gksudo firestarter

Or how do I view Firestarter connections

---

### Post by r4ik on 2006-08-03
Maybe this is what you want ?

[http://ubuntuforums.org/showthread.php?p=990636](http://ubuntuforums.org/showthread.php?p=990636)

Try his for a start,

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Good luck !

---

### Post by Jagot on 2006-08-03
> **neewby said:**
> NEED to PLAY MP3 and WMA and all codecs

What I need to INSTALL:confused:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by cantormath on 2006-08-03
> **neewby said:**
> WHATS the SECURITY FOR ubuntu

Do I need to download IPTABLES for or something

I need something to watch all traffic

or other


Any rundowns on What I Security Measures I should be taking Before roaming the net and other things,
Or where I can Download Doc for linux security for beginners.

other then that UBUNTU is "THE MAC"8)

Get automatix,
here is the install instructions:
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

when you install automatix, open it, click on the security sweet, and you get your antivirus, and firewall.

Make sure when you are down, to click yes when it asks if it should change back your repositories or sources.list.

---

### Post by nalmeth on 2006-08-03
Read "learn the command line" in my signature.

Go to "Ubuntu Document Storage Facility" in my signature. There is a new security section, there are a plethora of security tools.

Are you using gnome? Try installing gnome-control-center.
KDE has a good selection between kcontrol and systemsettings, but for gnome, you should be able to configure just about anything from the 'System' menu on the top panel.

---

### Post by neewby on 2006-08-03
another thing

I have INternet connection using

ADSL broadband connection wall

and my friend gave me a wireless pci card

can I use wireless pci card for anything

like connect to wireless connection???

---

### Post by Rich3077 on 2006-08-03
Thanks for the firewall instructions..
worked great.


> **T700 said:**
> Repeat after me:  "Linux is not Windows."  Say that 20 times.  :-)

1.  Keep updated.  Download and install all updates and patches that Ubuntu automatically sends you.

2.  By default, no ports are open, so a firewall is not needed.  If you like to wear pants and suspenders, go to the command line (terminal) and ```
type: sudo aptitude update
```
and then
```
sudo aptitude install firestarter
```
This will install a graphical frontend and wizard to configure IPtables.  Just go to the command line again and type ```
gksudo firestarter
``` and follow the wizard.

3.  Unless you are running a mail server that sends mail to Windows machines, you do not need an antivirus.  The only reason a mail server needs one is to avoid passing the viruses to Windows PC's.

4.  Don't run code or install programs unless you know and trust the source.

Have fun!
Paul

---

### Post by neewby on 2006-08-03
How Do i use Broken FILTER???

---

### Post by neewby on 2006-08-03
After installing and running automatix

Still cannot play wma files


Automatix is shit 

manualtix is better

---

### Post by ChadMMc on 2006-08-03
> **Jagot said:**
> Ubuntu does not have a centralised configuration utility like YaST.

I am not completely sure if this is what you mean but you can run the gnome-control-center. 

Not sure, I may be whistling in the dark. :-\"

---

### Post by neewby on 2006-08-04
Still codecs are not working after running automatix and installing codecs

---

### Post by soonindallas on 2006-08-04
> **cantormath said:**
> Get automatix,
here is the install instructions:
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

when you install automatix, open it, click on the security sweet, and you get your antivirus, and firewall.

Make sure when you are down, to click yes when it asks if it should change back your repositories or sources.list.

get automatix if you like.  do not run the script before you understand what it will do.  this script installs stuff on your computer.

---

### Post by nickpaton on 2006-08-04
> **neewby said:**
> another thing

I have INternet connection using

ADSL broadband connection wall

and my friend gave me a wireless pci card

can I use wireless pci card for anything

like connect to wireless connection???

Everyone - we're trying to deal with this on post 229156 - suggest not answering here, since it may confuse!  Any help within that post would be gratefully received.

---

### Post by UltraMathMan on 2006-08-04
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

whoops, forgot to check and see if there were more pages - sorry ](*,)

---

### Post by aysiu on 2006-08-04
Use a hard-to-guess password. Don't click **OK** on stuff that's not okay.

---

### Post by TFX360 on 2006-08-04
Hi,

NAT (your router) most of the time keeps them away. And if they really want in, they'll get in. Working ip to ip is a good way of hardening. But doesn't work in all situations and is work intensive like hell.

You can always run shields up (test of common ports and more) on [http://www.grc.com]("http://www.grc.com")

Kind regards,


TFX

---

### Post by Tomosaur on 2006-08-04
Can't believe I've never heard of Shields up. I'll be running that on the windows install to compare :P

---

### Post by TFX360 on 2006-08-04
Hi!

Believe it or not, with the firewall on in Windows and of course not adding exeptions in the firewall, it's a complete stealth system. But to be honest I never tested it without a NAT firewall.
But there is/was a difference with the firwall on/off.


Kind regards,


TFX

---

### Post by airtonix on 2006-08-05
> **neewby said:**
> another thing

I have INternet connection using

ADSL broadband connection wall

and my friend gave me a wireless pci card

can I use wireless pci card for anything

like connect to wireless connection???


You could, but i wouldnt touch it unless you know how to secure it.....unless you plan on using it as a way of saying "hey you cant prove i downloaded this xxxxxx, it could have been my neighbour or that guy parked out in the street!!"

Plausiable deniabillity for the masses.....lol

---

### Post by cleverselfreferentialname on 2006-08-05
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php) is the best guide to basic shell usage, IMHO.

Also check out the Advanced Bash Scripting guide if you want to get into it even more.

[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

But generally the first guide is adequate.

---

