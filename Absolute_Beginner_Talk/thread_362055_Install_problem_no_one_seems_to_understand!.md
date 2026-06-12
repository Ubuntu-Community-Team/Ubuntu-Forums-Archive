---
title: "Install problem no one seems to understand!"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by gbajosh on 2007-02-15
Everytime I attempt a apt-get update i get this...

```
 root@josh120-desktop:~# apt-get update
Err http://us.archive.ubuntu.com edgy Release.gpg                              
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://www.getautomatix.com edgy Release.gpg                               
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://www.davidpashley.com ./ Release.gpg                                 
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://security.ubuntu.com edgy-security Release.gpg                       
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://archive.canonical.com edgy-commercial Release.gpg                   
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://archive.ubuntu.com edgy Release.gpg                                 
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://us.archive.ubuntu.com edgy/multiverse Translation-en_US             
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://www.getautomatix.com edgy/main Translation-en_US                    
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://www.davidpashley.com ./ Translation-en_US                           
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://security.ubuntu.com edgy-security/main Translation-en_US            
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://archive.canonical.com edgy-commercial/main Translation-en_US        
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://archive.ubuntu.com edgy/main Translation-en_US                      
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://us.archive.ubuntu.com edgy/universe Translation-en_US               
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://security.ubuntu.com edgy-security/restricted Translation-en_US      
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://archive.ubuntu.com edgy/restricted Translation-en_US                
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://security.ubuntu.com edgy-security/universe Translation-en_US        
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://archive.ubuntu.com edgy/universe Translation-en_US                  
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://archive.ubuntu.com edgy/multiverse Translation-en_US
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://archive.ubuntu.com edgy-updates Release.gpg
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://archive.ubuntu.com edgy-updates/main Translation-en_US
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://archive.ubuntu.com edgy-updates/restricted Translation-en_US
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://archive.ubuntu.com edgy-updates/universe Translation-en_US
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://archive.ubuntu.com edgy-updates/multiverse Translation-en_US
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://archive.ubuntu.com edgy-backports Release.gpg
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
Err http://archive.ubuntu.com edgy-backports/main Translation-en_US
  Could not connect to 69.117.223.248:8080 (69.117.223.248), connection timed out
0% [Connecting to 69.117.223.248 (69.117.223.248)]


```

Please help me as this hinders my whole ubuntu experience :{

---

### Post by cet' on 2007-02-15
it seems to be down at the moment

```

PING 69.117.223.248 (69.117.223.248) 56(84) bytes of data.

--- 69.117.223.248 ping statistics ---
23 packets transmitted, 0 received, 100% packet loss, time 22000ms
```




 also archive.canonical.com resolves to somthing else for me....


```


PING archive.canonical.com (82.211.81.142) 56(84) bytes of data.
64 bytes from rockhopper.ubuntu.com (82.211.81.142): icmp_seq=1 ttl=43 time=295 ms
64 bytes from rockhopper.ubuntu.com (82.211.81.142): icmp_seq=2 ttl=43 time=295 
```

---

### Post by louis_nichols on 2007-02-15
It's just a matter of servers being down. This will be solved asap. In the meantime, if you really want, you can just try servers in other countries. You can do this by editing /etc/apt/sources.list and replacing each occurence of us.*rest-of-URL* with de.*rest-of-URL*. This will use servers in Germany. It's just a suggestion. Yiu can use any other country, I think.

---

### Post by gbajosh on 2007-02-15
my sources.list looks like

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu edgy universe

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security restricted main universe #Added by software-properties

deb http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu edgy multiverse

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse #Added by software-properties

deb http://www.davidpashley.com/debian/irssi-sarge/ ./

deb http://archive.canonical.com/ubuntu edgy-commercial main

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt edgy main

deb http://archive.ubuntu.com/ubuntu edgy-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END
```

the servers have been down for a long time i guess?  it has never worked for me.

---

### Post by volksman on 2007-02-15
like louis_nichols said, add a country code to the start of the url in your source.list:

ex:

Currently you have:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted

replace with:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted

or 

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) edgy-updates main restricted

Replace them ALL!

Can also ping the addy to make sure you can actually reach it....

---

### Post by punx45 on 2007-02-15
when i ping by domain name i get  195.248.90.38 as an IP, and it pings successfully.
```
PING archive.ubuntu.com (195.248.90.38) 56(84) bytes of data.
...
--- archive.ubuntu.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5021ms
rtt min/avg/max/mdev = 198.504/204.470/210.285/4.508 ms


```

whereas pinging the IP that is failing for you also fails.

a whois query shows that the 195*** IP belongs to Canonical Ltd, but the 69*** IP that is failing  belongs to an ISP.

Is this a DNS snafu on his end?  or are the repositories mirrored, and the one his aptitude is pointing to is down?

---

### Post by gbajosh on 2007-02-19
My new Sources.list looks like this...

```
## Uncomment the following two lines to fetch updated software from the network
deb http://eu.archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://eu.archive.ubuntu.com/ubuntu edgy restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://eu.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://eu.archive.ubuntu.com/ubuntu edgy-updates main restricted #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://eu.archive.ubuntu.com/ubuntu edgy universe

deb http://eu.security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://eu.security.ubuntu.com/ubuntu edgy-security restricted main universe #Added by software-properties

deb http://eu.security.ubuntu.com/ubuntu edgy-security universe

deb http://eu.archive.ubuntu.com/ubuntu edgy multiverse

deb http://eu.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://eu.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse #Added by software-properties

deb http://www.davidpashley.com/debian/irssi-sarge/ ./

deb http://eu.archive.canonical.com/ubuntu edgy-commercial main

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt edgy main

deb http://eu.archive.ubuntu.com/ubuntu edgy-updates universe multiverse

deb http://eu.archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

```

I tried this with us,Ca, and now EU.  All have the same thing.  I really don't get it.  can it be my router?  No one rlly seems to know, and it is hindering my ubuntu experience.  I do not want to have to switch back to m$ but its looking too likely :{

---

### Post by zvacet on 2007-02-20
In the software repositories you will see that you can choose between main server and your local.Try with your local whatever it is.It is just an idea.

---

### Post by Iesu on 2007-03-02
I hope you haven't stopped watching this thread and retreated to M$ gbajosh as I think I have your solution. I am fairly new to Linux and know very little about how it works, so my ability to help is limited but I have the same problem as you.
After a lot of searching I found a single post in some obscure forum that mentioned this problem and said that pinging the sites before we tried to connect would fix the problem. I have this problem with both aptitude and wget and also had a similar problem with YaST in openSUSE 10.1. openSUSE 10.2 seemed to work much better but I would really love to know if this could be just a matter of setting up our network settings properly or something equally simple as pinging every site in my sources.list file is simply not practical.
SO to any experts that see this, what does ping do differently to wget and aptitude that would make it able to connect but not the others?
P.S. to ping a site I type "ping (address) -c 1". The -c 1 makes it only do it once so I don't have to Ctrl+C to stop it. Forgive the obvious info but this is the absolute beginners forum.

---

