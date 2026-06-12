---
title: "Can't connect to Airport Extreme on iBook G4"
date: 2010-05-11
forum: Apple Hardware Users
---

### Post by Coldplayfan on 2010-05-11
Dear Ubuntu community,

I was easily able to install Ubuntu 10.04 (powerpc version) on my old iBook G4 just to see what it was like. After installation, I tried to connect to my Airport Extreme, and it didn't work.

For the past few days, I have been trying to research how to be able to connect to my Airport Extreme, and I have had no luck. Apparently, there is some sort of driver that I have to install called b43-fwcutter, but I have no clue where to find it or how to install it.

Can someone please help me with my problem? I'd greatly appreciate it.

Btw, the iBook obviously isn't the only computer I have, so I am able to download necessary packages on other computers, and transport it with USB flashdrives.

Thanks in advance!

Coldplayfan

---

### Post by linuxopjemac on 2010-05-11
in a terminal:

```
sudo apt-get install b43-fwcutter
```

Then let it do its job.
Reboot and enjoy internet. It worked for me too...

---

### Post by Coldplayfan on 2010-05-11
> **linuxopjemac said:**
> in a terminal:

```
sudo apt-get install b43-fwcutter
```

Then let it do its job.
Reboot and enjoy internet. It worked for me too...

When I try to run this is the terminal, it says that I can't find ports.ubuntu.com, my main guess is that it can't connect to the internet at all. 

I guess I should of mentioned that I don't have any ethernet cables handy with me, so the computer is completely cut off from the internet.....sorry about that. :-?

---

### Post by linuxopjemac on 2010-05-11
You need an internet connection yes, of course. There is a possibility without internet connection, although I never tried that.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#No%20Internet%20Access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#No%20Internet%20Access)

Please not that the link is not completely correct. You have to scroll down for the passage about b43-fwcutter without internet...


No Internet Access

If you do not have any other means of internet access on your computer, you will have to install b43-fwcutter and setup manually (without the firmware automatically downloading and being set up). b43-fwcutter is located on the Ubuntu install cd under ../pool/main/b/b43-fwcutter/ or in the official repositories online.

Double click on the package to install or in a terminal navigate to the folder containing the package and issue the following command:

```
:/b43-fwcutter/$ sudo dpkg -i b43-fwcutter*
```

Note: Do not select 'fetch and extract firmware'. Once installed in a terminal type the following to view the b43-fwcutter manual page for further instruction:

```
~$ man b43-fwcutter
```

---

### Post by Coldplayfan on 2010-05-12
Finally! I was able to get the internet working! All I was doing wrong was not actually downloading the drivers, and using the fwcutter command line to install the drivers. After putting the drivers on my computer, I simply just used the command line to extract the driver data to the firmware library.

Thanks for your help! :)

---

