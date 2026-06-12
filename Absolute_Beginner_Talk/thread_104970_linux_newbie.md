---
title: "linux newbie"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by Enter on 2005-12-17
well finally after 5 tries i installed Ubuntu linux :D
nowmy modem doesnt want to work properly so i cant connect to the internet have to use windowse xp :D 
my modem is SpeedTouch 330 can anyone point me to the driver downloads

Also what do i need to learn to use Ubuntu and what programs do i need to get

Thank you

---

### Post by bscbrit on 2005-12-17
I don't know much about the Speedmodem 330, but here are a few links to people who do.  Read through these and see if they help.  If not, then come back here,

[http://www.speedtouch.com/support.htm](http://www.speedtouch.com/support.htm)

[http://www.xs4all.nl/~pschram/english.html](http://www.xs4all.nl/~pschram/english.html)

[http://www.eglug.org/node/1074](http://www.eglug.org/node/1074)

---

### Post by kaamos on 2005-12-17
Some info in here as well: [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

---

### Post by Enter on 2005-12-17
well theres this site [http://speedtouch.sourceforge.net/](http://speedtouch.sourceforge.net/)
but it says nothing about ubuntu
btw its dsl modem :D

---

### Post by kaamos on 2005-12-17
Sorry, didn't realize that was a usb dsl-modem. The speedtouch package (that you gave the link to) can be found with synaptic. The package name is speedtouch.
Synaptic: [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

However, I found this that seems to be about the SpeedTouch 330
[https://wiki.ubuntu.com/UKSpeedtouchDSLHowTo](https://wiki.ubuntu.com/UKSpeedtouchDSLHowTo)

---

### Post by Enter on 2005-12-17
ok thanks ill check it out now...
ok then now do i need anything like a firewall or something?
dont think i need an antivirus so heres a stupid question: do i need an antivirus ? :d

---

### Post by kaamos on 2005-12-17
You won't need a firewall unless you start running a server of some kind (ssh, samba, ftp..). Ubuntu has by default all ports closed. Antivirus is only needed if your machine for example forwards files between windows machines (like a mail-server). So the antivirus programs are usually for checking files used in windows..

Short answer
- firewall: maybe, if you feel you need one, try firestarter
- AV, most likely no

---

### Post by Enter on 2005-12-17
well i have windowse on one partition :D - yess can i access them from ubuntu or no? cus i want my mp3s :D

about the firewall, dont i need to protect my self from port scans dos atacks?

sorry im not good with hardware and stuff related to it, im a web developer :D

---

### Post by bscbrit on 2005-12-17
A firewall is an extra security wall, desireable but not essential.  There are no viruses for linux 'in the wild' (They exist but are not found on the internet AFAIK).  But you could still send a virus to someone else that you had received, although it cannot affect you.  For this reason I use clamav.  It does the job efficiently and with little fuss.
But you should not worry about these until you have got you modem working.  In fact, if you install a firewall and do not set it up properly it might prevent your modem from working the way you expect it to so it is best to leave the firewall until you know you can browse, send email etc.  Some might argue that there is a risk that you could be attacked during this time but that risk is very slight.  I would strongly recommend that you do not worry about this for the time begin.
You didn't mention adware specifically (but I included it in your "etc"); there is no such thing as adware in OS software.
So my recommendation is 1. get the modem working. 2. install antivirus if you want and 3. install the firewall last.

---

### Post by kaamos on 2005-12-17
[QUOTE=Enter]well i have windowse on one partition :D - yess can i access them from ubuntu or no? cus i want my mp3s :D [/QUOTE]
Yes, you can access them. Check this: [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)
[QUOTE=Enter]about the firewall, dont i need to protect my self from port scans dos atacks?[/QUOTE] No, because all the ports are closed. :)

---

### Post by bscbrit on 2005-12-17
You can access your windows drives from Ubuntu.  If it is a FAT32 drive you can read and write, if it is NTFS you can read only. So you can easily access your mp3s etc.

kaamos is correct in advising that a firewall is not needed if you are running a standalone machine as all the ports are closed by default.  But, once you have your system working you might want to think about it as another level of security.  Certainly not essential but it might give you a warm feeling.

My antivirus detects 2 or 3 viruses a day on incoming mail.  None of them are any threat to me.  However, I would not want to send a virus to anyone else so I want to know that they are there and then remove them.  Clamav does that for me.

Now you are a linux user, you will discover that all the problems that are experienced by windows users are a thing of the past.  :p

---

### Post by Enter on 2005-12-17
well i think ill get a firewall lets live without an antivirus for once :D
and i think you missunderstood one question, sorry i didnt write it right
I meant can i access files on my windowze drives?

edit//
well ill still have to use winxp sometimes because if i want to play games etc. and use photoshop... gimp doesnt have all the thing photoshop has YET

edit2//
is there a way to remove the password becuase im an only user with no network so i dont need a password

---

### Post by bscbrit on 2005-12-17
Yes you can access your files on your windows drives.

if your windows drive is formatted as FAT32, you will be able to both read from it and write to it.

However, if your windoes drive is formatted as NTFS, then you can only safely read from it.

---

### Post by bscbrit on 2005-12-17
It is possible to enable oneself to log on automatically (without having to quote the password) but a password still must exist so that you can use the 'sudo' command (i.e. have root powers from time to time).  So the automatic log on will only save you 2 or 3 seconds each time you boot the computer.
But you are aware of the threat from crackers and other internet users.  True it is a very small threat but your password is another level of protection against this threat.  Do you really save that much time by making your machine less secure?

You can automate the login by:

System -> Administration -> Login Screen Setup

and select the automatic login from there.

---

### Post by Enter on 2005-12-17
well i think about it :)
well im gonna go try install the modem firmware

---

### Post by Enter on 2005-12-17
ok im having problems please be patient
ok ive downloaded the [http://ftp.linux.it/pub/People/md/warez/speedtouch-firmware_0.3012k_all.deb](http://ftp.linux.it/pub/People/md/warez/speedtouch-firmware_0.3012k_all.deb)
how do i install it now?

---

### Post by bscbrit on 2005-12-17
There is an Ubuntu specific package called 'speedtouch' which will install itself if you use synaptic or apt-get.  You can install your current package using 'sudo dpkg -i yourpackagename', but I would recommend the ubuntu version.

---

### Post by Enter on 2005-12-17
i searched and i searched the synaptic and there was no package called speedtouch
anyway i found this thread [http://ubuntuforums.org/showthread.php?t=44763&highlight=speedtouch](http://ubuntuforums.org/showthread.php?t=44763&highlight=speedtouch)

thanks anyway

---

### Post by bscbrit on 2005-12-17
You might need to check that all of you repositories are enable under synaptic - it is there, honest.  But your own package should do.

---

### Post by Enter on 2005-12-17
how do i check that?
because that thing didnt work i get a fatal error :(

---

### Post by Zimmer on 2005-12-17
Try and sort your repsitories out so that Synaptic sees more packages .It is a lot easier to use Synaptic than trying to manually install stuff...

Have a look here for how to do that
[http://ubuntuguide.squarecows.com/doku.php#repositories](http://ubuntuguide.squarecows.com/doku.php#repositories)

Zimmer

---

### Post by Enter on 2005-12-17
ok nothing works someone HELP!!!!
or im gonna shoot myself or smash my modem :D
i tryer
[http://www.ubuntuforums.org/showthread.php?t=44763&highlight=speedtouch](http://www.ubuntuforums.org/showthread.php?t=44763&highlight=speedtouch)
it gives a fatal error on step 3
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)
didnt work tryed about everything
[http://s1x.homelinux.net/projects/speedtouch_suite](http://s1x.homelinux.net/projects/speedtouch_suite)
doesnt generate something

---

### Post by rama on 2005-12-17
[QUOTE=bscbrit]There is an Ubuntu specific package called 'speedtouch' which will install itself if you use synaptic or apt-get.  You can install your current package using 'sudo dpkg -i yourpackagename', but I would recommend the ubuntu version.[/QUOTE]

Hi. I 'm also trying to setup my speedtouch router (530) to work through the usb port. So I got the speedtouch package from the repositories.Then what?

@Enter : Did you install this package and still failed to set up the router to work or did you try other methods?

PS: Just to clarify things, I am currently using the ethernet port of the same router. So I 'm guessing that all I need to do is make Ubuntu see the rooter as a network interface. Right?

---

### Post by Enter on 2005-12-17
im still trying to install it :D

---

### Post by rama on 2005-12-17
Have you tried these 2 [steps?]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#synaptic-usage") after doing that, update (via synaptic) and then search again for the package.

PS: The instructions on the link I gave you are pretty much the same with those that Zimmer gave you, but instead of doing the process "manually" you 'll use synaptic. Guess it's more fail safe.

---

### Post by Enter on 2005-12-17
yay i got it to work this way
[http://www.ubuntuforums.org/showthread.php?t=44763&highlight=speedtouch](http://www.ubuntuforums.org/showthread.php?t=44763&highlight=speedtouch)

im off to bed see ya early in the morning guys :D

---

### Post by bscbrit on 2005-12-17
Enter - great news.  Sorry but I had to go offline for a few hours - hard to believe, I know, but I have a life outside of linux!  See you around the forums.

---

### Post by Enter on 2005-12-18
no problem, i hope i stay theres so much to learn now :D
so ok where do i get firestarter? in the synaptic?

---

### Post by bscbrit on 2005-12-18
Yes, that the best way to install any program, IMHO.  If you search on 'firestarter' using the Search link at the top of this page you should find plenty of advice on setting it up.

---

