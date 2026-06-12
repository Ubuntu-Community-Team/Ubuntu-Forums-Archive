---
title: "Fastest depo?"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by janz84 on 2007-02-28
Are there speedier depositories rather than the default us/main one? For some reason apt and synaptic seem to download packages rather slowly lately.

---

### Post by oilchangeguy on 2007-02-28
have you tried automatix? see [www.getautomatix.com](www.getautomatix.com)

---

### Post by Quillz on 2007-02-28
I have heard that the US repos are slow at times. Try using an international one. Check the wiki for more information.

---

### Post by Rui Pais on 2007-02-28
automatix?

janz84 give a look at ubuntu **r**epo [mirrors]("https://wiki.ubuntu.com/Mirrors?action=show&redirect=Archive") and try with one or two closest to your country.

hth

---

### Post by janz84 on 2007-02-28
> **oilchangeguy said:**
> have you tried automatix? see [www.getautomatix.com]("http://www.getautomatix.com")

Yes, I have and unfortunately it took 2-3 hours to download all the apps at wanted at a snails pace of 100-200k/s. However, I do have a 8/.76 connect and usually get downloads at 500-1000k/s on windoze.

I will try the other mirrors that other posters were kind enough to link them in this thread and then I will see if there are any network performance gains.

---

### Post by jvc26 on 2007-02-28
You could try the [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) and try a different set of mirrors, or just use the generic ones from the sources.list on ubuntu guide.
Il

---

### Post by janz84 on 2007-02-28
> **Illuvator said:**
> You could try the [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) and try a different set of mirrors, or just use the generic ones from the sources.list on ubuntu guide.
Il

It's a possibility, however, when the source-o-matic asks for what county I live in and honestly answer the us, I get the same mirror as the one I started with...

It would be nice if there was a program that could determine the fastest mirror out of the list.

---

### Post by Brunellus on 2007-02-28
> **oilchangeguy said:**
> have you tried automatix? see [www.getautomatix.com](www.getautomatix.com)
automatix is a setup script.  It is not black magic.  It will not reduce load on the download mirrors you're using.  It does not clear up acne.

It is a setup script.

---

### Post by Rui Pais on 2007-02-28
> **janz84 said:**
> It would be nice if there was a program that could determine the fastest mirror out of the list.
```
sudo aptitude install netselect
```
allow to know which server is faster from a list you give...
```
sudo aptitude install netselect-apt
```
will build a sources.list based on above... (never use it but maybe you find it useful)

---

### Post by janz84 on 2007-02-28
Ok, I installed it... now how do I use the app?

edit... nvm... it's
```
 sudo netselect-apt 
```

and it determined the fastest for me was
```
 http://debian.lcs.mit.edu/debian/ 
```

hopefully thats an ubuntu repo and not just a debian one.

---

### Post by Rui Pais on 2007-02-28
> **janz84 said:**
> Ok, I installed it... now how do I use the app?

edit... nvm... it's
```
 sudo netselect-apt 
```

and it determined the fastest for me was
```
 http://debian.lcs.mit.edu/debian/ 
```

hopefully thats an ubuntu repo and not just a debian one.

sorry but thats not seems to be an ubuntu repo...

i used those a long time ago (ubuntu didn't exist...) 

you probably must need to give more on the command line to get ubuntu repos.

man pages are nice and give a lto of examples. they deserve a read.


edit: if i remember well i get a list of mirrors close to me (such as those on the list a point before) and run netselect with that list (and some flag?)...

---

### Post by janz84 on 2007-02-28
found another similar app, "apt-spy" which seems to have a more detailed explanation on what different command switches do... have to do some more research before I can find a effective batch mirror testing method.

edit: back to netselect-apt:

apparently it makes a file called mirrors_full in my home directory... tried putting in the list of us mirror-mirrors from the official mirrors list, however the command returns this error:
```
janz84@ubuntu:~$ sudo netselect-apt
Using distribution stable.
There is a already a mirrors_full file in the current
directory.  I'll use that, rather than downloading it again.

Choosing a main Debian mirror using netselect.
Usage: netselect [-v|-vv|-vvv] [-m max_ttl] [-s servers] [-t min_tries] host ...
netselect was unable to find a mirror, this probably means that
you are behind a firewall and it is blocking traceroute.

```interesting side note...
```

janz84@ubuntu:~$ sudo netselect-apt ubuntu
Invalid distribution: ubuntu

```

---

### Post by jackrobinson on 2007-02-28
> **Brunellus said:**
> automatix is a setup script.  It is not black magic.  It will not reduce load on the download mirrors you're using.  It does not clear up acne.

It is a setup script.
Its NOT a setup script.. have you seen the automatix2 code? It's a python application and  fast becoming an extremely sophisticated  package manager in its own right.

---

### Post by Brunellus on 2007-02-28
> **jackrobinson said:**
> Its NOT a setup script.. have you seen the automatix2 code? It's a python application and  fast becoming an extremely sophisticated  package manager in its own right.
Automatix's intrinsic merits or demerits as a package manager are not relevant to OP's problem.  OP has a network problem.  Does Automatix give OP more bandwidth somehow?

---

### Post by janz84 on 2007-02-28
I see my error, what I did with the file it downloads into my home directory, [http://www.debian.org/mirror/mirrors_full](http://www.debian.org/mirror/mirrors_full) , was that I simply put copied and replaced the urls in that file...

Maybe if I downloaded it again and organized the us mirror-mirrors I want in the way the debian mirrors are formated on the page, I could "fool" netselect-apt into thinking it's calculating the fastest mirror for debian.

---

### Post by Rui Pais on 2007-02-28
uhmmmm... 
i'm start to regret have point you to that app... 
seems that it was just dropped by someone on the repos without the minimum effort to adapt it to Ubuntu distro :(

anyway netselect seems to work. 
I copy-pasted from the list of mirrors (only some of the USA ones) and formated to be space separated and run it with -vv. Boring but easy to do.
here the results:
```
sudo netselect -vv http://mirrors.kernel.org/ubuntu/ http://mirror.cs.umn.edu/ubuntu/ http://lug.mtu.edu/ubuntu/ http://mirror.clarkson.edu/pub/distributions/ubuntu/ http://ubuntu.mirrors.tds.net/ubuntu/ http://www.opensourcemirrors.org/ubuntu/ http://ftp.ale.org/pub/mirrors/ubuntu/ http://ubuntu.secs.oakland.edu/ http://mirror.mcs.anl.gov/pub/ubuntu/
```
and got:
> Running netselect to choose 1 out of 11 addresses.      
...................................................................
[http://204.152.191.7/ubuntu/](http://204.152.191.7/ubuntu/)           214 ms  14 hops   90% ok ( 9/10) [  571]
[http://204.152.191.39/ubuntu/](http://204.152.191.39/ubuntu/)          214 ms  12 hops   90% ok ( 9/10) [  523]
[http://146.137.96.7/pub/ubuntu/](http://146.137.96.7/pub/ubuntu/)       9999 ms  30 hops    0% ok
[http://146.137.96.15/pub/ubuntu/](http://146.137.96.15/pub/ubuntu/)      9999 ms  30 hops    0% ok
[http://ftp.ale.org/pub/mirrors/ubuntu/](http://ftp.ale.org/pub/mirrors/ubuntu/)   9999 ms  30 hops    0% ok
[http://ubuntu.mirrors.tds.net/ubuntu/](http://ubuntu.mirrors.tds.net/ubuntu/)    354 ms  13 hops   90% ok ( 9/10) [  906]
[http://lug.mtu.edu/ubuntu/](http://lug.mtu.edu/ubuntu/)            9999 ms  30 hops    0% ok
[http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/)       692 ms  21 hops  100% ok (10/10) [ 2145]
[http://www.opensourcemirrors.org/ubuntu/](http://www.opensourcemirrors.org/ubuntu/)    407 ms  22 hops  100% ok (10/10) [ 1302]
[http://ubuntu.secs.oakland.edu/](http://ubuntu.secs.oakland.edu/)       9999 ms  30 hops    0% ok
[http://mirror.clarkson.edu/pub/distributions/ubuntu/](http://mirror.clarkson.edu/pub/distributions/ubuntu/)   9999 ms  30 hops    0% ok
  523 [http://204.152.191.39/ubuntu/](http://204.152.191.39/ubuntu/)


from that shorted list seems to wins (faster) the second.

---

### Post by janz84 on 2007-02-28
thanks for the fast reply, for it seemed a daunting task...

anyway here are my results of that query
```

Running netselect to choose 1 out of 11 addresses.      
...........................................................
http://lug.mtu.edu/ubuntu/            9999 ms  30 hops    0% ok
http://mirror.cs.umn.edu/ubuntu/       357 ms  19 hops   70% ok ( 7/10) [ 1479]
http://ftp.ale.org/pub/mirrors/ubuntu/   9999 ms  30 hops    0% ok
http://146.137.96.7/pub/ubuntu/       9999 ms  30 hops    0% ok
http://146.137.96.15/pub/ubuntu/      9999 ms  30 hops    0% ok
http://ubuntu.mirrors.tds.net/ubuntu/     39 ms  16 hops   90% ok ( 9/10) [  114]
http://ubuntu.secs.oakland.edu/       9999 ms  30 hops    0% ok
http://204.152.191.7/ubuntu/            92 ms  19 hops   90% ok ( 9/10) [  295]
http://204.152.191.39/ubuntu/           91 ms  18 hops   90% ok ( 9/10) [  282]
http://www.opensourcemirrors.org/ubuntu/     84 ms  20 hops   90% ok ( 9/10) [  279]
http://mirror.clarkson.edu/pub/distributions/ubuntu/   9999 ms  30 hops    0% ok
  114 http://ubuntu.mirrors.tds.net/ubuntu/

```so I guess I should use either [http://ubuntu.mirrors.tds.net/ubuntu/]("http://204.152.191.39/ubuntu/") or [http://www.opensourcemirrors.org/ubuntu/](http://www.opensourcemirrors.org/ubuntu/) in my scorces.list

---

### Post by janz84 on 2007-02-28
for now ill try the [http://ubuntu.mirrors.tds.net/ubuntu/]("http://204.152.191.39/ubuntu/") mirror...

edit... well those mirrors didn't work too well, but I did a little research and found that the UK has a solid backbone to NY, US.

Using the source-o-matic, I made a new source file and had download rates from the uk around 1000k...

---

### Post by Rui Pais on 2007-02-28
> **janz84 said:**
> thanks for the fast reply, for it seemed a daunting task...
No prob, i'm do it for myself too, cause i usually just copy source.list and change the version name... i discovered that in my case the one that was faster on first days of dapper is now completely beated by another one. I will try a new apt.source to see how better it will be. :)

 
> 
anyway here are my results of that query
```

Running netselect to choose 1 out of 11 addresses.      
...........................................................
http://lug.mtu.edu/ubuntu/            9999 ms  30 hops    0% ok
http://mirror.cs.umn.edu/ubuntu/       357 ms  19 hops   70% ok ( 7/10) [ 1479]
http://ftp.ale.org/pub/mirrors/ubuntu/   9999 ms  30 hops    0% ok
http://146.137.96.7/pub/ubuntu/       9999 ms  30 hops    0% ok
http://146.137.96.15/pub/ubuntu/      9999 ms  30 hops    0% ok
http://ubuntu.mirrors.tds.net/ubuntu/     39 ms  16 hops   90% ok ( 9/10) [  114]
http://ubuntu.secs.oakland.edu/       9999 ms  30 hops    0% ok
http://204.152.191.7/ubuntu/            92 ms  19 hops   90% ok ( 9/10) [  295]
http://204.152.191.39/ubuntu/           91 ms  18 hops   90% ok ( 9/10) [  282]
http://www.opensourcemirrors.org/ubuntu/     84 ms  20 hops   90% ok ( 9/10) [  279]
http://mirror.clarkson.edu/pub/distributions/ubuntu/   9999 ms  30 hops    0% ok
  114 http://ubuntu.mirrors.tds.net/ubuntu/

```so I guess I should use either [http://ubuntu.mirrors.tds.net/ubuntu/]("http://204.152.191.39/ubuntu/") or [http://www.opensourcemirrors.org/ubuntu/](http://www.opensourcemirrors.org/ubuntu/) in my scorces.list

yes, but don't forget that the list i post was just the first ones. USA have a lot of mirrors (of course) check others too.
I repeat the netselect 3 times to check if results persist and if you make changes to sources.list don't forget to make backups, ok 

edit: good luck :)

---

### Post by janz84 on 2007-02-28
The reason I picked one of the main mirrors over the ones listed for alternatives to the us one because they were only slightly faster than the us/main one (by 100k). I guess transfer rates can't just be determined by the ping. Thanks anyway for your help.

---

### Post by janz84 on 2007-03-01
[IMG]http://i92.photobucket.com/albums/l16/janz84/Screenshot.png[/IMG]

---

### Post by El_Matthews on 2007-03-01
You could also install apt-spy. this application writes a new sources based on bandwidth tests. So it will add the fastest one to your source list. I never tried it in ubuntu as I get downloads of 400KB with the local source, but on debian it worked well.

Of course, take a backup of your original source file before launching this.
cv /etc/apt/source.list /etc/apt/souce.list.orig

---

### Post by janz84 on 2007-03-01
> **El_Matthews said:**
> You could also install apt-spy. this application writes a new sources based on bandwidth tests. So it will add the fastest one to your source list. I never tried it in ubuntu as I get downloads of 400KB with the local source, but on debian it worked well.

Of course, take a backup of your original source file before launching this.
cv /etc/apt/source.list /etc/apt/souce.list.orig

I have apt-spy installed... however I have not the clue on how to use it...

---

### Post by El_Matthews on 2007-03-02
That question can be solved by typing :) 
```
man apt-spy
```

I don't have my Ubuntu in front of me but this is what I got from the internet:
apt-spy -d distribution  [ -a area ] [ -c config ] [ -e number ] [ -f file ] [ -i file ] [ -m mirror-list ] [ -o output-file ] [ -p proxy ] [ -s country-list ] [ -t time ] [ -u update-URL ] [ -w file ] [ -n number ] [ -h ] [ -v ] [ update ]

so it should simply start with 
```
apt-spy -d edgy
```

I will test this this weekend on my ubuntu and post the full command.

---

### Post by janz84 on 2007-03-02
Just installed the new Feisty Herd 5 and looky here on a new button for the software sources:
_[IMG]http://i92.photobucket.com/albums/l16/janz84/Screenshot-1.png[/IMG]_[URL="http://i92.photobucket.com/albums/l16/janz84/Screenshot-1.png"]
[/URL]

---

### Post by El_Matthews on 2007-03-05
> **El_Matthews said:**
> That question can be solved by typing :) 
```
man apt-spy
```

I don't have my Ubuntu in front of me but this is what I got from the internet:
apt-spy -d distribution  [ -a area ] [ -c config ] [ -e number ] [ -f file ] [ -i file ] [ -m mirror-list ] [ -o output-file ] [ -p proxy ] [ -s country-list ] [ -t time ] [ -u update-URL ] [ -w file ] [ -n number ] [ -h ] [ -v ] [ update ]

so it should simply start with 
```
apt-spy -d edgy
```

I will test this this weekend on my ubuntu and post the full command.


I testes this out and it seems that apt-spy is still checking the debian repositories.

you can use [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) to create a source file with local servers if you want.

---

### Post by Rui Pais on 2007-03-05
> **El_Matthews said:**
> I testes this out and it seems that apt-spy is still checking the debian repositories.

you can use [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) to create a source file with local servers if you want.

source-o-matic is a little basic. It gives the main mirror of the country, not the fastest.
It's not a speed tune tool.

---

### Post by kpk108 on 2007-03-24
See [http://www.ubuntuforums.org/showthread.php?t=392642](http://www.ubuntuforums.org/showthread.php?t=392642) for 7.04 Feisty Fawn.

---

