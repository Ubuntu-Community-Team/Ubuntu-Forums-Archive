---
title: "root terminal and Skype"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by Dutch on 2005-11-09
Hi,

To get Skype working I tried this how to :
[http://forum.skype.com/viewtopic.php?t=4489](http://forum.skype.com/viewtopic.php?t=4489)
I started with : Q: My driver loaded correctly but I still have no sound! 

Then I found out about the Skype How to from the unofficial Ubuntu 5.04 starters site.
But when I try to open a ROOT TERMINAL I get this message.
I fucked something up, I gess.
##
Failed to run /usr/bin/x-terminal-emulator:
 Child terminated with 1 status
##

How can I use my root terminal again ?

---

### Post by darth_vector on 2005-11-09
open a normal terminal and type

sudo su -

put in your password and you will have a root terminal.

---

### Post by Dutch on 2005-11-09
[QUOTE=darth_vector]open a normal terminal and type

sudo su -

put in your password and you will have a root terminal.[/QUOTE]

okt thanks, when I do That the terminal says:

##
paul is not in the sudoers file.  This incident will be reported.
paul@Paul:~$
##

---

### Post by darth_vector on 2005-11-09
is this your machine? the first account created in an ubuntu install is the adminstrator and should have an entry in the sudoers file.

if you are not the administator and there is no GRUB password, one way around this is to boot ubuntu into safe mode (there are no passwords in safe mode) and add yourself into the sudoers list.

alternatively you can ask the admin of the machine to give you root access. ask nicely :)

---

### Post by Dutch on 2005-11-09
[QUOTE=darth_vector]is this your machine? the first account created in an ubuntu install is the adminstrator and should have an entry in the sudoers file.

if you are not the administator and there is no GRUB password, one way around this is to boot ubuntu into safe mode (there are no passwords in safe mode) and add yourself into the sudoers list.

alternatively you can ask the admin of the machine to give you root access. ask nicely :)[/QUOTE]


Haha :-) No it is my own PC.
Because I wanted to use Skype i did something like this:
##

"Q: My driver loaded correctly but I still have no sound!

The first thing you should do is run the "alsamixer" program. By default, all channels are muted on a newly installed ALSA system so you will have to manually unmute the ones you want. The best tool for the job is alsamixer, which can access all the different channels offered by ALSA.

It might also be a permission problem. Initially, though that might depend on your distribution, I believe the sound devices are owned by root and only root has read/write permissions on it. If you system has an "audio" group in /etc/group, try adding yourself to that one. As root, execute the following command:
Code:

usermod -Gaudio username

Replace username with the name of the user you're going to run Skype with. You can also change the ownership of the dsp device so you can access it as a regular user, or set the permissions so that all users have read/write access to the device.
Code:

chown username /dev/dsp
chmod 666 /dev/dsp


The first line will make username the owner of the device. The second line will give everyone with an account on the system read/write access to the sound device. Note: You might have a /dev/dsp device even if you are using devfs - this will just be a symlink to /dev/sound/dsp so you do not have to fiddle with it.
Code:

# With devfs
$ ls -l /dev/dsp
lr-xr-xr-x 1 root root 9 Jul 2 02:03 /dev/dsp -> sound/dsp

# Without devfs
$ ls -l /dev/dsp
crw------- 1 username audio 14, 3 Jan 1 1970 /dev/dsp
## 

I think with this I fucked up my sudo rights ?
The sudo name is Paul, and I'm user paul

How can I get my rights back ?

---

### Post by Dutch on 2005-11-09
When I try to ad myself again > users and groups> i type in my password (root) then I get the message:

#
Failed to run users-admin:
 Child terminated with 1 status
#

Is this a serious problem ?

---

### Post by darth_vector on 2005-11-09
lol. i think booting into single user mode is your best bet. reboot your machine and go into the GRUB menu, highlight the current kernel you are using and type "e". this will allow you to edit the kernel argument. at the end of the kernel argument add ", single" without the quotes.

press enter to get back to the grub menu, then boot the kernel (by pressing enter again). you will get a root terminal (no passwords). open up the file /etc/sudoers in your fav text editor (it will have to be vim or pico, graphical stuff wont work) and add the following line:

paul ALL=(ALL)ALL

then

shutdown -r now

you may have to get rid of the single user mode argument for the kernel (i cant remember), but next time the machine boots you should be able to sudo again.

good luck. post back if you have problems

---

### Post by Dutch on 2005-11-09
[QUOTE=darth_vector]lol. i think booting into single user mode is your best bet. reboot your machine and go into the GRUB menu, highlight the current kernel you are using and type "e". this will allow you to edit the kernel argument. at the end of the kernel argument add ", single" without the quotes.

press enter to get back to the grub menu, then boot the kernel (by pressing enter again). you will get a root terminal (no passwords). open up the file /etc/sudoers in your fav text editor (it will have to be vim or pico, graphical stuff wont work) and add the following line:

paul ALL=(ALL)ALL

then

shutdown -r now

you may have to get rid of the single user mode argument for the kernel (i cant remember), but next time the machine boots you should be able to sudo again.

good luck. post back if you have problems[/QUOTE]


Oke I did **** it up realy then ! :-)

Oke I can edit that file with pico.
But I don't understand this line:
shutdown -r now What do u mean by it ?

Do I have to write it also in that file ?

After changing the file there is a new file sudoers~

---

### Post by ubuntu_demon on 2005-11-09
[QUOTE=Dutch]Oke I did **** it up realy then ! :-)

Oke I can edit that file with pico.
But I don't understand this line:
shutdown -r now What do u mean by it ?

Do I have to write it also in that file ?

After changing the file there is a new file sudoers~[/QUOTE]
No don't put that in the file.

just type it after editting so your computer reboots. This is the same (without the $) :
$ reboot

to install skype I recommend this repository :

```

## http://wiki.ubuntu-fr.org/doc/plf
deb ftp://antesis.freecontrib.org/freecontrib/mirrors/ubuntu/plf/ breezy free non-free
deb-src ftp://antesis.freecontrib.org/freecontrib/mirrors/ubuntu/plf/ breezy free non-free

```

I don't think you have to do anything with permissions or dev/dsp. Just put these lines in your /etc/apt/sources.list and type :
$sudo apt-get update ; sudo apt-get install skype

---

### Post by Dutch on 2005-11-09
THANKS man !

I just had to write paul when I wrote Paul !
The kernel line deleted  the "single" after rebooting !

How about this HOW TO for Skype ?
[http://ubuntuguide.org/#skype](http://ubuntuguide.org/#skype)

When updating the sorce list I getthis message:

(gedit:7313): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
root@Paul:/home/paul #


Is that a problem ? ore just ignore it ? ! ?

---

### Post by ubuntu_demon on 2005-11-09
[QUOTE=Dutch]THANKS man !

I just had to write paul when I wrote Paul !
The kernel line deleted  the "single" after rebooting !
[/QUOTE]

what do you mean ? I don't understand what you are saying. I'm dutch too you can add me on IM (see the PM I sent you or my profile).

[QUOTE=Dutch]
How about this HOW TO for Skype ?
[http://ubuntuguide.org/#skype](http://ubuntuguide.org/#skype)
[/QUOTE]

That guide is for hoary. I assume you run breezy. 

you can find breezy guides for doing stuff on the forums and in the wiki. I searched for you. You should follow the breezy one here :

[https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto)

You can use the package they have available or use the sources.list the one I gave (which has other stuff as well). It's best to use the repository because that way you can easily upgrade the package. (using apt / synaptic or update manager)

use the part from the guide beginning with "display configuration" if you decide to use the repo

[QUOTE=Dutch]
When updating the sorce list I getthis message:

(gedit:7313): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
root@Paul:/home/paul #

Is that a problem ? ore just ignore it ? ! ?[/QUOTE]

You should never be root unless you have messed up and need to boot into single user mode. After that just reboot and do everything with sudo.

the proper way to update your sources.list :
$ sudo pico /etc/apt/sources.list
OR
$ sudo gedit /etc/apt/sources.list

then (this will also upgrade your packages):
$sudo apt-get update ; sudo apt-get upgrade 

PS :
to get into single user mode you can also just choose recovery mode from the grub menu
here is my complete sources.list : 
[http://www.ubuntuforums.org/showthread.php?t=87946](http://www.ubuntuforums.org/showthread.php?t=87946)

---

### Post by ubuntu_demon on 2005-11-09
You said on IM that you are still using hoary. I'm sorry for the confusion. 

I figured you ran breezy because you didn't mention you ran hoary. I'm sorry for that. 
To install skype in hoary just do as outlined in the hoary section of :
[https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto)

If you have messed up your sources.list by mixing breezy and hoary stuff  I hope you didn't mess up too much. But no worries. We can help you :)

as long as you haven't typed (or upgraded using synaptic or update manager) :
$ sudo apt-get upgrade
you are still using hoary. If you have upgraded there is no easy way back ... it's the easiest to upgrade to breezy (see below).

Here's a sources.list for hoary :

```

deb http://nl.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nl.archive.ubuntu.com/ubuntu hoary universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu hoary universe multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security universe multiverse

## you might want to uncomment these lines (especially if you used them before)
##deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
##deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

## this is the skype repo from the wiki skypehowto
deb http://download.skype.com/linux/repos/debian/ stable non-free

```

I don't know about the current state of the hoary mirrormax extras repo.  But
You can get w32codecs and other restricted stuff for hoary here :
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

You may want to uncomment the backports repo.

If you decide to upgrade to breezy you can use my previously given breezy sources.list and look here for instructions :
[https://wiki.ubuntu.com/BreezyUpgrade](https://wiki.ubuntu.com/BreezyUpgrade)

This can safely be done. But in some instances you have to reconfigure xserver-xorg by :
$sudo dpkg-reconfigure xserver-xorg

---

### Post by ubuntu_demon on 2005-11-09
Okay I have messed up in my explanation a little here. Now we are upgrading to breezy. 

never assume a user is running breezy --> lesson learned

---

### Post by ubuntu_demon on 2005-11-09
I have to leave in half an hour so here are some tips.

Because you already have upgraded your existing packages to breezy this is the way to go. To make sure you have everything from breezy please do this command :

$ sudo apt-get install ubuntu-base ubuntu-desktop ; sudo apt-get dist-upgrade

[I]don't do the italic stuff from these two alinea's if the upgrade went well :
if you run into trouble with this previous command. Try this :
$sudo apt-get install ubuntu-base ubuntu-desktop -f

If that doesn't work please post the exact error. This website explains about how to deal with such problems on debian. But apt-get works the same in Ubuntu just don't go changing your sources.list into a debian sources.list ;) --> [http://www.linux.com/article.pl?sid=05/10/12/1952217](http://www.linux.com/article.pl?sid=05/10/12/1952217)[/I]

Now Reboot. 

If X doesn't start type this command in the terminal :
$sudo dpkg-reconfigure xserver-xorg

(answer each question with the default answer if you don't know what to choose. And make sure you choose the simple monitor configuration.)

Now look at the Post-Upgrade instructions from [https://wiki.ubuntu.com/BreezyUpgrade](https://wiki.ubuntu.com/BreezyUpgrade)

edit : might be useful for other people who want to help Dutch. His sources.list is posted here : [http://www.ubuntuforums.org/showpost.php?p=479100&postcount=3](http://www.ubuntuforums.org/showpost.php?p=479100&postcount=3)

[I]PS :
normally you won't go :$ sudo apt-get install ubuntu-base ubuntu-desktop ; sudo apt-get dist-upgrade

but you would do it this way (which has the least chance of problems) :

sudo apt-get install ubuntu-base ubuntu-desktop
change sources.list
sudo apt-get dist-upgrade[/I]

---

### Post by Dutch on 2005-11-09
Mmm after upgrading and doing the ; command I booted again.
The Grubb loader is there, no problem.But when starting up I get only the tty1 screen with login an d password question.
But no normal inlog screen.

I'll try later (after geting some sleep now 0:45 AM )to do something about the xserver.

Now working with windows....

---

### Post by ubuntu_demon on 2005-11-09
Can't hurt to make sure everything is installed by typing the command again:
$sudo apt-get install ubuntu-base ubuntu-desktop ; sudo apt-get dist-upgrade

To configure your xserver-xorg do (like I explained previously) :
$sudo dpkg-reconfigure xserver-xorg

talk to you tomorrow. Good night. (I've just arrived at my GF's place)

good luck :)

---

### Post by Dutch on 2005-11-10
> **ubuntu_demon]Can't hurt to make sure everything is installed by typing the command again:
$sudo apt-get install ubuntu-base ubuntu-desktop  said:**
> 

After doing this he says: Er zijn vereisten waaraan niet voldaan is, probeer -f te gebruiken
[QUOTE=ubuntu_demon]

To configure your xserver-xorg do (like I explained previously) :
$sudo dpkg-reconfigure xserver-xorg

Mmm I did that.Then he says, thers is no Xserver installed.
Then I say: sudo apt-get install X-server-xorg
Then he says can't find X-server-xorg
[QUOTE=ubuntu_demon]
talk to you tomorrow. Good night. (I've just arrived at my GF's place)

good luck :)[/QUOTE]

Glad u made it to the trains !
It is a little difficult now with no x-server ore place to get it from.
But w'll get there !

edit: bij apt-get install xserver-xorg geeft aan :
vereisten Ubuntu minimaal maar het zal niet geinstalleerd worden.
Vereisten Ubuntu standaard maar het zal niet geinstalleerd worden.

vereisten Nautilus.data(>=2.12.1-ubuntu1) maar geinstaleerd is 1:2.12.1-ubuntu2

---

### Post by ubuntu_demon on 2005-11-10
[QUOTE=Dutch]After doing this he says: Er zijn vereisten waaraan niet voldaan is, probeer -f te gebruiken

Mmm I did that.Then he says, thers is no Xserver installed.
Then I say: sudo apt-get install X-server-xorg
Then he says can't find X-server-xorg
[/quote]

Now you have to apply the (italic) stuff I said previously. This is the case because of the weird way the upgrading was done. It can be hard to solve but it probably isn't impossible to solve.

I'm gonna explain it a bit below. If it doesn't work post the errors. I'll talk to you tonight on msn. good luck!

[QUOTE=Dutch]
Glad u made it to the trains !
[/quote]

me too :)

[QUOTE=Dutch]
It is a little difficult now with no x-server ore place to get it from.
But w'll get there !
[/quote]

Yeah we'll probably get there :)

The next time that you upgrade to the next ubuntu version make sure to exactly follow the way the wiki suggests then these apt problems won't arise (you may have to reconfigure xserver-xorg though).

One question : is your /home on a different partition than / ?
If you don't know just post the results of :
$ mount

[QUOTE=Dutch]
edit: bij apt-get install xserver-xorg geeft aan :
vereisten Ubuntu minimaal maar het zal niet geinstalleerd worden.
Vereisten Ubuntu standaard maar het zal niet geinstalleerd worden.

vereisten Nautilus.data(>=2.12.1-ubuntu1) maar geinstaleerd is 1:2.12.1-ubuntu2[/QUOTE]

Try this :
$sudo apt-get -f install
$sudo apt-get -f remove
$sudo apt-get upgrade -f dist-upgrade

*** (look below)

$ sudo apt-get remove firefox mozilla-firefox  -f
$sudo apt-get install ubuntu-minimal -f
$sudo apt-get install ubuntu-base -f
$sudo apt-get install xserver-xorg -f
$sudo apt-get install nautilus -f
$sudo apt-get install ubuntu-desktop -f
$sudo apt-get dist-upgrade -f
$sudo apt-get --purge remove portmap -f

now this command won't show up any more errors if you are lucky :
$sudo apt-get install ubuntu-base ubuntu-desktop ; sudo apt-get dist-upgrade

But If there are errors please post ALL the exact errors. 

If it does work now is the time to do a reboot. If X doesn't start then : sudo dpkg-reconfigure xserver-xorg

After the upgrade is done and X is running look at the post-upgrade instructions. And ask us if you don't understand. 
(for some reason there are two slightly different pages)

[https://wiki.ubuntu.com/BreezyUpgrade](https://wiki.ubuntu.com/BreezyUpgrade)
[https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)

If you want to learn about apt-problems : this website explains about how to deal with such problems on debian. (you have a dist-upgrade problem so not everything applies to you IMO) But apt-get works the same in Ubuntu just don't go changing your sources.list into a debian sources.list --> [http://www.linux.com/article.pl?sid=05/10/12/1952217](http://www.linux.com/article.pl?sid=05/10/12/1952217)

for some reason this article isn't available on this time. But I found it in google's cache here :

[http://64.233.183.104/search?q=cache:3C61n_0xKbYJ:www.linux.com/article.pl%3Fsid%3D05/10/12/1952217](http://64.233.183.104/search?q=cache:3C61n_0xKbYJ:www.linux.com/article.pl%3Fsid%3D05/10/12/1952217)


*** if there is some package that you are sure belongs to hoary and is still causing troubles then do :

$ dpkg --purge* packagename*

---

### Post by Dutch on 2005-11-10
Mmm glad to hear from U.
Mmmm next time when u upgrade ? 
This started just with getting the sound to work with Skype.

I'll print ure post and switch over to Linux.
I'll edit the results.

Like to hear from you on MSN maybe with mic ?

Edit later:

---

### Post by ubuntu_demon on 2005-11-10
[QUOTE=Dutch]Mmm glad to hear from U.
Mmmm next time when u upgrade ? 
[/QUOTE]

for example when you move to Dapper

[QUOTE=Dutch]
This started just with getting the sound to work with Skype.
[/QUOTE]

I know. It went wrong when I thought you was running breezy and when you didn't notice my sources.list was for breezy. I'm really sorry for that,

[QUOTE=Dutch]
I'll print ure post and switch over to Linux.
I'll edit the results.
[/QUOTE]

okay thnx

[QUOTE=Dutch]
Like to hear from you on MSN maybe with mic ?

Edit later:[/QUOTE]

Do you have a seperate /home partition ? In the worst case scenario you have to reinstall Ubuntu having a seperate /home partition is easy if that would be required.

I'm currently online. I'll stay online (but I also have to spend time with my girlfriend).

Maybe gnome-meeting is possible with this pc. But it is a very slow pc and I don't know whether that will work.(currently logged into a pc at my home using vnc because that's faster)

---

### Post by Dutch on 2005-11-10
No exuses needed.U were realy great with helping me out !
U did a great job Thanks.
I'm using Ubuntu again the new version !

Here is my test result with:

sudo apt-get install ubuntu-base ubuntu-desktop ; sudo apt-get dist-upgrade

The result is:

##
paul@Paul:~$ sudo apt-get install ubuntu-base ubuntu-desktop ; sudo apt-get dist-upgrade
Password:
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
ubuntu-base is reeds de nieuwste versie.
ubuntu-desktop is reeds de nieuwste versie.
0 pakketten opgewaardeerd, 0 nieuwe pakketten geïnstalleerd, 0 verwijderen en 1 niet opgewaardeerd.
7 pakketten niet volledig geïnstalleerd of verwijderd.
Er moeten 0B aan archieven opgehaald worden.
Na het uitpakken zal er 0B extra schijfruimte gebruikt worden.
Instellen van postfix (2.2.4-1ubuntu2) ...

Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Starting Postfix Mail Transport Agent... postfix/postfix-script: fatal: the Postfix mail system is already running
                                                                         [fail]
invoke-rc.d: initscript postfix, action "start" failed.
dpkg: fout bij afhandelen van postfix (--configure):
 subproces post-installation script gaf een foutwaarde 1 terug
dpkg: vereistenproblemen verhinderen de configuratie van mailx:
 mailx is afhankelijk van postfix | mail-transport-agent; maar:
  Pakket postfix is nog niet geconfigureerd.
  Pakket mail-transport-agent is niet geïnstalleerd.
  Pakket postfix die voorziet in mail-transport-agent is nog niet geconfigureerd.
dpkg: fout bij afhandelen van mailx (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van mutt:
 mutt is afhankelijk van postfix | mail-transport-agent; maar:
  Pakket postfix is nog niet geconfigureerd.
  Pakket mail-transport-agent is niet geïnstalleerd.
  Pakket postfix die voorziet in mail-transport-agent is nog niet geconfigureerd.
dpkg: fout bij afhandelen van mutt (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van lsb-core:
 lsb-core is afhankelijk van postfix | mail-transport-agent; maar:
  Pakket postfix is nog niet geconfigureerd.
  Pakket mail-transport-agent is niet geïnstalleerd.
  Pakket postfix die voorziet in mail-transport-agent is nog niet geconfigureerd.
dpkg: fout bij afhandelen van lsb-core (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van lsb-graphics:
 lsb-graphics is afhankelijk van lsb-core; maar:
  Pakket lsb-core is nog niet geconfigureerd.
dpkg: fout bij afhandelen van lsb-graphics (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van lsb-cxx:
 lsb-cxx is afhankelijk van lsb-core; maar:
  Pakket lsb-core is nog niet geconfigureerd.
dpkg: fout bij afhandelen van lsb-cxx (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van lsb:
 lsb is afhankelijk van lsb-core; maar:
  Pakket lsb-core is nog niet geconfigureerd.
 lsb is afhankelijk van lsb-graphics; maar:
  Pakket lsb-graphics is nog niet geconfigureerd.
 lsb is afhankelijk van lsb-cxx; maar:
  Pakket lsb-cxx is nog niet geconfigureerd.
dpkg: fout bij afhandelen van lsb (--configure):
 vereistenproblemen - blijft ongeconfigureerd
Fouten gevonden tijdens behandelen van:
 postfix
 mailx
 mutt
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
Opwaardering wordt doorgerekend... Klaar
De volgende pakketten zijn achtergehouden:
  xine-ui
0 pakketten opgewaardeerd, 0 nieuwe pakketten geïnstalleerd, 0 verwijderen en 1 niet opgewaardeerd.
7 pakketten niet volledig geïnstalleerd of verwijderd.
Er moeten 0B aan archieven opgehaald worden.
Na het uitpakken zal er 0B extra schijfruimte gebruikt worden.
Wilt u doorgaan [J/n]? j
Instellen van postfix (2.2.4-1ubuntu2) ...

Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Starting Postfix Mail Transport Agent... postfix/postfix-script: fatal: the Postfix mail system is already running
                                                                         [fail]
invoke-rc.d: initscript postfix, action "start" failed.
dpkg: fout bij afhandelen van postfix (--configure):
 subproces post-installation script gaf een foutwaarde 1 terug
dpkg: vereistenproblemen verhinderen de configuratie van mailx:
 mailx is afhankelijk van postfix | mail-transport-agent; maar:
  Pakket postfix is nog niet geconfigureerd.
  Pakket mail-transport-agent is niet geïnstalleerd.
  Pakket postfix die voorziet in mail-transport-agent is nog niet geconfigureerd.
dpkg: fout bij afhandelen van mailx (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van mutt:
 mutt is afhankelijk van postfix | mail-transport-agent; maar:
  Pakket postfix is nog niet geconfigureerd.
  Pakket mail-transport-agent is niet geïnstalleerd.
  Pakket postfix die voorziet in mail-transport-agent is nog niet geconfigureerd.
dpkg: fout bij afhandelen van mutt (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van lsb-core:
 lsb-core is afhankelijk van postfix | mail-transport-agent; maar:
  Pakket postfix is nog niet geconfigureerd.
  Pakket mail-transport-agent is niet geïnstalleerd.
  Pakket postfix die voorziet in mail-transport-agent is nog niet geconfigureerd.
dpkg: fout bij afhandelen van lsb-core (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van lsb-graphics:
 lsb-graphics is afhankelijk van lsb-core; maar:
  Pakket lsb-core is nog niet geconfigureerd.
dpkg: fout bij afhandelen van lsb-graphics (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van lsb-cxx:
 lsb-cxx is afhankelijk van lsb-core; maar:
  Pakket lsb-core is nog niet geconfigureerd.
dpkg: fout bij afhandelen van lsb-cxx (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van lsb:
 lsb is afhankelijk van lsb-core; maar:
  Pakket lsb-core is nog niet geconfigureerd.
 lsb is afhankelijk van lsb-graphics; maar:
  Pakket lsb-graphics is nog niet geconfigureerd.
 lsb is afhankelijk van lsb-cxx; maar:
  Pakket lsb-cxx is nog niet geconfigureerd.
dpkg: fout bij afhandelen van lsb (--configure):
 vereistenproblemen - blijft ongeconfigureerd
Fouten gevonden tijdens behandelen van:
 postfix
 mailx
 mutt
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)
paul@Paul:~$
##

---

### Post by ubuntu_demon on 2005-11-10
okay almost there.

Now try :
$sudo apt-get remove -f

---

### Post by Dutch on 2005-11-10
Hi U asked me to give the commando , see the result below please !
Thanks.
###
paul@Paul:~$ sudo apt-get -f remove
Password:
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
0 pakketten opgewaardeerd, 0 nieuwe pakketten geïnstalleerd, 0 verwijderen en 1 niet opgewaardeerd.
7 pakketten niet volledig geïnstalleerd of verwijderd.
Er moeten 0B aan archieven opgehaald worden.
Na het uitpakken zal er 0B extra schijfruimte gebruikt worden.
Instellen van postfix (2.2.4-1ubuntu2) ...

Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Starting Postfix Mail Transport Agent... postfix/postfix-script: fatal: the Postfix mail system is already running
                                                                         [fail]
invoke-rc.d: initscript postfix, action "start" failed.
dpkg: fout bij afhandelen van postfix (--configure):
 subproces post-installation script gaf een foutwaarde 1 terug
dpkg: vereistenproblemen verhinderen de configuratie van mailx:
 mailx is afhankelijk van postfix | mail-transport-agent; maar:
  Pakket postfix is nog niet geconfigureerd.
  Pakket mail-transport-agent is niet geïnstalleerd.
  Pakket postfix die voorziet in mail-transport-agent is nog niet geconfigureerd.
dpkg: fout bij afhandelen van mailx (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van mutt:
 mutt is afhankelijk van postfix | mail-transport-agent; maar:
  Pakket postfix is nog niet geconfigureerd.
  Pakket mail-transport-agent is niet geïnstalleerd.
  Pakket postfix die voorziet in mail-transport-agent is nog niet geconfigureerd.
dpkg: fout bij afhandelen van mutt (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van lsb-core:
 lsb-core is afhankelijk van postfix | mail-transport-agent; maar:
  Pakket postfix is nog niet geconfigureerd.
  Pakket mail-transport-agent is niet geïnstalleerd.
  Pakket postfix die voorziet in mail-transport-agent is nog niet geconfigureerd.
dpkg: fout bij afhandelen van lsb-core (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van lsb-graphics:
 lsb-graphics is afhankelijk van lsb-core; maar:
  Pakket lsb-core is nog niet geconfigureerd.
dpkg: fout bij afhandelen van lsb-graphics (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van lsb-cxx:
 lsb-cxx is afhankelijk van lsb-core; maar:
  Pakket lsb-core is nog niet geconfigureerd.
dpkg: fout bij afhandelen van lsb-cxx (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van lsb:
 lsb is afhankelijk van lsb-core; maar:
  Pakket lsb-core is nog niet geconfigureerd.
 lsb is afhankelijk van lsb-graphics; maar:
  Pakket lsb-graphics is nog niet geconfigureerd.
 lsb is afhankelijk van lsb-cxx; maar:
  Pakket lsb-cxx is nog niet geconfigureerd.
dpkg: fout bij afhandelen van lsb (--configure):
 vereistenproblemen - blijft ongeconfigureerd
Fouten gevonden tijdens behandelen van:
 postfix
 mailx
 mutt
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)
paul@Paul:~$
###

---

### Post by ubuntu_demon on 2005-11-10
First we are removing all the packages that are giving problems but aren't really essential for your system by :
$sudo apt-get remove postfix -f --purge
$sudo apt-get remove mailx -f --purge
$sudo apt-get remove mutt -f --purge
$sudo apt-get remove -f

And I want to see the output of the last command :)

---

### Post by Dutch on 2005-11-10
For the first command I got this result:
###
paul@Paul:~$ sudo apt-get -f remove
Password:
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
0 pakketten opgewaardeerd, 0 nieuwe pakketten geïnstalleerd, 0 verwijderen en 1 niet opgewaardeerd.
7 pakketten niet volledig geïnstalleerd of verwijderd.
Er moeten 0B aan archieven opgehaald worden.
Na het uitpakken zal er 0B extra schijfruimte gebruikt worden.
Instellen van postfix (2.2.4-1ubuntu2) ...

Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Starting Postfix Mail Transport Agent... postfix/postfix-script: fatal: the Postfix mail system is already running
                                                                         [fail]
invoke-rc.d: initscript postfix, action "start" failed.
dpkg: fout bij afhandelen van postfix (--configure):
 subproces post-installation script gaf een foutwaarde 1 terug
dpkg: vereistenproblemen verhinderen de configuratie van mailx:
 mailx is afhankelijk van postfix | mail-transport-agent; maar:
  Pakket postfix is nog niet geconfigureerd.
  Pakket mail-transport-agent is niet geïnstalleerd.
  Pakket postfix die voorziet in mail-transport-agent is nog niet geconfigureerd.
dpkg: fout bij afhandelen van mailx (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van mutt:
 mutt is afhankelijk van postfix | mail-transport-agent; maar:
  Pakket postfix is nog niet geconfigureerd.
  Pakket mail-transport-agent is niet geïnstalleerd.
  Pakket postfix die voorziet in mail-transport-agent is nog niet geconfigureerd.
dpkg: fout bij afhandelen van mutt (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van lsb-core:
 lsb-core is afhankelijk van postfix | mail-transport-agent; maar:
  Pakket postfix is nog niet geconfigureerd.
  Pakket mail-transport-agent is niet geïnstalleerd.
  Pakket postfix die voorziet in mail-transport-agent is nog niet geconfigureerd.
dpkg: fout bij afhandelen van lsb-core (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van lsb-graphics:
 lsb-graphics is afhankelijk van lsb-core; maar:
  Pakket lsb-core is nog niet geconfigureerd.
dpkg: fout bij afhandelen van lsb-graphics (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van lsb-cxx:
 lsb-cxx is afhankelijk van lsb-core; maar:
  Pakket lsb-core is nog niet geconfigureerd.
dpkg: fout bij afhandelen van lsb-cxx (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van lsb:
 lsb is afhankelijk van lsb-core; maar:
  Pakket lsb-core is nog niet geconfigureerd.
 lsb is afhankelijk van lsb-graphics; maar:
  Pakket lsb-graphics is nog niet geconfigureerd.
 lsb is afhankelijk van lsb-cxx; maar:
  Pakket lsb-cxx is nog niet geconfigureerd.
dpkg: fout bij afhandelen van lsb (--configure):
 vereistenproblemen - blijft ongeconfigureerd
Fouten gevonden tijdens behandelen van:
 postfix
 mailx
 mutt
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)
paul@Paul:~$ sudo apt-get remove postfix -f --purge
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De volgende pakketten zullen VERWIJDERD worden:
  lsb* lsb-core* lsb-cxx* lsb-graphics* mailx* mutt* postfix*
0 pakketten opgewaardeerd, 0 nieuwe pakketten geïnstalleerd, 7 verwijderen en 1 niet opgewaardeerd.
7 pakketten niet volledig geïnstalleerd of verwijderd.
Er moeten 0B aan archieven opgehaald worden.
Na het uitpakken zal er 6689kB schijfruimte vrijkomen.
Wilt u doorgaan [J/n]? j
(Database inlezen ... 96344 bestanden en mappen geïnstalleerd.)
lsb wordt verwijderd ...
Wissen van configuratiebestanden voor lsb ...
lsb-graphics wordt verwijderd ...
lsb-cxx wordt verwijderd ...
lsb-core wordt verwijderd ...
mailx wordt verwijderd ...
Wissen van configuratiebestanden voor mailx ...
mutt wordt verwijderd ...
Wissen van configuratiebestanden voor mutt ...
postfix wordt verwijderd ...
 * Stopping Postfix Mail Transport Agent...                              [ ok ]
Wissen van configuratiebestanden voor postfix ...
paul@Paul:~$
###

---

### Post by ubuntu_demon on 2005-11-10
okay now we solved the apt-get mess  (using msn) :)

Now take a look at the post-upgrade instructions on those 2 Breezy Upgrade wiki's.

After that :
$sudo apt-get install skype

If you have any problems with skype just go to the skype wiki I gave you previously.

If you have questions just ask.

---

### Post by Dutch on 2005-11-10
Wel fellow Dutchmen U deserved Ure titel ! Ububtu expert.
Thanks for grading me up to 5.10

Later I keep u posted about that (damn) sound problem :-)
Thanks !

---

