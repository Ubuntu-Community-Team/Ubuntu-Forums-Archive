---
title: "Newbie needs some help!"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Nahalmmv on 2008-01-28
Hello on and all. I'm new to the forums, and new to ubuntu really but let me cut to the chase.

I have a dell inspiron E1505 laptop with an ATI x1400 video card, and thus far I have failed nearly every endeavor to install any alternate operating system (alternate meaning anything other than windows) because for some reason (as far as I have been reading), many linux distributions are not compatible with my video card. :(

I'm very much a newbie to linux and unix and all that jazz, and the only thing I have successfully gotten to work on that laptop is Damn Small Linux. I tried linux mint 3.0 and 4.0 but both shout the same jazz back at me that every other linux distribution shouted at me.

I'm just, for the most part, requesting some person to person assistance with getting *something* working on the laptop that is linux based, and has wireless capability, as I am going to be using it for college and thought linux would be a safer bet for me and my files and stuff.

I know how to burn ISOs, how to partition, how to do this and that but I can't seem to get anything to work. I'm here cause I did a google search for ATI x1400 compatible linux versions and this was on the search results.

So if anyone would be kind, please respond, and let's get something together so I can continue my eager pursuit into linux!

Thanks :)

---

### Post by Rocket2DMn on 2008-01-28
FYI, many colleges are very picky about the OSes they support, so they will probably not offer you assistance with getting your linux machine setup on their network.  That being said, you can always set up a dual boot system.
Your video card probably won't work with the open source ATI drivers ( see [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) ) but should work with the proprietary drivers ( see [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) ).
So, if you haven't been able to install from the LiveCD, you can download the alternate install cd which is just a text-based installer with no live session, but it works very well.  You can get it at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box at the bottom for the Alternate install cd.  
After install, you can run the directions at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-44352176e719033e226dffcab95c6e2647bdb882](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-44352176e719033e226dffcab95c6e2647bdb882)
If you don't even get a GUI after install, let us know and we'll go from there.

---

### Post by spiderbatdad on 2008-01-28
while the majority of ati cards work out-of-the-box in Ubuntu, some do not. It seems I have seen other posts regarding that particular card. I don't see it listed with the xserver-radeon drivers. The easiest things to do, as you must know, is to try out the live cd before making an installation. That way you can test Ubuntu without affecting your system.

---

