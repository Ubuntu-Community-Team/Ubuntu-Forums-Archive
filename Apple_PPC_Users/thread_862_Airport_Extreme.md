---
title: "Airport Extreme"
date: 2004-10-16
forum: Apple PPC Users
---

### Post by sparkx on 2004-10-16
Is there any word on when Airport Extreme cards might be supported? I just installed on a G4 ibook and so far everything seems to be running smoothly, with the exception of not being able to see my AE card.

---

### Post by daniels on 2004-10-16
Unfortunately, no -- Apple will not release any specs, so no-one can actually write a driver for it.

---

### Post by sparkx on 2004-10-16
Bugger. 

It's not a huge issue, as there is usually an ethernet cable handy somewhere and that is working just fine. Is there anywhere that we can write to at Apple requesting that they release specs, or a linux driver?

---

### Post by daniels on 2004-10-16
I don't think so -- people have been actively pursuing Apple about this for quite some time now, to no avail.

---

### Post by wmealing on 2004-10-17
Contrary to popular belief, apple does not manafacture their own hardware.  its almost always a rebadged chipset of someone else.

This chipset is a broadcom 4301 chipset.  The drivers for this chipset can not be released by the manafacturers because this card has the ability to broadcast in a spectrum that is reserved for military use.

Because of this, broadcom imposes these limitations in software.  By releasing the specifications on how to get this card to work, they may be inadvertantly allowing people to broadcast on a restricted frequency, and therefore making them liable.

However, it is not all bad news.  There are those who are working on the broadcom drivers to provide a free and functional set of drivers for Free operating systems available from  [http://linux-bcom4301.sourceforge.net](http://linux-bcom4301.sourceforge.net). This driver is not in a workable state but it is in development.

Others have tried petitioning broadcom at [http://www.petitiononline.com/BCM4301/](http://www.petitiononline.com/BCM4301/), to no vail, their hands are tied.

x86 users can use the ndiswrapper, although this driver only works on x86 as it can translate the windows calls into native linux calls, and leave the assembly the same. While this isnt a truely "Free" source, it does work for some people.

---

### Post by Castaa on 2004-10-20
[quote=wmealing]Contrary to popular belief, apple does not manafacture their own hardware.  its almost always a rebadged chipset of someone else.

This chipset is a broadcom 4301 chipset.  The drivers for this chipset can not be released by the manafacturers because this card has the ability to broadcast in a spectrum that is reserved for military use.

Because of this, broadcom imposes these limitations in software.  By releasing the specifications on how to get this card to work, they may be inadvertantly allowing people to broadcast on a restricted frequency, and therefore making them liable.

However, it is not all bad news.  There are those who are working on the broadcom drivers to provide a free and functional set of drivers for Free operating systems available from  [http://linux-bcom4301.sourceforge.net](http://linux-bcom4301.sourceforge.net). This driver is not in a workable state but it is in development.

Others have tried petitioning broadcom at [http://www.petitiononline.com/BCM4301/](http://www.petitiononline.com/BCM4301/), to no vail, their hands are tied.

x86 users can use the ndiswrapper, although this driver only works on x86 as it can translate the windows calls into native linux calls, and leave the assembly the same. While this isnt a truely "Free" source, it does work for some people.[/quote]

Good post.  I had always wondered why apple/broadcom were to protective of the airport extreme specs.

---

### Post by chascon on 2005-02-16
[http://www.ussg.iu.edu/hypermail/linux/kernel/0304.3/1149.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0304.3/1149.html)
says that there is NO such FCC regulation prohbiting receiving some partitcular frequency.  So the FCC argument foating around is bogus.  And considering that radio frequencies are public, there is no valid argument concerning the privacy of (listening in on) radio frequencies.

I've already signed the petition, and emailed broadcom several times.  They said that we can get drivers from apple.  Therefore, I'm going to ask apple for linux drivers.  Yes this is stupid, asking apple to provide linux source or/and drivers but that was recomened by my emails with broadcom.  Besides, I have to have documention that I did everything in my power before I go complaing the the Better Business Bureau that my hardware is not supported ... computers without OSes are illegal here.  Thus, I want to argue that airport extreme support is an integral part of an OS and thus subject to being supported regardless of what ever OS  want to run on my computer.  Otherwise this is smells of an collusion between apple and braodcom to lock us into OS X.  Can you spell "monopoly"?
   
If you want apple contacts concerning airport extreme:
[http://www.apple.com/pr/library/2003/jan/07airportextreme.html](http://www.apple.com/pr/library/2003/jan/07airportextreme.html)
Natalie Welch 408 974-5430
welch at apple.com

Rena Specktor
Edelman
650 429-2742
reena.spektor at edelman.com

Mind you there is a apple media helpline 408 974-2042

can anyone confirm if there is a ppc propietary driver at 
[http://www.linux-wlan.org](http://www.linux-wlan.org)
or with
/docs/wlan_adaptors.html.gz

About airport extreme, yes there is definately a opensource project going on as we speak.  I also hear that there might be hope with MOL making airport extreme work.  I hope they fix it so that the entire MacOSX partition does NOT have to be accessed, just the the necessary driver program as they do with windows emulation programs.  It'll save processing power, I ***ume.

---

### Post by TDave on 2005-02-23
I thought Yellow Dog claimed to have this working somewhere? Wouldn't they have a solution? I could be wrong in my guesswork though...

TD

---

### Post by benjim on 2005-02-25
Has there been any updates to the linux-bcom4301 project recently?

It looks pretty quiet...

---

### Post by chascon on 2005-04-27
has anyone read the following links?

"the broadcom chipset used by apple 
for the airport extreme is also used in the Linksys WAP54G wifi access point 
... which runs under linux. This of course means there is a kernel module that 
drives the chip, and thus that either Linksys or Broadcom have code some 
driver for it. It makes me angry to think they would have gone that far and 
stopped there without considering their customers who care about running linux 
on their apple hardware."
[http://lists.debian.org/debian-powerpc/2004/02/msg00445.html](http://lists.debian.org/debian-powerpc/2004/02/msg00445.html)

and 

"A few months ago, I wrote to the kernel list describing the
relationship between Linksys (now business unit of Cisco Systems),
their WRT54G 802.11g wireless home gateway, and Linux. At the time,
we had recently discovered that the WRT54G was using a great deal of
software made available under the GPL, but was not giving credit to
the authors, or providing the source as required by the GPL.

After a bit of public pressure, Linksys posted their "GPL Code Center"
[1], where they claim that "the GPL source code contained in this
product is available for free download" [2]. Shortly after the code
center was made available, a group of developers pointed out to
Linksys that their source code, particularly their Linux kernel code,
was incomplete.

Previously, it was thought that the WRT54G source releases had only
neglected to include the source code for the various kernel modules
used to run the ethernet and wireless interfaces. However, at this
time, it is clear that the kernel proper of the WRT54G itself has had
functionality added to it. This functionality is not present in the
kernel code that Linksys has provided at their "GPL Code Center".

That is to say, there is code STATICALLY LINKED with the Linux kernel
running this device that is not present in the source download. This
code seems to be shared between the Broadcom ethernet and wireless
chips. It appears to be primarily responsible for configuring the
Sonics' SiliconBackplane and handling DMA transactions for both
devices."
[http://www.ussg.iu.edu/hypermail/linux/kernel/0309.3/0904.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0309.3/0904.html)

---

### Post by philcolbourn on 2005-05-22
[QUOTE=daniels]I don't think so -- people have been actively pursuing Apple about this for quite some time now, to no avail.[/QUOTE]
 In my ignorance, if an OS X driver exists for darwin (I presume it must) then could an osx-wrapper or a darwin/bsd-wrapper be a possibility (like the ndiswrapper)?

I am guessing that the network driver API for BSD/darwin should be well defined.

When I only used x86s I thought ndiswrapper-like wrappers were the solution to every propriety driver. Now that I have a powerbook I see the world differently: ndiswrapper gave me some freedom but not the freedom to use different hardware.

---

### Post by Bryan.Bernstein on 2005-10-12
I'd love to be able to use my AirPort Extreme card.  Until then, we can all buy USB 2.0 Wi-fi adaptors.  But my PowerBook rev. a is only USB 1.1 :(  I wonder if there is an adaptor for me?

---

### Post by fl1pper on 2005-10-12
[QUOTE=sparkx]Is there any word on when Airport Extreme cards might be supported? I just installed on a G4 ibook and so far everything seems to be running smoothly, with the exception of not being able to see my AE card.[/QUOTE]
That's cool, but let me ask you something: have you popped in a DVD yet?

---

### Post by Bryan.Bernstein on 2005-10-12
[QUOTE=fl1pper]That's cool, but let me ask you something: have you popped in a DVD yet?[/QUOTE]

:(  Is there a legal response to this?  For now I'll just play movies on my real big monitor---my TV.

---

### Post by fromtheflames on 2005-10-15
[Check this out](http://ubuntuforums.org/showpost.php?p=412981&postcount=2)

---

