---
title: "how to enable airport with out internet"
date: 2010-02-26
forum: Apple Hardware Users
---

### Post by stones863 on 2010-02-26
ok heres my problem i have jaunty installed on my ibook g4 but i cant enable the airport cardbecuase my onboard nic has been ripped off so i cant connect a wire from the router i have 2 other comps that are online my question is how can i inable the restricted driver without internet on the mac im still a lil new to the linux scene so i need some help lol i just need to know how to enable the airport card without internet on the mac

---

### Post by llamabr on 2010-02-26
That was a pretty long post with no periods or commas.  nice.

what machine we talking about here?  On my old ibook, I couldn't get airport to work properly with ubuntu, since they no longer support the ppc architecture, but a fresh installation of debian lenny, and everything worked, right out of the box.

---

### Post by stones863 on 2010-02-26
lol sry my bad. its an ibook g4 everywhere else says that it works fine i just have to enable the restricted driver which i need internet to do, but my ethernet port has been ripped off the mobo lol.just need to know if i can do it without internet?

---

### Post by linuxopjemac on 2010-02-27
I guess when you download that package on another computer, put it on a USB stick, you should be happy, right ?

You have an iBook, I don't think there is a restricted driver for your architecture. You need open source. b43 is the one you need I think.

[http://ubuntuforums.org/showthread.php?t=1392844&highlight=b43-fwcutter](http://ubuntuforums.org/showthread.php?t=1392844&highlight=b43-fwcutter)

---

### Post by linuxopjemac on 2010-02-27
I tried to find where to download the b43-fwcutter package for powerpc, but I can't find it...can someone else post the link to this binary?

I could find the source package:
[http://packages.ubuntu.com/source/karmic/b43-fwcutter](http://packages.ubuntu.com/source/karmic/b43-fwcutter)

---

### Post by linuxopjemac on 2010-02-27
from the ubunu wiki:

> No Internet Access

If you don't have any other means of internet access on your computer, you will have to install b43-fwcutter and setup manually (without the firmware automatically downloading and being set up). b43-fwcutter is located on the Ubuntu install cd under ../pool/main/b/b43-fwcutter/ or in the official repositories online.

Double click to install or in a terminal issue the following command:

~$ sudo dpkg -i b43-fwcutter*

See Also: [http://manpages.ubuntu.com/manpages/karmic/en/man1/b43-fwcutter.1.html](http://manpages.ubuntu.com/manpages/karmic/en/man1/b43-fwcutter.1.html)

[link]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

---

### Post by llamabr on 2010-02-27
Well, I have the same machine, and when ubuntu didn't install over wireless, I installed debian lenny instead.  Since ubuntu no longer supports the ppc architecture, you're going to have much better luck working with debian on that machine.  Or at least I did.

---

### Post by linuxopjemac on 2010-03-01
Ilamabr: you already made your point with Debian Lenny. Although I agree with you, there is no need to keep on repeating your statements.

---

### Post by las_vegas on 2010-03-01
You should be able to find the B43 driver on your Install CD, in the 'pool' folder.

---

