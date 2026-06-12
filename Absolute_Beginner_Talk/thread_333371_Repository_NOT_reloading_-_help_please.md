---
title: "Repository NOT reloading - help please"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by davethesteam on 2007-01-07
Oh dear!!
Appear to be able get hold of downloads (wanted to get hold of Realplayer so I could listen to the beeb) Came into my download manager ok but I now find I cannot RELOAD in Synaptic or anywhere else for that matter- reload goes as far as loading-- 7 out of 21 files but then stops and I have to cancel. 
By unchecking everything in Software Resources, a limited reload is possible ( 4 files)- is this an internet access issue or is it a Synaptic / reload issue.
Expert advise would be appreciated!!! so I can increase my available usage of Ubuntu 6.10  Edgy
Davethesteam

---

### Post by taurus on 2007-01-07
What happens if you run this commnad from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
```

---

### Post by jeremy on 2007-01-07
If Taurus' suggestion does not work, then post a copy of your /etc/apt/sources.list here.

---

### Post by davethesteam on 2007-01-07
david@david-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_GB
57% [Connecting to security.ubuntu.com (1.0.0.0)]

---

### Post by taurus on 2007-01-07
And I assume your network is working, right?

```
ping -w 3 www.yahoo.com
```

---

### Post by davethesteam on 2007-01-07
Thank you all - reply to Jeremy

david@david-desktop:~$ etc/apt/sources
bash: etc/apt/sources: No such file or directory
david@david-desktop:~$

---

### Post by taurus on 2007-01-07
> **davethesteam said:**
> Thank you all - reply to Jeremy

david@david-desktop:~$ etc/apt/sources
bash: etc/apt/sources: No such file or directory
david@david-desktop:~$

```
cat    /etc/apt/sources.list
```

---

### Post by davethesteam on 2007-01-07
> **taurus said:**
> And I assume your network is working, right?

```
ping -w 3 www.yahoo.com
```

david@david-desktop:~$ ping -w 3 [www.yahoo.com](www.yahoo.com)
PING [www.yahoo-ht2.akadns.net](www.yahoo-ht2.akadns.net) (209.73.186.238) 56(84) bytes of data.
64 bytes from [www.yahoo.com](www.yahoo.com) (209.73.186.238): icmp_seq=1 ttl=49 time=87.9 ms
64 bytes from [www.yahoo.com](www.yahoo.com) (209.73.186.238): icmp_seq=2 ttl=49 time=86.2 ms
64 bytes from [www.yahoo.com](www.yahoo.com) (209.73.186.238): icmp_seq=3 ttl=49 time=86.8 ms

--- [www.yahoo-ht2.akadns.net](www.yahoo-ht2.akadns.net) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2006ms
rtt min/avg/max/mdev = 86.234/87.013/87.927/0.776 ms
david@david-desktop:~$ 


Thank you - looks OK to me - does it you?

---

### Post by taurus on 2007-01-07
> **davethesteam said:**
> david@david-desktop:~$ ping -w 3 [www.yahoo.com](www.yahoo.com)
PING [www.yahoo-ht2.akadns.net](www.yahoo-ht2.akadns.net) (209.73.186.238) 56(84) bytes of data.
64 bytes from [www.yahoo.com](www.yahoo.com) (209.73.186.238): icmp_seq=1 ttl=49 time=87.9 ms
64 bytes from [www.yahoo.com](www.yahoo.com) (209.73.186.238): icmp_seq=2 ttl=49 time=86.2 ms
64 bytes from [www.yahoo.com](www.yahoo.com) (209.73.186.238): icmp_seq=3 ttl=49 time=86.8 ms

--- [www.yahoo-ht2.akadns.net](www.yahoo-ht2.akadns.net) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2006ms
rtt min/avg/max/mdev = 86.234/87.013/87.927/0.776 ms
david@david-desktop:~$ 


Thank you - looks OK to me - does it you?

The network is a go.  :mrgreen:

---

### Post by davethesteam on 2007-01-07
> **taurus said:**
> ```
cat    /etc/apt/sources.list
```

david@david-desktop:~$ cat    /etc/apt/sources.list


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy restricted


## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security restricted
david@david-desktop:~$

---

### Post by taurus on 2007-01-07
How come you only have one repo enable in your /etc/apt/sources.list besides the CD-ROM???  Why don't you make a backup of it and use this one instead.

```
sudo cp /etc/apt/sources.list   /etc/apt/sources.list.orig
gksudo gedit /etc/apt/sources.list
```
Now, erase everything and paste these in there.

```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu edgy multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy multiverse

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu edgy-commercial main 

```
Save it and run these two commands at the prompt.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by davethesteam on 2007-01-07
> **taurus said:**
> How come you only have one repo enable in your /etc/apt/sources.list besides the CD-ROM???  Why don't you make a backup of it and use this one instead.

```
sudo cp /etc/apt/sources.list   /etc/apt/sources.list.orig
gksudo gedit /etc/apt/sources.list
```
Now, erase everything and paste these in there.

```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu edgy multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy multiverse

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu edgy-commercial main 

```
Save it and run these two commands at the prompt.

```
sudo aptitude update
sudo aptitude upgrade
```
Thank you Taurus

Did as stated and get this reponse back on Terminal:

david@david-desktop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_GB
30% [Connecting to security.ubuntu.com (1.0.0.0)] [Connecting to gb.archive.ubun30% [Connecting to security.ubuntu.com (1.0.0.0)] [Connecting to gb.archive.ubun
30% [Connecting to security.ubuntu.com (1.0.0.0)] [Connecting to gb.archive.ubun

---

### Post by taurus on 2007-01-07
You are still using the original /etc/apt/sources.list!  Can you paste it here one more time?

```
cat  /etc/apt/sources.list
```

---

### Post by davethesteam on 2007-01-07
> **taurus said:**
> You are still using the original /etc/apt/sources.list!  Can you paste it here one more time?

```
cat  /etc/apt/sources.list
```
This is what I kept as back up - is that the one you wanted??
Thank you
david@david-desktop:~$ cat    /etc/apt/sources.list


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy restricted


## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security restricted main multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe main multiverse
david@david-desktop:~$

---

### Post by taurus on 2007-01-07
You never pasted the stuff, repos, that I included in my previous post!  The questions is which one do you want to use?  Do you want to use your /etc/apt/sources.list or do you want to use the version that I've included?  It's up to now.

---

### Post by davethesteam on 2007-01-07
> **taurus said:**
> You never pasted the stuff, repos, that I included in my previous post!  The questions is which one do you want to use?  Do you want to use your /etc/apt/sources.list or do you want to use the version that I've included?  It's up to now.

Yes, I will need to use the one you gave me on your post #11

Have I not done that??
I am afraid I am rather confused as to how to acheive this - the responses I got after your post #11 suggested that the downloads were not working - if I have done it wrong - I apologise but please bear with me and advise.

This is what I got after -- upgrade:

david@david-desktop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
david@david-desktop:~$ 

and this is what I get now after :

david@david-desktop:~$ cat    /etc/apt/sources.list


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy restricted


## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main restricted
david@david-desktop:~$ 
Thanks again and regards

---

### Post by taurus on 2007-01-07
Right now, you only have two repos (both for security updates) plus the CD-ROM in /etc/apt/sources.list so do you want to keep using the same one or do you want to use those extra repos that I have?  Let me know if you want to use the version that I've included and I will show you how to add them again.  ;)

---

### Post by davethesteam on 2007-01-07
> **taurus said:**
> Right now, you only have two repos (both for security updates) plus the CD-ROM in /etc/apt/sources.list so do you want to keep using the same one or do you want to use those extra repos that I have?  Let me know if you want to use the version that I've included and I will show you how to add them again.  ;)

Thank you Taurus
I would like to use the ones you provided me with - as I would like to cast as broad a net as possible.
Regards and thanks again
PS it is now bed time in the UK - I will pick these up next time I am on my home computer

---

### Post by taurus on 2007-01-07
Okay, here goes.

From a terminal, Applications -> Accessories -> Terminal, type
```
sudo mv /etc/apt/sources.list  /etc/apt/sources.list.orig
gksudo gedit /etc/apt/sources.list
```
The file should be empty so just paste these lines to it.

```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu edgy multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy multiverse

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu edgy-commercial main

```
Save it (make sure it's /etc/apt/sources.list).  Take a quick look at it to be sure it has all those repos in there.

```
cat /etc/apt/sources.list
```
If everything is good, then update the list and upgrade it.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by davethesteam on 2007-01-08
> **taurus said:**
> Okay, here goes.

From a terminal, Applications -> Accessories -> Terminal, type
```
sudo mv /etc/apt/sources.list  /etc/apt/sources.list.orig
gksudo gedit /etc/apt/sources.list
```
The file should be empty so just paste these lines to it.

```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu edgy multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy multiverse

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu edgy-commercial main

```
Save it (make sure it's /etc/apt/sources.list).  Take a quick look at it to be sure it has all those repos in there.

```
cat /etc/apt/sources.list
```
If everything is good, then update the list and upgrade it.

```
sudo aptitude update
sudo aptitude upgrade
```


This is what I get after the first instruction - not good I fancy - by the way, I notice I have no edit button on my Repository section of the system:
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main
Regards
David

---

### Post by taurus on 2007-01-08
Save that version and at the prompt, what happens when you update it?

```
sudo aptitude update
```
Any error messages?

---

### Post by null0 on 2007-01-08
> **davethesteam said:**
> 
64 bytes from [www.yahoo.com](www.yahoo.com) (209.73.186.238): icmp_seq=1 ttl=49 time=87.9 ms
64 bytes from [www.yahoo.com](www.yahoo.com) (209.73.186.238): icmp_seq=2 ttl=49 time=86.2 ms
64 bytes from [www.yahoo.com](www.yahoo.com) (209.73.186.238): icmp_seq=3 ttl=49 time=86.8 ms

notice the happy ping :mrgreen:

---

### Post by davethesteam on 2007-01-08
> **taurus said:**
> Save that version and at the prompt, what happens when you update it?

```
sudo aptitude update
```
Any error messages?

david@david-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.c

I don't think there are any error messages

---

### Post by davethesteam on 2007-01-08
> **davethesteam said:**
> david@david-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.c

I don't think there are any error messages

Wrong there!! as below:

david@david-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg                                  
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                        
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg                    
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.c

---

