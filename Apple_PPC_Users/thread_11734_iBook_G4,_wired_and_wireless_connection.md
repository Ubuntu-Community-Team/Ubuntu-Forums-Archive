---
title: "iBook G4, wired and wireless connection"
date: 2005-01-18
forum: Apple PPC Users
---

### Post by netsec on 2005-01-18
Okay, I have seen it mentioned in a couple places but not a thread nor a solution.  I am running a G4 iBook.  I installed Ubuntu with the wired ethernet connection because that is what I run at home.  This week I am travelling and the hotel where I am staying has only wireless.  I have gone into /etc/network/interfaces to attempt a manual setup.  I have used the network configuration GUI.  I have deactivated the wired connection (no check on the GUI) and attempted a wireless connection. Wireless looks for but does not receive DHCP and deactivates itself.  I believe I have looked through every FAQ and thread and found nothing that worked.  

I am sending this on the mac side or I'd really be up a creek.  I need help.

---

### Post by Viro on 2005-01-19
[QUOTE=netsec]Okay, I have seen it mentioned in a couple places but not a thread nor a solution.  I am running a G4 iBook.  I installed Ubuntu with the wired ethernet connection because that is what I run at home.  This week I am travelling and the hotel where I am staying has only wireless.  I have gone into /etc/network/interfaces to attempt a manual setup.  I have used the network configuration GUI.  I have deactivated the wired connection (no check on the GUI) and attempted a wireless connection. Wireless looks for but does not receive DHCP and deactivates itself.  I believe I have looked through every FAQ and thread and found nothing that worked.  

I am sending this on the mac side or I'd really be up a creek.  I need help.[/QUOTE]
 You have not said anything about the wireless ethernet adapter you're using. If it's Airport Extreme, you're out of luck. AE is based on the Broadcom chipset. Broadcom hasn't released any drivers for their products and as such they won't work under Linux.

---

### Post by netsec on 2005-01-19
Duh.  You're right.  

It's just a regular airport, not the extreme.  I have used yellow dog and it sets up whichever network it finds.  I was hoping that Ubuntu would do the same.  As it is, just getting the airport to work would keep me from Yellow Dog permanently.

---

### Post by chascon on 2005-01-23
Ok, I going to correct this rumour I hear all over the net. I don't know why everyone denies their existance.  It could be simple ignorance, incompetance, or simple ambivilence but there are linux/unix drivers for airport extreme.  Yes I said airport EXTREME.
First of all there is a linux driver listed, although [propietary I believe, at [http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

Second see:
[http://www.monkey.org/openbsd/archive/misc/0302/msg01000.html](http://www.monkey.org/openbsd/archive/misc/0302/msg01000.html)

"Has anyone looked into porting over the changes made to NetBSD (and subsequently FreeBSD) that allow Airport Extreme cards in the newer Apple notebooks (and possibly other 802.11g equipment) to connect to HostAP systems? Apparently, they fail to con"nect properly because the 802.11g cards advertise bit rates higher than the standard 802.11b ones, and just cut the connection, resulting in a association failure. I'm willing to do any testing necessary to get this working :) Thanks, Ben -- It is ok to be ignorant in some areas, but some people abuse the privileg"

and

[http://www.monkey.org/openbsd/archive/misc/0307/msg00807.html](http://www.monkey.org/openbsd/archive/misc/0307/msg00807.html)

"It worked with the older airport extreme firmware but not with
the current firmware.  Here's a workaround:

Index: if_wi_hostap.c
===================================================================
RCS file: /cvs/src/sys/dev/ic/if_wi_hostap.c,v
retrieving revision 1.25
diff -u -r1.25 if_wi_hostap.c
--- sys/dev/ic/if_wi_hostap.c	16 May 2003 02:30:40 -0000	1.25
+++ sys/dev/ic/if_wi_hostap.c	1 Jul 2003 22:29:25 -0000
@@ -570,9 +570,11 @@
 	seq = take_hword(&pkt, &len);
 	status = take_hword(&pkt, &len);
 	challenge_len = 0;
+#if 0
 	if (len > 0 && (challenge_len = take_tlv(&pkt, &len,
 	    IEEE80211_ELEMID_CHALLENGE, challenge, sizeof(challenge))) < 0)
 		return;
+#endif
 
 	if (sc->sc_arpcom.ac_if.if_flags & IFF_DEBUG)
 		printf("wihap_auth_req: station %s algo=0x%x seq=0x%x\n","

So if there is something that can be adapted and learned from here, well then there's more than just hope.

Also, if you look at [http://www.macsense.com/product/broadband/wpe800_b.html](http://www.macsense.com/product/broadband/wpe800_b.html)
you'll find out chips the airport extreme card uses (I assume this because the "aerocard extreme" manufacturers claim inter-operability).  The chip sets mentioned are BCM4306 and BCM2050.  Thus the free software concentration should be on these chips if we're to get gnu-linux drivers, or help (port?) the freebsd driver rather than negate existence of an open/free driver.

Also, making a ppc ndiswrapper is possible but no ppc developers are dedicated enough to even start this project.  Yes I know this would be a lot of work.  But why not say it is possible rather than deny it is possible as I've read elsewhere.

Personally apple's choosing a card whose manfactuer has a reputation for not releasing specs to the open source community , and one with a weird plug that disallows one to use an alternative wireless internal cards (yes I know about usb externals.  This is not the point!) is evidence of apple's attempt to corner macppc buyers into using their OS.  This is a limiting of freedom and I believe aple's move goes against the free market goals.  Something that M$ themselves have been criticized for, monopolizing their OS onto PCs.  Personally I don't like where apple is going.  This is not classic capitalism, it is monopolizing in my mind. Yes I know what capitalism is, I've studied it.  Capitalism does not allow for cornering the market.  It is supposed to allow healthly competition and variety to benefit customers, not a control of what OS goes onto a subset architecture, which happens to probibly be largest 'market share' of a subset architecture.  Does anyone think pegasus actually sells lots of PPCs compared to apple?

And for those that are thinking, "You have the right to not choose apple hardware", don't fool yourself.  When the options are dictated to you, and you're offered only a subset of a larger set of posibilities, your freedom is restricted.

I honestly don't know what I can do, other than diseminate this info.  But I hope that people now know that there people working on this, at least the Freebsd people.  Hope people get involved somehow.

If the community is complacent about supporting airport extreme and freebsd gets it working (meaning Freebsd macppc will benefit [the webpage hasn't been update in yrs but the project is still chugging along.  There is an iso now]), I don't care, it's Freebsd for my ibook G4 (which now has openbsd).  I'll keep ubuntu-ppc on this iMac though.

---

### Post by chascon on 2005-01-23
Oh and lets not forget the opensource project
[http://sourceforge.net/projects/linux-bcom4301/](http://sourceforge.net/projects/linux-bcom4301/)

I wish they got things done faster.

---

### Post by Castaa on 2005-01-23
[QUOTE=chascon]Oh and lets not forget the opensource project
 [http://sourceforge.net/projects/linux-bcom4301/]("http://sourceforge.net/projects/linux-bcom4301/")
 
 I wish they got things done faster.[/QUOTE]
 
 I think people using the Airport Extreme chipset are running Windows x86 drivers through an emulation layer.  No one running Apple hardware using using Airport Extreme hardware.  That I have ever read.

---

### Post by Viro on 2005-01-24
[QUOTE=Castaa]I think people using the Airport Extreme chipset are running Windows x86 drivers through an emulation layer.  No one running Apple hardware using using Airport Extreme hardware.  That I have ever read.[/QUOTE]
 That's why binary only drivers are evil. They work only on one platform. Or else, we'd get nVidia accelerated drivers for PPC Linux as well.

@chascon
None of those links you provided tell you how to get Airport Extreme to actually work.

---

### Post by netsec on 2005-01-24
nor does it answer my issue with the airport (not extreme), wired ethernet and iBook.

---

### Post by chascon on 2005-01-29
[http://sourceforge.net/projects/linux-bcom4301/](http://sourceforge.net/projects/linux-bcom4301/)

I didn't promise a way to install on ppc, although I'd love to be able to say how.

Now the above link is working towards a driver that willl be portable to various archs.
And they do have access to the specs of airport extreme by way of an unnamed company.

The problem is that these devs are obligated to not divulge publically.  That's why it is going slow.
It is interesting to note that their site mentions, to the best of my recollection and  presumably prior to getting access to specs, that they hope some company will feel obligated by gpl to make the specs public or co-operate with open/free source devs (I'm paraphrasing).  What I understand from this is that airport extreme uses open/free source code in their driver.  Thus, if this is true, in my opinion braodcom is violating gpl license because gpl obligates them to make public the source.  The only exception to the above rule is if broadcom were not to distribute the driver they could keep the source (and changes) to themselves.  But since drivers for airport extreme hardware (a broadcom product) are distributed with OSs, the drivers should be opened up (again my interpretation of gpl).  Perhaps, broadcom's refusal to co-operate with the public directly is their legal attempt around this.  They dump the responcibility of providing drivers for their hardware to apple (as per an email I have from them).  They basically told me, your want drivers, get them from apple.  Yeah right, as if apple is going to distribute linux drivers!  Shows how stubborn and how commited they are to their refusal to co-operate with free source (idiots in my book).  Apple's whole reason behind broadcom and the odd connector is obviously to limit interoperablity.  Ergo, it's an attempt to lock their hardware customers to their bloated and slow OS (or at least this is how I feel being an owner of a 2004 ibook with airport extreme).

I give broadcom two fingers up, three if you count ...

---

### Post by dark0rbit on 2005-01-31
all ibook g4s have an airport extreme card, look in apple system profiler.

---

### Post by Castaa on 2005-01-31
[QUOTE=Viro]That's why binary only drivers are evil. They work only on one platform. Or else, we'd get nVidia accelerated drivers for PPC Linux as well.
 
 @chascon
 None of those links you provided tell you how to get Airport Extreme to actually work.[/QUOTE]
 
 I read the reason Broadcom hasn't released the specs or code for the card is that the hardware broadcasts and receives frequencies that are outside of civilian ranges.

---

### Post by chascon on 2005-02-03
"I don't buy the theory about government frequencies.  This theory asks
one to believe that government frequencies are not intercepted or
tampered with in some fashion.  They are tampered with and can be done
so easily.  Legally sold scanners enable one to listen in to all sorts
of private signals.  Also, mundane Radio shack parts apparently will
allow the techy in the know to manipulate government frequencies.  The
idea that they keep their specs in the dark because an insignificant
number of geeks might want to fool around with government frequencies is
not sound because these are not numbers to worry about, and because it's
not as if broadcom would be setting a precedence enabling the
manipulation of government frequencies by the public.  The concept of
broadcom not releasing specs because they do not want to "step on
government toes" is also problematic because it is ethnocentric.  It
assumes that these set of frequencies are illegal in all localities
where wireless is sold (globally).  Although I have not studied it, this
is probably not so.

The one [theory] about [broadcom] having [a] competitive edge [by not releasing specs for airport extreme] makes sense.  Especially
considering the history, regularly refusing to co-operate I'm told, that
broadcom has towards free/open source movements."

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

### Post by chascon on 2005-04-27
I know that there was a meeting between Stallman an ibm on which one of the subjects was setting up a protection fund for free software against devious software companies.  I wonder if they spoke about taking companies like braodcom to court for their violations against GPL, asumming that airport extreme has GPL code drivers.

---

### Post by webman2k on 2006-12-07
Here's my quick and painless guide in getting Airport Extreme to run using Edgy on an iBook G4:

[http://ubuntuforums.org/showthread.php?t=314036](http://ubuntuforums.org/showthread.php?t=314036)

- Have fun ;)

---

