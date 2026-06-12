---
title: "[Office Prg] Speech, Voice Recognition : Is there any program in Linux?"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-03-12
Is there a program in the repos ??

(sphinx, xvoice, freespeech and viavoice are not in the repositories)
  
WHich one is the best one ?
  
Thank you very much !!
  
Patrick

---

### Post by Pragmatist on 2006-03-18
Didn't see anything through synaptic.  This might help:
[http://www.google.com/linux?hl=en&lr=lang_en&q=voice+recognition&btnG=Search](http://www.google.com/linux?hl=en&lr=lang_en&q=voice+recognition&btnG=Search)

---

### Post by noObiE_4_life on 2006-04-03
Best seems to be ViaVoice + Xvoice, for example see [http://linuxjournal.com/article/6383](http://linuxjournal.com/article/6383) which is four years old. Big problem is the IBM pulled ViaVoice. Even if its a flawed product, Id love to try it. If you are just looking for command recognition, what about perlbox voice? 
Try: [http://applications.linux.com/article.pl?sid=05/01/18/2148234&tid=39&tid=49&tid=13&tid=47](http://applications.linux.com/article.pl?sid=05/01/18/2148234&tid=39&tid=49&tid=13&tid=47)

---

### Post by patrick295767 on 2006-05-05
I installed sphinx for the moment ... 
it' s not soo great for the moment ... it's not understanding any single word .. 
i'll follow your advices !!
  
sphinx installatino script + freespeech : 
```

#!/bin/bash
cd /root/freespeech

apt-get -f install gnome-libs-data libgnomeui-0 gconf libgdk-pixbuf2 libgdk-pixbuf-dev gnome-vfs-extfs libgnomevfs2-common libgnomeprint15 libgnomeprint-data libgnomeprint-dev libgnome-vfs0 libgnome-vfs-common libgnome-vfs-dev libgal-dev libgal2.0-6 libgal2.0-common libgal-data
apt-get -f install hamlib3 hamlib-dev

apt-get -f -y install gnome-common

# remove all automake plz

apt-get -f -y install automake1.4
apt-get -f -y install aclocal
apt-get -f -y install autoconf
apt-get -f -y install cvs
apt-get -f -y install libtool 
apt-get -f -y install make
apt-get -f -y install doc++
apt-get -f -y install perl
apt-get -f -y install m4

also fftw3
also fftw-dev
(no need of vflow maybe)

aclocal
automake
autoconf
echo "type ./configure"
echo "**"


# to install vflow
#apt-get -f -y install ruby
#apt-get -f -y install ruby1.8-dev
#apt-get -f -y install libft-perl
# not working

apt-get -f -y install sphinx2-bin
apt-get -f -y install sphinx2-language
apt-get -f -y install sphinx2-hmm-6k


```

---

### Post by patrick295767 on 2006-05-05
It looks very pitty that we would need wine and windows ... :-( 
[http://ubuntuforums.org/showthread.php?t=45834&highlight=sphinx](http://ubuntuforums.org/showthread.php?t=45834&highlight=sphinx)

---

### Post by bodhi.zazen on 2006-05-08
I have Dragon Naturally speaking up-and-running on Lnux with wine. Only uses 1 dll from windows, the rest are all native to wine.

Results are not pretty, but better then windows.

Follow this thread:

[http://ubuntuforums.org/showthread.php?t=168711&highlight=voice+recognition](http://ubuntuforums.org/showthread.php?t=168711&highlight=voice+recognition)

Or E-mail me if I can be of further assistance.

---

### Post by patrick295767 on 2006-05-09
I'll give a try soon ... Thank you !!!
  
This Ubuntu-thread about computer Intelligence...
([http://www.ubuntuforums.org/showthread.php?p=997393#post997393](http://www.ubuntuforums.org/showthread.php?p=997393#post997393))

---

### Post by patrick295767 on 2006-05-30
[> url]http://linuxjournal.com/article/6383[/url]
  
Has someone viavoice IBM under linux (how is it with configuration ?) ??

Greetz
   
Who knows about making interface with linux box & electronic as working interface ?
  
I have IBM viavoice and have some troubles to install it via wine/cvscedega
 
Has someone some ideas to make voice recognition working via viavoice & xvoice both friends together ?? :-)
  
The vvinstall script was done for redhat :-(

---

### Post by ontos81 on 2006-07-14
Hello,

I found a howto named "[GETTING VIAVOICE SPEECH RECOGNITION WORKING ON A MODERN LINUX DISTRO]("http://taint.org/wk/ViaVoiceModernLinux")" explaining step by step how to install and configure ViaVoice. I didn't test it yet, but it seems very good. Please let me know if that works for you!

---

### Post by bodhi.zazen on 2006-07-14
I tried to get ViaVoice running a year ago-> No luck.

This how-to looks interesting. Where can I find:

ViaVoice_runtime-3.0-1.2.i386.rpm

The link from the How-to is broken.

No alternate download site found via google. Without this rpm, no install.

If you find the rpm I will test.

---

### Post by patrick295767 on 2006-08-01
> **bodhi.zazen said:**
> I tried to get ViaVoice running a year ago-> No luck.

This how-to looks interesting. Where can I find:

ViaVoice_runtime-3.0-1.2.i386.rpm

The link from the How-to is broken.

No alternate download site found via google. Without this rpm, no install.

If you find the rpm I will test.


step by step:
>  
1/Sun Java 1.5.0: [https://jdk-distros.dev.java.net/ubuntu.html](https://jdk-distros.dev.java.net/ubuntu.html)
 
2/update-alternatives java and set the Sun version as the default.
  
3/ libstdc++2.9-glibc2.1 package from Debian 3.0 (woody/oldstable)
dpkg -i libstdc++2.9-glibc2.1_2.91.66-4_i386.deb
  
4/sudo rpm -Uvh packagename.rpm --nodeps
 
[http://xvoice.sourceforge.net/gentoo.txt](http://xvoice.sourceforge.net/gentoo.txt)
[http://volker.dnsalias.net/linux/vv/viavoice-SuSE8.2.html](http://volker.dnsalias.net/linux/vv/viavoice-SuSE8.2.html)
 
5/(vvuser script to be downloaded)
 
6/ sudo apt-get install alsamixergui 

References: 
Thank you very much Scott !!

---

### Post by benner on 2006-08-01
i found this list of windows.linux equivalent programs very useful and it has some voice recognition stuff on it.

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

---

### Post by bodhi.zazen on 2006-08-01
Thanks Patrick. I will have to look at this when I have more time.

I assume it works, but, do you have viavoice up and running?

---

### Post by patrick295767 on 2006-08-02
> **bodhi.zazen said:**
> Thanks Patrick. I will have to look at this when I have more time.

I assume it works, but, do you have viavoice up and running?

Not fully & perfectly yet. I have the same matter as you : the time :-)

Greetings

---

### Post by patrick295767 on 2006-09-25
[http://volker.dnsalias.net/linux/vv/viavoice-SuSE8.2.html](http://volker.dnsalias.net/linux/vv/viavoice-SuSE8.2.html)

since the time; someone managed ?

thx

---

### Post by mips on 2006-11-09
Came across this today, [http://www.wizzardsoftware.com/wizzard_wizzscribe_si.php](http://www.wizzardsoftware.com/wizzard_wizzscribe_si.php)

---

### Post by bodhi.zazen on 2006-11-09
> **mips said:**
> Came across this today, [http://www.wizzardsoftware.com/wizzard_wizzscribe_si.php](http://www.wizzardsoftware.com/wizzard_wizzscribe_si.php)

Very cool. $3400 OUCH ! Server and workstation with 2 GB RAM OUCH !

---

### Post by rvk on 2007-02-12
The open source community is working hard on speech recognition (SR) software, but still has a lot of work to do. SR is very complex and people with the required knowledge rare.

To speed up this process we, normal users, can contribute 'our voice'. That helps in developing the necessary 'Acoustic Models'. If you want to help out go to [http://www.voxforge.org/](http://www.voxforge.org/) and find out how (quite easy).

Robin

---

### Post by patrick295767 on 2007-11-01
> **rvk said:**
> The open source community is working hard on speech recognition (SR) software, but still has a lot of work to do. SR is very complex and people with the required knowledge rare.

To speed up this process we, normal users, can contribute 'our voice'. That helps in developing the necessary 'Acoustic Models'. If you want to help out go to [http://www.voxforge.org/](http://www.voxforge.org/) and find out how (quite easy).

Robin

thanks :!!

nota: the last version of sphinx was using java, and is not that much "Linux" anymore, destined for windwos more. Installation is complex in linux

---

