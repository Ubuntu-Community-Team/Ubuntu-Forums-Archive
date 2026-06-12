---
title: "Install with G4 Cube"
date: 2004-11-29
forum: Apple PPC Users
---

### Post by riccardo on 2004-11-29
Hello again ...

Now that my desktop has become completely ubuntulinux, I want to extend the empire!  My G4 cube design has been sitting doing very little after my rows with installing other ppc linuxes.  I had such sweet success with the warty install that I felt brave and put the same cdrom into my cube.

I restarted the machine with the <C> key pressed.  The result was that the cdrom booted as requested.  I then began the install.  The first step is to choose the keyboard /language.  Suddenly my keyboard is not registering.  I have lost all input from the keyboard.  What's happening!?

Has anyone else experienced this freeze?  My keyboard is perfectly (Apple) standard.  Should I try the keyboard from my iMac??  Maybe there is/are some commands to pass along to the kernel to allow it to work with the keyboard.  Ideas please?


riccardo


richard.jenkins at internode.on.net

---

### Post by adamward on 2004-11-29
Give the official keyboard from your iMac a try.  I had a problem with a third party keyboard the first time I tried to install YDL 3.0 on my old iMac.  The official keyboard solved my problems.

Hope it works!

--adam

---

### Post by riccardo on 2004-11-29
Adam

Thanks for your assistance.  I should have been more precise - I am using an Apple keyboard as supplied with my cube when I bought it new - back when it was the latest and greatest.  I shall give the keyboard from my iMac a try.

Thanks


riccardo

---

### Post by johnny_g on 2004-11-30
What I did to get it installed on my cube:

for the install used 'expert' mode and just skipped the keyboard part. Worked like a gem for the installation part but a new problem arose.

I can't boot into Linux; it freezes when initializing plug-and-play (not sure of the exact phrasing). Any way around this problem (suggestions)?

Cheers,

John

---

### Post by Dragonfly_X on 2006-03-14
I have a similar problem. Myne freezes when installing the Ubuntu Base. :confused:

---

### Post by th3joker on 2007-11-25
Hi,

I managed to get Fedora working on my Cube and ran it as my Web Server and Mail Server until recently.

I tried Yellow Dog and Ubuntu too but found the Fedora install by far the most reliable and easy.

I've just put Tiger on it for my Daughter and it's all working well, still use it for Music and some Movie watching. Leopard won't install at the moment because of the CPU being outside of Leopard specs, the install DVD boots though so I reckon I can get it running.

Would love to upgrade it but will wait until I can afford a standard one as I want to keep an original hanging around as I still love these things.

I also have a Mac Pro Quad Intel and a Mac Mini which I upgraded to a Core 2 Duo 2.66 GHz with a 1TB SATA external using the internal SATA mod.

---

### Post by oswaldkelso on 2007-11-25
> **riccardo said:**
> Hello again ...

Now that my desktop has become completely ubuntulinux, I want to extend the empire!  My G4 cube design has been sitting doing very little after my rows with installing other ppc linuxes.  I had such sweet success with the warty install that I felt brave and put the same cdrom into my cube.

I restarted the machine with the <C> key pressed.  The result was that the cdrom booted as requested.  I then began the install.  The first step is to choose the keyboard /language.  Suddenly my keyboard is not registering.  I have lost all input from the keyboard.  What's happening!?

Has anyone else experienced this freeze?  My keyboard is perfectly (Apple) standard.  Should I try the keyboard from my iMac??  Maybe there is/are some commands to pass along to the kernel to allow it to work with the keyboard.  Ideas please?


riccardo


richard.jenkins at internode.on.net

I'm not sure if this will help but I had a lot of trouble setting up my macs due to key board problems.

e.g. install is ok but X fails and you are locked out because ctr+alt F1 fails to give you a shell, because the keyboard mapping is wrong! catch 22 Anyway I've found when I run

dpkg reconfigure-xserver-xorg

NOTE: this is in debian so I suspect its the same in ubuntu please check first.

I choose the default settings i.e. us. Even though I have a gb British keyboard also pc105 (europe) rather than macintosh. This seems to give me 95% of the keys in the right place Smile The @ and " are reversed and number pad numbers fail but its very usable. Much more so than no shell Smile I then tweek from there.

---

