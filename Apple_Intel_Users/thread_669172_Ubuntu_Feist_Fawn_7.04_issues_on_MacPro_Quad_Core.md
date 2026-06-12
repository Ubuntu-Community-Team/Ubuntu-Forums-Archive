---
title: "Ubuntu Feist Fawn 7.04 issues on MacPro Quad Core"
date: 2008-01-16
forum: Apple Intel Users
---

### Post by grammataki on 2008-01-16
Hello Everyone,

This post has probably been two weeks in the making.  I have come to the brink of insanity and I think my hair is starting to fall out.  [http://ubuntuforums.org/images/smilies/star.png](http://ubuntuforums.org/images/smilies/star.png) Jokes aside, I apologise if there is a simple fix to my problem but hopefully someone can point me in that direction.  There is a free bag of popcorn to someone who can help me
[http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif) So, here goes...

First of all, here are my specs:
Apple MacPro Quad Core (November 2007)
ATI X1900XT graphics card
5GB RAM
Bluetooth
Hard Drive 1:  500GB running OSX Leopard (sdd), plus emi partition
Hard Drive 2: sdc1 (some EMI partition????) 200MB
                      sdc2 swap space 5GB
                      sdc3 Ubuntu partition (usually formatted as ext3 with mount point '/' 289Gb
                      sdc4 OSX Leopard 14GB
Hard Drive 3:  sdb OSX Tiger, plus emi partition
Hard Drive 4:  sda Back Up drive

Ok, so I spent maybe 48 hours trying to install Ubuntu Gutsy Gibbon on this system but to no avail.  Eventually I concluded that as I couldn't access the interent from the LiveCd when installing, it would be useless to continue, so I gave up.

Then I decided to try Feisty Fawn 7.04 (as I have successfully installed on a powerbook in the past.  Yes, I could access the internet , so I thought it would be ok.  Unfortunately, I encountered the same problems as with Gutsy Gibbon.  What problems?  Heres a list of most:

- grub install failing
- when grub is ok, sometime I get to retsrat but after the black screen, I get a flashing cursor forever
- at some point it stated to the grub boot, showing two kerenl options and something about a memory test but when choosing the first one, I would get Error 17 cannot mount partition (I have tried many suggested fixes on forums)
- after following some forums, it would load but only say Grub at the top of the screen in capital leters and go nowhere
- after continually trying to reinstall, rEFIt now has five linux icons (but none lead to succesful load of Gutsy Gibbon.

Not sure what other information I can provide that can help pinpoint my issue.  Im not really proficient at this but have followed all instructions to a tea.  Appreciate peoples patience here.  I have read many other people have successfully installed and hope I can also do so one day.  Please help [http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)


Grammatis


Sorry I haven't responded recently.  I managed to get Ubuntu 7.04 running fairly well last week apart from the noisy GPU fan.  There were some instructions on the net about installing cpu temp reader for the xeon processors but couldnt get that working for fan control.  Anyway, This morning I tried to get Ubuntu 7.10 installed.  Lots of issues as installation seemed slightly different for me with setting drive localities and such.  Eventually I managed to make it bootable!  Yeah!!  Thanks for everyones help and support.  Ofcourse nothing is perfect.  Things I need to iron out include:  

- internet still not working (even on LiveCD) (is this because I havent got the MacPro kernel installed yet?  I couldnt do this as it cant find some files and internet is down anyway)

- graphics driver (need internet for this but have downloaded it in leopard and will try installing with envy program

thanks again

---

### Post by cyberdork33 on 2008-01-16
> **grammataki said:**
> 
First of all, here are my specs:
Apple MacPro Quad Core (November 2007)
ATI X1900XT graphics card
5GB RAM
Bluetooth
Hard Drive 1:  500GB running OSX Leopard (sdd), plus emi partition
Hard Drive 2: sdc1 (some EMI partition????) 200MB
                      sdc2 swap space 5GB
                      sdc3 Ubuntu partition (usually formatted as ext3 with mount point '/' 289Gb
                      sdc4 OSX Leopard 14GB
Hard Drive 3:  sdb OSX Tiger, plus emi partition
Hard Drive 4:  sda Back Up drive

- at some point it stated to the grub boot, showing two kerenl options and something about a memory test but when choosing the first one, I would get Error 17 cannot mount partition (I have tried many suggested fixes on forums)

This is a common error to people installing on the Mac Pro since you are installing to a drive other than the primary. The "problem" you posted which I quoted above is when you were closest to having it working. You have to edit the /boot/grub/medu.lst file for your Ubuntu partition and have it reference hard drive 1 instead of hard drive 3. This seems to be some oddity defect of the Apple BIOS emulation method. There are several posts by Mac Pro users here that have installed Ubuntu as I have stated.

Here is one where the steps to install grub manually are shown, plus the discovery that you have to change the partition reference in the menu.lst file.
[http://ubuntuforums.org/showthread.php?t=553587](http://ubuntuforums.org/showthread.php?t=553587)

---

### Post by grammataki on 2008-01-17
Thank you for the reply.  Great news, I have 7.04 working on my MacPro.  

Just in case it helps anyone else, I now realise there were two levels of confusion I was going through.  The first was that in the partitioner (from Live CD), it was reversing the order of my drives, but I understood that within a few minutes.  For the past few days, what I didnt understand was that it would be regardingmy 3rd drive as (hd0).  WHich upon following the instruction on the post above got the whole thing working!  Few!

It runs quite ok, but applied the ATI driver and ever since the fan is running very loud and wont stop.  I am also applying updates at the moment so I cant stop and restart the computer just yet.  I have read this is normal but am concerned about overheating my internal components with time.  If I use the original driver, will the fan stop working crazy.


A few issues still remain though all is working ok.  My issues are:

- when I reboot and press option, there are two windows options avalable (I guess its Linux here) and when I press one it just goes to a black page with the words GRUB on the top and hangs.  If tI press the other one, it loads grub ok BUT

- It says error 23, so I go into the editor and change the boot to (hd0) from (hd2,3) and press b for boot and all is well

-can I remove the extra linux icon from the osx option menu?
-can  I do something to bypass error 23 and permanently set the grub to (hd0)?

-I havent tried refit yet but imagine the 6 extra icons for linux (after reinstalling 55 times) are still there.  Can I remove them somehow?  I cant seem to find a guide for this but will keep looking

-also, when I boot into my 1st drive (hd3), it says it cant recognise the disk with linux on it, is this normal?  Can I configure it to?

- is there a guide for compiling a kerbnel on Mac Pro for 7.04?

Finally, if I can get this working, I would be still interested in upgrading to 7.10.  I couldnt access the internet when I tried before so am concerne I would be wasting my time.  I couldnt access the net from the CD at all and am concerned it will be the same when I have 7.10 running.  Any suggestions here?  

I will report back with the fan status after rebooting from the updates

Thanks again.


Grammatis

---

### Post by cyberdork33 on 2008-01-17
> **grammataki said:**
> It runs quite ok, but applied the ATI driver and ever since the fan is running very loud and wont stop.  I am also applying updates at the moment so I cant stop and restart the computer just yet.  I have read this is normal but am concerned about overheating my internal components with time.  If I use the original driver, will the fan stop working crazy. I think this is more of a problem with the power control system rather than your computer getting really hot... There are some posts regarding changing the fan speed manually.

> **grammataki said:**
>  - when I reboot and press option, there are two windows options avalable (I guess its Linux here) and when I press one it just goes to a black page with the words GRUB on the top and hangs.  If tI press the other one, it loads grub ok BUT
First, do yourself a favor and install rEFIt (in OSX), it will give you a better OS chooser.

> **grammataki said:**
>  - It says error 23, so I go into the editor and change the boot to (hd0) from (hd2,3) and press b for boot and all is well

-can I remove the extra linux icon from the osx option menu?
No. Unfortunately. Try rEFIt and see if it is really an issue to start with. You likely got grub stage 1 installed to 2 locations so it shows both bootloaders.

> **grammataki said:**
>  -can  I do something to bypass error 23 and permanently set the grub to (hd0)?
yep, edit the entries in /boot/grub/menu.lst (and change the automagic config options so that updates don't break it later).

> **grammataki said:**
> -I havent tried refit yet but imagine the 6 extra icons for linux (after reinstalling 55 times) are still there.  Can I remove them somehow?  I cant seem to find a guide for this but will keep looking Unfortunately, rEFIt cannot be configured like that. It just searches for bootable items, and give you the option to choose them. Try installing and see what you get, and I can try to help you fix things from there.

> **grammataki said:**
>  -also, when I boot into my 1st drive (hd3), it says it cant recognise the disk with linux on it, is this normal?  Can I configure it to? Don't understand what you are doing here. what is on hd3? this mught just be that extra copy of grub stage 1 i was talking about.

> **grammataki said:**
>  - is there a guide for compiling a kerbnel on Mac Pro for 7.04?there is a tutorial for compiling a kernel in the FAQ. It is relatively the same for any computer. Just be sure to get the latest mactel patches, and hope to find a config file to get you started.

> Finally, if I can get this working, I would be still interested in upgrading to 7.10.  I couldnt access the internet when I tried before so am concerne I would be wasting my time.  I couldnt access the net from the CD at all and am concerned it will be the same when I have 7.10 running.  Any suggestions here?
If you intend to use 7.10 then it is best to start from a clean install. I know you were having issues, but you will have to do some more debugging to figure out the issue. If the network works in 7.04, then I can almost guarantee that it will work in 7.10.

---

### Post by bunted on 2008-01-18
I am running 7.10 on a Mac Pro with almost exactly your specs as well.  I really have no real problems, even got my wacom tablet working.  My only concern is the entire CPU load not equal to fan speed issue I've read about.

My other post about this issue:

[http://ubuntuforums.org/showthread.php?t=670977](http://ubuntuforums.org/showthread.php?t=670977)

---

### Post by grammataki on 2008-01-21
> **bunted said:**
> I am running 7.10 on a Mac Pro with almost exactly your specs as well.  I really have no real problems, even got my wacom tablet working.  My only concern is the entire CPU load not equal to fan speed issue I've read about.

My other post about this issue:

[http://ubuntuforums.org/showthread.php?t=670977](http://ubuntuforums.org/showthread.php?t=670977)
Hi there,

Thanks for your post, I really need some help in getting the ineternet up and running.  I have tried a hundred times but if you could point me out to the exact instructions you used after installing it would be a great help. 

Have you installed the cpu sensor for the xeon processors?  I wasnt able to do this in Feisty Fawn (then again Im not the best at linux programming even though I follow things to a tea.

Thanks again.


Grammatis

---

### Post by grammataki on 2008-01-21
> **bunted said:**
> I am running 7.10 on a Mac Pro with almost exactly your specs as well.  I really have no real problems, even got my wacom tablet working.  My only concern is the entire CPU load not equal to fan speed issue I've read about.

My other post about this issue:

[http://ubuntuforums.org/showthread.php?t=670977](http://ubuntuforums.org/showthread.php?t=670977)


Thanks for your post.  Im having some trouble with applying the 2.6.23 kernel.  I get the following message when following the terminal instructions from the forum page you linked:

root@Ubuntu:~# apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev libncurses5 libncurses5-dev subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

Also, firefox can access the net no problems now (after blocking ivp6) but the update manager cannot access the net.  Strange and I cant get my newbie head around it.  Any help would be appreciated.

Based on other posts, I wont be putting my CPUS under load.  Not until the issue is addressed.  Hopefully in the next release.

Grammatis

---

### Post by bunted on 2008-01-23
@grammataki

First off, do you have all of your repositories enabled in Synaptic?  Look in the menus.

Secondly, I really had no problems with my internet upon install.  I don't use wireless though, do you?  Or maybe it has something to do with the two network cards in the mac pro.  Have you tried both?

Third, I tried to compile my own kernel to no avail.  (You need a custom kenel with the mactel patches to be able to use the sensors.)  It's fairly difficult and one mistake out of 3000 options means you can't boot.  I'll try to tackle it again when I have the time.

---

### Post by grammataki on 2008-01-23
> **bunted said:**
> @grammataki

First off, do you have all of your repositories enabled in Synaptic?  Look in the menus.

Secondly, I really had no problems with my internet upon install.  I don't use wireless though, do you?  Or maybe it has something to do with the two network cards in the mac pro.  Have you tried both?

Third, I tried to compile my own kernel to no avail.  (You need a custom kenel with the mactel patches to be able to use the sensors.)  It's fairly difficult and one mistake out of 3000 options means you can't boot.  I'll try to tackle it again when I have the time.


Thanks Bunted.  I will look into the repositories thing in a minute.  From what I remember, it starts checking but never finishes.  Upon install, I had to block ivp6 to get internet working so dont know whats going on, but at least I can fire up firefox.  I will try with the other network port to see if it affects internet.  Im relieved to hear the kernel configuration is cumbersome (it sounds so simple on the instruction forums).  If you have luck with it, please let me know.  Thanks again everyone, Im going to keep working on getting it up and running properly.

---

