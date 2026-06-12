---
title: "just installed but can't add/remove programs"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by mdinfamy on 2007-11-20
Hello.  I just installed Ubuntu like two min ago (the latest version).  I go to add/remove and it says the list of applications is out of date and I follow and do what it says and it shows that its being downloaded and installed like 6/6 complete and then nothing happens.  I tried to play mp3 files and so it searched for the codec and again acted like it was installing but at the end it says and then I cant play my file

The playback of this movie requires a MPEG-1 Layer 3 (MP3) decoder plugin which is not installed.

Basically I can't install anything for ubuntu, so I guess its not connecting to the main server for some reason.  I was able to download other things and my internet connection is fine.  

PS do Ubuntu users need a firewall/antivirus? Any particular you would recommend?  
Thanks in advance.

---

### Post by Pumalite on 2007-11-20
Post the output of:
sudo apt-get update

---

### Post by dpar on 2007-11-20
> 
PS do Ubuntu users need a firewall/antivirus? Any particular you would recommend?
Thanks in advance.

[http://psychocats.net/ubuntu/security#firewallantivirus](http://psychocats.net/ubuntu/security#firewallantivirus)

---

### Post by mdinfamy on 2007-11-20
hm I just posted that subo text in the terminal and it did it and said done
however it didn't solve my problem

---

### Post by Pumalite on 2007-11-20
You have to copy and paste here in the forum so we can help you.

---

### Post by mdinfamy on 2007-11-20
Well first of all I think but I'm not sure that its related to a message I got while Ubuntu was initally installing on my computer.  I got a message that said that it could not reach the update site at the time and to check that out later when it was installed.  And now I'm having a hard time updating like my movie player and adding new programs from the add/remove.  The music player goes like this:

when i try to play mp3 
1) The required software to play this file is not installed. You need to install suitable codecs to play media files. Do you want to search for a codec that supports the selected file?

The search will also include software which is not officially supported.

2) I click search
3) I try to put a check in the box of what I want to install which is GSStreamer extra plugin
4) The use of this software may be restricted in some countries. You must verify that one of the following is true:

• These restrictions do not apply in your country of legal residence
• You have permission to use this software (for  example, a patent license)
• You are using this software for research purposes only
5) I press confirm
6) The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection. 
7) I click refresh
8) Acts like it downloads - shows 6/6 complete
9) I close and then error message comes up saying
The playback of this movie requires a MPEG-1 Layer 3 (MP3) decoder plugin which is not installed.

---

### Post by dpar on 2007-11-20
> **Pumalite said:**
> Post the output of:
sudo apt-get update


Please do as Pumalite asks. We would like to see the output of the command, so copy and paste the output to the forum, please.

---

### Post by mdinfamy on 2007-11-20
administrator@Computer:~$ sudo apt-get update
[sudo] password for administrator:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
administrator@Computer:~$

---

### Post by Dr Small on 2007-11-20
> **mdinfamy said:**
> administrator@Computer:~$ sudo apt-get update
[sudo] password for administrator:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
administrator@Computer:~$
cdrom needs to be commented out (#) in /etc/apt/sources.list:
```
sudo nano /etc/apt/sources.list
```

And add a hash symbol (#) to the beginning of entries with cdrom://
Save it, (CTRL + O) and exit (CTRL + X)

Dr Small

---

### Post by mdinfamy on 2007-11-20
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

is what I got after entering in sudo nano /etc/apt/sources.list


didnt know what to do from there

---

### Post by Pumalite on 2007-11-20
Comment out means putting # in front of cdrom.

---

### Post by mdinfamy on 2007-11-20
okay so i put # in front of deb cdrom and then saved it.
Then I put this in:

administrator@Computer:~$ sudo apt-get update
Reading package lists... Done

However, my problem still isnt solved. Weird.

---

### Post by mdinfamy on 2007-11-20
The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection. 

keeps coming up when  i try to install from the add/remove.
is it something in the preferences tab?

or sometimes

The information about available software is out-of-date

To install software and updates from newly added or changed sources, you have to reload the information about available software.

You need a working internet connection to continue.

---

### Post by AcademyKP03 on 2007-11-20
i'm having the same problem -- EXACTLY

I keep going in circles trying to get the ADD/Remove program to work

glad to see, its not just me ...

Any ideas?

I do remember when installing that it said something about later I would have to get updates (not available yet) ....

---

### Post by mdinfamy on 2007-11-20
I GOT IT
IT JUST STARTED WORKING FOR ME

Try this go to add/remove programs
then go to preferences

I did a few things so I'm not sure what solved it, but it got solved.  Now I put checks in all those boxes on the first screen in preferences except for the last one,  
Idk if that solved it but I think what did solve it was that you see

Download from : main server
click on the arrow next to it
and go to other
select best server
and then choose that server 

then exit out of everything
and then start add/remove programs again
and try installing something and see if it works

IF that doens't do it- then I'm not compltely sure what did it for me - try the above advice - if it wasn't what I just told you, then it was the advice given to me earlier in this thread.

Thanks everyone. My problem is solved.

---

### Post by Sims2789 on 2007-11-20
> **mdinfamy said:**
> Well first of all I think but I'm not sure that its related to a message I got while Ubuntu was initally installing on my computer.  I got a message that said that it could not reach the update site at the time and to check that out later when it was installed.  And now I'm having a hard time updating like my movie player and adding new programs from the add/remove.  The music player goes like this:

when i try to play mp3 
1) The required software to play this file is not installed. You need to install suitable codecs to play media files. Do you want to search for a codec that supports the selected file?

The search will also include software which is not officially supported.

2) I click search
3) I try to put a check in the box of what I want to install which is GSStreamer extra plugin
4) The use of this software may be restricted in some countries. You must verify that one of the following is true:

&#8226; These restrictions do not apply in your country of legal residence
&#8226; You have permission to use this software (for  example, a patent license)
&#8226; You are using this software for research purposes only
5) I press confirm
6) The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection. 
7) I click refresh
8) Acts like it downloads - shows 6/6 complete
9) I close and then error message comes up saying
The playback of this movie requires a MPEG-1 Layer 3 (MP3) decoder plugin which is not installed.

If you can install things now but the DVD player doesn't work and you don't want to watch movies  *now*, download something called VLC Media Player from Applications -> Add/Remove. It's better than  Ubuntu's default movie player.

EDIT: I just saw the previous post, but download VLC anyway; it's really good and can play .iso's.

---

### Post by Kedster on 2007-11-20
go to 
System>Administration>Software sorces 

then u open that delselect the cd from the list and select everything else uless the others on the forum say so becuase i could b makin a mistake but thaat it the GUI(guided user interface( way to fix ur problem i think

---

### Post by AcademyKP03 on 2007-11-20
> **mdinfamy said:**
> I GOT IT
IT JUST STARTED WORKING FOR ME

Try this go to add/remove programs
then go to preferences

I did a few things so I'm not sure what solved it, but it got solved.  Now I put checks in all those boxes on the first screen in preferences except for the last one,  
Idk if that solved it but I think what did solve it was that you see

Download from : main server
click on the arrow next to it
and go to other
select best server
and then choose that server 

then exit out of everything
and then start add/remove programs again
and try installing something and see if it works

IF that doens't do it- then I'm not compltely sure what did it for me - try the above advice - if it wasn't what I just told you, then it was the advice given to me earlier in this thread.

Thanks everyone. My problem is solved.




----


Yah, that worked for me too .... thanks!

SOLVED

---

