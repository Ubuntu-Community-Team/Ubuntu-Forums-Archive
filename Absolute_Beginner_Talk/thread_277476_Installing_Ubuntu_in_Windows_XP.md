---
title: "Installing Ubuntu in Windows XP"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by knight17 on 2006-10-14
I am connecting to the internet using a LG CDMA modem so I afraid I can't get a driver for that in Ubuntu Linux.Is there anything  I can try such as virtualisation etc...
Thanks

---

### Post by raul_ on 2006-10-14
Try running the Dapper Live Cd, and see if u can connect to the internet through there

---

### Post by NeonShadow on 2006-10-14
Go ahead and install Ubuntu.

From this article you should find all you need:
[http://www.linuxquestions.org/linux/answers/LinuxQuestions_org/CDMA_modem_phone_Howto](http://www.linuxquestions.org/linux/answers/LinuxQuestions_org/CDMA_modem_phone_Howto)


From what it looks like, you are using a similar service to what I have. I'm using Verizon EVDO service with PC5740 aircard.

There are several ways to connect, but simplest seems to be modifying wvdial dialer... it doesn't connect 100% of the time, but you just have to re-try. Also, it will install the driver as a usb device and there are restrictions on how fast it will connect. So far I have not able to have a sustained speed of more than 177kbps.

There are several how-to's if you search for EVDO on linux or something of the sort. One has a patch to the kernell, which I tried, and got speeds of 700+kbps, but it did not persist and caused some other errors - I'm 100% sure I didn't do it right, as there are people for whom it has worked.

---

### Post by knight17 on 2006-10-16
Thanks for the link NeonShadow, it is useful to me

---

### Post by knight17 on 2006-10-16
Another question Can I install Ubuntu in Windows XP

---

### Post by bulldog on 2006-10-16
As an application in XP??

No you can't.

It's an Operating System,not an application.

---

### Post by elchinovi on 2006-10-16
> **knight17 said:**
> Another question Can I install Ubuntu in Windows XP

What do you mean with "install Ubuntu in XP"...?
You can have both by dualbooting and have the choice at startup...
Is that what you want to do?

---

### Post by guilag on 2006-10-16
Yes you can !

But you have to use a Virtual Machine like Virtual PC or VM-Ware. I suggest you this article: [http://johnbokma.com/mexit/2005/11/07/vmware-player-ubuntu-installation.html]("http://johnbokma.com/mexit/2005/11/07/vmware-player-ubuntu-installation.html")

It show`s you how to install ubuntu on WinXP via the ubuntu installation iso file !

Enjoy !

---

### Post by knight17 on 2007-03-09
Can you tell me about the performance of such a setup any idea ?
> **guilag said:**
> Yes you can !

But you have to use a Virtual Machine like Virtual PC or VM-Ware. I suggest you this article: [http://johnbokma.com/mexit/2005/11/07/vmware-player-ubuntu-installation.html]("http://johnbokma.com/mexit/2005/11/07/vmware-player-ubuntu-installation.html")

It show`s you how to install ubuntu on WinXP via the ubuntu installation iso file !

Enjoy !

---

