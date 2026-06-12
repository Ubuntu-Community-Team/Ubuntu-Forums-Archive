---
title: "Can't download updates"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by andrew222 on 2007-01-01
The orange box withe white star in it appeared next to the date display, so I clicked it to download the updates and I got 21 messages like this



W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_093-0ubuntu18.0edgy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_093-0ubuntu18.0edgy1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/udev/libvolumeid0_093-0ubuntu18.0edgy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/libvolumeid0_093-0ubuntu18.0edgy1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)



I also get  similar messages when I try to use the synaptic package manager.  Even when I try to use the Add/remove programs app as well.  

I think I have some serious problems with Ubuntu right now...can someone help me??

---

### Post by meng on 2007-01-01
Just checking - you haven't installed anon-proxy have you? That could cause this problem I understand.

---

### Post by taurus on 2007-01-01
What does your /etc/apt/sources.list look like?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by bulldog on 2007-01-01
Can you post your sources.list?```
cat /etc/apt/sources.list
```

**EDIT:too slow**:-)

---

### Post by andrew222 on 2007-01-01
Thank You very much for your replies, 

meng:  
If I did install any anon-proxy,  I am totally unaware of having done so...

taurus and bulldog:

Here is what I got by running the command   'cat /etc/apt/sources.list'

==================================================
andrew@ubuntuOne:~$ cat /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted multiverse universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted multiverse universe main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted multiverse universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted multiverse universe main

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse universe main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse universe main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted multiverse universe main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted multiverse universe main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted multiverse universe main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted multiverse universe main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
andrew@ubuntuOne:~$ 

=======================================================


Hope this helps,  any advice and help is welcome.  Thanks again for the help,  I really do appreciate it....


Andrew

---

### Post by taurus on 2007-01-01
You have a few Dapper repos while you are running Edgy!

```

deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```
It's never a good thing to mix the two so you need to edit your /etc/apt/sources.list and replace the **dapper** with **edgy**...

Then, you have five lines for automatix!  You only need one so you can remove the other four then.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
Save the change and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by sjust on 2007-01-01
taurus I think you posted the wrong command:-k  It should be gksudo gedit /etc/apt/sources.list. The one you posted is to edit your hard drive and cdroms and such.

---

### Post by andrew222 on 2007-01-01
Thank you taurus

I ran the first line  ' gksudo gedit /etc/fstab '  and received this message

/////////////////////////////////////////////////////////////////////////////////


andrew@ubuntuOne:~$ gksudo gedit /etc/fstab

(gedit:8381): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

///////////////////////////////////////////////////////////////////////////////


Is there a way to fix this??

---

### Post by taurus on 2007-01-01
> **sjust said:**
> taurus I think you posted the wrong command:-k  It should be gksudo gedit /etc/apt/sources.list. The one you posted is to edit your hard drive and cdroms and such.

#-o 

That's what happened when you tried to type and watched tv at the same time...  

Thanks.

---

### Post by taurus on 2007-01-01
> **andrew222 said:**
> Thank you taurus

I ran the first line  ' gksudo gedit /etc/fstab '  and received this message

/////////////////////////////////////////////////////////////////////////////////


andrew@ubuntuOne:~$ gksudo gedit /etc/fstab

(gedit:8381): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

///////////////////////////////////////////////////////////////////////////////


Is there a way to fix this??

If "gksudo gedit /etc/apt/sources.list" doesn't work, you can always use nano...

```
sudo nano -w /etc/apt/sources.list
```
And when you are done editing it, hold <Ctrl> while pressing x.  Answer "yes" and hit the Return key (twice)...

---

### Post by sjust on 2007-01-01
Andrew222 just use sudo instead of gksudo, I think your permissions are not set right. Then again I get the same thing when I try that line.

---

### Post by andrew222 on 2007-01-01
sjust and taurus:

I tried  ' gksudo gedit /etc/apt/sources.list ' and got the file up to edit... Now is the task of working on editing it now...

Thanks again....

---

### Post by andrew222 on 2007-01-01
I replaced all of the words 'dapper' with 'edgy' and erased 4 of the automatix lines as specified...

I tried the line ' sudo aptitude update ' and got this message,  I then tried to download updates and still got some errors....

Hopefully you can help me with this problem...

\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\


andrew@ubuntuOne:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

//the error list goes on further....just so you get an idea...

///////////////////////////////////////////////////////////////////////////////////////////////////////////////





.................................I edited the sources.list file and this is how it looks now....


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted multiverse universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted multiverse universe main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted multiverse universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted multiverse universe main

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse universe main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse universe main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted multiverse universe main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted multiverse universe main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted multiverse universe main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted multiverse universe main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

---

### Post by taurus on 2007-01-01
Edit your /etc/apt/sources.list (gksudo gedit /etc/apt/sources.list) again and place a # in front of these lines...

```

#deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe
#deb http://security.ubuntu.com/ubuntu edgy-security universe
#deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```
Save it and see what happens when you try to update the list.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by andrew222 on 2007-01-01
I edit the file to the specifications and ran ' sudo aptitude update '

I got similar results to that of the last execution

Is there any other steps I can take to try to fix this problem??


//////////////////////////////////////////////////////////////////////////////////////////////

andrew@ubuntuOne:~$ gksudo gedit /etc/apt/sources.list


andrew@ubuntuOne:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

//list does go on further... 

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////


Here is what the sources.list file looks like after commenting out the specified lines....

............................................................................................................................................................


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted multiverse universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted multiverse universe main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted multiverse universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted multiverse universe main

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse universe main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse universe main
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted multiverse universe main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted multiverse universe main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted multiverse universe main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted multiverse universe main
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

---

### Post by taurus on 2007-01-01
Try to remove the "**us.**" from all the repos in /etc/apt/sources.list and see if it can update...

---

### Post by Balaam's Miracle on 2007-01-01
What stands out to me is the errormessage:
> Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

Call me a noob, but to me it looks like the updatemanager is trying to connect to your own PC to look for updates so instead of endlessly editing your sources.list, perhaps it's a good idea to look at your network settings to see if anything in your settings could cause this.

---

### Post by andrew222 on 2007-01-01
I just edited out all instances of 'us' from source.list

I am still receiving error messages.  I posted them below...

The thought of looking at the network settings sounds like an interesting idea

Any help is welcome.. thank to all who are helping me with this monster problem....


////////////////////////////////////////////////////////////////////////////////////////////////////

andrew@ubuntuOne:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

//the list goes on much further...all instances have the same 'Could not connect to.......' message'

/////////////////////////////////////////////////////////////////////////////////////////////

Here is the edited version of source.list, I have backed up the previous version although I posted it here................................



deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy restricted multiverse universe main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy restricted multiverse universe main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted multiverse universe main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted multiverse universe main

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse universe main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse universe main
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted multiverse universe main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted multiverse universe main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted multiverse universe main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted multiverse universe main
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

---

### Post by taurus on 2007-01-01
Post the output of this command from a terminal?

```
ifconfig
```

p.s.  Didn't you download jre-6 from Sun's site (while in Ubuntu)?

---

### Post by andrew222 on 2007-01-01
Hello taurus,  here is the output from 'ifconfig'

\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\

andrew@ubuntuOne:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:76:12:A0:3A  
          inet addr:68.198.52.25  Bcast:255.255.255.255  Mask:255.255.240.0
          inet6 addr: fe80::20c:76ff:fe12:a03a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:272978 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66722 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:126433153 (120.5 MiB)  TX bytes:6792671 (6.4 MiB)
          Interrupt:177 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:634 errors:0 dropped:0 overruns:0 frame:0
          TX packets:634 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26750 (26.1 KiB)  TX bytes:26750 (26.1 KiB)

////////////////////////////////////////////////

I did download jre-6 from Sun's website while on Ubuntu....


Thank you very much for your help....


Andrew

---

### Post by taurus on 2007-01-01
So your network connection is good then!!!

What do you get when you run this command?

```
ping -w 3 www.unf.edu
```

---

### Post by andrew222 on 2007-01-01
Glad to hear the network connection is good...

Here is the output for 'ping -w 3 www.unf.edu'

andrew@ubuntuOne:~$ ping -w 3 [www.unf.edu](www.unf.edu)
PING [www.unf.edu](www.unf.edu) (139.62.200.194) 56(84) bytes of data.
64 bytes from [www.unf.edu](www.unf.edu) (139.62.200.194): icmp_seq=1 ttl=45 time=51.6 ms
64 bytes from [www.unf.edu](www.unf.edu) (139.62.200.194): icmp_seq=2 ttl=45 time=50.7 ms
64 bytes from [www.unf.edu](www.unf.edu) (139.62.200.194): icmp_seq=3 ttl=45 time=50.6 ms

--- [www.unf.edu](www.unf.edu) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 50.626/51.015/51.668/0.464 ms
andrew@ubuntuOne:~$

---

### Post by andrew222 on 2007-01-01
Hello taurus,

If this problem continues into this evening,  I think it might be a good idea for me to format and re-install a new edgy installation.  I really appreciate your help but I do not want to consume more of your time...

---

### Post by taurus on 2007-01-01
Sorry.  Had to run upstairs to use the copy machine...

What does your /etc/hosts look like?

```
cat /etc/hosts
```
And if you wish, you can check out Edgy.

---

### Post by andrew222 on 2007-01-01
Here is what /etc/hosts/ looks like...

/////////////////////////////////////////////////

andrew@ubuntuOne:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       ubuntuOne

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
andrew@ubuntuOne:~$

---

### Post by taurus on 2007-01-01
And you said you didn't have proxy or something like that?  I guess it's time for Plan B--Edgy!!!

---

### Post by andrew222 on 2007-01-01
Thank you very much for your help...I just burned an edgy iso image to a cd.  I will format this partition this afternoon...

Andrew

---

### Post by taurus on 2007-01-01
Were you able to run synaptic/apt-get/aptitude before?

---

### Post by andrew222 on 2007-01-01
I was able to run that before...  I just started having problems this week..  I accidentally formatted the partition 6 weeks ago using gparted.  I installed dapper, then did an update through the command line to get edgy, that may be cause of the problems that arose...

---

### Post by taurus on 2007-01-01
Probably.  Some people have no luck at all when they upgrade from Dapper to Edgy while others have no problem whatsoever.  So, it's best to backup your important files and reinstall Edgy from fresh, saving you some hair and headache!  ;)

---

### Post by andrew222 on 2007-01-01
I just formatted and made a fresh installation of edgy...

Thank you for your help.  If I have difficulties getting the java jre and jdk on ubuntu ( Sun sure doesn't make it easy )  I may be back here on this message board.

I wish you a peaceful and prosperous new year.....

Andrew

---

### Post by taurus on 2007-01-01
Better to create a new thread if you have a problem since this one is getting a little long now!  ;)

---

### Post by andrew222 on 2007-01-01
I certainly will create a new thread.  Thanks again for your help....

---

### Post by ubuntu27 on 2007-01-04
> **andrew222 said:**
> I just formatted and made a fresh installation of edgy...

Thank you for your help.  If I have difficulties getting the java jre and jdk on ubuntu ( Sun sure doesn't make it easy )  I may be back here on this message board.

I wish you a peaceful and prosperous new year.....

Andrew

Java is on the repos now, so you should not have any problems installing it. :)

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)


```
sudo aptitude install sun-java5-bin
```

---

