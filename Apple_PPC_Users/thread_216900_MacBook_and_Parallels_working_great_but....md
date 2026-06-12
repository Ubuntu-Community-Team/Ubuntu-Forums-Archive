---
title: "MacBook and Parallels working great but..."
date: 2006-07-16
forum: Apple PPC Users
---

### Post by apt on 2006-07-16
Ok I've sucsessfully got Ubuntu running great with Parallels on my MacBook(Networking, wireles everything works) but I've come across a screen resolution problem.

I managed to add the macbooks native 1280x800 resolution to the xorg.conf files using:

```
sudo gedit /etc/X11/xorg.conf

```

and adding 1280x800 to the 24bit section. when i reboot the screen is in the full MacBook 1280x800 size at the login screen but when I try and login the screen blanks out and returns me to the login screen after a few seconds. I had to login as a failsafe terminal session to change the xorg.conf file back to 1200x800 in order to login again correctly.

Can anyone help me with this problem?

Adrian

---

### Post by jedsen on 2006-07-16
As per [this guide]("http://bin-false.org/?p=17"):
**[COLOR="DarkRed"]To get video working, using Synaptic and turn on the Universe Repo, then search for 915resolution, install it, and restart[/COLOR]**

---

### Post by apt on 2006-07-16
Thats a no go...915resolution does not recognize my video card ](*,) 

Any more help?

---

### Post by jedsen on 2006-07-16
That's odd, as that guide is something like "how to get ubuntu working on a macbook". What error message do you get?

---

### Post by apt on 2006-07-16
As part of the setup you run 915resolution via terminal and it is supposed to list the supported resolutions... it does not recognize my video card.

I cant get the setup any further until it list my card.

Adrian :-k

---

### Post by jedsen on 2006-07-17
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by jedsen on 2006-07-17
Please click one of I think the i910 might be the driver you want, not the i965.

---

### Post by jedsen on 2006-07-17
You don't need to find your exact video card, as there is no driver for it. You might try the i910 driver, or better.

---

### Post by hajk on 2006-07-17
Guys, guys... the OP is running Ubuntu in a Parallels VM on his MacBook, so the best resolution he is going to get depends on what the VM is offering. This *may* not be the native 1200x800 resolution of the MacBook. As I understand it, there are Parallels Tools coming with the Parallels Desktop package that can be used to boost screen resolution from VGA to SVGA on Windows versions running in the Parallels VM; may be it works on Ubuntu Linux as well. If not, VGA is all you're going to get.:( 

So, he should read through the Parallels manual for answers, or direct a support question to the Parallels helpdesk directly. The 915resolution suggestion only works when Ubuntu is installed directly to the HD of the MacBook using BootCamp.

---

### Post by apt on 2006-07-18
Thanks for that reply.. i'll direct was support requests to parallels.

Thanks to all who helped.

Adrian

---

### Post by chasisaac on 2006-07-18
> **apt said:**
> Ok I've sucsessfully got Ubuntu running great with Parallels on my MacBook(Networking, wireles everything works) but I've come across a screen resolution problem.


Welcome to the limitations of Paralles. All I can say is 

```


apt-get complain GRRRRRRR


```

---

### Post by apt on 2006-07-18
I'm sure it will get better especially now that Apple is stocking it in Apple Stores

[http://arstechnica.com/journals/apple.ars/2006/7/18/4684](http://arstechnica.com/journals/apple.ars/2006/7/18/4684)

Adrian ;)

---

### Post by hamegro on 2006-09-11
Hi.

Could you tell me how you got Ubuntu run in Parallels?

With me, it doesn't work: After a fine install from a Ubuntu iso image onto the Parallels virtual hd, the boot process of the virtual ubuntu installation fails with the "loading hardware drivers".

Someone out there, who faced this problem too??

Thanks in advance and regards

hamegro

---

### Post by hajk on 2006-09-12
Hard to tell if anything went wrong during the install. I certainly didn't have any problems myself, I installed a few weeks ago in the stable Parallels version, have upgraded to the latest beta in the meantime. You mught want to compare with my notes on the install, see my sig.

---

### Post by mike3k on 2006-09-12
If you add custom screen resolution in Parallels (go to edit VM, under Video add the resolution you want) it will tell the OS running in the VM that those resolutions are available.

---

### Post by SeaHawk22 on 2006-09-17
Apt


Are you running a macbook or a macbook pro?
The reason I ask is I want to install Ubuntu on my macbook and xgl/compiz but  since it has an integrated graphics card I am not sure how it will handle it. 
I have two gigs of ram so there isnt a shortage of memory for the integrated card to fight for. 

(at least I think that is how it works:)  )

---

### Post by SeaHawk22 on 2006-09-17
Ahh, nevermind parallels does not support 3d graphics :(

---

