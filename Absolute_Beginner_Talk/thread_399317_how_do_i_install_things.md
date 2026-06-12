---
title: "how do i install things?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by tobyfountain on 2007-04-02
Hi,
I've just installed Ubuntu on my Sony Vaio n21/m and I'm pretty impressed. I'm just having serious trouble getting my wireless card to work. I have tried to install Network Manager but it does not show you how to install it for a beginner - I dont understand any of the things it tells me to do, or where to put the code it gives me.
Please can someone tell me how to install either Network Manager or ndiswrapper in nice, easy beginner language? 
Thanks
Toby:KS

---

### Post by miggols99 on 2007-04-02
There are a few ways to install things. The easiest way is go to

Applications >> Add/Remove

A more advance method is:

System >> Administration >> Synpatic Package Manager

Or you can do it from the command line. I recommend aptitude:

sudo aptitude install name-of-program

---

### Post by tobyfountain on 2007-04-02
ok, thanks.
i have got the files in a folder on my desktop. how do I install them from there, and which is the right one to choose?
thanks
toby

---

### Post by natman on 2007-04-02
I know the feeling, To get wireless working make sure that ubunut actually knows its there first off, go to networking and see if the wireless box is ticked, then click properties and fill in the details.
To get any program intsalled use "synaptic" or open a terminal and type
[HTML]sudo apt-get install nameofprogram[/HTML]

Good Luck

---

### Post by mikeyphi on 2007-04-02
> **tobyfountain said:**
> Hi,
I've just installed Ubuntu on my Sony Vaio n21/m and I'm pretty impressed. I'm just having serious trouble getting my wireless card to work. I have tried to install Network Manager but it does not show you how to install it for a beginner - I dont understand any of the things it tells me to do, or where to put the code it gives me.
Please can someone tell me how to install either Network Manager or ndiswrapper in nice, easy beginner language? 
Thanks
Toby:KS

Have a look at here [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by tobyfountain on 2007-04-02
thanks, i tried that and it says it cant find the package ndiswrapper, even though it is on my desktop. how do i show it where it is, or, whats the correct filename?
thanks
toby

---

### Post by atomic0x on 2007-04-02
Welcome to Ubuntu!

Most of the commands you will see in the forums here need to be entered in a terminal window.  You can find this by clicking on Applications, Accessories, then Terminal.

What wireless card are you trying to install?  Check the model number and revision if possible.
Can you point us to the tutorial that you are trying to follow?

---

### Post by tobyfountain on 2007-04-02
it says i cant install network-manager as my pc type (i386) is not supported. and ideas?

---

### Post by miggols99 on 2007-04-02
Is there a .deb file? If so use that.

---

### Post by tobyfountain on 2007-04-02
not that I can see. I just downloaded the file from the interent on another computer and transferred it here. sorry if its basic, but I really don't understand how to install it.
if someone can tell me how to use it with add/remove, I might be able to figure it out from there.
thanks
toby

---

### Post by mikeyphi on 2007-04-02
> **tobyfountain said:**
> it says i cant install network-manager as my pc type (i386) is not supported. and ideas?

Did you get that message when you tried to install network manager using APPLICATIONS - ADD/REMOVE .....or?

---

### Post by atomic0x on 2007-04-02
What is the name of the file that you downloaded?  Also which version of ubuntu are you using?  If unsure click on System -> About Ubuntu and it will be listed there.

---

### Post by flyboy_2003 on 2007-04-02
In the Windows world you just find a file with an EXE extension on the net and then doubt click it. While this is (sometimes) possible in the Linux world (although Linux software will very often have RPM or DEB as an extension), it is not normally how we do it.

We use trusted software repositories and tools like APT (Advanced Package Tool) and Synaptic.

Try Googling apt and synaptic. 

Apt itself is a command line tool, and Synaptic is the graphical front end to it.

Cheers.

---

### Post by eentonig on 2007-04-02
forget downloading and installing programs int the windows way of doing. Linux has a much more develloped way of dealing with that (allthough you will currently find it shitty as hell, I bet.)

do you have any networking at all on that box currently? If so, use the proivded tools under System\administration\synaptic.


this will open a nice GUI where you can search for all known and trusted applications to install. Try doing it this way.

Or go read on help.ubuntu.com and follow the guides they provide.

---

