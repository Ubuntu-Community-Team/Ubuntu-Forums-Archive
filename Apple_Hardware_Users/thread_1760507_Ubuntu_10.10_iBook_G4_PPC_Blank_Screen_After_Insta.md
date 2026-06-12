---
title: "Ubuntu 10.10 iBook G4 PPC Blank Screen After Installation"
date: 2011-05-17
forum: Apple Hardware Users
---

### Post by amisdar on 2011-05-17
Hi guys, need some help here.

I installed Ubuntu 10.10 alternate PPC on my iBook G4. I have to used this command upon installation or else it went to white screen which doesn't go away:

install video=ofonly

Installation went smooth till the end.

After reboot, it did prompt me to pick l or c, then yaboot screen appear. However, after I entered 'Linux' and hit Enter, nothing happened - blank screen.

I can't figure out what went wrong.... help please :-)

---

### Post by linuxopjemac on 2011-05-17
Give me a link of your iBook in everymac.com please.

---

### Post by amisdar on 2011-05-17
> **linuxopjemac said:**
> Give me a link of your iBook in everymac.com please.

Thanks! Here's mine:

[http://www.everymac.com/systems/apple/ibook/stats/ibook_g4_933_14.html](http://www.everymac.com/systems/apple/ibook/stats/ibook_g4_933_14.html)

---

### Post by linuxopjemac on 2011-05-18
at yaboot prompt type:
```
Linux 1
```
Then you are asked to give the root password. YOu have to download a specific xorg.conf file for your type of iBook:
```
wget http://mac.linux.be/files/xorg/ibook6.txt
mv ibook6.txt /etc/X11/xorg.conf
```
CTRL-D to resume booting
Good luck...

---

### Post by amisdar on 2011-05-19
Thanks! Did what you proposed but after I keyed "Linux 1" and hit Enter, the screen went blank again. There's no screen asking for root password at all.

Is there any other way to get to command line interface?

---

### Post by linuxopjemac on 2011-05-19
Try:
```
Linux 1 video=ofonly nosplash
```

---

### Post by avtolle on 2011-05-19
My experience with Ubuntu 10.10 results in the following alternate instructions:

At the second yaboot prompt, type ```
Linux single
```which will result in a menu appearing. You will want to select the option which reads "root shell with networking". Use the arrow keys to scroll to it, then hit the Tab key to highlight OK, and press the return (enter) key. You will end up at a root console where you would enter the commands in post #4, second code block. Once that is done, and the command prompt returns, instead of control-d (returns you to the maintenance menu, where if you select resume normal boot, you (I) end up at a root desktop), type ```
reboot
``` and hit the return key. If all has gone well, you will get a desktop after logging in; if not, try the video=ofonly as before.

Good luck.

---

### Post by amisdar on 2011-05-20
Thanks linuxopjemac and avtolle! I'll give it a try later today after work...

Will give an update on how it goes :-)

Thanks again!

---

### Post by amisdar on 2011-05-20
> Linux 1 video=ofonly nosplash

> Linux single

Sorry guys, both of options above lead my iBook to blank screen :confused:

---

### Post by snafu006 on 2011-05-20
On the second black screen as the computer is booting up Where it as yaboot Press TAB then type Linux install video=ofonly

---

### Post by amisdar on 2011-05-21
> **snafu006 said:**
> On the second black screen as the computer is booting up Where it as yaboot Press TAB then type Linux install video=ofonly

Thanks, it didn't work. Anyway, command above is the one that I used upon installation.

FYI, the installation went smooth, no graphic, all text based. My problem now is after the installation has been completed, I don't have access to the Ubuntu interface, not even command line.

---

### Post by snafu006 on 2011-05-21
i don't know then i would try MINTPPC or 10.04 i really do not like 10.10 i think it has problems but ill try to help you more.

---

### Post by snafu006 on 2011-05-21
Ok lets see reboot your computer and put your ubuntu cd in hold alt or option key. Click the ubuntu iso and when it brings you to the black install screen hit TAB.

First Check the cd for errors By Typing check-powerpc if all is goos then

Second Try one of the two cli-powerpc witch is a text base install maybe you need to try a reinstall or
rescue-powerpc and thats going to copy over files and try it stop the errors.

Give thos a try and lets us know how it go's good luck.

---

### Post by jigzat on 2011-05-24
Hello everyone, I was having the same issues in my Imac and I decided to try Debian and it worked as it should but I decided to give another chance to Ubuntu and I have to say that nothing works. I tried 11.04 10.10 10.04 and 10.04 server and they all seem to have the same issue. The only version that  I can install is 10.04 server but after installation I got an orange screen even though I didn't install any GUI. The other versions don't have any option to install directly just live which doesn't work either and the check option gives the same result.

---

### Post by Mineria on 2011-11-21
Seeing latest reply was made May 24th, 2011, and still nothing happened?

I have the same problem with getting a black screen when Ubuntu loads on my P57 and GeForce 4.
The installation CD works fine btw.
Tried the examples above from the second yaboot, but nothing gives me a terminal, the darn things just wants to fire up Gnome.
There is no such issue when I use the ATI R128 from my older G4.
Neither is there any issue when I install MintPPC 9.3

Also worth to mention, after the Ubuntu 10.10 splash screen (with drum sounds), I can blindly hit Enter, type in my account password and hit Enter, and then hear the disk work a bit plus the very loud startup Ubuntu sound comming out of my Mac's speaker.

Except... all of these above have issues with letting me getting no more than 800x600..
which can be fixed but still having issues with flickering, since the distros can't figure 100% correct display values for the xorg.conf..
No wonder that I still prefer MS on my main rig.

I could probably report this as a bug, but seeing that the developers just wait them out and close them when people have given up makes no point.

EDIT: Just downloaded ubuntu-10.04-desktop-powerpc.iso and fired it up, this seems to work, even boots into 1680x1050

---

### Post by rsavage on 2011-11-21
> **Mineria said:**
> Seeing latest reply was made May 24th, 2011, and still nothing happened?

....apart from maybe the releases of 11.04 and 11.10?

---

### Post by Mineria on 2011-11-21
> **rsavage said:**
> ....apart from maybe the releases of 11.04 and 11.10?
11.x got no none beta images for the PPC, 10.10 is the latest.
Updating 10.10 to 11.04 on a G4 is a no go too, tried that.
10.04 LTS seems to be the last good working copy.

---

### Post by rsavage on 2011-11-21
Please look again at the PPC downloads page.

---

### Post by harlock59 on 2012-08-13
Hello,

i am using an imac g4 flat panel 1ghz usb2 and i ran fine with lucid linx powerpc but i've tried to upgrade to maverick and now i get a black screen.

what should i do now ?

my imac is this one [http://www.everymac.com/systems/apple/imac/specs/imac_1.0_15_fp.html](http://www.everymac.com/systems/apple/imac/specs/imac_1.0_15_fp.html)

---

### Post by 2blue on 2012-08-14
You might have to go for lubuntu or xubuntu on those specs, regular Ubuntu might run a bit too slow for pratical use. It`s well worth testing the different between regular Ubuntu and one of the lighter running versions. I would also burn a new install CD of Precise Pangolin (12.04) and do it from scrach. You will have major upgrades and updates and possible difficulties upgrading from 10.04 to 12.04, it will take longer than a new install on low specs. It`s not impossible to upgrade but probably smoother to do a new intall. 

Best of Luck

---

### Post by harlock59 on 2012-08-14
i did try 12.04 before installing lucid lynx but i had a problem of display, i have a geforce 4mx

---

### Post by 2blue on 2012-08-14
I`m not familiar with your model, all I can do is guide you to the [faq ]("https://wiki.ubuntu.com/PowerPCFAQ#Shouldn.27t_it_just_work_out_the_box_nowadays.3F")pages, where you hopefully will find the answer. A black screen is not an uncommon problem, and luckily there usually is a way about it. It might be easier to make a new thread on the subject.

---

