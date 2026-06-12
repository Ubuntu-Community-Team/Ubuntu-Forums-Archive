---
title: "first tribulations"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Hasdrubal on 2007-09-01
Once upon a time Hasdrubal got sick and tired of microschoft(duth for microba***rd) and took a leap in to the abyss known as ubuntu.
I'm a twit, no idea what I got into! here's my spec's:
MB=asus m2n32-si deluxe
proc.+amd64 3500+
VC=nvidia geforce6200
running=Ubuntu6.06 lts X64pc

now perhaps I'm at the wrong place but have to start somewhere.

I can't seem to reach certain webpages, i suspect lack of java, tried to download java linux, page loads yet never comes.

tried to follow instructions to install nvidia drivers but a prerequisite was a command(lspci | grep -i nvidia), don't know how to enter the script or in which program, can't find com.prompt.
the recommended way to install the binary drivers is to use System &#8594; Administration &#8594; Restricted Devices Manager. but restr.dev.man. is not in my menu.

I would like to use data on windows HD(all media formats mp3,mp4,avi,mpg,mpeg,dvd,wmvsorry etc.) is this possible? When trying to enter drive it cant launch.there is enough diskspace to partition and shuffle in order to convert.

So these are my first tribulations, can anyone help me? much appreciated!

---

### Post by banewman on 2007-09-01
Lots to sort out! An easier way would be to join the chat at #ubuntu. In your menu - applications - internet there is a listing for Gaim - use that to connect to ubuntu servers. Lots of people there to answer each question at a time. Java can be enabled through firefox. At the top of firefox click edit-preferences and select enable java. :)

---

### Post by AndyCooll on 2007-09-01
1. Not quite sure where you got the idea that you need to use the command line to install Nvidia drivers. Just click System > Administration > Restricted Drivers Manager.

The command line is Applications > Accessories > Terminal 

2. Sharing a Windows drive is possible. It will probably be an NTFS drive. For that you will need to install NTFS-3G. Here is the howto: [MountingWindowsPartitions/ThirdPartyNTFS3G]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G")

3. Java can also be installed using the Add/Remove facility under Applications.

:cool:

---

### Post by Hasdrubal on 2007-09-01
thx alot guys going to try tips imminently, but the restricted thigamyjig doesnt follow that menu.

---

### Post by nonewmsgs on 2007-09-01
ohhh you're using ubuntu 6.06!!!! there is no restricted driver option for that
that option is in 7.04 (i would recomend 7.04, but that's your choice)

does this help?
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

