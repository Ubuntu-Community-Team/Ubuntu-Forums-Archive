---
title: "Anyone using Gutsy on Mac/Intel?"
date: 2007-06-13
forum: Apple Intel Users
---

### Post by thully on 2007-06-13
I've been trying Gutsy - the development/alpha build of the next Ubuntu - on my MacBook and have found that many issues are resolved since Feisty - namely, suspend and trackpad performance (the latter needs an Xorg.conf fix, but works better in Gutsy nevertheless).  The computer suspends and resumes as fast as OS X, and the trackpad, with Xorg.conf tweaks, works VERY well, including two-finger tapping and edge scrolling (which are erratic in Feisty).  Is anyone else braving the waters of Gutsy on their Macs?

---

### Post by thully on 2007-06-13
I'm talking about using it w/dual-boot, btw.  Everything in both versions runs fine in VMware...

---

### Post by SectionThree on 2007-06-13
I never thought about braving it until I read your post. Are there any issues I should be aware of before I jump in?

(I have a new MacBook, and it was an ordeal getting the AirPort card to work in Feisty)

---

### Post by thully on 2007-06-13
Well, you must be warned that it *is* alpha software - so have a backup OS in case it breaks.
Also, I've had issues with fonts - you may have to make some tweaks there...

---

### Post by SectionThree on 2007-06-13
Well, like you, I've got the dual-boot thing going, and I think I can handle font-tweaking issues, so I'm gonna do it!:twisted:

---

### Post by thonuz on 2007-06-14
I just did a Gutsy install and have noticed a couple of things:
1. right side of touchpad will scroll
2. wireless percentage increase (though the madwifi install took a while as there were errors with gcc and kernel source, headers and such. Not sure what the culprit was, but I expect it to break again)
3. The battery life indicator does not seem to be working correctly. Currently it says 75% and 35 minutes remaining. 
I was primarily interested in the following from [http://www.ubuntu.com/testing/tribe1](http://www.ubuntu.com/testing/tribe1)

"For massive power, heat and headache reduction the kernel now features dynticks, which in laptops should mean more battery life and burnfree laps, and in desktops, media center pcs etc. a quieter, cooler environment.
For laptops especially, a new wireless stack is used that will allow for a much better wifi performance and driver management."

I can't make any comparisons yet. I suppose I should install feisty on another partition to test.
It seems about has hot as mac though.

---

### Post by SectionThree on 2007-06-14
Well, I haven't done it yet. Is there a way to upgrade from Feisty using apt-get this early in the game, or am I going to just have to suck it up and install Gutsy from the CD?

---

### Post by thonuz on 2007-06-15
Use the cd is what I did. Daily build. (6-12 I think was mine. warning and all that)
you need to always have a /home partition in case.
Anyway gutsy did not format my user files. Just back up first in case. I use an ipod to backup all my stuff.
I can confirm battery life improvement. It is either the kernel or the brightness settings and or wireless. The gnome battery power applet was updated and the time down removed for the time being.
I'm not sure about the fan settings people are complaining about. So far there is no fan sound and it does not feel hotter than mac, so I may not tweak it for 1800 rpm or something. 
Incidentally, tests show processors last longer with more heat near the threshhold level.Unless you leave the computer in standby all the time.
warning: about keeping files on a test system. Also make sure you keep Email copies on server.

---

### Post by thonuz on 2007-06-16
Macbook Intel core 2D basic white model report: 
I can confirm less heat and better fan speed than I had before.
CPU 0: 55 °C
CPU 1: 56 °C
(my Sony Vaio used to run in excess of 90c and I hit 100c a few times. I know that does not seem possible as that's melting temp, good hardware I guess cause it still works great though bits of paneling have broken off)

Fan is running at a perfect speed from what I can notice. 
I'm running unplugged with screen bright. way down. WIreless was a pain to install, but madwifi works.Make sure you have build essentials and madwifi tools installed. I had a problem loading the ath_pci module. I also check headers against the kernel uname -r and also installed source. gcc version errors and such. 

Can't tell if battery life is better. Right now it says 45 min and 56%, but i don't think that's right, So after 5 minutes it says 
:~/mactel-linux/trunk/tools/temperature$ sudo ./coretemp 
CPU 0: 57 °C
CPU 1: 58 °C
battery life monitor is working better. At least its not going backwards

---

### Post by benanzo on 2007-06-16
To get a good idea of what is draining the battery have a look at [PowerTOP]("http://www.linuxpowertop.org/") from Intel.  It's great.  You've got to have a 2.6.21+ kernel.  I am pretty sure it will run on the Gutsy kernel, but it might suggest some tweaks.  I have gone through everything it suggests and now get ~2.5 hours - not terrible compared to Feisty's 1.5-2 hours on my first gen MacBook.

---

### Post by SectionThree on 2007-06-17
Allright, I'm going in!

I'll get back to y'all on my progress sometime this coming week;)

---

### Post by zAo on 2007-06-18
Nope: Still no Wifi drivers for my C2D iMac, still crappy ATI drivers.

---

### Post by mabovo on 2007-06-18
> **thonuz said:**
> Macbook Intel core 2D basic white model report: 
I can confirm less heat and better fan speed than I had before.
CPU 0: 55 °C
CPU 1: 56 °C
(my Sony Vaio used to run in excess of 90c and I hit 100c a few times. I know that does not seem possible as that's melting temp, good hardware I guess cause it still works great though bits of paneling have broken off)

Fan is running at a perfect speed from what I can notice. 
I'm running unplugged with screen bright. way down. WIreless was a pain to install, but madwifi works.Make sure you have build essentials and madwifi tools installed. I had a problem loading the ath_pci module. I also check headers against the kernel uname -r and also installed source. gcc version errors and such. 

Can't tell if battery life is better. Right now it says 45 min and 56%, but i don't think that's right, So after 5 minutes it says 
:~/mactel-linux/trunk/tools/temperature$ sudo ./coretemp 
CPU 0: 57 °C
CPU 1: 58 °C
battery life monitor is working better. At least its not going backwards


Could You please post a guide "How to install Gutsy on MAC/Intel" ? 
I've just bought a lap like yours and I do prefer Ubuntu.
Thanks.

---

### Post by thonuz on 2007-06-19
I don't think a guide is really possible as its under development.
Basically just follow the steps for Feisty. [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
1. partition and install refit. I have osx/ubuntu about 50/50
2. then just install gutsy from cd (64 bit version).
3. upgrade your packages and go for the madwifi install. Works great, Just make sure you have build-essential installed, correct gcc, etc. Things are constantly being updated and will break. In fact the netwrok manager is broke as I write this but netapplet works and I have strong wireless but no wired for some reason. 
4. backup your stuff to stick or ipod is what I do

Extra things that you will need to fix:
backlight control: 
go to  /usr/share/hal/fdi/policy/10osvendor$ 
and edit 10-macbook-backlight.fdi
so that the product matched c2d by changing the value to "2.1" as below:
 <match key="smbios.system.product" string="MacBook2,1">

For battery monitoring install powertop: it is in synaptic. It will tell you where the drain is.

For temp I installed coretemp
 svn co [https://svn.sourceforge.net/svnroot/mactel-linux](https://svn.sourceforge.net/svnroot/mactel-linux) mactel-linux
then
cd mactel-linux/trunk/tools/temperature/
and
sudo modprobe msr
finally
sudo ./coretemp 


Some other things that have improved so far: fonts look really good better than feisty. Also my HP lazerjet 1018 works using the drivers here [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) borders are not chopped off anymore.

Mac comment follows;
Mac is only useful in case my internet connection breaks. I don't care about isite or itunes as I don't use either.
Editing a simple site is a joke in osx. Iweb does not work and I gave up on dreamweaver. All I needed was to change a font color on a title of an index page. In Ubuntu I used quanta and Kompozer which has a 64 version along with other good stuff here [http://www.getdeb.net/](http://www.getdeb.net/)
I don't know if its the intel processor but mac osx seems unstable. safari will lock up the entire computer at times and the fan will blow so loud I have to leave the library. Also I have not much luck watching some of my purchased dvds. Its also faster to navigate in ubuntu and do things. but that may be because I don't know how to use mac so well. I end up using 2 hands in mac where in ubuntu I use one. Also right click works great in gutsy with 3 finger tap. As far as the apple logo you can just color some penguin or something on paper and tape it over the apple logo. It will shine some light through and you will not feel like such a jerk.

---

### Post by kzm. on 2007-06-20
i have some question about coretemp installation, may be you can help me out. 
because when i checked out the svn and did
sudo ./coretemp 

it said: coretemp: command not found

btw does it work onder feisty?

---

### Post by kzm. on 2007-06-20
never mind.. found the missing step: make
[http://ubuntuforums.org/showthread.php?t=469277](http://ubuntuforums.org/showthread.php?t=469277)

---

