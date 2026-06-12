---
title: "Questions. Maybe moving to Ubuntu."
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by muxecoid on 2006-06-18
I moved the usual linux chain Mandriva->Fedora->Debian->SuSE.
I was generally satisfied in SuSE although some things (improper detection of my monitor modelines, poor USB support) did not please me. Recently I updated SuSE 10.0 to 10.1 and I feel like it was great leap backward. The system is relatively unstable now. I reinstalled. The unstability remained, but the automatic configuration worked even worse, than in 10.0. Also it messed up by MBR so I needed to remove my master drive from list in BIOS to boot WinXP.
Ubuntu looks like the next step in my linux chain. I'm already downloading it (i386-DVD), but there are some questions about it.
Does it detect and easily installs AC97 integrated audio?
Does it detect and configure mouse as 3-button wheeled if it is?
Does it include transparent installation of Flash player?
Does it have transparent Java installation?
If so would Opera Web Browser see Java and Flash without extra configuration?
[offtopic] (Yes, I know, Mozilla is great, but it's great for W3C DHTML and most web-sites, even corporate ones, in Israel are written in Microsoft DHTML so Mozilla does not work well here and you need Opera. Some sites here are written for IE or Mozilla but not Opera so you must have as many browsers as possible. Just imagine, most of the web hosting providers in Israel use flawy MS Server instead pf apache under linux. Some Israeli hosters even use webserver for Mac).
[/offtopic]
**Is there an easy way to install nVidia GeForce drivers?** What about nVidia drivers from LiveCD? (with showing license on boot or whatever).
Does it generate modelines for CRT displays correctly?
**What about automatically configuring Israeli cable ISPs with DHCP+pptp connection? What about connecting to Israeli ISPS from liveDVD?**
It's GNOMish... Can I turn of FAMD painlessly?
What about runlevel configuration? What about managing apache+MySQL from runlevel tool?
What about easy dual boot with WinXP installed on slave HDD?
What about writing to NTFS?
Also needed: Easy codec install (DivX, XviD, MPEG2).
Correctly detecting scanners. (UMAX Astra 3400)
Correctly working with S1-MP3 USB drive.
Good Palm (JPilot) support.
No permission security paranoia when it comes to ports in /dev
Stable, but uo to date online apt repository.


Waiting for answers.

---

### Post by Nonno Bassotto on 2006-06-18
[QUOTE=muxecoid]
Does it detect and easily installs AC97 integrated audio?
Does it detect and configure mouse as 3-button wheeled if it is?
Does it include transparent installation of Flash player?
Does it have transparent Java installation?
[/QUOTE]
I'm not sure about the rest of your question, but this things worked without any problem for me. Don't forget to add extra repositories, like the plf, for codecs and so on.

---

### Post by muxecoid on 2006-06-18
Thank you. Luckily these features work OK in most modern linux distros.

What about distros with easy connect to ISPs in Israel?

---

### Post by cotcot on 2006-06-18
Opera can be installed using the instructions in [https://wiki.ubuntu.com/OperaBrowser]("https://wiki.ubuntu.com/OperaBrowser")

Positive for AC97, 3-wheel mouse, java, codecs (the clue is having the correct repositories. Please check Dapper guides. There are several available. Here is one : [http://doc.gwos.org/index.php/DapperGuide]("http://doc.gwos.org/index.php/DapperGuide")

Your scanner is not supported : [http://http://www.sane-project.org/cgi-bin/driver.pl?manu=UMAX+&model=astra&bus=any&v=&p=]("http://http://www.sane-project.org/cgi-bin/driver.pl?manu=UMAX+&model=astra&bus=any&v=&p=")

Writing to NTFS is possible but marked as 'experimental'. This means do this on your own risk.

---

### Post by muxecoid on 2006-06-18
> Your scanner is not supported
I followed the link. Astra 3400 is listed as unsupported although it was completely supported in earlier versions of sane. Also please note that UMAX Astranet ia101 is completely supported although it is just renamed Astra 3400. Sometimes I really hate linux way and linux philosofy of screwing up everything.

---

### Post by uzi09 on 2006-06-18
well, i'd recommend giving the live cd a try before going forth with the install.

also, ubuntu has a new version out every 6 months!! so it's pretty frikkin up-to-date with **_most_** of the latest and greatest hardware.

---

### Post by muxecoid on 2006-06-19
What about logging in as root?

---

### Post by aysiu on 2006-06-19
[QUOTE=muxecoid]What about logging in as root?[/QUOTE]
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by muxecoid on 2006-06-19
People, thank you. Tried it, it looks great as for now. Or, at least, better than many other distros.

---

### Post by tseliot on 2006-06-20
[QUOTE=muxecoid]**Is there an easy way to install nVidia GeForce drivers?** What about nVidia drivers from LiveCD? (with showing license on boot or whatever).[/QUOTE]
My script (Envy):
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

or the excellent Automatix

---

### Post by Gustav on 2006-06-20
The modline detection isn't that great but it's quite easy to fix after install. (detected 1280x1024 but after some fixing I've got 1600x1200@85Hz)

---

### Post by stig on 2006-06-20
[QUOTE=cotcot]Your scanner is not supported : [http://http://www.sane-project.org/cgi-bin/driver.pl?manu=UMAX+&model=astra&bus=any&v=&p=]("http://http://www.sane-project.org/cgi-bin/driver.pl?manu=UMAX+&model=astra&bus=any&v=&p=")
[/QUOTE]

Clicking on this link takes you to the Microsoft web site whereas entering it in a browser gives the sane page.

---

