---
title: "Hello from a newbie!"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by macheadPDX on 2005-12-02
Hello Everyone,

Just starting to play with Linux! I've tried Knoppix a while back but completely forgot about it. I'm trying UBUNTU Brreezy Live CD now! It worked really well in my iMac, but still trying to get it to run in my old ThinkPad. The boot-up has been running for several hours now (currently at the "Preparing for live session" stage)... Not really sure what's going on.:confused:  Can somebody please advise? Should I restart? Thanks in advance! 

I guess I'll wait for now and see if it works.


macheadPDX

Specs: IBM ThinkPad w/433 mhz Celeron
          Windows 98 SE

---

### Post by AndyCooll on 2005-12-02
Yes, restart. It should be much faster than that before you see some action! :cool:

---

### Post by macheadPDX on 2005-12-03
Thank You AndyCooll!

I found that using 'live pci=noapci' speeds up the boot process.

After looking around using the live CD, I've finally decided to go for it. I installed UBUNTU Breezy without a problem. It just took a lot of time to complete but it's well worth it. 

Now I just have to learn the ins and outs of Linux. First challenge is installing applications. I see that there is no easy way to install the new version of FireFox (1.5)...Or maybe not... This is an opinion from a newbie... I also use Citrix ICA Client for work. I was able to successfully install this with help from the forum postings.

So far so good! I don't regret nuking Windows for good!:D 

macheadPDX

---

### Post by SickTwist on 2005-12-03
New versions of programs work a little differently in distributions like Ubuntu than what you are used to in Windows.

In Windows, it is the user's job to keep track of new versions of every program. If a new version is released, you have to upgrade each program individually. Also, little testing is done by Microsoft or the program developer to ensure that the new version will play nice with everything else that you have installed.

Ubuntu developers and beta-testers make sure that all of the programs in the Ubuntu repositories play nice together so that there are not any conflicts. A stable release of Ubuntu freezes the versions of all the included programs to ensure problems don't arise for users. Every 6 months, users get a new version of Ubuntu with new versions of almost every program. In addition, rather that having to upgrade these programs one-by-one, the entire upgrade process can be done with a few simple clicks of the mouse or commands in a terminal. Then once again, all of the programs are current and will work together smoothly.

Yes, it is possible to install Firefox 1.5 manually using the binary from Mozilla.org, compiling from source, or using a backports repository. But all of these methods could cause potential conflicts. However that choice is up to you ;)

If you are really interested in Firefox 1.5, search around the forums and you are sure to find descriptions of how others have tried to do it and how well they fared.

---

### Post by macheadPDX on 2005-12-03
Thank you SickTwist!

Just curious... Is the UBUNTU method of delivering updates called "backporting"? I see the value of this method specially if one wants a stable platform to work with!

Thanks again!

macheadPDX

---

### Post by Terry of Astoria on 2005-12-03
Backports are newer versions of applications made available for the current stable release of Ubuntu. 
  In ubuntu to install progs you can use Synaptic, in the System menu
OR use the command-line program aptitude. 
See the ubuntu wiki about it
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#synaptic-usage](http://help.ubuntu.com/starterguide/C/faqguide-all.html#synaptic-usage)
Hello and welcome to Ubuntu from a fellow Oregonian.

---

### Post by SickTwist on 2005-12-03
[QUOTE=macheadPDX]Thank you SickTwist!

Just curious... Is the UBUNTU method of delivering updates called "backporting"? I see the value of this method specially if one wants a stable platform to work with!

Thanks again!

macheadPDX[/QUOTE]

You're very welcome. Also just so you are aware, even though all of the program versions are frozen in an Ubuntu release, they still receive security updates.

For example, Breezy Badger was released with Firefox 1.0.7. If Mozilla were to release a security update within Ubuntu's support period (which is currently at least 18 months from the release date), Ubuntu developers will backport those security updates and release a new version of Firefox via the Ubuntu update manager. Firefox will still read v1.0.7, but it will contain all the latest security fixes. This process ensures that all of the programs will work together and it frees the user from having to check for security updates one-by-one for all of the various packages installed. ;)

---

### Post by macheadPDX on 2005-12-05
[QUOTE=Terry of Astoria]Backports are newer versions of applications made available for the current stable release of Ubuntu. 
  In ubuntu to install progs you can use Synaptic, in the System menu
OR use the command-line program aptitude. 
See the ubuntu wiki about it
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#synaptic-usage](http://help.ubuntu.com/starterguide/C/faqguide-all.html#synaptic-usage)
Hello and welcome to Ubuntu from a fellow Oregonian.[/QUOTE]

Hey Terry of Astoria! Thanks!

---

