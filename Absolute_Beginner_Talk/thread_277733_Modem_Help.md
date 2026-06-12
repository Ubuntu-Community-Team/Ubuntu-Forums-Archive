---
title: "Modem Help"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by vladimir007 on 2006-10-15
Hello Ubuntu Users,

	Subject: 	Modem Help

	Modem Information:-

	Conexant V.92 HSF (SOFT MODEM) internal

	Made by ASKEY

	Modem Product of Taiwan

	Model No. : 1456VQL1T

	---------------------------------------------------------

	I have Ubuntu 6.06 Dapper Drake on a Laptop.

	I have installed the necessary drivers for conexant
	given on 'linuxant'.
	I followed the procedure of 'HOWTO.TXT'.
	The one which had:  Three files in one directory,
	conexant-Ubuntu.. + HOWTO.TXT + a subdirectory
	modem-hsfpci...
	The drivers were installed.

	Difference made:
	
	Before installation of drivers:
	system->administration->networking->gnome ppp when used
	and used 'autodetect' tab then it resulted in an error
	"could not detect modem .... or modem ..busy".

	After installation of drivers:
	system->administration->networking->gnome ppp when used
	and used 'autodetect' tab then it automatically selects
	'/dev/modem'

	There is no entry of '/dev/HSF0' or '/dev/HSF' in the 
	drop down list box for modem port.
	
	When you click on 'activate' tab, nothing happens.

	I cannot use even 14.4kbps speed.

	I want to try many other things also, but i want 
	information about the following things:-

	i) How can you create,open,modify&save and delete a file
	   through terminal or root terminal in any directory?
	   ( Whenever i try to do any of these operations,
	     message seen "permission denied".
	     I always use root terminal. )

	ii) Can we actually hear the dial tone, the modem
	    dialing sound on dapper drake or any ubuntu linux
	    when we click on 'activate' tab or using wvdial?
	    ( I have kept the "Loud' enabled )

      
      I have never connected the pc to the internet through
      a linux machine.

	**Any help would be appreciated.**

---

### Post by NeoLithium on 2006-10-15
> **vladimir007 said:**
> 

	i) How can you create,open,modify&save and delete a file
	   through terminal or root terminal in any directory?
	   ( Whenever i try to do any of these operations,
	     message seen "permission denied".
	     I always use root terminal. )

	ii) Can we actually hear the dial tone, the modem
	    dialing sound on dapper drake or any ubuntu linux
	    when we click on 'activate' tab or using wvdial?
	    ( I have kept the "Loud' enabled )


While I can't help with a bunch of technical stuff for a dialup connection, I can answer a couple of the questions for you.

Initially, you may want to try typing this into a terminal window: ```
sudo pppconfig
``` and that should bring up the setup dialog to enable a dialup connection with Ubuntu.  I believe there is an automatic detection of the modem on the first screen; so if you don't see it there, it should have a utility to help you find it.

i) Depending on the directory where you are; you may require superuser permissions to do modifications/creations/etc.  When in doubt, you can type **sudo** before the command in the terminal window, enter your root password, and the whole box is yours.  Just take care on what you're editing, a good practice is to double check what you are doing as root, to save yourself headaches.  Generally you have permission as a normal user in any subdirectories of /home/<username>/ others, of course, would require the superuser permissions.

ii) The modem should allow you to hear the dialing, in a terminal window, type ```
 alsamixer
``` then take a look through the options to ensure that your modem speaker isn't muted, and has it's volume high enough; I believe that they are set either low volume or on mute by default.

Hopefully some of this helps :)

---

### Post by ieee488 on 2006-10-15
When I dial out on my modem, I can hear the modem tones.

On my PC  **sudo wvdialconf**  command showed that my modem was at ttyS14.

---

### Post by vladimir007 on 2006-10-16
Hello NeoLithium , ieee488 & all ubuntu users,

          Thank you for information.


                I have tried all the things mentioned by you.

 Can anybody tell me :-

 [B]How can you create,open,modify&save and delete a file
 through terminal or root terminal in any directory?
 ( Whenever i try to do any of these operations,
 message seen "permission denied".
 I always use root terminal. )[/B]

 **Any help would be appreciated.**

---

### Post by junglepeanut on 2006-10-16
Can you list the commands you are trying?

If you are root, I suspect you are using vim?

If so 

vim filename 

should work, I would not understand why it would not.

If you do not like vi

try one of the editors you like, but please show me how you are opening the file as this may clear up the issue. 

Also how are you going root? Are you doing single user on boot up or "sudo su" or is it "sudo -H" i forget it has been a while since I did it. But either of these should be working fine.

---

### Post by vladimir007 on 2006-10-16
Hello,


           I am going to the root using "sudo su" only.
          
           Please tell me is there any other way to go to the root?

          I only know sudo su.


List of commands used:-

wvdial .............  username, passwd , dialong no. not found
(i cannot save the file wvdial.conf when i enter username... )

sudo pppconf       .............. creates a connection
(I donot know how to dial it )

syetm->administrationm->networking:-
  i click on "activate " tab nothing happens.

/* If you more commands , please also tell me */

---

### Post by Bachstelze on 2006-10-16
> **vladimir007 said:**
> Hello,
I am going to the root using "sudo su" only.
Please tell me is there any other way to go to the root?
I only know sudo su.

Either use *sudo -i* to get a root terminal or *sudo command* to run a single command as root. So here's what you need to do.

*sudo wvdialconf /etc/wvdial.conf* will probe your modem and create the wvdial config file.

*sudo nano /etc/wvdial.conf* will launch nano (command-line text editor) with your config file in it. Edit it to suit your needs than save it with Ctrl+O, return. Then exit nano (Ctrl+X).

Then dial with *sudo wvdial*, voilà :)


Note : if you get a "carrier lost" message while dialing, try adding the following line to your wvdial.conf :

carrier check = no

---

### Post by vladimir007 on 2006-10-16
Hi hmmtolife & all,

                It worked. Thank you for your suggestion.

 Now Please help me in dialing the modem.

If i use wvdial, it gives error:

 username configuration wrong
 password configuration wrong 
 phone no configuration wrong

I use ctrl+c to break it.

Its not helping me.

Gnome ppp detects the modem but used activate tab nothing happens.

No sound from speakers when activate tab is used.

I have not muted the sound , I can see videos & hear any sound file.

I am using alsa only.

I also tried alsa mixer. ABSOLUTE NO USE 

 CAN
 ANYBODY
 HELP 
 ME
 ?

 I WANT TO USE INTERNET ON MY PC USING DIAL-UP.

---

### Post by Bachstelze on 2006-10-16
Please paste the contents of your /etc/wvdial.conf, that's because wvdialconf adds weird stuff in it.

---

### Post by vladimir007 on 2006-10-17
Hi Hmmtolife,


           Thank you for your suggestion.

          Y E S 

          I T 

          W O R K E D.

---

