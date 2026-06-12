---
title: "LinuxMint looses network connection"
date: 2011-06-04
forum: Any Other OS
---

### Post by DeMus on 2011-06-04
Hi,
I'm using Mint 9 in the 64-bits version. Since a couple of days my wired network connection stops working. It (eth0) just disappears from the list in the network manager. I can reboot and it is back and functions as it has always done. I did not install any new software lately, just the normal updates which come in almost every day. Are there any more MInt users with this problem, so I know it is related to software or an update? If not, it must be something here.
I watched the log files and found this:

CODE: SELECT ALL
Jun  3 22:17:18 linuxmint9 kernel: [   80.434590] NetworkManager[1163]: segfault at 18 ip 00007f7ff212f00e sp 00007fff9db9a4e0 error 4 in libdbus-glib-1.so.2.1.0[7f7ff2124000+21000]
Jun  3 22:17:18 linuxmint9 kernel: [   80.910377] NetworkManager[2567]: segfault at 18 ip 00007fdb21b7400e sp 00007fff65e6fa50 error 4 in libdbus-glib-1.so.2.1.0[7fdb21b69000+21000]
Jun  3 22:17:18 linuxmint9 kernel: [   81.218267] NetworkManager[2573]: segfault at 18 ip 00007f207220600e sp 00007fff6b52b630 error 4 in libdbus-glib-1.so.2.1.0[7f20721fb000+21000]
Jun  3 22:17:19 linuxmint9 kernel: [   81.700112] NetworkManager[2579]: segfault at 18 ip 00007fa36ea0200e sp 00007fff4b75d460 error 4 in libdbus-glib-1.so.2.1.0[7fa36e9f7000+21000]
Jun  3 22:17:19 linuxmint9 kernel: [   82.020041] NetworkManager[2587]: segfault at 18 ip 00007f11bfc9200e sp 00007fffcdf2a880 error 4 in libdbus-glib-1.so.2.1.0[7f11bfc87000+21000]
Jun  3 22:17:20 linuxmint9 kernel: [   82.407164] NetworkManager[2593]: segfault at 18 ip 00007f259b35b00e sp 00007fff88128ba0 error 4 in libdbus-glib-1.so.2.1.0[7f259b350000+21000]
Jun  3 22:17:20 linuxmint9 kernel: [   82.790910] NetworkManager[2601]: segfault at 18 ip 00007fc1ae3f700e sp 00007fff5784e120 error 4 in libdbus-glib-1.so.2.1.0[7fc1ae3ec000+21000]
Jun  3 22:17:20 linuxmint9 kernel: [   83.089331] NetworkManager[2608]: segfault at 18 ip 00007f09d1f3100e sp 00007fff7a311c80 error 4 in libdbus-glib-1.so.2.1.0[7f09d1f26000+21000]
Jun  3 22:17:21 linuxmint9 kernel: [   83.405838] NetworkManager[2614]: segfault at 18 ip 00007fc41c3e700e sp 00007ffff92a6240 error 4 in libdbus-glib-1.so.2.1.0[7fc41c3dc000+21000]
Jun  3 22:17:21 linuxmint9 kernel: [   83.767931] NetworkManager[2621]: segfault at 18 ip 00007fe658c6a00e sp 00007fff0137ae20 error 4 in libdbus-glib-1.so.2.1.0[7fe658c5f000+21000]


Who has any idea what to do to fix this error?
Thanks.
DeMus

---

### Post by DeMus on 2011-06-04
Thank you very much for placing my thread in a group where nobody ever comes. I may have forgotten so please help, what was the meaning of Ubuntu again?

---

### Post by IWantFroyo on 2011-06-04
Ubuntu means: "Linux for human beings."
You might find more help in the Mint forums.
I don't know LM's policies for LTSs, so your version might be already outdated, anyway. That means most of the devs will be concentrating on later versions, and not thoroughly testing your updates.
I would advise using a flash drive to back up your data, and installing Mint 11.

---

### Post by ivanovnegro on 2011-06-04
> **IWantFroyo said:**
> Ubuntu means: "Linux for human beings."
You might find more help in the Mint forums.
I don't know LM's policies for LTSs, so your version might be already outdated, anyway. That means most of the devs will be concentrating on later versions, and not thoroughly testing your updates.
I would advise using a flash drive to back up your data, and installing Mint 11.

I would not, because Mint 11 has the same bugs like in Ubuntu 11.04, the LTS is working great and better IMHO, why this recommendation to a user instead to help?

To the OP, I hope someone could provide you more help as I can, I am not using Mint and not experienced such an issue.

---

### Post by DeMus on 2011-06-04
> **IWantFroyo said:**
> Ubuntu means: "Linux for human beings."
You might find more help in the Mint forums.
I don't know LM's policies for LTSs, so your version might be already outdated, anyway. That means most of the devs will be concentrating on later versions, and not thoroughly testing your updates.
I would advise using a flash drive to back up your data, and installing Mint 11.

Thank you for your answer. LinuxMint 9 is the Mint version of Lucid and still 2 years in operation from now. So it is an active OS.
The Mint forums are not as active as the Ubuntu forum, atleast the general help. So I placed my thread there to find out it has been moved. I am pretty pissed about that, Mint is Ubuntu in a different jacket.
Do you happen to have an idea what could cause my loss of network connection?
Thanks.

---

### Post by sffvba[e0rt on 2011-06-04
@OP - I do not see how you can be frustrated about your thread being placed in the appropriate section of the Ubuntu forums... could you please link me to your post on this matter in the Linux Mint section?



Regards
404

---

### Post by DeMus on 2011-06-04
> **not found said:**
> @OP - I do not see how you can be frustrated about your thread being placed in the appropriate section of the Ubuntu forums... could you please link me to your post on this matter in the Linux Mint section?



Regards
404

This is the address of the webpage, but you will find the same story there:

[URL="http://forums.linuxmint.com/viewtopic.php?f=47&t=74223&sid=2460faede7b821fb6336642732963393"]_[COLOR="Blue"]Mintforums[/COLOR]_
[/URL]

Well, since Mint is a derivative of Ubuntu I was hoping it would stay in the General Help forum since that is the most active one.
Hope somebody can help me, that's much more important.
Thanks for your answer.

---

### Post by sffvba[e0rt on 2011-06-04
Thanks for posting the issue in the Mint forums too... often people only post in un-related forums and that doesn't help to make the official forum (in this case Mint) more popular and useful... As of this moment I don't have an answer for you... it would seem to be an isolated issue (for now)... I will however give you a bump on the Mint forums... maybe that helps


404

---

### Post by DeMus on 2011-06-05
> **not found said:**
> Thanks for posting the issue in the Mint forums too... often people only post in un-related forums and that doesn't help to make the official forum (in this case Mint) more popular and useful... As of this moment I don't have an answer for you... it would seem to be an isolated issue (for now)... I will however give you a bump on the Mint forums... maybe that helps


404

Thanks. I still have no idea what is going on. Hopefully somebody else either here or in the Mint forum knows what it is.

---

### Post by DeMus on 2011-06-05
It turned out to be a program I use to see what is on Usenet. I did change one thing in the program and it was OK, now I have changed that one item back into the original setting and it is still okay.

Thanks everyone.

---

### Post by DeMus on 2011-06-05
I still don't know what happened, but this is the story:
Whenever I would start a certain program I would loose my eth0 in the network-manager. A simple reboot would bring it back, until I used the same program again.
Later this afternoon, it became even worse and suddenly I had no network connection anymore. Even after a reboot, my network would not start. Panic.
I then took my brand new laptop, with Windows 7 I have to admit, and also that had no connection to my network or the internet.
I started to suspect the switch on my computer table. I checked all cables and they were okay. Then I rebooted the switch and .... I have a working network connection again. No matter what program I start and use, I have a working connection.
On the switch also a wireless router is connected, especially for our neighbors to hitch-hike on our fast internet connection until they have their own connection. I wonder if they also had problems the last couple of days. If so, sorry.

It looks like I have found what was causing this mess, although it might still be a little bit too early to tell.
Thanks everyone for trying to help.

---

### Post by sffvba[e0rt on 2011-06-05
All is well that ends well :)



404

---

