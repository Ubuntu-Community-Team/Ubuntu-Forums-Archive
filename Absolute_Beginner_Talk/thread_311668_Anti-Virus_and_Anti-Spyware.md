---
title: "Anti-Virus and Anti-Spyware"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by ityro on 2006-12-03
My system: HP/compaq nx9010 Notebook with Pentium 4 2.66GHz CPU, 40GB HDD, 768MB RAM, CDROM: CD-R, and Floppy; Printer: HP Deskjet 5740; Scanner: HP Scanjet 3770; and an Iomega 80GB removable USB HDD. Windows System: XP Pro (SP2).

Hello to all,

I believe I read on one of the Ubuntu Sites/Forums that on a dual-boot system all the Anti-Virus and Anti-Spyware programs used on the Windows System will also benefit Ubuntu.

Anyone out there agree?  Any Anit-Virus, Anti-Spyware suggestions for Ubuntu?

I installed Ubuntu 11/28/2006 but have been using the following Security Programs on the XP side:
Zone Alarm Suite 6.5, WinPatrol, Search&Destroy, SnoopFree Privacy, HostsMan, SOPHOS Rootkit, Spyware Blaster, Windows Defender and the Malicious Software Removal Tool.

Thank You for your time.

---

### Post by xtacocorex on 2006-12-03
I don't think there are any anti-spyware programs that are stand alone for Linux, but there is spam-assassin for email servers.  There could be a way to use it to scan files, but I've never used it.

There is also clamav for anti-virus.

---

### Post by Sef on 2006-12-03
You don't need an anti-virus for GNU/Linux, unless you have an email client, and only then so you don't infect your friends who use Windows.  It is possible for a virus to ride on top of the GNU/Linux system: i.e. your system will be an asymptomatic carrier.

---

### Post by ddbann on 2006-12-03
what about web based email. gmail, hotmail etc?

---

### Post by equal on 2006-12-03
Web based email services generally have their own built in anti-virus software. Your system AV can't scan their server, but it will scan any attachments you download .

---

### Post by ityro on 2006-12-03
Thanks to all. I have installed Clamav but I can't find it. I have looked in all the menus but it's not there. However, when I search system files it is there.

I tried to use Avast, none of the versions for Ubuntu would install but I am registered.

Thanks Again.

---

### Post by ReaderRat on 2006-12-03
Just FYI....You do have a firewall protecting you, called iptables. The GUI front-end for it can be installed through Synaptic Package Manager. It is called **[COLOR="Red"]Firestarter[/COLOR]**.

[**[color=red]Firestarter Manual[/color]**](http://www.fs-security.com/docs.php)

---

### Post by az on 2006-12-03
> **ityro said:**
> 

I believe I read on one of the Ubuntu Sites/Forums that on a dual-boot system all the Anti-Virus and Anti-Spyware programs used on the Windows System will also benefit Ubuntu.

No.  That is false.  Those applications offer no benefit.  They are made for windows along with all the viruses and spyware out there.

> **ityro said:**
> 

Anyone out there agree?  Any Anit-Virus, Anti-Spyware suggestions for Ubuntu?

Just keep up-to-date with your security updates.  This is free-libre open source software.  It is ridiculously easy to make spyware for closed-source operating systems.  This is not so for free and open systems.  How do you think it can get installed on your system?

The same goes for viruses - They work well on systems which have vulnerabilities that cannot be closed (it would make your system stop working).  This is not the case for free and open software.

> **ityro said:**
> 
I installed Ubuntu 11/28/2006 but have been using the following Security Programs on the XP side:
Zone Alarm Suite 6.5, WinPatrol, Search&Destroy, SnoopFree Privacy, HostsMan, SOPHOS Rootkit, Spyware Blaster, Windows Defender and the Malicious Software Removal Tool.


How do people live like that?

---

### Post by drphilngood on 2006-12-03
> **ityro said:**
> Thanks to all. I have installed Clamav but I can't find it. I have looked in all the menus but it's not there. However, when I search system files it is there....
Install clamtk with it for a GUI or try Aegis, it´s another virus scanner that many recommend.

---

### Post by ityro on 2006-12-03
> **ReaderRat said:**
> Just FYI....You do have a firewall protecting you, called iptables. The GUI front-end for it can be installed through Synaptic Package Manager. It is called **[COLOR="Red"]Firestarter[/COLOR]**.

[**[color=red]Firestarter Manual[/color]**](http://www.fs-security.com/docs.php)

I did not know about iptables but I did install Firestarter about 10 minutes after installing Ubuntu.

I have one problem with Firestarter: It does not start on system start or restart. I have set/reset the option but I have to manually start it each time. Should I uninstall/reinstall Firestarter or just uninstall and leave it to iptables or ---?

Thanks for your help.

---

### Post by mdsmedia on 2006-12-03
> **azz said:**
> 
How do people live like that?I think the same thing when Windows users reel off the security "system" they have on their machines. 

It's like having the marines gaurding the new bank you've purchased and left all the doors open, when you could have Fort Knox for free and just open the door after looking through a peephole to make sure your visitor is welcome.

---

### Post by ReaderRat on 2006-12-03
As I said, FYInfo, I am not as "security conscious" as you, and I run Ubuntu with iptables. **[COLOR="Red"]Firestarter, ClamAV, Panda AV[/COLOR]** are for folks who don't trust Linux yet.

---

### Post by hardyn on 2006-12-03
I have not tried it, but AVG does have a linux anivirus program; i be curious to hear about it if anybody tries it out.

---

### Post by mdsmedia on 2006-12-03
> **ReaderRat said:**
> As I said, FYInfo, I am not as "security conscious" as you, and I run Ubuntu with iptables. **[COLOR="Red"]Firestarter, ClamAV, Panda AV[/COLOR]** are for folks who don't trust Linux yet.I'm not implying I trust Linux implicitly.....although I do trust Linux and I don't worry about it either. I have iptables (obviously) and Firestarter installed, and clamav too....just in case.

---

### Post by xopher on 2006-12-03
> Security Programs on the XP side:
Zone Alarm Suite 6.5, WinPatrol, Search&Destroy, SnoopFree Privacy, HostsMan, SOPHOS Rootkit, Spyware Blaster, Windows Defender and the Malicious Software Removal Tool.

Funny :)

And to answer the question how to start it on system start (firestarter), you don't need to. Firestarter is just a graphical way of configuring the firewall, which is enabled even if firestarter is closed, if you didn't disable it of course.

If you want it to run on system start, there are a few guides on the forums, so try searching.

---

### Post by drphilngood on 2006-12-03
> **ityro said:**
> ...I have one problem with Firestarter: It does not start on system start or restart. I have set/reset the option but I have to manually start it each time. Should I uninstall/reinstall Firestarter or just uninstall and leave it to iptables or ---?

Thanks for your help.

See here:

[Firestarter_Guide]("http://doc.gwos.org/index.php/Firestarter_Guide")

---

### Post by ityro on 2006-12-03
> **drphilngood said:**
> Install clamtk with it for a GUI or try Aegis, it´s another virus scanner that many recommend.

Thanks so much. Could not get Clamav to go but I did get Aegis going.

---

### Post by poohbear1616 on 2006-12-03
Someone correct me if I'm wrong here.......clamav runs under the title of freshclam in the back ground......also you can install klamav which is a gui for clamav, which ads it to your menu.

---

### Post by drphilngood on 2006-12-03
> **ityro said:**
> Thanks so much. Could not get Clamav to go but I did get Aegis going.

Now that you have installed clamtk, you can just type ¨clamtk¨ in a terminal to run it but to update your signatures and scan certain files you´ll need to run it as root.

edit:
Here is readme file for it that you might like:
[Clamtk_Readme-file]("http://clamtk.sourceforge.net/README")

---

### Post by drphilngood on 2006-12-03
> **poohbear1616 said:**
> Someone correct me if I'm wrong here.......clamav runs under the title of freshclam in the back ground......also you can install klamav which is a gui for clamav, which ads it to your menu.

Klamav is for the KDE Desktop.  Just see here:
[http://klamav_Main-Page]("http://klamav.sourceforge.net/klamavwiki/index.php/Main_Page")

---

### Post by poohbear1616 on 2006-12-04
> Klamav is for the KDE Desktop.

 :oops: Sorry about that, Was asleep at the wheel and forgot which forum I was in.

---

### Post by drphilngood on 2006-12-04
> **poohbear1616 said:**
> :oops: Sorry about that, Was asleep at the wheel and forgot which forum I was in.

Nothing to be sorry about my friend.  This isn´t a competition; we´re just here to help each other.;)

---

### Post by jbaloul on 2007-08-09
This mite answer some of your questions...
[http://howtoforums.net/viewtopic.php?t=549](http://howtoforums.net/viewtopic.php?t=549)

JB

---

