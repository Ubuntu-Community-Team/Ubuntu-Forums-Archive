---
title: "How to install video drivers"
date: 2005-08-13
forum: Absolute Beginner Talk
---

### Post by BARAI127835 on 2005-08-13
Hi guys, I need some help please!
I'm new to ubuntu,had it installed with no problems at all but........now I have NO clue on how to install the video drivers......:( That's the price you pay  for using windows for so long.:).I had downloaded the video drivers from Nvidia web site,but Im totally lost on how to install it, can you guys help.............Please.
Any help with be greatly appreacited.

Thanks

Rick

---

### Post by weasel fierce on 2005-08-13
Im sure someone else will have specifics, but open up Synaptic Package Manager, and search for your card or manufacturer. That way, you can install in a single mouse click or two :)

---

### Post by applejack on 2005-08-13
I saw this page earlier follow the NVIDIA instructions.
[https://wiki.ubuntu.com//BinaryDriverHowto](https://wiki.ubuntu.com//BinaryDriverHowto)

---

### Post by BARAI127835 on 2005-08-13
Thank you guys, I did that but now i have to find out on how to boot into ROOT to install the drivers, because so far all I have is the refresh rate of 60mhz, I want to go to 85, but thanks for all the info.
If is there is anyone out there kind enough to explain to me on how to get to root it will be appreaciated...once again thank you.
(Sometimes I wonder, why have I been using using windows for so long, this is much more stable although the comands and layouts are confusing but I'm learning).

Thanks 

Rick

---

### Post by applejack on 2005-08-14
Hi

The root acount is disabled by default. If you want to run a commad with root privileges just type sudo before it like this example.

sudo chown bob *

If it asks for a password just type in the one you use for your main account.  All the graphical configuration utilities use sudo by default including Synaptic which is what you will be usng to install the drivers. If that aks you for a  password just give the password for your main account that you typed in during the install.

more info on root here.
[https://wiki.ubuntu.com/RootSudo?highlight=%28root%29](https://wiki.ubuntu.com/RootSudo?highlight=%28root%29)

---

