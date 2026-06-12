---
title: "Broadband keeps disconnecting."
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by hyfather on 2007-12-22
Greetings!

    I recently started using Ubuntu 6.06, and I am loving it! Except for this odd issue which dampens my spirit.
    I configured my broadband connection (I live in India, Connection Provider: BSNL) by using the *pppoeconf* utility from the terminal. The connection seems to have been configured only partially because every time I connect (*sudo pon dsl-provider*), it starts up, I open a few web pages, and then and snaps within 30 seconds. The *plog* command tells me "Modem Hangup".
    I can't get anything done except waste my time on this distressing *pon-plog-pon-plog* cycle.
    I should also mention, that this problem is rather sporadic. It occurs seven times out of ten that I try to get online. The other three times, the connection seems to be working without a glitch, or snapping after every thirty-odd minutes, which is something I can deal with.
    And yes, I am a newbie, with no prior Linux experience. Any help will be really appreciated.

Thank you,
Nikhil M.


P. S. I am not sure whether this thread belongs to Networking Forum or this Beginner Forum. Could some admin move it, if that is the case, or should I post it there too?

P. P. S. Merry Christmas!

---

### Post by nowshining on 2007-12-22
have u tried a live cd of gutsy to see if this is an OS issue or not?

---

### Post by hyfather on 2007-12-22
No, I haven't. I don't have a Gutsy distribution CD at my disposal, and neither do I have sufficient bandwidth! I have requested a free CD from the Canonical guys, but that is going to take another six to ten weeks.
    Anyway, what do you mean by an OS issue? Its certainly not a generic OS issue, because I haven't come across any threads regarding this. An OS issue on my Hardware is also unlikely, because the same problem persists when I run the 64-bit Dapper on my Athlon 2800+, and when I run the 32-bit Dapper on my Toshiba Satellite.
    Taking into account the fact that the Windows XP (SP2) gives no connectivity issues, prima facie, and IMHO, this seems like an issue regarding connection settings. So, how do I go about troubleshooting this one?

---

### Post by nowshining on 2007-12-22
i was really heading toward kernel issues, on certain hardware, i can't help u on setting up broadband, i use dial-up and have not had a chance to have it yet on linux/ubuntu.

U'll have to be patient and wait for someone else to come along, by the way the windows kernel/ works diff. than the linux one. I did read while searching for various things that certain versions of the linux kernel can have trouble with certain hardware. 

U can (easily) download a more recent kernel version from the official kernel site

[www.kernel.org](www.kernel.org)

and compile it urself - on my site it shows u how or u can search the forums on a howtwo guide for installing the vanilla kernel of linux. Yes ubuntu uses debain (debain.com) unstable packages, which uses the in the end kernel from kernel.org heavily or so patched to their likeing.

---

### Post by hyfather on 2007-12-24
The kernel? You really think there is a problem with the kernel. I thought the LTS 6.06 kernel would have been stable! Anyway, if everything else fails, I think I'll have to redo the kernel.

Oh, and by the way, here is what *plog* typically displays:

[I]Dec 25 02:01:34 hyfather-laptop pppd[3754]: local  IP address 59.95.10.105
Dec 25 02:01:34 hyfather-laptop pppd[3754]: remote IP address 59.95.0.1
Dec 25 02:01:34 hyfather-laptop pppd[3754]: primary   DNS address 218.248.240.208
Dec 25 02:01:34 hyfather-laptop pppd[3754]: secondary DNS address 218.248.255.193
Dec 25 02:01:35 hyfather-laptop pppd[6049]: No response to 4 echo-requests
Dec 25 02:01:35 hyfather-laptop pppd[6049]: Serial link appears to be disconnected.
Dec 25 02:01:35 hyfather-laptop pppd[6049]: Connect time 3.0 minutes.
Dec 25 02:01:35 hyfather-laptop pppd[6049]: Sent 57673 bytes, received 286019 bytes.
Dec 25 02:01:41 hyfather-laptop pppd[6049]: Connection terminated.
Dec 25 02:01:42 hyfather-laptop pppd[6049]: Modem hangup
[/I]

Do you think something is wrong with my settings?

Here is the dsl-provider file in etc/ppp/peers:

[I]# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
usepeerdns
plugin rp-pppoe.so eth0
user "hyfather"
[/I]

Thank you!

---

