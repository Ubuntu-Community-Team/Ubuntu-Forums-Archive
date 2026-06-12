---
title: "About to give up on ubuntu"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by robertjastrow on 2007-08-23
I am frustrated to no end.  Although when unix system are running good, they run good, when it comes to getting them working, good luck.

Sorry, just needed to say that.....

I am looking for help with setting up my wireless card.  I got it working with a previous install of SUSE 10.2 on the same machine (toasted that partition for ubuntu).  I have a HP Pavillion zv6000 series laptop with an internal AirForceOne Boradcom wireless adapter.  I have found tons of sites with all sorts of instruction on how to get this card to work (btw it works fine in xp), but in typical unix fassion the instruciton are never complete and never take into account errors that take the user may encounter.  I have tried both the wrapper and fwcutter process and have gotten neither to work.  Tried both as myself using sudo command and as root logged in to the console.  I am about to switch back to SUSE, but I really want to use ubuntu as it seems much more streamlined from a user standpoint and if it will do what I am looking for I want to install it for a couple of users at work to get those that dont need/want ms away from the monopoly.

Please help....

Let me know what info you may want and I will do a clean install of the OS and walk through any recomendations you have and pass on any information you need to assist.

Thanks....

---

### Post by Dark Star on 2007-08-23
Though you can search this querie, But since you made up your mind no 1 can stop .. you :|

---

### Post by robertjastrow on 2007-08-23
I am making a desperate atemp to get assistance.  I have tired several posted recomendation and have had no luck and am at a lost.  Can you help?  I dont want to give up, ubuntu has a much cleaner and streamlined interface than suse that users will feel more comfortable with, but we have several of these HP laptops in our environment and wireless is a need vs a want.

---

### Post by mikex on 2007-08-23
Stick with it. I can't answer your question but I have been getting through a lot of hurdles myself after installing it last week. If you can work through your issues for a week and still can't use it for your needs, then you might want to reconsider. Give it a week and see if anyone can help you here.

---

### Post by LaRoza on 2007-08-23
[http://www.segundanariz.com/ubuntu/?p=31](http://www.segundanariz.com/ubuntu/?p=31)

Is that similar to yours?

(For google searches, type the device name then "Ubuntu")

---

### Post by Dark Star on 2007-08-23
> **LaRoza said:**
> [http://www.segundanariz.com/ubuntu/?p=31](http://www.segundanariz.com/ubuntu/?p=31)

Is that similar to yours?

(For google searches, type the device name then "Ubuntu")
Post you result after following  the tip on the blog Hope the link by laroza helps you :D

---

### Post by Terl on 2007-08-23
> **robertjastrow said:**
> I am frustrated to no end.  Although when unix system are running good, they run good, when it comes to getting them working, good luck.

Sorry, just needed to say that.....

Understand...it can get frustrating sometimes

> .... but in typical unix fassion the instruciton are never complete and never take into account errors that take the user may encounter. ...

Not fair.  The open source community documents quite well.  I will grant you that sometimes it takes a while to sink in as it is technical, but all in all, help is much much easier to find than with, say, Windows.  

I noted that you state it works with XP.  Of course it will, just about all this hardware is made with Windows in mind.  Linux is secondary to the manufacturers.

> Please help....

Let me know what info you may want and I will do a clean install of the OS and walk through any recomendations you have and pass on any information you need to assist.

Thanks....

All that said, I did google a little and found this:  [http://wiki.linuxquestions.org/wiki/Broadcom_4318_Airforce_one_54g_card]("http://wiki.linuxquestions.org/wiki/Broadcom_4318_Airforce_one_54g_card")

If that does not work, let us know.  Also, though you are frustrated (been there many times myself), if you could outline what you've tried before and exactly the messages you get if errors appear, post those as well.

---

### Post by deadgobby on 2007-08-23
Nothing wrong with Suse at all. That is one thing I love about linux. Find the distro that works for you. I have Suse on a other box and happy with that distro. Ubie is still my fav. 
Gobby

---

### Post by Terl on 2007-08-23
> **deadgobby said:**
> Nothing wrong with Suse at all. That is one thing I love about linux. Find the distro that works for you. I have Suse on a other box and happy with that distro. Ubie is still my fav. 
Gobby

deadgobby has a good point; one I meant to ask too.  What went wrong with SuSe?  Or, rather, what is it you saw in Ubuntu that you liked?  Maybe you can get that in SuSe.

---

### Post by robertjastrow on 2007-08-23
I have tried several variants of the wrapper and the cutter process.  I will retry the cutter latter today and post all text to the results.  I gather from what I have read that the cutter process is the the better of the two (?).  I see errors and have no idea if they are normal or if there is something I am doing wrong.

I like the simplicity of the install and clean user interface.  It seems to install as default all the tools a typical user would need (ie open office, etc..) thus installing it is something I can pass on to desktop support with little worry.  They all I have to deal with is the wireless access (at the point I get the instructions in place correctly).

Thanks....

---

### Post by robertjastrow on 2007-08-23
Ok here is the full text of what I did to get this to work.  These instructions came from LaRoza  suggestion ([http://www.segundanariz.com/ubuntu/?p=31](http://www.segundanariz.com/ubuntu/?p=31)).  These steps worked.  These steps were done on a HP Pavilion zv6000 series laptop with built in Broadcom 4318 (Air Force One?) wireless adapter.  Also before the last reboot I disconnected the ethernet cable and unchecked the 'Wired connection' in System>Administration>Network to ensure I was not getting a false positive on my final results.  I type all of this from my wireless laptop within Ubuntu.  Individual steps are at the bottom of this submittal.

Thanks for all the supporting responses for this problem.

________________________________________________________________________________________


user@computer:~$ sudo apt-get install bcm43xx-fwcutter
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcm43xx-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 26.6kB of archives.
After unpacking 123kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe bcm43xx-fwcutter 1:006-1 [26.6kB]
Fetched 26.6kB in 13s (2013B/s)                                                
Preconfiguring packages ...
Selecting previously deselected package bcm43xx-fwcutter.
(Reading database ... 103489 files and directories currently installed.)
Unpacking bcm43xx-fwcutter (from .../bcm43xx-fwcutter_1%3a006-1_amd64.deb) ...
Setting up bcm43xx-fwcutter (006-1) ...
--16:42:38--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:42:41 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@computer:~$ 


Downloaded wl_apsta.zip from [http://www.box.net/shared/esuqm5y415](http://www.box.net/shared/esuqm5y415)


Extracted wl_apsta.o from wl_apsta.zip


user@computer:~$ uname -r
2.6.20-16-generic
user@computer:~$ sudo bcm43xx-fwcutter -w /lib/firmware/2.6.20-16-generic ~/Desktop/wl_apsta.o
Password:

  filename   :  wl_apsta.o
  version    :  3.130.20.0
  MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3
  microcodes :  2 4 5 11 
  pcms       :  4 5 

  microcode  :  2
  revision   :  0x0127
  patchlevel :  0x000e
  date       :  2005-04-18
  time       :  02:36:27

  microcode  :  4
  revision   :  0x0127
  patchlevel :  0x000e
  date       :  2005-04-18
  time       :  02:36:27

  microcode  :  5
  revision   :  0x0127
  patchlevel :  0x000e
  date       :  2005-04-18
  time       :  02:36:27

  microcode  :  11
  revision   :  0x0127
  patchlevel :  0x000e
  date       :  2005-04-18
  time       :  02:36:27

extracting bcm43xx_microcode2.fw ...
extracting bcm43xx_microcode4.fw ...
extracting bcm43xx_microcode5.fw ...
extracting bcm43xx_microcode11.fw ...
extracting bcm43xx_pcm4.fw ...
extracting bcm43xx_pcm5.fw ...
extracting bcm43xx_initval01.fw ...
extracting bcm43xx_initval02.fw ...
extracting bcm43xx_initval03.fw ...
extracting bcm43xx_initval04.fw ...
extracting bcm43xx_initval05.fw ...
extracting bcm43xx_initval06.fw ...
extracting bcm43xx_initval07.fw ...
extracting bcm43xx_initval08.fw ...
extracting bcm43xx_initval09.fw ...
extracting bcm43xx_initval10.fw ...
user@computer:~$ 



Reboot



System>Administration>Network enabled 'Wireless connection' by unchecking 'Enable roaming mode' and entering default in the 'Network name (ESSID)' field.



user@computer:~$ sudo modprobe bcm43xx
Password:
user@computer:~$ 



Reboot


__________________________________________________________________

Here are the steps I took (all commands are run from the logged in users home directory):

1:  sudo apt-get install bcm43xx-fwcutter
2:  Download wl_apsta.zip from [http://www.box.net/shared/esuqm5y415](http://www.box.net/shared/esuqm5y415) to desktop
3:  Extract wl_apsta.o from wl_apsta.zip to desktop
4:  uname -r
5:  sudo bcm43xx-fwcutter -w /lib/firmware/<results of uname> ~/Desktop/wl_apsta.o
6:  REBOOT
7:  System>Administration>Network - Enable 'Wireless connection' by unchecking 'Enable roaming mode' and enter your ssid in the 'Network name (ESSID)' field.  Click OK.  Ensure 'Wireless connection is checked'.  Click CLOSE.
8:  sudo modprobe bcm43xx
9:  REBOOT

Wireless should be up when your log back in.

__________________________________________________________________

---

