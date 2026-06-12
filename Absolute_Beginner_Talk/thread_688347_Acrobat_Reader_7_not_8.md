---
title: "Acrobat Reader 7 not 8"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by dwanders on 2008-02-05
I need to install Acrobat Reader 7 (not 8) on Ubuntu 7.10 Gutsy (not 64 bit). I have it running fine on One PC that I upgraded - but I cannot locate the sources to add to my sources.list in order to get this version installed on a new build. 

I would gladly use other packages like Evince or even Acroread 8, however we are tied to a plugin for Acroread called DateStamp that prints the current date on the bottom of every page - this is what we use for the expiration of the printout. 

I need Acroread, and the plugins for Mozilla/Firefox version 7 running on Ubuntu 7.10. 

Any help is greatly appreciated.

---

### Post by monkey56657 on 2008-02-05
[http://www.adobe.com/products/acrobat/readstep2_allversions.html](http://www.adobe.com/products/acrobat/readstep2_allversions.html)

You can download version 7 direct from adobe from this page. 

Available as .rpm .deb .tar.gz .tar.bz2

Enjoy :KS

---

### Post by Seisen on 2008-02-05
Its available in the medibuntu repositories. But make sure to install Adobe 7.0 like you want because Adobe reader 8.0 is also available.
[URL="https://help.ubuntu.com/community/Medibuntu"]
https://help.ubuntu.com/community/Medibuntu[/URL]

---

### Post by dwanders on 2008-02-05
Thanks folks! When I try the link, it only shows version 8.1.1 as an option. And when I try the mediubunt, I also can only locate 8, and the browser plugins.

---

### Post by Seisen on 2008-02-05
Even when you look in synaptic? I know if you apt-get in will pull Adobe Reader 8.0 so try looking for it in Synaptic or Add/Remove Programs

---

### Post by monkey56657 on 2008-02-05
Sorry your right version 7 isnt available as .deb it is as .rpm. 

You can always use alien to convert rpm to deb or download and compile the other tar.gz

---

### Post by dwanders on 2008-02-05
Even in Synaptic - I only show 8.1.1 for acrobat, plugins, mozilla-plugins & escript all version 8.1.1 no seven.

---

### Post by dwanders on 2008-02-05
Thanks for the info (alien rpm -> deb) and all that, but if its at all possible I am hoping to be able to do an apt-get rather than make installs! :) I think I will keep that little nugget as a last resort kinda thing.

---

### Post by monkey56657 on 2008-02-05
You can check out some of the .deb's here

[http://ftp.osuosl.org/pub/ubuntu/pool/multiverse/a/acroread/](http://ftp.osuosl.org/pub/ubuntu/pool/multiverse/a/acroread/)

but by the filename it suggests for older versions of ubuntu but it might work...

---

### Post by Seisen on 2008-02-05
Well than that sucks, but I did find the 7.0 debs here [http://http://ftp.osuosl.org/pub/ubuntu/pool/multiverse/a/acroread/]("http://http://ftp.osuosl.org/pub/ubuntu/pool/multiverse/a/acroread/")

---

### Post by dwanders on 2008-02-05
WOW - why in the he double hockey sticks anyone in there right minds are still using that other O$ is truly beyond me. (Unless it is for some lame manufacture that refuses to support Linux, and even then - the users should ban said mfg!). 

You guys are the absolute boom, and OSL is my new favorite hang out:lolflag:

I down loaded all the Acroread_7.0.8-0.0.ubuntu2_i386.debs (cause they did not declare an Ubuntu version). 

Then I simply did:

sudo dpkg -i *.deb from the folder I downloaded it to and we are smokin.

Thanks a ton folks!  - you've made my day!

---

### Post by dwanders on 2008-02-05
Just an added FYI - right after I did that, the Updater told me I had some upgrades and tried to install the 8.0. versions! so I had to disable updates from the sources for mediubuntu!

---

### Post by Seisen on 2008-02-05
> **dwanders said:**
> Just an added FYI - right after I did that, the Updater told me I had some upgrades and tried to install the 8.0. versions! so I had to disable updates from the sources for mediubuntu!

You can also lock the version of Adobe Reader you want so it won't try to upgrade it. This way in case you want anything else from the Medibuntu repository you can still use it.

---

