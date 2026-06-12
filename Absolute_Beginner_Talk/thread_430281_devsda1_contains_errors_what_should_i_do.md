---
title: "/dev/sda1 contains errors what should i do?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by misfito on 2007-05-02
Hello sorry to bother u guys again.

I got a big problem:

My computer keeps freezing over and over again...Sometimes it recovers quickly but sometimes it totally crash. After a recent crash I restared it and some messages appeared on screen: 

> /dev/sda1 contains a file system with errors, check forced
[17179716.616000] ata3: command 0*25 timeout, stat 0*50 host_stat 0*22 1.1%
/dev/sda1:
Deleted inode 15908885 has zero dtime. FIXED
/dev/sda1:/========================                     /87.3%

After it finished checking for errors another message came out saying that some problems in ROOT were fixed and the system will restart.


But things are not doing well at all.... every time I load a program it takes more than usual or doesn't load at all. I really dont know what to do :(

Last thing I installed was azureus but I allready unistall it without any results.

---

### Post by misfito on 2007-05-02
OMG I really need help now...This thing has created a loop. It keeps reseting over and over with out any reason and it redirect me to the user/password screen.
I was running a game (enemy territory) when it froze and restarted...I reenter the password and user name(because it brought me to the screen that I mentioned before)  and I came here to post this (ubuntu's forums) when it restarted again, I did the same as before and I came back and when I was writing It did it again so this time the loop happened I restared it all. 
     When this first happened I used Firefox but the time I was able to finish the post I used Mozilla. I tought it was the game  that I was running the first time, the 1 responsible for all this.... but when it did it during I was using Firefox made me wonder that was something else....

Any ideas????:confused:

---

### Post by jiminycricket on 2007-05-02
Does the X screen crash when you try to log in?  Or does the whole computer restart?

If the X screen crashes, do sudo dpkg-recofigure xserver-xorg and choose the vesa driver, unless you have an nVidia or ATI X**** card.

If you  are getting random crashes, try running the Ubuntu live cd and choose "test memx86".  That will tell us if your RAM is damaged.

---

### Post by misfito on 2007-05-02
last update to my problem:
I got this message in a window:
> Nautilus has quit unexpectedly
with these options:
*Restart application *quit *inform the developers

And jiminycricket, I'll check for RAM errors right away and my video card is a ATI Radeon 9550xl 256MB. I dont know if it matters.
And the X screen didnt crash. I think you are talking about the welcome screen where you enter your name and password. Right? I got no problems with that.

Last thing i did was insert the Ubuntu disk to see if I coud check for errors in the system thru it but I didn't know how..:confused:

---

### Post by misfito on 2007-05-02
> **jiminycricket said:**
> Does the X screen crash when you try to log in?  Or does the whole computer restart?

If the X screen crashes, do sudo dpkg-recofigure xserver-xorg and choose the vesa driver, unless you have an nVidia or ATI X**** card.

If you  are getting random crashes, try running the Ubuntu live cd and choose "test memx86".  That will tell us if your RAM is damaged.

I did what you said to me...test mem86 ...It didnt find any errors.
Could it be then like you said something's wrong with the video card?


Any other idea?

---

### Post by misfito on 2007-05-03
Now I can't get the updates from the notification icon...I clicked on it and it asked me for
the administrator password, I wrote the password and a window appeared for less then a second like a flash and tha's it, I've been unable to get the updates...Everything else seems allright since i did the memtest86. The question is there's any way to restore the system to an early time or to check the system for errors?:confused: 
How can i get the updates with using the notification icon?

It seems the I got this problem:

E: Type 'Linux' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

---

### Post by taurus on 2007-05-03
There is something wrong with the first line in your /etc/apt/sources.list.  Therefore, you need to edit it

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line to comment it out.  Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```
Otherwise, post your /etc/apt/sources.list here.

---

### Post by misfito on 2007-05-03
This is what happened:
```
hugo@My-linux:~$ gksudo gedit /etc/apt/sources.list
(gedit:6048): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
hugo@My-linux:~$ sudo aptitude update
E: Type 'The' is not known on line 3 in source list /etc/apt/sources.list
E: Type 'The' is not known on line 3 in source list /etc/apt/sources.list
E: The list of sources could not be read.
hugo@My-linux:~$ sudo aptitude upgrade
E: Type 'The' is not known on line 3 in source list /etc/apt/sources.list
E: Type 'The' is not known on line 3 in source list /etc/apt/sources.list
E: The list of sources could not be read.
```

Also i got another message:

> 
E: Type 'The' is not known on line 3 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

This time looks like the problem is on line 3:


> #Linux My-linux 2.6.15-28-386 #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

---

### Post by taurus on 2007-05-03
Looks like your /etc/apt/sources.list is all screwed up.  Can you post it here?

```
cat /etc/apt/sources.list
```

p.s.  And you are running Edgy.

---

### Post by vav on 2007-05-03
All of the descriptive lines in sources.list should have a # before them. Only ones beginning with deb are fine by 
themselves.

Change that and run the update.

Your hard disk may be developing issues.

---

### Post by misfito on 2007-05-03
I puted a # before each line, but now when i click over the update notification icon nothing happens :(

---

### Post by misfito on 2007-05-03
> **taurus said:**
> Looks like your /etc/apt/sources.list is all screwed up.  Can you post it here?

```
cat /etc/apt/sources.list
```

p.s.  And you are running Edgy.

Can u do me a favor?
Can you post here how your /etc/apt/sources.list looks?

I tried to fix it by putting # before each line like I said before but it didn't help.

---

### Post by brennydoogles on 2007-05-03
Here is my sources.list if it helps 
```

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu edgy-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

```

Note that you do not comment out (put a # before) anything that starts with the word deb.

---

### Post by misfito on 2007-05-03
grazie...thank you...gracias...danke...I apreciate it ;)

---

### Post by misfito on 2007-05-03
I tried to run the update thru the terminal using:

```
sudo aptitude update
sudo aptitude upgrade
```

after repairing the sources.list with breenydoogle's one copy/paste

I got this:



> Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]
Get:2 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release [6733B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release [50.9kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release [50.9kB]
Get:9 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]
Get:10 [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages [7846B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release.gpg [191B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release [34.7kB]
Get:13 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release [4874B]
Get:14 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages [1066B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release [38.4kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages [80.7kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages [80.7kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release [44.6kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages [940kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages [5678B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages [40.0kB]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages [3786B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages [5678B]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources [16.5kB]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources [937B]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources [4723B]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources [430B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages [40.0kB]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources [4723B]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages [40.0kB]
42% [28 Packages bzip2 0] [19 Packages 106899/940kB 11%] [30 Packages 5396/40.0k
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dist s_edgy-security_universe_binary-i386_Packages - open (2 No such file or director y)
42% [29 Sources bzip2 0] [19 Packages 106899/940kB 11%] [30 Packages 5396/40.0kB
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dist s_edgy-security_universe_source_Sources - open (2 No such file or directory)
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages [3786B]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages [5974B]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages [3559kB]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages [126kB]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources [274kB]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources [1436B]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources [1068kB]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources [45.0kB]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages [3559kB]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources [1068kB]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages [81.1kB]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages [14B]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages [23.8kB]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages [14B]
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources [24.2kB]
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources [14B]
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Sources [4694B]
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Sources [14B]
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages [17.8kB]
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages [14B]
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages [40.1kB]
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages [6087B]
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources [5571B]
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources [14B]
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources [14.4kB]
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources [2371B]
Fetched 11.4MB in 58s (195kB/s)
Reading package lists... Done
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures  couldn't be verified because the public key is not available: NO_PUBKEY CC919A3 1E23C5FC3
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packa ges (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary- i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/univers e Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_un iverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
hugo@My-linux:~$ run apt-get update
bash: run: command not found
hugo@My-linux:~$ sudo  apt-get update
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release

Get:2 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]
Get:4 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release [6733B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release.gpg [191B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources
Fetched 6928B in 1s (4190B/s)
Reading package lists... Done

W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3
W: You may want to run apt-get update to correct these problems

What should I do next?

thank you

---

