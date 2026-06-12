---
title: "HowTo: Easily install the Hibernate mode for Newbies ?"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-20
Hi,

Maybe, is there an sh bash to be run in order to make it easily ....

Thanks !!

Patrick

---

### Post by nocturn on 2005-10-20
[QUOTE=patrick295767]Hi,

Maybe, is there an sh bash to be run in order to make it easily ....

Thanks !!

Patrick[/QUOTE]

If your laptop/PC is supported by default, it will work without modifications when choosing hibernate.

If it doesn't, the workarrounds are not suited for newbies yet, it's better to wait it out until the newer kernels support this better.

Note that your ACPI implementation may be so broken that it will never work without reprogramming part of your BIOS (using a software solution).

---

### Post by patrick295767 on 2005-10-20
[QUOTE=nocturn]If your laptop/PC is supported by default, it will work without modifications when choosing hibernate.

If it doesn't, the workarrounds are not suited for newbies yet, it's better to wait it out until the newer kernels support this better.

Note that your ACPI implementation may be so broken that it will never work without reprogramming part of your BIOS (using a software solution).[/QUOTE]

Hi, 

I installed the ubuntu as server ... and install fvwm on my laptop. 
I still dont have the ACPI implementtation installed ... 
please could you let me know how to installed these things ?

thx a lot 

Pat'

---

### Post by patrick295767 on 2005-10-20
[QUOTE=patrick295767]Hi, 

I installed the ubuntu as server ... and install fvwm on my laptop. 
I still dont have the ACPI implementtation installed ... 
please could you let me know how to installed these things ?

thx a lot 

Pat'[/QUOTE]
  
  
Which one of them should I choose to install from the following deb packages ?
   
[http://packages.debian.org/cgi-bin/search_packages.pl?keywords=acpi&searchon=names&subword=1&version=stable&release=all](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=acpi&searchon=names&subword=1&version=stable&release=all)
 
  
thanks
pat'

---

### Post by poofyhairguy on 2005-10-20
[QUOTE=patrick295767]Which one of them should I choose to install from the following deb packages ?
   
[http://packages.debian.org/cgi-bin/search_packages.pl?keywords=acpi&searchon=names&subword=1&version=stable&release=all](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=acpi&searchon=names&subword=1&version=stable&release=all)
 
  
thanks
pat'[/QUOTE]


None. You should not use Debian packages in Ubuntu. They are too different.

If you want suspend support, you have to grok this:

[http://ubuntuforums.org/showthread.php?t=75443](http://ubuntuforums.org/showthread.php?t=75443)

---

### Post by patrick295767 on 2005-10-20
[QUOTE=poofyhairguy]None. You should not use Debian packages in Ubuntu. They are too different.

If you want suspend support, you have to grok this:

[http://ubuntuforums.org/showthread.php?t=75443](http://ubuntuforums.org/showthread.php?t=75443)[/QUOTE]

Thank you for your reply !!!
I'll try soon ;...
Actually, When I saw the webpage, I thought : 
"damn linux is not easy !!!"
  
A lot of steps before achieving to this hibernate !
But I'"ll try of course !! Thank you very much again !

Patrick

---

