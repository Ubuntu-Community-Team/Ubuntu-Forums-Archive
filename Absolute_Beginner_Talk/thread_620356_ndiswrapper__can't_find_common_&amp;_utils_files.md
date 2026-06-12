---
title: "ndiswrapper : can't find common &amp; utils files"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by Radiolad on 2007-11-22
Hi, I've been running Gutsy on an X86 P11 machine with Wireless connectivity for about 2 weeks. I downloaded **ndiswrapper-common**, and** ndiswrapper-util** whilst using a _wired_ Ethernet connection and all is well with a 89-100% connection (brilliant !)

Now...here's the problem..... I've also been running _**Fiesty**_ for approx 12 months on an iMac via a wired Ethernet connection. I thought I would download the above mentioned ndiswrapper(common and util) via SYNAPTIC as I have done with Gutsy and run it via Wireless as well ......**but I cannot locate the files**. I have ticked all the repository 'boxes' in order to search for them but still no luck.
Is it because ndiswrapper is not compatible with Fiesty ??
I've noticed that the *Software sources  GUI* is  different in Gutsy (it has a 3rd party option which Fiesty does not have)

Your help and advice would be appreciated. Cheers, Radiolad.

PS. If I can download them using a 'terminal ' command I'm still a NEWBIE in this area so an idiot cut and paste guide would be helpful  :confused:

---

### Post by overdrank on 2007-11-22
> **Radiolad said:**
> Hi, I've been running Gutsy on an X86 P11 machine with Wireless connectivity for about 2 weeks. I downloaded **ndiswrapper-common**, and** ndiswrapper-util** whilst using a _wired_ Ethernet connection and all is well with a 89-100% connection (brilliant !)

Now...here's the problem..... I've also been running _**Fiesty**_ for approx 12 months on an iMac via a wired Ethernet connection. I thought I would download the above mentioned ndiswrapper(common and util) via SYNAPTIC as I have done with Gutsy and run it via Wireless as well ......**but I cannot locate the files**. I have ticked all the repository 'boxes' in order to search for them but still no luck.
Is it because ndiswrapper is not compatible with Fiesty ??
I've noticed that the *Software sources  GUI* is  different in Gutsy (it has a 3rd party option which Fiesty does not have)

Your help and advice would be appreciated. Cheers, Radiolad.

PS. If I can download them using a 'terminal ' command I'm still a NEWBIE in this area so an idiot cut and paste guide would be helpful  :confused:

HI maybe this link will help
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-8dab2e7796e2e5c434430a92af48a9ba2af48b85](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-8dab2e7796e2e5c434430a92af48a9ba2af48b85)

---

### Post by Radiolad on 2007-11-22
> **overdrank said:**
> HI maybe this link will help
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-8dab2e7796e2e5c434430a92af48a9ba2af48b85](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-8dab2e7796e2e5c434430a92af48a9ba2af48b85)

Hi, Many thanks for the link. I'm going to give it a try on my Feisty machine.

Any ideas as to why SYNAPTIC (via Fiesty) will not find them ??

Cheers, Radiolad   :)

---

### Post by spiderbatdad on 2007-11-22
different repo.
did you get ndisgtk from synaptic as well?

---

### Post by Radiolad on 2007-11-22
> **spiderbatdad said:**
> different repo.
did you get ndisgtk from synaptic as well?

Hi,....Yes, ndisgtk has been picked up on Synaptic on my Feisty (iMac) machine but I have not installed it !!!   Is this me not seeing the wood for the trees ? :(

---

### Post by spiderbatdad on 2007-11-22
I'm sorry I don't know what the fiesty repos look like. In Gutsy it's a supported package called ndiswrapper-common-utils.1.9, or something like that. I think for fiesty you need 1.8. You can probably find it on SourceForge. I'll look for a link and post back for you if you still need it.

---

### Post by Radiolad on 2007-11-22
> **spiderbatdad said:**
> I'm sorry I don't know what the fiesty repos look like. In Gutsy it's a supported package called ndiswrapper-common-utils.1.9, or something like that. I think for fiesty you need 1.8. You can probably find it on SourceForge. I'll look for a link and post back for you if you still need it.

Hi, I would be most grateful.  Cheers.

---

### Post by Radiolad on 2007-11-22
> **Radiolad said:**
> Hi, I would be most grateful.  Cheers.

Hi.  I AM AN IDIOT !!!   I'm running DAPPER 6.06.1 on my iMac (not Feisty)
....but the query remains the same. 
Sorry for my incompetance. :(

---

### Post by spiderbatdad on 2007-11-22
[http://sourceforge.net/search/?words=ndiswrapper+utils&type_of_search=soft&pmode=0&words=ndiswrapper+utils+1.8&Search=Search](http://sourceforge.net/search/?words=ndiswrapper+utils&type_of_search=soft&pmode=0&words=ndiswrapper+utils+1.8&Search=Search)

this looks interesting.
what you want is ndiswrapper utilities 1.8 but the above shows another sort of GUI installer that may be even better for you to use. There is also a good how-to in the networking section of this forum called Troubleshooting your wireless something or other. If you do a thread search "troubleshooting wireless" i think you'll find it.

---

### Post by overdrank on 2007-11-22
> **Radiolad said:**
> Hi.  I AM AN IDIOT !!!   I'm running DAPPER 6.06.1 on my iMac (not Feisty)
....but the query remains the same. 
Sorry for my incompetance. :(

:confused:

---

### Post by Radiolad on 2007-11-22
> **spiderbatdad said:**
> [http://sourceforge.net/search/?words=ndiswrapper+utils&type_of_search=soft&pmode=0&words=ndiswrapper+utils+1.8&Search=Search](http://sourceforge.net/search/?words=ndiswrapper+utils&type_of_search=soft&pmode=0&words=ndiswrapper+utils+1.8&Search=Search)

this looks interesting.
what you want is ndiswrapper utilities 1.8 but the above shows another sort of GUI installer that may be even better for you to use. There is also a good how-to in the networking section of this forum called Troubleshooting your wireless something or other. If you do a thread search "troubleshooting wireless" i think you'll find it.

Hi, Thanks for the link. I'll give it a try.
Apologies to 'Overdrank' for the confussion.......
I'm a long-term 'Windows' man trying to escape ....slowly, slowly ...but I'm getting there:)

I'll let you know how I get on.
Cheers, Radiolad.

---

### Post by Radiolad on 2007-11-22
> **spiderbatdad said:**
> [http://sourceforge.net/search/?words=ndiswrapper+utils&type_of_search=soft&pmode=0&words=ndiswrapper+utils+1.8&Search=Search](http://sourceforge.net/search/?words=ndiswrapper+utils&type_of_search=soft&pmode=0&words=ndiswrapper+utils+1.8&Search=Search)

this looks interesting.
what you want is ndiswrapper utilities 1.8 but the above shows another sort of GUI installer that may be even better for you to use. There is also a good how-to in the networking section of this forum called Troubleshooting your wireless something or other. If you do a thread search "troubleshooting wireless" i think you'll find it.

Hi, ....Well I'm completly out of my depth with the info on the 'sourceforge site' because once the 'ndis ...' is downloaded it is all 'terminal driven'  from then on !

From the link given by **Overdrank** earlier, I have managed to download/install **ndiswrapper-common_1.38,ubuntu_all.deb**  But the 'util' file is for i386 architecture only, and I'm trying to install onto my **iMac** which is PPC   :confused:

I have tried re-booting to see if the Wireless link would respond as it did on my i386 machine  but it just sits there with its link light shining.
N.B When I check for devices, the ZYXEL  dongle is detected on the USB connection.

*This is where I start getting sucked back to  (arrgh) .....Windows* :mad:

PLEASE .....throw me a life-line :roll:

---

### Post by spiderbatdad on 2007-11-22
that program reports to be a GUI. Have you searched for it in applications and such?
Now, [http://ubuntuforums.org/showthread.php?t=571194&highlight=troubleshooting+wireless](http://ubuntuforums.org/showthread.php?t=571194&highlight=troubleshooting+wireless)

this is a good link to troubleshooting your problem. If your network is not encrypted you should be able to connect fairly easily, without a lot configuration. Just enable wirelss and manually configure by clicking on the network monitor in the taskbar. Best of luck.

---

### Post by Radiolad on 2007-11-22
> **spiderbatdad said:**
> that program reports to be a GUI. Have you searched for it in applications and such?
Now, [http://ubuntuforums.org/showthread.php?t=571194&highlight=troubleshooting+wireless](http://ubuntuforums.org/showthread.php?t=571194&highlight=troubleshooting+wireless)

this is a good link to troubleshooting your problem. If your network is not encrypted you should be able to connect fairly easily, without a lot configuration. Just enable wirelss and manually configure by clicking on the network monitor in the taskbar. Best of luck.

Hi, Thanks for this link  :)  I'll give it a go in the cold light of day. I'm off to the land of ZZZzzzzz zzzz  zzzz now !!!!
Thanks again.  Radiolad.

---

