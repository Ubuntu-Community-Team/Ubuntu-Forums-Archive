---
title: "Difference between .tar.gz and .rpm"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Joseaa on 2007-04-21
Hello,

Can someone explain to me the difference between .tar.gz and .rpm files ? If left up with an option to choose between the two, which one should be preferred.

---

### Post by overdrank on 2007-04-21
> **Joseaa said:**
> Hello,

Can someone explain to me the difference between .tar.gz and .rpm files ? If left up with an option to choose between the two, which one should be preferred.

Hi here is a quick search 
[http://ubuntuforums.org/search.php?searchid=18454883](http://ubuntuforums.org/search.php?searchid=18454883)

---

### Post by pillu on 2007-04-21
> **Joseaa said:**
> Hello,

Can someone explain to me the difference between .tar.gz and .rpm files ? If left up with an option to choose between the two, which one should be preferred.

I think tar.gz is just a way to compress files...like the .zip format for windows. The rpm is the format for installling programs in red hat linux or fedora....

As for installing, if you are getting a tar.gz that probably means you are installing from source. For that you need to get the build-essentials package and run some commands to compile the source code....I am not sure about the specifics as I haven't done it myself

You can get rpm and install from it too...You will need the alien package (I think)...

As you can see both of the above options are a kind of pain in the butt...can you not install from the repositories or get the file in a .deb format? What are you trying to install?

pillu

---

### Post by annda on 2007-04-21
the tar.gz files are source files. they contain raw C programs that need to be compiled.

.rpm are packages for RedHat based linux distributions, like SUSE. you can rebuild them to be useful for a Debian based system like Ubuntu. search the forums for 'alien' to accomplish that.

what is it exactly that you are trying to install?

---

### Post by Donnieb on 2007-04-21
Hi, tar.gz are compressed files meant for for all distros of linux which usually contain source code and readme files for information, and rpm are Redhat Package Manager files meant for Redhat or distro with RPM manager utility. I hope this clear it up for you.

---

### Post by Joseaa on 2007-04-21
To be more particular, I was trying to install Adobe flash player. The web-site offers two options, was wondering which one to select <URL: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

---

### Post by overdrank on 2007-04-21
> **Joseaa said:**
> To be more particular, I was trying to install Adobe flash player. The web-site offers two options, was wondering which one to select <URL: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Hi you can install flash with automatix it is great! :guitar:

---

### Post by mcduck on 2007-04-21
Just install the flash player with Ubuntu's package management, no need to download anything from Adobe's web site :D

---

### Post by overdrank on 2007-04-21
> **mcduck said:**
> Just install the flash player with Ubuntu's package management, no need to download anything from Adobe's web site :D

Well said mcduck I forgot Thanks!

---

