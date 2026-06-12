---
title: "Double-boot: OS X and Ubuntu on macbook pro 5,3 using liveCD"
date: 2013-03-31
forum: Apple Hardware Users
---

### Post by Aquawood on 2013-03-31
[FONT=Helvetica]Double-boot: OS X and Ubuntu on macbook pro 5,3 using liveCD[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]Hi guys, I just installed ubuntu 12.10 64-bit on my mac operating OS X 10.8.3. Basically,  I follow the official guide on this link below:[/FONT]
[FONT=Helvetica]
[/FONT]
[COLOR=#021EAA][FONT=Helvetica]_[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)_[/FONT][/COLOR]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]But there are some tricks we have to beware of, or you will probably end up with black screens or splash. It seems like Apple does not like users to install ubuntu on their products, thus makes it really tricky to complete the whole process. Not to mention that the difficulty varies among products with different hardware. This tutorial works for my macbook pro 5,3(mid 2009).[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]Here is how I get it done:[/FONT]
[FONT=Helvetica]
[/FONT]

[LIST=1]
[*]Check if  your optical-disk drive is functional. Since we are going to install via liveCD, the first thing we are going to do is to check. If not, try to clean it.
[*]Use quality DVDs. My mac is manufactured in 2009, so the super drive does not working as stable as I would like it to be, if you are using macs that are not so new, please use quality DVDs and if one disk fails, shut down the computer and do it again (reboot seems does not reset the super drive). Not sure this is useful for new macs.
[*][COLOR=#000000]Download ubuntu 64-bit [http://www.ubuntu.com/download/desktop/questions?distro=desktop&bits=64&release=latest](http://www.ubuntu.com/download/desktop/questions?distro=desktop&bits=64&release=latest) . I have seen people suggest using 64-bit mac [[FONT=Helvetica Neue Light]ubuntu-12.10-desktop-amd64[/FONT][FONT=Helvetica Neue]**+mac.iso**[/FONT]]("http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-amd64+mac.iso") but that did not work for me.[/COLOR]
[*]Burn iso file to the DVD. (follow the official guide). After the burning, if you re-insert the DVD, system will not read it, and prompts &#8221;The disk you inserted was not readable by this computer&#8221;. It doesn&#8217;t matter, just proceed to next step.
[*]Partition your hard disk. Add a new partition in Disk Utility and format it to msdos(will be addressed later).
[*]Install rEFIt.(follow the official guide)
[*]Reboot and get into the rEFIt, select boot from liveCD. **Here comes the trick: press esc right after the blink cursor appear on the top-left on the screen.** Or my mac will fall into an eternal black screen. Not sure it happens to all the macs, seems like only a few people mentions it in their tutorial.
[*]Hit enter after your esc gets response, there will be some lines jump out onto the screen which I can not remember.
[*]A purple screen with a man and a keyboard on the bottom will show up. **Here&#8217;s another trick: press F6 to enter install menu.** In the menu, press F6 and select &#8220;nomodeset&#8221;.
[*]**Move to install ubuntu, add &#8220;b43.blacklist=yes&#8221; to the boot options.** Before adding this, all my attempts end up with error:
[/LIST]
[COLOR=#323333][FONT=Monaco]b43-phy0 ERROR: Firmware file "b43/ucode16.fw" not found
b43-phy0 ERROR: Firmware file "b43-open/ucode16.fw" not found
b43-phy0 ERROR: You must go to [[COLOR=#021EAA]http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware[/COLOR]]("http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware") and download the correct firmware for this driver version. Please carefully read all the instruction on this website.[/FONT][/COLOR]
[FONT=Helvetica]and eventually splashes screen. [/FONT]
[FONT=Helvetica]
[/FONT]11.Start install. Continue to a window that asking if you want to install alongside with OS X or erase the OS X or manually partition. Select the last one and it will bring you into the gparted to     manually modify your partition table.[FONT=Helvetica]
[/FONT][FONT=Helvetica]    a.Delete the &#8220;msdos&#8221; format partition(should appear as the last one on the table).         And it becomes free space without format.    [/FONT]
[FONT=Helvetica]    b.Select the free space, create a new partition about 1G with format &#8220;swap area&#8221;. [/FONT]
[FONT=Helvetica]    c.Select the remaining free space, create a new partition with format EXT4.        Choose &#8220;/&#8221; as root point[/FONT]
[FONT=Helvetica]    d.On the bottom, select the boot loader(grub) to the partition you with format         EXT4.

12.[/FONT]Continue and reboot. In the eEFIt, we can see the tux, select it, we enter the grub menu. **Trick: press "e" while selecting ubuntu, add boot option: b43.blacklist=yes** and **nomodeset**. I initially try to directly boot ubuntu but it ends up with black screens and splashes. Not sure this happens to other macs, nobody mentions this in their tutorial. After the recovery mode, it should be OK to boot the ubuntu smoothly.
[FONT=Helvetica]
Additional info for wireless set-up:
After getting into ubuntu desktop, connect to Internet use wire. Open terminal and try the following code:
1. sudo apt-get update
2. sudo apt-get install b43-fwcutter
[/FONT][FONT=Helvetica]
[/FONT]
[FONT=Helvetica]Here are some other links I referring to, hopefully they will be helpful for you:[/FONT]
[COLOR=#021EAA][FONT=Helvetica]_[http://clusterbleep.net/blog/2012/05/09/ubuntu-12-04-splash-screen-lockup-with-livecd/](http://clusterbleep.net/blog/2012/05/09/ubuntu-12-04-splash-screen-lockup-with-livecd/)_[/FONT][/COLOR]
[COLOR=#021EAA][FONT=Helvetica]_[http://www.warp1337.com/content/install-ubuntu-1210-quantal-quetzal-macbook-pro-101-retina-solved](http://www.warp1337.com/content/install-ubuntu-1210-quantal-quetzal-macbook-pro-101-retina-solved)_[/FONT][/COLOR]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]Cheers[/FONT]

---

