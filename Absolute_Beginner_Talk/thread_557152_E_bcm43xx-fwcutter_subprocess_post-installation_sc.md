---
title: "E: bcm43xx-fwcutter: subprocess post-installation script returned error exit status 1"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by alex.m.f on 2007-09-22
hello all

absolute newb here. 

i'm getting the error message in the title of this post every time I try to install something with Synaptic Package Managaer.

do i need to reinstall something?

any help most appreciated

a

---

### Post by por100pre1 on 2007-09-22
> **alex.m.f said:**
> hello all

absolute newb here. 

i'm getting the error message in the title of this post every time I try to install something with Synaptic Package Managaer.

do i need to reinstall something?

any help most appreciated

a

```
sudo apt-get install -f
```

Post the results... :-k

---

### Post by tjd_maximum on 2007-09-25
Well, I have the same problem I think so here goes: 

```

tony@Raz:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up bcm43xx-fwcutter (006-1) ...
--16:54:20--  http://boredklink.googlepages.com/wl_apsta.o
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:54:20 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@Raz:~$ 

```

my original problem is that I keep getting.
```

Errors were encountered while processing:
 bcm43xx-fwcutter
```

---

### Post by SpiritIsReality on 2007-09-25
howdy
```
man apt-get
```
says at the -f option
>        -f, --fix-broken
          Fix; attempt to correct a system with broken dependencies in place.
          This option, when used with install/remove, can omit any packages to
          permit APT to deduce a likely solution. Any Package that are
          specified must completely correct the problem. The option is
          sometimes necessary when running APT for the first time; APT itself
          does not allow broken package dependencies to exist on a system. It
          is possible that a system&#8217;s dependency structure can be so corrupt
          as to require manual intervention (which usually means using
          dselect(8 ) or dpkg --remove to eliminate some of the offending
          packages). Use of this option together with -m may produce an error
          in some situations. Configuration Item: APT::Get::Fix-Broken.

trails

---

### Post by tjd_maximum on 2007-09-25
Actually I was looking around and I found this suggestion:

 ```
sudo apt-get remove --purge bcm43xx-fwcutter
```

I'm pretty sure this is more or less what you just suggested and this seems to be working so far. So thanks for the help.

---

### Post by SpiritIsReality on 2007-09-25
[http://www.google.ca/search?hl=en&q=%22E%3A+Sub-process+%2Fusr%2Fbin%2Fdpkg+returned+an+error+code+%281%29%22&as_q=%22dpkg%3A+error+processing+bcm43xx-fwcutter+%28--configure%29%22&btnG=Search%C2%A0within%C2%A0results](http://www.google.ca/search?hl=en&q=%22E%3A+Sub-process+%2Fusr%2Fbin%2Fdpkg+returned+an+error+code+%281%29%22&as_q=%22dpkg%3A+error+processing+bcm43xx-fwcutter+%28--configure%29%22&btnG=Search%C2%A0within%C2%A0results)
[http://ubuntuforums.org/showthread.php?p=3407174](http://ubuntuforums.org/showthread.php?p=3407174)
not sure if this helps.
looking thru last link
I'm thinking heimo has the answer.
similar approach used here
[http://ubuntuforums.org/showthread.php?t=558315](http://ubuntuforums.org/showthread.php?t=558315)

trails

---

### Post by SpiritIsReality on 2007-09-25
ok
good goin pard
I wasn't suggesting anything 
I was just kickin' the info aound hopin' something
would fall out.

trails

---

### Post by mattaphore on 2007-09-28
I have this same problem...

My wireless is working fine, but whenever I install updates I always get that error... and the post-installation script tries to contact the "http://boredklink.googlepages.com/wl_apsta.o " website.

Did running "sudo apt-get remove --purge bcm43xx-fwcutter" fix the problem or did it also get rid of your wireless? I would really hate to get rid of my wireless, since it took me so long to get it working in the first place. (I'd rather live with the error)...



> **tjd_maximum said:**
> Actually I was looking around and I found this suggestion:

 ```
sudo apt-get remove --purge bcm43xx-fwcutter
```

I'm pretty sure this is more or less what you just suggested and this seems to be working so far. So thanks for the help.

---

### Post by mattaphore on 2007-09-28
I felt gutsy and I ran the remove bcm43xx-fwcutter command...

My wireless is still working, so that's good. It turned out that my wireless was set up using ndiswrapper instead of fwcutter... so the error I was getting was from a previous failed install.


Just so everyone knows, that sub-process error occurs because the installer is trying to find boredlink.googlepages.com/wl_apsta.o

That site crashed cuz it went way over its bandwidth and everyone who was trying to install their wireless through one of the suggested methods on the forum was getting pointed to boredlink.googlepages.com/wl_apsta.o
:guitar:
anywho, all is well now.

---

### Post by SpiritIsReality on 2007-09-28
howdy
good to hear.
sorry I missed your first post. I'm very inexperienced with wireless. 
 ndiswrapper or bcm43xx-fwcutter.
I saw your first post this morning, and went looking for how to tell whether
the cutter was used, and if so was it needed after being used....didn't get far...
was called away...
the info I was going after is somewhere at
[http://help.ubuntu.com/community/WifiDocs](http://help.ubuntu.com/community/WifiDocs)
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=ndiswrapper&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=ndiswrapper&titlesearch=Titles)
and on the forum advanced search, keywords ndiswrapper bcm43xx, titles only, all forums...

glad everything worked. thanks for the info.
trails

---

