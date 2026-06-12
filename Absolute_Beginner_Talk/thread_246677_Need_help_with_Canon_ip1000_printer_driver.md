---
title: "Need help with Canon ip1000 printer driver"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by senorJ on 2006-08-29
Hello,

Having trouble getting my canon ip1000 printer working under Dapper. I have searched the Ubuntu forums high and low and have done loads of research into the problem.

I tried the free version of TurboPrint and whilst this does enable my printer to a degree it also leaves a TurboPrint logo on top of printed content (which defeats the point of using TurboPrint for me). I am reluctant to pay for the full version as it is roughly the cost of my printer.

It seems that many people are having this problem with the ip1000 and I've heard people say that canon do not provide Linux drivers. I recently found the following link:

[http://software.canon-europe.com/software/canon_print_filter_for_linuxs22414.asp?model=](http://software.canon-europe.com/software/canon_print_filter_for_linuxs22414.asp?model=)

I downloaded the driver and documentation for my printer but unfortunately the files are rpm based. I remember reading somewhere that rpms can be converted to deb files using alien, I tried to have a go at this but as a Linux newbie I didn't get far before I got out of my depth.

Just wondered if anyone could help or advise if using alien is a workable solution for my problem.

Cheers
Jay

Ubuntu / Gnome
Dapper 6.06 / 2.14.3

---

### Post by PPAAUULL on 2006-08-29
Might want to take a look at this webpage. it helped me it might be able to hel you a bit. [https://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/](https://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/)

Paul

---

### Post by senorJ on 2006-08-29
Thanks for that,

I tried again with some success but got this error when trying to convert one of the rpms:

Warning: Skipping conversion of scripts in package bjfilter-pixmaip1500-lprng: postrm
Warning: Use the --scripts parameter to include the scripts.
bjfilter-pixmaip1500-lprng_2.50-2_i386.deb generated

The alien man page says this:

-c, --scripts
Try to convert the scripts that are meant to be run when the package is installed and removed. Use this with caution, becuase these scripts might be designed to work on a system unlike your own, and could cause problems. It is recommended that you examine the scripts by hand and check to see what they do before using this option.

I'm a bit concerned I'm gonna screw up my system and/or not known how to remove the drivers if I need to.

Hmm...sod it - I'll give it a go

---

### Post by senorJ on 2006-08-29
Didn't work ](*,) 

I converted the rpms to debs using alien (with the -c option) no problem.

Then I installed the debs, but once I had done this I could get no further.

So still no closer to getting my printer working. Guess I will uninstall this driver and think about getting a new printer - shame though as the canon ip1000 is compact and cheap to run.

Help?

---

