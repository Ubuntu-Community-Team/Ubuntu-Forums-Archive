---
title: "Hung on install at &quot;Checking Network Hardware&quot;"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by Fred H Olson on 2006-03-13
When I try to install Ubuntu 5.1 (or boot the Live disk) it hangs at the
"Checking Network Hardware" step.  I've waited as long as 50 minutes.
After it is hung I can not access a virtual terminal with ctrl-alt-f1 etc
(I can earlier).

My hardware is an old AT  (not ATX, tho I have upgraded most components) :

date
installed
4/01 MothBD FIC VA503+ Super Socket 7 AT motherbd ( [www.fic.com.tw](www.fic.com.tw))
4/01 CPU   AMD K6-2 3D 500 MHz
4/01 RAM   256 MB RAM
1/04 NIC   TRENDnet PCI 10/100 Network Card) - Realtek TE-100-PCIWN
4/04 hda   Western Digital 40GB 7200 rpm ATA 100 HD (hda - see below)
1/05 CD    Lite On 52X/32X/52X CD-RW Drive
1/04 Modem Bestdata 56SX92 external RS232 modem
/99? hdb   4 GB HD (installed to put RedHat Linux in ???)

I have rarely used the NIC card and it is a bit suspect tho there are some
indications that it works tho I have had trouble with higher levels of
networking and it is not clear where the problem is.  Most recently at an
"Installfest" where the network itself seemed a bit flaky. Using Fedora
Core 1 that I have been using, DHCP did not seem to find the name server
tho ping to an IP address worked.  Knoppix live CD found the network.

So what can hang the install?  Shouldn't it be more graceful if it can not
find network hardware or a network connection?  Is it really checking hardware as it says or is it checking for a connection?

Fred H Olson,  fholson [at] cohousing.org
Minneapolis, MN, USA

PS  I'm new to Ubuntu but am a moderately skilled user of Linux --
Red Hat 8 and Fedora Core 1 (with Gnome).  I like what I've read about
Question that I have not seen an answer to:  Is there any connection
between ubuntu.com and ubuntu.org ?  The latter is
"website of the World Forum of Civil Society Networks - UBUNTU".
I have not been able to see any reference from one to the other tho they
both got the name the same place and sound like they would be supportive
of each other maybe.

---

### Post by Pragmatist on 2006-03-13
>  1/04 NIC   TRENDnet PCI 10/100 Network Card) - Realtek TE-100-PCIWN
 1/04 Modem Bestdata 56SX92 external RS232 modem

Well, if it were me, I would disconnect Modem2 and try again with only Modem1.  If that didn't work, I'd install with only Modem2 and not Modem1.  If neither worked I would install with neither attached.  Of, if I was lazy, I would just disconnect both modems, install Ubuntu, and figure out how to make the modem's work later.

Probably, because external, serial, modems virtually always work in Linux, I would leave that one connected and disconnect the Realtek.  Then I'd try and reinstall again...rinse repeat :)

That is just me.  The best way is to research both modems, and make sure they work in Linux if that is what you require.

---

