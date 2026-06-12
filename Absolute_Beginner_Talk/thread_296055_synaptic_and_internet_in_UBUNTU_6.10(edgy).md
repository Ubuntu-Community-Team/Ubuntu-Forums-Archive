---
title: "synaptic and internet in UBUNTU 6.10(edgy)"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by edy_zakaria on 2006-11-09
Hi, i am a new user... a really new. i want to move from windows to linux. after a quite long search & confusing distros, i found out ubuntu is worth a try. i dont linux at all. i also surprised that linux require quite a lot of terminal function. but i want learn it. only that i am limited with resources of daily using and practice especially for networking. currently i apply linux using ubuntu in my office in hope proposing linux to my boss to change all windows to linux. but i'm stuck....[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:

ok, here is my stucks....

synaptic... one which said important facility in ubuntu but stuck... my office using a proxy to go through internet and i have read some threads about this problem. but to no solution. the same error message of 407 proxy need authentication or 502 error.... i quite confused of some people give them solution to put in the synaptic -> setting -> preferences -> network -> with uid:pwd@proxy-server:port in which when i tried is no effect.
i confused with the terms... let say :
my uid = edy
my pwd = xxx
my proxy internet ip addr = 192.168.1.100 (example only)
my port = 8080
should i key in edy:xxx@192.168.1.100:8080 ?

in synaptic network setting they have own column for ip addr and port, it's quite funny to apply the above. though i still applied with no result. i also try to apply in System -> administration -> networking : i keyed in like the above and my internet browser can't online again.

before i'm messing with that i already set for :
my LAN in system -> perferences -> network and i filled in my static ip address. 

my system -> administration -> network i filled in with the above proxy internet and port + (because there is a detail/entry for user and pass) user and pass.

by this i can surf the internet....but not synaptic...

please help....

---

### Post by Bachstelze on 2006-11-09
Try to set the environment variables, like this :

```
export http_proxy='edy:xxx@192.168.1.100:8080'
```

---

### Post by edy_zakaria on 2006-11-09
sorry a long reply. i have to switch with windows due to dual boot. i still work with windows for my program....sigh.... if only i can get this ubuntu run well soon....

anyway.. i've tried ur solution. but no effect. i get this reply when i press the reload button in synaptic :

[http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-i386/Packages.gz:](http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://id.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:](http://id.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://id.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:](http://id.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://id.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:](http://id.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://id.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:](http://id.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://id.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:](http://id.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://id.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:](http://id.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://id.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:](http://id.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://id.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:](http://id.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )


when i run -- through terminal --

edy@edy-desktop:~$ sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg
  Temporary failure resolving '3dy@192.168.1.4'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
  Temporary failure resolving '3dy@192.168.1.4'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
  Temporary failure resolving '3dy@192.168.1.4'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US
  Temporary failure resolving '3dy@192.168.1.4'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US
  Temporary failure resolving '3dy@192.168.1.4'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg
  Temporary failure resolving '3dy@192.168.1.4'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
  Temporary failure resolving '3dy@192.168.1.4'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
  Temporary failure resolving '3dy@192.168.1.4'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
  Temporary failure resolving '3dy@192.168.1.4'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US
  Temporary failure resolving '3dy@192.168.1.4'
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg
  Temporary failure resolving '3dy@192.168.1.4'
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_US
  Temporary failure resolving '3dy@192.168.1.4'
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
  Temporary failure resolving '3dy@192.168.1.4'
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
  Temporary failure resolving '3dy@192.168.1.4'
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
  Temporary failure resolving '3dy@192.168.1.4'
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
  Temporary failure resolving '3dy@192.168.1.4'
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
  Temporary failure resolving '3dy@192.168.1.4'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg)  Temporary failure resolving '3dy@192.168.1.4'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2)  Temporary failure resolving '3dy@192.168.1.4'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2)  Temporary failure resolving '3dy@192.168.1.4'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2)  Temporary failure resolving '3dy@192.168.1.4'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2)  Temporary failure resolving '3dy@192.168.1.4'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg)  Temporary failure resolving '3dy@192.168.1.4'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2)  Temporary failure resolving '3dy@192.168.1.4'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2)  Temporary failure resolving '3dy@192.168.1.4'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2)  Temporary failure resolving '3dy@192.168.1.4'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2)  Temporary failure resolving '3dy@192.168.1.4'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg)  Temporary failure resolving '3dy@192.168.1.4'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2)  Temporary failure resolving '3dy@192.168.1.4'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2)  Temporary failure resolving '3dy@192.168.1.4'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2)  Temporary failure resolving '3dy@192.168.1.4'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2)  Temporary failure resolving '3dy@192.168.1.4'
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/Release.gpg](http://wine.budgetdedicated.com/apt/dists/edgy/Release.gpg)  Temporary failure resolving '3dy@192.168.1.4'
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2)  Temporary failure resolving '3dy@192.168.1.4'
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
edy@edy-desktop:~$ 

i get those result...(sorry to copy all...)

i also have tried to create apt.conf in /etc/apt and add these lines :

Acquire::http::Proxy "http://edy:3dy@192.168.1.4:8080";
Acquire::ftp::Proxy "ftp://edy:3dy@192.168.1.4:8080";

but no effect....

btw... before i am doing your solution a i didn't get the -->Temporary failure resolving '3dy@192.168.1.4' <-- message...

please help....](*,)

---

### Post by Bachstelze on 2006-11-09
Now, now, now, is your proxy 192.168.1.4 or 192.168.1.100 ?

And I'm not sure how to deal with authentication, my school proxy doesn't require it, try to google a bit ;)

---

### Post by edy_zakaria on 2006-11-09
i'm sorry if it confused u. 192.168.1.100 i gave is just an example, instead of using proxy.com. because i'm confused with other thread saying 'proxy.com' what does it mean ??

the 192.168.1.4 is my true ISA ip addr. 

i post my stuck in here is in hope to get help by somebody. this is really a problem for me as a first time linux user. i've tried to see other thread but also not solving...

i think i quite fell in love with ubuntu... but look like i can't apply in office. quite a disappointing for. i envy other people who dont have this prob....

is anyone out there can help me.. please.... because i really don't want to change to other distro...

i'll try to google like u said... though i confused what to google...

thank you.

---

### Post by edy_zakaria on 2006-11-14
i'm back.... sigh....and still no solution... i try to google... get ntlmaps... installed it.... run it.... still stuck....

i try to install pclinuxos which 'they' said 'easier' but still stuck... no i'm back to ubuntu (fell in love)...

can anyone out in ubuntu give me the solution ?

i still get 502 proxy server denies bla bla bla... in both synaptic manager and apt-get or aptitude....

here is my 'complete' info of my office proxy...
hostname : isaserver
ip addr : 192.168.1.4
ip port : 8080
user : edy
pass : 3dy

i have try to set in network proxy with these setting and internet is on but synaptic and apt-get is no.

i have try export http proxy still no effect.
i have used the method of edy:3dy@192.168.1.4:8080... in synaptic proxy setting and also in system preference still no effect...
i have exported the http & ftp still no effect...

what is wrong ? in pclinux os also the same. is it i am stupid ? or my firewall really suck ? or firewall is sucks ? or i am sucks ? 
](*,)

pleeeeaaaseeee heeeelllppp.......

---

