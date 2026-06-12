---
title: "Behind proxy, cant apt-get"
date: 2005-10-24
forum: Absolute Beginner Talk
---

### Post by bete on 2005-10-24
I cant seem to apt-get, i think it is because of a proxy and lots of closed ports here where i have my ubuntu computer.

When i try to "apt-get install vlc" i get the following error(translated from norwegian, so ill add the norwegian original error incase any norwegians here):

In norwegian:
> bt@ubuntu:~$ apt-get install vlc
E: Kunne ikke åpne låsefila /var/lib/apt/lists/lock - open (13 Ikke tilgang)
E: Kan ikke låse listemappa
bt@ubuntu:~$


In translated English:
> bt@ubuntu:~$ apt-get install vlc
E: Could not open the filelock /var/lib/apt/lists/lock - open (13 No permissions)
E: Can not lock listdirectory
bt@ubuntu:~$


Is this because of the proxy or just some other issue?

I am pretty sure i will encounter a problem with the proxy later even if this is not the problem. So if someone could explain how i configure my ubuntu to the proxy  so i can apt-get

---

### Post by doclivingston on 2005-10-24
That problem is due to the fact that apt-get needs to run as root to install packages. Try running ```
sudo apt-get install vlc
```

---

### Post by bete on 2005-10-24
Thank you, that worked..

But :P
> bt@ubuntu:~$ sudo apt-get install xmms
Reading packetlist ... Done
Creating overview of dependencies ... Done
The packet xmms is not available, but a different packet shows to it.
That may mean that the packet is missing or expired, or only exists from a different source.
E: The packet xmms doesnt have a installcandidat.
bt@ubuntu:~$


or in norwegian:
> bt@ubuntu:~$ sudo apt-get install xmms
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold ... Ferdig
Pakken xmms er ikke tilgjengelig, men en annen pakke henviser til den.
Dette kan bety at pakken mangler, er utgått, eller bare finnes
tilgjengelig fra en annen kilde.
E: Pakken xmms har ingen installasjonskandidat
bt@ubuntu:~$


---

### Post by bete on 2005-10-24
This is wierd, it seems i cant find anything with apt-get at all..

I tried several like vlc, xmms, azureus..

> bt@ubuntu:~$ sudo apt-get install azureus
Reading Packetlist ... Done
Creating overviews over dependence relations... Done
E: Could not find the packet Azureus


I heard something about source list? Is this a possible solution?

---

### Post by doclivingston on 2005-10-24
Try running ```
sudo apt-get update
``` to re-fetch the repository listings. Thay may either fix the problem, or give you a more useful error message.

---

### Post by bete on 2005-10-24
> bt@ubuntu:/$ sudo apt-get update
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy Release.gpg
Feil [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy Release.gpg
  Klarte ikke å koble til no.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Oppkobling nektes) [IP: 82.211.81.182 80]
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy Release
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy/universe Sources
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy/main Sources
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy/restricted Sources
Feil [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy/universe Sources
  Klarte ikke å koble til no.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Oppkobling nektes) [IP: 82.211.81.182 80]
Feil [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy/main Sources
  Klarte ikke å koble til no.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Oppkobling nektes) [IP: 82.211.81.182 80]
Feil [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy/restricted Sources
  Klarte ikke å koble til no.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Oppkobling nektes) [IP: 82.211.81.182 80]
Klarte ikke å skaffe [http://no.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://no.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Klarte ikke å koble til no.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Oppkobling nektes) [IP: 82.211.81.182 80]
Klarte ikke å skaffe [http://no.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://no.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  Klarte ikke å koble til no.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Oppkobling nektes) [IP: 82.211.81.182 80]
Klarte ikke å skaffe [http://no.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://no.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  Klarte ikke å koble til no.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Oppkobling nektes) [IP: 82.211.81.182 80]
Klarte ikke å skaffe [http://no.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://no.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz)  Klarte ikke å koble til no.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Oppkobling nektes) [IP: 82.211.81.182 80]
Leser pakkelister ... Ferdig
E: Klarte ikke å laste ned alle oversiktfilene. De ble ignorerte, eller gamle ble brukt isteden.
bt@ubuntu:/$


Basicly what it says is "cant connect to no.archive.ubuntu.com:80 (and so on)

E: Could not download all overview files. They were ignored, or old ones were used instead.

Crap.. Must be the proxy thing..

---

### Post by patrick295767 on 2005-10-24
[QUOTE=bete]Basicly what it says is "cant connect to no.archive.ubuntu.com:80 (and so on)

E: Could not download all overview files. They were ignored, or old ones were used instead.

Crap.. Must be the proxy thing..[/QUOTE]
 
A progression thread that can maybe give you some additional information concerning installing from a server ubuntu (from almost nothing).
[http://www.ubuntuforums.org/showthread.php?t=64557](http://www.ubuntuforums.org/showthread.php?t=64557)

My linux boxes are now working magnificently !

Courage courage !

Patrick

---

### Post by rockrhino27 on 2005-10-24
Bete, 

     Once you get things working.  A useful trick with apt-get to find various packages is the command apt-cache.  So if you want to search for xmms for example.  You would type "apt-cache search xmms", then you will get a list of all xmms packages.  Then just pick and choose what you want to install.

---

### Post by odin on 2005-10-24
[QUOTE=bete]Basicly what it says is "cant connect to no.archive.ubuntu.com:80 (and so on)

E: Could not download all overview files. They were ignored, or old ones were used instead.

Crap.. Must be the proxy thing..[/QUOTE]

If you say you are behind a proxy you have to "tell" every application you use that needs the internet to work somethings about your proxy.In the case of apt you have to edit /etc/apt/apt.conf.d/proxy.This file doesnt exist by default so just:

vi /etc/apt/apt.conf.d/proxy

then you have to press "i" for inserting text and type:

Aquire::http::Proxy "http://your_proxy's_IP:port used";

then press ESC and after that :wq to save changes and quit.
Run again sudo apt-get update and you should see a difference.

Hope this was the solution but try with synaptic if you dont get it working.

---

### Post by public_void on 2005-10-24
I'm also behind a proxy, and I think thats what stoppping me from updating my repositories (note my thread [here]("http://www.ubuntuforums.org/showthread.php?t=80917")). I tried what odin suggested but it isn't working, says "E212: Can't open file for writing". But I set the proxy settings under System->Preferences->Network Proxy, and everything is going okay, except the repositories thing.

---

### Post by bete on 2005-10-25
[QUOTE=odin]If you say you are behind a proxy you have to "tell" every application you use that needs the internet to work somethings about your proxy.In the case of apt you have to edit /etc/apt/apt.conf.d/proxy.This file doesnt exist by default so just:

vi /etc/apt/apt.conf.d/proxy

then you have to press "i" for inserting text and type:

Aquire::http::Proxy "http://your_proxy's_IP:port used";

then press ESC and after that :wq to save changes and quit.
Run again sudo apt-get update and you should see a difference.

Hope this was the solution but try with synaptic if you dont get it working.[/QUOTE]

Did just what you said and it diddnt work :(
Synaptic does not work either.

---

### Post by sunny_nwho on 2005-12-03
check acquire spelling it has to be acquire not aquire

---

### Post by odin on 2005-12-05
[QUOTE=sunny_nwho]check accquire spelling it has to be accquire not aquire[/QUOTE]

Sorry,I spell wrong but I think the right way is this:

Acquire::http::Proxy "http://your_proxy's_I : Port used";

Well at least it's working for me....

---

