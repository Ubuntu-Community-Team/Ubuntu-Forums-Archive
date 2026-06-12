---
title: "Connection Problems (Driver Update?)"
date: 2012-01-31
forum: Any Other OS
---

### Post by Gelegenheit on 2012-01-31
I've been having problems with the WiFi at school.  Internet often cuts out and I need to reboot my wireless adapter to have any hope of having access to the internet.  I am not entirely sure if "cut out" is an entirely accurate term because, when it does stop, Firefox thinks for a long time before saying that it is unable to connect to the server at X or that the connection timed out.

"lspci -nnk | grep -ia2 net" reveals
[HTML]Kernel driver in use: intel ips
    Kernel modules: intel_ips
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8181]
    Kernel driver in use: rtl8192ce
    Kernel modules: rtl8192ce
03:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
    Subsystem: Toshiba America Info Systems Device [1179:fd50]
    Kernel driver in use: atl1c
[/HTML]Is it possible that the use of a kernel driver that is not tailored to the WiFi adapter would lead to a lower level of performance?  WiFi works adequately while at home.  I'm hesitant to say "fine" or "great" because I have not done any empirical tests on whether it works the same on Linux as it does on the Windows 7 in which I installed Linux.  But I do not need to constantly reboot my adapter.

The fact that I am using a driver that does not match the hardware makes me wonder if the lower speeds incurred by having to share with numerous other WiFi devices, a managed network, and the geography of the WiFi, combined with an inexact driver would make my connection more prone to stoppages than other students.  But the fact that the driver is for an RTL8192CE doesn't make sense in  the problem.  Realtek's Linux driver for the 8188CE is labeled  92CE_SE_DE, suggesting to me that the use of an 8192 driver is not the problem.

 But, there is also the question of, if my WiFi connection is so weak, why is my connection registering as strong?  While I was taking care of my grandmother and before I used Linux Mint extensively on this particular computer, Windows 7 and my dad's phone would say that the WiFi was screaming fast but I was experiencing problems with my connection to the internet.  Right now, Network settings is telling me that my current speed is 54 Mb/s (I am not sure if this would be shared among the students or if this is my share).  Yet, I am currently typing without a connection to the internet, relying on the fact that I got to the page before the internet stopped.

When I use Windows and have this problem, the network menu tells me that I am able to connect to the network fine but the network is not able to connect to the internet.  I am a bit skeptical of this because other people are able to access the internet.

Another thought is that there is something about Toshibas, Realteks, and/or Linux that makes the internet want to grind to a halt.  I noticed someone else on a Toshiba with Windows 7 having trouble with his internet while the person next to him was having no problems.  And, while speaking to someone who also used Linux (Ubuntu), he said that the campus hated Linux.  I never thought to ask if he had looked into into his driver.  I hope to God that it is not an unsurmountable problem with Linux or a hardware failure.  But, if either of these were the case, why would I be able to connect to the internet rather well at home or able to connect at all, however spottily?

Perhaps updating the driver will help?  If I am using an older driver than is available, would it be possible that using the recently updated Linux driver (2 Jan 2012) would fix the problem.  The problem with this is that 1). I never effectively learned how to use a tar.gz to install an application or a driver and 2). I am not entirely sure of how I would rollback the driver if the updated driver not only fails to fix the problem but destroys my ability to use WiFi.  I've already backed up the files that I would need if I were to abandon ship and moved them to the Windows partition but it would be a pain to completely uninstall Linux and start from scratch because I did not know how to rollback a driver.

Sorry if it seems like I am rambling.  The fact that I can't just install or update a certain package has me out of my comfort zone and I could probably use the perspective of someone who is more familiar with such a problem than I.

---

### Post by Paddy Landau on 2012-02-01
I don't know much about wireless, but I see no one else has answered you, so I'll give it a bash.

First:

The fact that you have problems with Windows as well as Linux points to something perhaps more fundamental. I can only guess what it may be -- problems with the wireless card; a loose connection in your computer; a poor computer design that inhibits your connection; problems with the campus network that perhaps (incorrectly) favours certain types of wireless...

Second:

You wrote, "... the Windows 7 in which I installed Linux." Do you mean that you have installed WUBI? Solutions to WUBI are sometimes different from solutions to a native installation.

Third:

I have had problems with Realtek wireless before. It is possible that a later kernel version would solve this. Try [downloading the latest Ubuntu]("http://www.ubuntu.com/download/ubuntu/download"), burn it to CD (or preferably USB), boot from it (without installing), and see whether or not you still get the same problems.

If you don't get problems, it probably means that the latest version has a better driver, and you would get better results by installing the latest version. (If possible, I would recommend a clean installation rather than an upgrade.)

HTH

---

### Post by Gelegenheit on 2012-02-01
Thank you for the reply.

1.  I've been suspecting that it might  be a hardware fault like a loose connection or something similar because  it happened on both Win7 and Linux Mint and at my grandmother's and  school.  But, that would not explain why my connection would be fine at  home.  I am also hesitant to find out if a hardware issue is the case  because laptops are not as easy to crack open and look inside as  desktops and I would rather exhaust more possibilities than start poking  around in there unless I was sure I or some techie needed to.
  The  quick talk with the Linux user made me suspect a discriminative policy  as well. If that were the case, how would I know for sure if it was and  would there be any way of rectifying this?
He also told me that he  was using a version prior to Ubuntu's switchover to Unity.  A more  current kernel could fix it.  I am also using a custom kernel that I  found to allow me to see the battery due to something like lazy coding  on the part of Toshiba.  That may have something to do with it but I  think that I was experiencing problems before getting that kernel. 

2.   I installed using Linux Mint's packaging of Wubi (I don't have my  install disc on me to give you the precise name) but it is effectively  the same as Wubi.  Whether or not the differences between Ubuntu and  Linux Mint (a Ubuntu derivative) are the cause of the problem are  unknown.

3.  I'll be sure to burn a disk for the current Ubuntu  to see if a more recent version will help.  Ideally, I would not be  using a completely clean install because of the issue with the battery  being adequately addressed.  But I will at least look into updating to  see if it is an issue with the kernel.

Another option is to use a Windows driver from Realtek and see if that addresses the issue.

---

### Post by Perfect Storm on 2012-02-01
Moved to Other OS/Distro Talk.

---

### Post by Paddy Landau on 2012-02-02
OK, you did not say that you were using WUBI. I believe -- but I may be wrong -- that WUBI can be a bit different from a native installation.

Also, you are using Mint; although it's an Ubuntu derivative, it is not in fact part of the Ubuntu family, so it very well may be using a different kernel and driver.

One possible reason for differences between home, grandmother and school could be the router. Sometimes, a router is picky about the receiver, believe it or not. I myself have suffered from that same problem until I replaced my router. So... does your grandmother have a different make of router from your one at home? What about your school?

Although it is possible that your school has a discriminatory policy, it is very unlikely.

If you can get a Linux driver from Realtek, that would be great. If Realtek offers only Windows drivers, you may be able to use it with [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"), which allows you to use a Windows driver on Linux for your wireless. It is a very long time since I last used ndiswrapper, so please read the instructions; I don't remember how.

---

### Post by Gelegenheit on 2012-02-02
Currently using Ndiswrapper with the latest Windows driver because I needed to update my Windows driver anyway.  It seems better but not perfect.  It is a bit hard a cause.  I will try installing the Linux driver tonight and see if that helps tomorrow.  Thanks a ton for the help.

---

