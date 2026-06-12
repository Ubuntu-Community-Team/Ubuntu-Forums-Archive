---
title: "Scanner- CanoScan LIDE 25"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by t2000kw on 2007-04-19
I don't see a place for a scanner under administration. There are drivers available for this scanner, as SUSE supported it and even detected it during installation. 

Any ideas as to where to go for installation information?

Thanks in advance!!!

Donald

---

### Post by kyphi on 2007-04-19
A good place to look is under Applications, Graphics, XSane Image Scanner.  The CanoScan Lide 25 should work out of the box.

---

### Post by t2000kw on 2007-04-19
Well, good news and bad news.

Good news: It shows the LIDE 25 scanner in the title bars of the windows

Bad news: It acts like it's scanning but scans totally black images. I have a white piece of paper in the scanner now with some text on it and all I'm seeing is a black scan.

---

### Post by t2000kw on 2007-04-19
More on this problem . . .

I installed Kooka, and it does the same thing, so it's a system device setup problem. It worked last night in SUSE, and nothing unusualy has happened to it, but I can check it in Windows tomorrow to make sure it didn't suddenly break tonight.

---

### Post by Michal77 on 2007-04-20
I've the same scanner. Works perfectly 'out off box' with Edgy, but after update to Feisty stopped. System detects it but when i try scan nothing happen.
:confused: 
M.

---

### Post by t2000kw on 2007-04-20
How can we file a bug report on this? I'm new to Ubuntu.

---

### Post by Argos_Bling on 2007-04-21
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488](https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				You can use the Launchpad bug reporting tool - just create an account and add to the existing bug report.

Quoting the developers, after this bug was introduced late in Feisty:
"Unfortunately this option needs to remain enabled so that a good chunk of other users can have suspend/resume, which ultimately is more important than a working scanner.

Hopefully someone sooner or later will fix this properly."

---

### Post by t2000kw on 2007-04-21
I found the web site, but there appears to be no way to sign in or report a bug. I'm overlooking something. I did look for a reporting tool and either it's missing or I can't find it in the multitude f menus. Is it something that needs to be added to Ubuntu?

---

### Post by Argos_Bling on 2007-04-21
You need to register to create a Launchpad account:

[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488/+login](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488/+login)

The "Not registered yet?" section will lead you through the steps to create an account, and once you are registered and logged-in, you can return to the bug and add your comments to the rapidly-growing list.

---

### Post by imon9 on 2007-04-21
hello...just to inform both of you..this bug is already quite well-known at this moment. Scanner probelm is due to the kernel in Feitsy which inactivate the USB port when scanner not being used ... this back-fired since xsane had difficultties waking the port up...

anyway, it say there is 2 way to do it: (one which i personnaly already tried - which is command line)

(1) command line: 
open up synaptic or use apt and install "sane" and "sane-utils"
then open up the terminal and scan using the command "scanimage"

option usually needed =
eg: scanimage -x 210 -y 290 --resolution 400 --mode Color > output.pmn
     (x=witdh in mm , y = height... output as .pmn image file)

(2) some script that keep the ports awake called "prods" (i am searching about it now)

hope the next update of kernel will get things fixed (but seems like someone told me it wont be that soon)

---

### Post by t2000kw on 2007-04-21
Is this true with all distributions of Linux after a certain date, or just Ubuntu?

Is there a way to recompile the kernel (don't know how but did it before folling directions) to fix the problem?

---

### Post by t2000kw on 2007-04-21
I tried the work-around and it did scan somehting but didn't output it into any program.

Am I supposed to have a particular program open when invoking the comand?:

scanimage -x 210 -y 290 --resolution 400 --mode Color > output.pmn

---

### Post by t2000kw on 2007-04-21
I forgot to mention--I did install the two packages using Synaptics.

---

### Post by imon9 on 2007-04-22
the output.pmn will be located in your /home/<user>/ folder usually 
you will have to use the terminal to run the "scan image program"

btw, if you want to put it in a specific folder, use such command:
scanimage -x 210 -y 290 --resolution 400 --mode Color > /home/scan/output.pmn
so the output.pmn will be in /home/scan/

btw, about wether this problem appear all along or recently..well, according to those who check it out...it happen after kernel-2.6.20-12 installation/upgrade (feisty is using 2.6.20-14 or 15)

in ubuntu edgy (up to kernel 2.6.20-9...everything seems to be fine)

there is sucessful case where ppl recompile their new kernel by disabling the "usb suspend" option...so it might work for you.

though, i am yet to find out how to do that.

---

### Post by autocrosser on 2007-04-22
I just posted the workaround to the Launchpad bug report: Install a program called Gscan2pdf. To install:

Edit your apt sources.list <code> sudo gedit /etc/apt/sources.list

and add these lines:
#Gscan2pdf
deb [http://gscan2pdf.sourceforge.net/download/debian](http://gscan2pdf.sourceforge.net/download/debian) binary/

save & close.....then start Synaptic & update.
Search for gscan2pdf, then highlight it/right click & add all depends EXCEPT sane. return & download.

This software will scan & save as a PDF or tiff file. I'm going to keep it because of the PDF save.

---

### Post by fsando on 2007-04-23
> **autocrosser said:**
> I just posted the workaround to the Launchpad bug report: Install a program called Gscan2pdf. To install:

Edit your apt sources.list <code> sudo gedit /etc/apt/sources.list

and add these lines:
#Gscan2pdf
deb [http://gscan2pdf.sourceforge.net/download/debian](http://gscan2pdf.sourceforge.net/download/debian) binary/

save & close.....then start Synaptic & update.
Search for gscan2pdf, then highlight it/right click & add all depends EXCEPT sane. return & download.

This software will scan & save as a PDF or tiff file. I'm going to keep it because of the PDF save.

I tried it (my scanner is agfa snapscan 1212u).
Started gscan2pdf from command line its default scanner is 'generic' of some kind. I selected my agfa snapscan from the dropdown menu and got the following (after some long waiting times):
```
~$ gscan2pdf
[snapscan] Scanner warming up - waiting 7 seconds.
scanimage: open of device snapscan:libusb:001:004 failed: Error during device I/O
Unknown message: scanimage: open of device snapscan:libusb:001:004 failed: Invalid argument

```
Ther is an option to chose frontend (scanimage or scanadf) but only scanimage is available - scanadf is greyed out

---

### Post by autocrosser on 2007-04-23
Looks like libusb is the guilty party again......I got some mail from sane-development-list last night, they are pointing fingers at the USB_SUSPEND & recomending that Ubuntu's dev team should do some re-compiling....I'll be posting the info to the posted bugs tonight.
 
I'll try to keep everyone up to speed as to how that develops. :(

---

### Post by autocrosser on 2007-04-23
Information from Sane-development-list:

Message: 8
Date: Mon, 23 Apr 2007 09:20:19 +0200
From: Gerhard Jaeger [EMAIL="gerhard@gjaeger.de"]<gerhard@gjaeger.de>[/EMAIL]
Subject: Re: [sane-devel] scanner
To: [EMAIL="sane-devel@lists.alioth.debian.org"]sane-devel@lists.alioth.debian.org[/EMAIL]
Message-ID: [EMAIL="200704230920.20028.gerhard@gjaeger.de"]<200704230920.20028.gerhard@gjaeger.de>[/EMAIL]
Content-Type: text/plain;  charset="ansi_x3.4-1968"

On Sonntag, 22. April 2007, JKD wrote:
[INDENT]> El Sun, 22 de Apr de 2007, a las 11:13:15AM +0200, guido dom dijo:
[INDENT]> > There must definitively be something fundamenally wrong with Feisty if such
> > a number of users are experimenting problems with their scanner (Iam too
> > with a canon N670U that is recognised but does not start).
> > 
> > Both SANE and UBUNTU should, in my humble opinion, already have reacted with
> > a patch or a solution (or an advice to buy another scanner!!!).
> >  [/INDENT]> 
> May be it's not a SANE specific problem but kernel's experimental
> changes and updated libraries that conflict with binary verions provided
> by Ubuntu, and other distros. At least, testing with a backend (not
> related to your scanner), the one provided by distro didn't work and
> the same one compiled from SANE sources in Feisty worked like a charm.
> 
> So one solution could be to compile SANE against current library versions
> in each distro and after testing its funtionability, notify maintainers
> to update their packages.
>  [/INDENT]It is in fact a problem that has been introduced by the kernel-option
CONFIG_USB_SUSPEND (which is marked as experimental). Disable that,
recompile the kernel and the stuff should work. I also got some
success reports, where libusb has been recompiled.

- Gerhard

---

### Post by t2000kw on 2007-04-23
I'm also going to post this separately but thought this might be a good place to also post it.

I want to recompile my kernel. How do I make a floppy (or CDROM) boot disk from where I can attempt to configure a new kernel?

Also, is there a set of directions for doing this? I have directions for Suse, Fedora, and Mandriva, but these may have different commands and file locations than Ubuntu.

I did this before, a long time ago, under Suse, I think. But rather than switch and start all over again just because I have a book that covers these three and not Ubuntu, I would like to get this distro going.

I'd also like to know how to recompile a portion of Linux, specifically the libusb section. Apparently you can do just part of it???

---

### Post by autocrosser on 2007-04-23
You can search the forum about building a new kernel--there is a Wiki page devoted to the topic. As for recompiling libusb, I am looking into that one. I'll report as to the sucess or failure but I do not have high hopes for it. Gerhard, who is a developer with Sane indicates it is a hit-or-miss. I don't want to do a custom kernel, so you know the way I'm heading.....

---

### Post by autocrosser on 2007-04-24
OK- I recompiled libusb last night--no luck. The scanner worked once & then was silent the rest of the evening. 
 
I posted to the bug report the idea to create two kernels. One for desktop users that do not need USB_SUSPEND & one for laptops that do. I realize that this will still affect some laptops that want to use a scanner, but I feel that the number in that group would be very small compaired to the present problem.

---

### Post by episodic on 2007-04-28
Anyword on this? I just recently converted to ubuntu on the promise that my scanner (an lide 20) would work fine. It did work fine under the bootable version 6 disk - so I assumed (foolishly) that the next version feisty would have support for the same hardware. It should'nt go backwards.

---

### Post by ra-ma on 2007-04-28
> **Michal77 said:**
> I've the same scanner. Works perfectly 'out off box' with Edgy, but after update to Feisty stopped. System detects it but when i try scan nothing happen.
:confused: 
M.
It's exactly the same for me with a Canon N650u. Before upgrading from Edgy it worked surprisingly fine (Edgy has been my first attempt with Linux again since 2 years) but with Feisty the scanner is somehow regognized but there's no activity when I try scanning.

---

### Post by autocrosser on 2007-04-29
WOOOOOT!!!!! Check it out everyone!!!!

[http://bugzilla.kernel.org/show_bug.cgi?id=8231](http://bugzilla.kernel.org/show_bug.cgi?id=8231)

Now all we need is the kernel team to backport it----

---

### Post by imon9 on 2007-05-04
GOOD NEWS!!! someone compiled a fix of the kernel in .deb format (actually is by fishor in the bugzilla tread.

I already tried it and it fix my problme already!!

please refer to the following post to download the kernel-fix deb files. (YAY! no more recompiling kernel myself!)

here is the link
[http://ubuntuforums.org/showthread.php?t=432130](http://ubuntuforums.org/showthread.php?t=432130)

---

### Post by fsando on 2007-05-04
> **imon9 said:**
> GOOD NEWS!!! someone compiled a fix of the kernel in .deb format (actually is by fishor in the bugzilla tread.

I already tried it and it fix my problme already!!

please refer to the following post to download the kernel-fix deb files. (YAY! no more recompiling kernel myself!)

here is the link
[http://ubuntuforums.org/showthread.php?t=432130](http://ubuntuforums.org/showthread.php?t=432130)

I just installed it, and it does wonders for my scanner (agfa snapscan 1212u). But it does not work with xgl-ati-beryl, maybe some tweaking can fix that but it doesn't work out of the box.
xgl loads allright but but all elements (like buttons and menus) are unreadable. I logged out (knowing the positions of the buttons) and logged into gnome which show no problems.

---

### Post by imon9 on 2007-05-04
so, does this means you can't continue using the modified kernel? and you're back to the old one that breaks the scanner?

hmm...i hope i could help u with the xgl-ati thing, but seriously, i got no idea... hope you figure them out anyway

---

### Post by jeanjean84 on 2007-05-04
Hi,

after upgrading to Feisty, my scanner Epson Perfection 660 (using snapscan) stopped working  :( 

I searched around and found the Bug #85488 in linux-source-2.6.20 (Ubuntu)

fishor's fix (i.e. recompiled kernel) is working perfectly for me ! 

I have a desktop and no proprietary drivers, ... so no problem !!! 

Xsane works ! gscan2pdf works ! xscanimage works ! scanimage works !

Everything works (so far) !  :lolflag: 

Thanks, fishor !  :)

---

### Post by fsando on 2007-05-04
> **imon9 said:**
> so, does this means you can't continue using the modified kernel? and you're back to the old one that breaks the scanner?

hmm...i hope i could help u with the xgl-ati thing, but seriously, i got no idea... hope you figure them out anyway

Yes and no, it means that this build is not perfect but it certainly solves my scanning problems, so big thanks for the pointer.

Another issue is that I normally use the low-latency version so the modified kernel is markedly slower.

I guess it should be possible (in principle) for me to compile my own version of the lowlatency+ati-driver without  USB_suspend,  though I'm not experienced enough to go there myself.

I boot into the modified when I need to scan (using normal gnome), otherwise I'm in the lowlatency version with support for ati+xgl etc.

---

### Post by t2000kw on 2007-05-04
I tried the "new" kernel and had problems--Xserver wouldn't load, couldn't get to ubuntu, other boot errors showing up, no GUI. 

How do I remove the "new" kernel. I tried using Synaptics but it still shows up on the menu when I boot again. Id no longer shows up in Synaptics, though.

---

### Post by fsando on 2007-05-04
> **t2000kw said:**
> I tried the "new" kernel and had problems--Xserver wouldn't load, couldn't get to ubuntu, other boot errors showing up, no GUI. 

How do I remove the "new" kernel. I tried using Synaptics but it still shows up on the menu when I boot again. Id no longer shows up in Synaptics, though.
I'm not sure how to remove it completely - it should probably be deleted from where it sits (I just don't know where) but to remove it from your boot list:
Edit your menu.lst and remove the entry referring to that new kernel - next time you boot just boot into the good one.
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by cisoprogressivo on 2007-05-07
I have this scanner, and i have the same problem.
I've tried the patched kernel, but i have some problems compiling my ATI drivers.
Maybe i will wait the next Ubuntu kernel release.
Now i use 2.6.20-15.
When will be released 2.6.20-16? Will be patched?

---

### Post by t2000kw on 2007-05-07
I eventually reinstalled Ubuntu Feisty, copied my Windows  email program (Agent) into a directory under Wine after I reinstalled it, and copied my Foxfire bookmarks file into the regular /home location for now. I will be moving /home to its own partition again and now have directions on how to make Ubuntu "see" the /home partition if I should reinstall Ubuntu again. It requires using the live CD before the first boot into Ubuntu after the installation is done. 

As for the next version of Ubuntu, you may not want to wait that long and might want to try a late beta version in late August. Here's the schedule:

[https://wiki.ubuntu.com/GutsyReleaseSchedule](https://wiki.ubuntu.com/GutsyReleaseSchedule)

Final release is set for October 18.

If you upgrade, you'll need to change your sources.list--all instances of Feisty will need to be changed to Gutsy. I don't think that happens automatically when you upgrade, but it might. Perhaps someone will see this and comment on it???

---

### Post by John Jason Jordan on 2007-05-10
> **cisoprogressivo said:**
> I have this scanner, and i have the same problem.
I've tried the patched kernel, but i have some problems compiling my ATI drivers.
Maybe i will wait the next Ubuntu kernel release.
Now i use 2.6.20-15.
When will be released 2.6.20-16? Will be patched?
I have the CanoScan LIDE 30 which worked fine under Dapper and Edgy, but after upgrading to Feisty I get the same black page that everyone else is getting. 

I discovered another workaround. If I boot with a Knoppix 5.0 live CD I can scan just fine. Then, if I click on the penguin I can get a root terminal window, mount my hard drive, and save the images. 

It's kinda clunky, but luckily I don't need to scan very often. I don't know how to compile a kernel and I don't have time to learn right now. This will get me by until someone fixes the kernel.

---

### Post by cisoprogressivo on 2007-05-10
i've find the solution:
instal scanbuttond and start it before you scanning application.
It works for sure ;)

---

### Post by t2000kw on 2007-05-10
> **John Jason Jordan said:**
>  

I discovered another workaround. If I boot with a Knoppix 5.0 live CD I can scan just fine. Then, if I click on the penguin I can get a root terminal window, mount my hard drive, and save the images. 

It's kinda clunky, but luckily I don't need to scan very often. I don't know how to compile a kernel and I don't have time to learn right now. This will get me by until someone fixes the kernel.

Has anyone tried this with a live CD for Edgy Eft? Or other versions of linux with a kernel earlier than Feisty?

---

### Post by t2000kw on 2007-05-10
> **cisoprogressivo said:**
> i've find the solution:
instal scanbuttond and start it before you scanning application.
It works for sure ;)

It "sort of" works, but not for all scanner programs. It works OK with Xsane. 

Unfortunately, it does nothing to fix other USB-related problems that originate with the implementation of USB_SUSPEND.

---

### Post by John Jason Jordan on 2007-05-10
> **t2000kw said:**
> Has anyone tried this with a live CD for Edgy Eft? Or other versions of linux with a kernel earlier than Feisty?
I first tried it with Knoppix 5.10, but discovered that 5.1 uses kernel 2.6.19.7, and I got the same results as with Feisty. Then I found an old Knoppix 5.01 disk, and that worked. Once I had something that worked I stopped looking for additional solutions. But, in theory, it ought to work with Dapper or Edgy live CDs, as long as your scanner worked originally under Dapper or Edgy. You might try also Fedora 7 test4, as I think it's still on 2.6.18. Or was that Etch? Linux makes your mind go to mush.

---

### Post by gewitty on 2007-05-11
Just to add a bit more fuel to the flames :) . I have this problem with my Epson Perfection 1670. It worked fine in Edgy, but since I upgraded to Feisty it has serious problems. After booting my PC, if I run Xsane, I can get just one single scan, then the scanner locks out. The power light turns from steady green to flashing red. The only way I can re-set it is by rebooting again. This clearly appears to be due to the CONFIG_USB_SUSPEND function. I tried installing scanbuttond, but this had no effect.

Since I don't have the knowledge to install an edited kernel, I guess I'm stuck like so many other users, unless someone comes up with a workaround that the likes of me can understand.

I'm amazed that no-one spotted this during beta testing. It must affect a huge number of people.

---

### Post by parsim on 2007-05-11
A "me too" with a Canon LIDE 25. Just one scan from XSane. But "scanimage" works fine, so I've been doing all my scanning with:
```
scanimage -x 210 -y 290 --resolution 200 --mode Color > output.pmn
```
... and then edit in Gimp.

---

### Post by gewitty on 2007-05-11
> **parsim said:**
> A "me too" with a Canon LIDE 25. Just one scan from XSane. But "scanimage" works fine, so I've been doing all my scanning with:
```
scanimage -x 210 -y 290 --resolution 200 --mode Color > output.pmn
```
... and then edit in Gimp.

That works. Not very user-friendly, but better than nothing. I wonder why scanimage doesn't get ambushed by CONFIG_USB_SUSPEND?

Thanks for the tip.

---

### Post by gewitty on 2007-05-11
Got a note from Oliver Schwarz who works on SANE development. He explains why scanimage works, whilst Xsane and other front-ends don't - 

"*This has been discussed on the sane-devel mailing list recently. It seems that scanimage keeps the connection to the scanner open while it is running, which prevents a suspend. xsane closes the connection each time it has finished a scan job. *"

So now you know.

---

### Post by Argos_Bling on 2007-05-11
> **gewitty said:**
> I'm amazed that no-one spotted this during beta testing. It must affect a huge number of people.They did, many times. The developers made a very brief post saying:
"Unfortunately this option needs to remain enabled so that a good chunk of other users can have suspend/resume, which ultimately is more important than a working scanner."
The bug was then marked as low priority and no more seems to have been forthcoming from the developers, despite MANY beta testers reporting the bug. To be honest this has left me wondering whether to bother bug reporting next time around :( - surely if a change at the end of alpha testing introduces a regression, then the change should be rolled back? Ah well, it's easy to criticise when it isn't you that has the job.

---

### Post by pinus on 2007-05-12
Reading this I doubt that Ubuntu is the right distribution for me. Ignoring such a serious bug without providing a workaround (e.g. another Kernel) is more than I can stand.

---

### Post by Argos_Bling on 2007-05-13
One solution to get scanners working under Feisty is to run it with an Edgy kernel - this works as long as all your hardware worked under Edgy:

Add the following to your sources.list:
[CODE]deb http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted
[deb http://security.ubuntu.com/ubuntu edgy-security main restricted/CODE]

Then do a sudo apt-get update && sudo apt-get update cycle - although nothing is likely to get updated.

Then install the edgy kernel:
sudo apt-get install linux-image-2.6.17-11-generic

Reboot into this kernel, and voila - your Feisty system can use the scanner.

For Nvidia users:
Before reboot, edit xorg.conf to use the "nv" driver, then test the new kernel for a while. If you are happy, remove the nvidia-glx package, and download and install the Nvidia driver direct from nvdia,com.

Ati users: unsure, but probably a similar process to the above.
Other restricted modules (madwifi, fcdsl) - unknown.

---

### Post by JimmyME on 2007-05-14
I'm keeping Edgy until or if this scanner problem in Feisty is fixed.

Does any know if there's any chance XSANE/SANE can be altered to behave like scanimage and keep the connection open?

I find this totally ridiculous that the Feisty development group knew that scanners that worked in Edgy wouldn't work in Feisty and they deemed that not important enough to address.  

HUH?

I do a lot of photography with the computer and use the scanner heavily.  This makes me wonder about the maturity of those leading Ubuntu development to write off this issue (as per the quoted response a few messages above).

---

### Post by Talon2 on 2007-05-14
> **Argos_Bling said:**
> They did, many times. The developers made a very brief post saying:
"Unfortunately this option needs to remain enabled so that a good chunk of other users can have suspend/resume, which ultimately is more important than a working scanner."

Hey, it isn't like suspend/resume has been very successful in this release.  Search launchpad or these forums with "suspend" and tell me how well power mangement works.

---

### Post by gewitty on 2007-05-15
There are a lot of discussions going on around the forums about this issue. It has certainly made more than a few people cross.

Take a look at the (steadily) growing list of bug report messages here - [http://tinyurl.com/2sdhgg](http://tinyurl.com/2sdhgg)

Or some of the debates in these threads:

[http://tinyurl.com/2rxnfp](http://tinyurl.com/2rxnfp)
[http://tinyurl.com/374r7c](http://tinyurl.com/374r7c)
[http://tinyurl.com/2qt5xu](http://tinyurl.com/2qt5xu)

Surely we must see a patch for this problem soon?

---

### Post by Ahunt on 2007-05-16
Hi everyone:

I am new to Ubuntu (one month) and have it operational at home on one PC with another running XP. As described here in this thread my Canon LiDE 20 won't work with Ubuntu 7.04 Feisty Fawn. I have read the whole thread here, plus the other ones in the forum on the subject.

I am finding it a bit hard to understand how this "bug" was intentionally introduced with Feisty when these USB scanners worked fine with Edgy. 

One of my reasons for setting up a PC at home is to evaluate using Ubuntu as an alternative to switching to Vista at work, when XP support expires on 14 April 2009. So far I have found that Ubuntu would be a great upgrade from XP - easy to install on the desktops and server and with a minimal training bill for the users on the system to transition from XP. But our necessary reliance on Canon USB scanners at work to get our job done there (newspaper publishing) means that it is a "no brainer" that Ubuntu won't sell in that work environment. I would hate to have an induced "bug" like this push work places like mine into Vista just because we have to run scanners!

I am hoping the Dev team do read this and take this all into account in designing a fix for this in Gutsy, if not before. No need for a response - I can do all my scanning on XP at home for now, but this has to be fixed!

Adam

---

### Post by autocrosser on 2007-05-16
Gutsy will be using a much newer kernel than Feisty---remember, Linux is a "moving target" & is constantly updated---unlike XP & Vista. I have already seen a fair amount of the 2.6.22 kernel tree introduced--this "should" include the USB_SUSPEND fix for scanners--I'll post as soon as I know for sure--It looks like I'll be updating to it within the next couple of days.

---

### Post by parsim on 2007-05-16
> **Talon2 said:**
> Hey, it isn't like suspend/resume has been very successful in this release.  Search launchpad or these forums with "suspend" and tell me how well power mangement works.

Heh, yeah, suspend doesn't work for me either. It seems prone to locking up the keyboard and mouse after a resume... both of which are USB. Coincidence??

---

### Post by Ahunt on 2007-05-16
Dear AC:

Nice to hear from you - I am heartened that this problem is being addressed! It is also nice to know that people such as yourself prowl the beginner forums helping us beginners out, even if only with reassurances!

As mentioned, by April 2009 it would be nice to go to the boss with a recommendation to transition to Ubuntu instead of Vista or pay MS for another five years to keep our XP network supported. I have an on-going list of Ubuntu issues that will need to be addressed to be able to make a recommendation without reservations for Ubuntu for the office network. Most of these are finding replacement apps for existing specialized Windows ones. I am trying to stay away from the concept of running Windows apps via an emulator!

Every little bit helps and your confidence that Gutsy will solve the USB scanner problem is appreciated. 

To all the developers: "Keep up the great work on Ubuntu - the newbies  appreciate your efforts!"

Adam

---

### Post by Ebuntor on 2007-05-18
There's a great fix for the problem on Launchpad by **Fraz**. It only works for XSane

[https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488](https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488)

Here's a very simple explanation:[LIST]
[*]Open the terminal and type
[*]```
 sudo aptitude install scanbuttond
```
[*]After the installation simply type ```
scanbuttond
``` to run the program.[/LIST]What this program does is explained on Launchpad
>  the daemon allways watches for the scanner and the usb did not suspend. the real function of this software is to look for the buttons on the scanner and do something usefull lke
scanning -> printing - scanning -> email
To make this program run at startup so you don't have to think about it every time:[LIST]
[*]Go to **System** => **Preferences** => **Sessions**
[*]Under the **Startup Programs **click the **New** button
[*]A new windows will appear. Fill in any name you'd like in the name box, "Scanbutton" for example. In the command box enter **scanbuttond **(with a "d" at the end)[/LIST]I tried it with my scanner and it works great. :) And the buttons on my scanner now work too!
I know it isn't a real fix but at least your scanner works.

---

### Post by sk8dork on 2007-05-19
> **Ebuntor said:**
> There's a great fix for the problem on Launchpad by **Fraz**. It only works for XSane

[https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488](https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488)

Here's a very simple explanation:[LIST]
[*]Open the terminal and type
[*]```
 sudo aptitude install scanbuttond
```
[*]After the installation simply type ```
scanbuttond
``` to run the program.[/LIST]What this program does is explained on Launchpad
To make this program run at startup so you don't have to think about it every time:[LIST]
[*]Go to **System** => **Preferences** => **Sessions**
[*]Under the **Startup Programs **click the **New** button
[*]A new windows will appear. Fill in any name you'd like in the name box, "Scanbutton" for example. In the command box enter **scanbuttond **(with a "d" at the end)[/LIST]I tried it with my scanner and it works great. :) And the buttons on my scanner now work too!
I know it isn't a real fix but at least your scanner works.

this works for me. after installing and starting scanbuttond, i just hooked up my canoscan lide 25 for the first time, fired up gimp, aquire > xsane, and voila.

---

### Post by Ahunt on 2007-05-20
I tried this fix and it works - sort of. 

I keep finding that most Ubuntu fixes create more problems that they solve.

Scanbuttond was found and installed fine. Xsane was then able to find the scanner and control it somewhat, some of the time. 

My scanner is a very similar ConoScan LiDE 20 to the one mentioned above. Xsane was able to do a preview about half the time I tried it. The rest of the time it seemed to want to run the scanner shuttle backwards against the parking stop until I either rebooted or unplugged the scanner. 

It did this on "scan" as well - sometimes scanning fine, but not returning the shuttle - just running against the stop at the other end. A couple of times it did preview, scan and save okay (although it produced very large files, but I suspect that is a setting problem - this scanner on XP produces very compact files)

I am just afraid that its control of the scanner is so erratic that it will damage the scanner.

Any ideas what is going on here?

Adam

---

### Post by gewitty on 2007-05-21
I confirm that this fix works for my Epson Perfection 1670.

---

### Post by redsoftretro on 2007-05-22
Hi

I had same problem with CanoScan 650U.

Command line works fine...

scanimage --format tiff --resolution 150 -x 215 -y 297 > ~/Desktop/myscan



Also try this fix

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg322180.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg322180.html)

---

### Post by Ebuntor on 2007-05-22
> **sk8dork said:**
> this works for me. after installing and starting scanbuttond, i just hooked up my canoscan lide 25 for the first time, fired up gimp, aquire > xsane, and voila.

Well I'm glad it works for you too. :)

---

### Post by matchstich on 2007-05-25
i am using dapper and when i try the sudo aptitude install scanbuttond.

i get  sudo aptitude install scanbuttond
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "scanbuttond"
The following packages have been kept back:
  checkinstall
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

dapper can't use it?

bummer.

---

### Post by Ebuntor on 2007-05-25
> **matchstich said:**
> i am using dapper and when i try the sudo aptitude install scanbuttond.

i get  sudo aptitude install scanbuttond
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "scanbuttond"
The following packages have been kept back:
  checkinstall
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

dapper can't use it?

bummer.
                                                      Actually the bug we're talking about is only related to Feisty as far as I know. 

But to your question: I'm certainly no expert but I suspect Dapper just doesn't have scanbuttond in the repositories. You can manually download and install it quite easily.[LIST]
[*]First download the .deb file from     here:     [http://ftp.gva.es/mirror/debian/pool/main/s/scanbuttond/scanbuttond_0.2.3-4_i386.deb](http://ftp.gva.es/mirror/debian/pool/main/s/scanbuttond/scanbuttond_0.2.3-4_i386.deb)
[*]Go to the directory where you     downloaded the file to and simply dubble click it like any other     program.
[*]The GDebi Package Installer should     start now
[*]Click the "Install Package"     button in the top right corner, you"ll probably have to enter     your password first.
[*]After that the package should     install itself and you're done!
[*]To test if the package has actually been installed you can     run it from the terminal, to run the program type     ```
scanbuttond
``` you should also be able to see the package     listed in Synaptic.[/LIST]Let me know if it works! :)

---

### Post by autocrosser on 2007-05-26
Now as for updates---Gutsy Kernel 2.6.22-5 still is scanner-less, both my Canon Lide20 & my HP 4370 do black scans--I have not used any of the fixes in the posts--scanbuttond drives my HP 4370 crazy & as of the 2.6.22-4 kernel the scanner.sh script no longer works. I'm going to update the bug report & include Gutsy in it.

---

### Post by JimmyME on 2007-05-26
Autocrosser,

Thanks for the updates.

The scanner issue is the only reason I'm not upgrading to Feisty from Edgy.

I check into the forum every few days to see if anything has changed, but will hang tight till I read that the scanner problems are fixed here.

Thanks again for keeping us in the loop.

Jim
Maine

---

### Post by dejavu_01 on 2007-05-31
> **Ebuntor said:**
> There's a great fix for the problem on Launchpad by **Fraz**. It only works for XSane

[https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488](https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488)

Here's a very simple explanation:[LIST]
[*]Open the terminal and type
[*]```
 sudo aptitude install scanbuttond
```
[*]After the installation simply type ```
scanbuttond
``` to run the program.[/LIST]What this program does is explained on Launchpad
To make this program run at startup so you don't have to think about it every time:[LIST]
[*]Go to **System** => **Preferences** => **Sessions**
[*]Under the **Startup Programs **click the **New** button
[*]A new windows will appear. Fill in any name you'd like in the name box, "Scanbutton" for example. In the command box enter **scanbuttond **(with a "d" at the end)[/LIST]I tried it with my scanner and it works great. :) And the buttons on my scanner now work too!
I know it isn't a real fix but at least your scanner works.


Thank you, I confirmed that this solution works after a tiring and desperate attempt in setting up my Canoscan LiDE 25.   Ubuntu just makes life easier than other distro I used before

---

### Post by t2000kw on 2007-06-01
Well, this is where it gets interesting. (Keep in mind that I'm running Feisty and like it except for the scanner fiasco.)

I doubt Mark Shuttleworth reads these forums, but his distribution is about to become possibly the worst one in the eyes of the public really soon because of all of this. And I wish this weren't about to happen, but . . .

Dell is now offering Ubuntu 7.04 (Feisty Fawn) on their Linux computers. You can order it online right now. The standard price includes no support. Then there is a 30-day basic support, a 1 yr basic, and a 1 yr standard.

Imagine when someone who has a business buys a Dell Ubuntu desktop and can't use his scanner. Or even the average consumer who has no support option chosen.

Did Dell pick Feisty over other options (Dapper, or even Fedora, SuSE, etc.) to kill the idea of a Linux computer on the market, or did they just make a bad decision when choosing this particular release of Ubuntu? I'm hoping they just made a bad decision and would like to believe that the naysayers are wrong and that Dell does not have an evil plan to keep Linux out of their offerings.

This won't look good for Dell or Ubuntu. Hopefully, this might be the force to push Ubuntu into offering an early fix and not make the public wait for the next release. This still is bad for customers who choose no support. But if a kernel (or other) update that actually fixes this problem would be offered in the updates offered, I think Dell might be able to contact those customers and offer to help them through the update process if they are uncomfortable following the simple update process the first time.

Then again, maybe Dell can offer to sell disappointed Ubuntu PC customers Windows PCs that will work with scanners. 

If I've read correctly, it can be fixed, as other distributons have USB_SUSPEND enabled (which may or may not be related to the problem Ubuntu is experiencing) and still have good scanner support.

---

### Post by keithpeter on 2007-06-01
> **parsim said:**
> A "me too" with a Canon LIDE 25. Just one scan from XSane. But "scanimage" works fine, so I've been doing all my scanning with:
```
scanimage -x 210 -y 290 --resolution 200 --mode Color > output.pmn
```
... and then edit in Gimp.

Me too as well with a Canon LIDE 20 scanner on Feisty Xubuntu (ie xsane not installed before doing sudo aptitude install sane sane-utils). 

Actually better scans than I ever had from Dapper with this scanner and the Xsane thingy.

---

### Post by lifeempowered.com on 2007-06-02
> **Ebuntor said:**
> There's a great fix for the problem on Launchpad by **Fraz**. It only works for XSane

[https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488](https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488)

Here's a very simple explanation:[LIST]
[*]Open the terminal and type
[*]```
 sudo aptitude install scanbuttond
```
[*]After the installation simply type ```
scanbuttond
``` to run the program.[/LIST]What this program does is explained on Launchpad
To make this program run at startup so you don't have to think about it every time:[LIST]
[*]Go to **System** => **Preferences** => **Sessions**
[*]Under the **Startup Programs **click the **New** button
[*]A new windows will appear. Fill in any name you'd like in the name box, "Scanbutton" for example. In the command box enter **scanbuttond **(with a "d" at the end)[/LIST]I tried it with my scanner and it works great. :) And the buttons on my scanner now work too!
I know it isn't a real fix but at least your scanner works.

THANK YOU!  Works perfectly for my LiDE 30!

---

### Post by Ebuntor on 2007-06-02
> **lifeempowered.com said:**
> THANK YOU!  Works perfectly for my LiDE 30!

You're welcome. Glad to be of help. :)

---

### Post by minj on 2007-06-06
> **Ebuntor said:**
> You're welcome. Glad to be of help. :)

Works for me too!

---

### Post by t2000kw on 2007-06-06
After the recent kernel update, scanbuttond works with Kooka also. I don't pass any special parameters or switches to the program. It works well as it is.

---

### Post by Shadoglare on 2007-06-06
> **t2000kw said:**
> Imagine when someone who has a business buys a Dell Ubuntu desktop and can't use his scanner. Or even the average consumer who has no support option chosen.

I actually do use my scanner for business purposes - and I can tell you if I had bought this from Dell, they'd have it back. I've had products sitting on a shelf for weeks because I haven't been able to work with scans of the literature for it, and have been a tad too busy to spend a bunch of time trying to figure out the problem. 

If this would have been my first attempt at using Linux, more than likely I'd just "trade up" to Windows and never screw with it again. 

As it turns out in my case the thing was working fine with Ubuntu before the "new and improved" upgrade (which broke a *lot* of stuff) so I at least knew off hand it *should* work...

---

### Post by Shadoglare on 2007-06-06
Well, I tried the scanbuttond fix... worked great.... for *one* scan :(

---

### Post by t2000kw on 2007-06-06
What other things were broken after thew upgrade to Feisty?

Or was this with the latest Feisty kernelupdate a few days ago?

---

### Post by Shadoglare on 2007-06-06
OK, what's working for me (at least for the time being) is basically not using XSane. 
I installed Kooka, tried it out a little bit ago and it appears to work wonderfully - as far as I'm aware there's no plugin for it for GIMP, but Kooka itself has a "load in graphics app" function that, once you've scanned your image, lets you load it up in GIMP from within the Kooka app. 

I'll keep an eye on this thread to see if a "real" fix every comes down the road though :/

---

### Post by Shadoglare on 2007-06-06
> **t2000kw said:**
> What other things were broken after thew upgrade to Feisty?

Or was this with the latest Feisty kernelupdate a few days ago?

Nope, this was the 7.04 update, which I did a few weeks ago. 

I'm sure there are probably other things - for me *personally*, the update broke the NVidia video driver, the scanner, CD ripping to mp3, and audio CD burning. May have jacked up DVD rip/burns as well, haven't tried it yet. 
Other threads that were linked here seem to indicate that a lot of USB devices are having issues after the update.

---

### Post by t2000kw on 2007-06-06
Interesting. I can do all of that except scan (unless I use Scanbuttond). I also have my Nvidia driver working. 

As for Kooka, if I go back and run scanbuttond a second time I can scan another page, sometimes more. 

With Xsane, after running scanbuttond, I can scan more than one page without having to run scanbuttond again. 

So you might give the scanbuttond another run after scanning one page just to see if it works.

(I don't use any parameters with the scanbuttond command.)

Good news from the alpha testing front (heard fomr one of the testers). Best guess is that this USB related problem will be fixed in Gutsy. One of the newer kernels is supposed to already have the fix in place.

---

### Post by Ebuntor on 2007-06-07
> **Shadoglare said:**
> Well, I tried the scanbuttond fix... worked great.... for *one* scan :(

Was the Scanbuttond daemon still active after the first scan? You need to keep the program running or you can add it to the startup program list.

---

### Post by Shadoglare on 2007-06-07
> **Ebuntor said:**
> Was the Scanbuttond daemon still active after the first scan? You need to keep the program running or you can add it to the startup program list.

Yeah, doesn't seem to make a difference. I added it to the startup group, and now I can scan *once* after starting up.

Even if I end the scanbuttond process and then start the program again, it still doesn't work any longer for that session :/

---

### Post by imon9 on 2007-06-08
scanbuttond occasionally causes my scanner to "not return to original position" after a preview or scan... and make my scanner moter make a loud sqeuking sound... non of these happen when i roll back to kernel 2.6.17-10 which did not have USB_suspend yet... however, suspend doesnt work as expected and resuming from hibernate always disabled my wifi card :(

i tried the latest gutsy 2.6.22-16 with no sucess...still same problem with scanner , webcam ... suspend & hibernate works with wifi being disable

---

### Post by JimmyME on 2007-06-28
Anything new on the Feisty Scanner problems?

---

### Post by jaycee15* on 2007-07-02
FWIW, my Lide 25 works fine after installing and running gscan2pdf.  This is the only way I am able to get the scanner working ok with Feisty.  See earlier postings in this thread for info on installing gscan2pdf.

---

### Post by Shadoglare on 2007-08-09
> **jaycee15* said:**
> FWIW, my Lide 25 works fine after installing and running gscan2pdf.  This is the only way I am able to get the scanner working ok with Feisty.  See earlier postings in this thread for info on installing gscan2pdf.

Just tried it, doesn't work for me. Scanner still gave me one scan after booting and then died. 

And I just got a huge shipment of new product to scan in... this is gonna be great having to reboot every time! *GRUMBLE*

So.... any updates yet on getting this thing working, or are the coders just going to ignore it until everybody gets annoyed enough to switch back to Microsoft? *grumble. again.*

---

### Post by t2000kw on 2007-08-09
> **Shadoglare said:**
> So.... any updates yet on getting this thing working, or are the coders just going to ignore it until everybody gets annoyed enough to switch back to Microsoft? *grumble. again.*

You can read all about it here:
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488)

and Mark Shuttleworth's latest comments on this toward the end of that bug report thread:
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488/comments/401](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488/comments/401)
there was another post or two of his there as well, but I can't find them quickly.

He did give us the impression that this will be fixed in Gutsy, NOT in a Feisty update. 

Of course, if this turns out to be untrue, I will switch to another distribution (maybe SuSE or Fedora, since they worked on addressing this problem very quickly!)  or install Dapper, the last LTS version. 

Remember, the interim releases are cutting edge, and we pay a bit for that "privilege," but we also have the ability to install the LTS versions, which should be less problematic. 

I have to agree, though, that this could have been fixed in a Feisty update by now and should have.

---

### Post by Shadoglare on 2007-08-12
> **t2000kw said:**
> He did give us the impression that this will be fixed in Gutsy, NOT in a Feisty update. 

Of course, if this turns out to be untrue, I will switch to another distribution (maybe SuSE or Fedora, since they worked on addressing this problem very quickly!)  or install Dapper, the last LTS version. 


I think I may check out the liveDVD edition of OpenSUSE and see how that goes. 
I'm sure the percentage of Ubuntu users who have scanning as a requirement is pretty low, but I happen to be one of them, and I've already been without it since the last update came out, what, two or three months ago?

---

### Post by JimmyME on 2007-08-14
> **t2000kw said:**
> You can read all about it here:
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488)

and Mark Shuttleworth's latest comments on this toward the end of that bug report thread:
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488/comments/401](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488/comments/401)
there was another post or two of his there as well, but I can't find them quickly.

He did give us the impression that this will be fixed in Gutsy, NOT in a Feisty update. 

Of course, if this turns out to be untrue, I will switch to another distribution (maybe SuSE or Fedora, since they worked on addressing this problem very quickly!)  or install Dapper, the last LTS version. 

Remember, the interim releases are cutting edge, and we pay a bit for that "privilege," but we also have the ability to install the LTS versions, which should be less problematic. 

I have to agree, though, that this could have been fixed in a Feisty update by now and should have.

I found his comments to be vague, big business mumbo jumbo where no guilt or responsibility is admitted and with no stated commitment to fixing the problem.

What we're talking about here is not some incompatibility with an obscure piece of hardware.  

We're talking about SCANNERS.

Sheesh!

Fix it already.

---

### Post by t2000kw on 2007-08-14
I was trying to be nice, but my personal feelings ar that this could have been fixed in an update. I read that Debian has this fixed without a kernel update by using somethining the Sane program. But it's the kernel that caused it. 

And, also my feeling, scanners are important.

Their reasoning on the matter is that if we wanted stability, we would have installed the LTS version or paid for support. If we paid for support, we would have had the problem addressed somehow. That's what was mentioned, anyway. Whether it's true or not, since I'm not paying for support, I don't know. I can't imagine that at least one company that paid for support would not have called for support on this issue, and if there was a fix, it would have been offered to the community. But maybe that's one way os showing that we get what we pay for and is an encouragement to buy support?

---

### Post by Stinger on 2007-08-15
Please give the developers some air , it takes time to sort these thing out and find the best solution for this kinda problem.

For all those affected by the problem I would recommend Egdy , don't fiddle around trying a workaround ,    wait until the problem is fixed in Gutsy.

At the moment it seems like there are two approaches to a solution and disabling USB_SUSPEND isn't one of them.

1. Blacklisting all known USB devices known to cause trouble so they don't get suspended.

2. A fix in the SANE backend so all scan devices known to give trouble don't get supended.

Or maybe both in combination ?

Be patient a solution is on it's way as we speek and use Edgy in the meantime.

Ubuntu ROCKS !!

---

### Post by tashmooclam on 2007-08-15
Just thought I would mention....
My Canon Canoscan Lide 30 doesn't work with Ubuntu 7.04 and XSane Image Scanner.
I got a big black image, but the scanner really wasn't doing anything. 
I'm not inclined to do anything about it right now. I'll wait to see if this ever is fixed with some update or other. I hope so.
I'll try taking a pic using my digital camera with the document photo setting. "There are two ways to skin a cat."

---

### Post by Shadoglare on 2007-08-18
> **t2000kw said:**
> Of course, if this turns out to be untrue, I will switch to another distribution (maybe SuSE or Fedora, since they worked on addressing this problem very quickly!)  or install Dapper, the last LTS version. 

So yeah.. I installed OpenSUSE 10.2 yesterday... and once it was fully installed and all of the updates since the original release were downloaded... it was a matter of about 3-5 minutes to get the scanner working perfectly. 
I didn't even have to screw around with configuring SANE - it's got a "control panel" style scanner applet that auto-detected the scanner, identified it correctly, asked which backend I preferred to use (sane, of course), and configured it for the other apps like XSane to see. 

So... it was nice talking to you folks, but I think that's probably it for me when it comes to Ubuntu.

---

### Post by t2000kw on 2007-08-18
Unfortunately, the slow response to this serious problem is turning away many people from what I've read here and elsewhere. 

Hopefully Canonical will learn from this mistake and it won't be repeated again. By "mistake" here I don't mean having a problem, I mean how the problem was addressed.

---

### Post by Bachstelze on 2007-08-18
Oh, come *on*, this problem has been addressed countless times ! The reason why your LiDE is only displaying ablack image in Xsane is because of a ne in-kernel USB suspend feature, it has *nothing* to do with Ubuntu ! The issue is fixed in kernel 2.6.22, thus in Gutsy. Meanwhile, a workaround is to use scanbuttond to keep the USB connection active and preven the kernel's suspend feature from activating. Close xsane, do

```
sudo apt-get install scanbuttond
scanbuttond
```

then launch xsane again, you're there.

---

### Post by t2000kw on 2007-08-18
That would be great if the scanbutton thing actually worked for everyone. It doesn't! I AM happy that it works perfectly for you. For the rest of us, we either use another OS to get our scanning work done or are waiting six months to do our scanning (or, rebooting for each scan). Unfortunately, some, like the person who posted a couple of posts before, don't want to wait the six months to get use of their scanner. 

Sorry, but work-arounds are just that, and they often don't work very well, either. It doesn't allow it to work with scanning programs that I use, and if I do use Xsane (which is definitely not my first choice), it works for one scan. That's all. Then I have to reboot. Not very convenient! Windows does better than that, and I don't really want to use it but it works for scanning. And I don't think people should have to install multiple Linux distros with multi-boot capability just to have scanning capabilities in one and the other nice features in the other. 

The problem IS with Ubuntu in a way since they control which features in the kernel are enabled. That's part of what makes one distro different from another, isn't it? When this kernel was first offered to the public (including Canonical. SuSE, Red Hat, etc.) it was stated that this was experimental and probably not ready for prime time. Some distros listened, some didn't, tried it and found it was a serious problem but fixed it (some after working at it for a while), and one is widely known in the Linux community for ignoring it altogether in their current distribution. Guess which distro was the one that ignored it? I won't name names but it begins (and ends)  with a "U." 

Let's hope those who follow the Linux underground forums will come back to Ubuntu at a later time when things have been set straight. I'm waiting it out, but not very patiently.

---

### Post by lkraemer on 2007-08-22
Folks,
t2000Kw has it pegged.  The workaround doesn't work for me either.  My Canoscan Lide 25
stops after a Preview and hangs when using SCANBUTTOND.  If I scan at 50 DPI it makes it at
times and sometimes I can even possibly get a preview at 300 DPI, but never at any higher
DPI.  And I've tried the Scrips posted on [https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488/](https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488/)
(MUST change DEV and BUS to what lsusb detects on your system)

#!/bin/sh
echo "prodding scanner begins ..."
         for i in `seq 1 1000`;
        do
cat /dev/bus/usb/001/004 > /dev/null
sleep 1
        done
echo "scanner is now having a nice rest..."

This Script works for a bit then my scanner quits and causes the USB port to Increment
and I have to KILL the script, edit it, and re-run it.

Will some of you fine folks that own a Canoscan Lide 25 try scanning a 8.5x11 Photo
at say 600 DPI and 1200 DPI and VERIFY  that it actually does work.  It's hard to believe
I'm the only one having problems trying to get it to preview/scan over 300 DPI.

Next I'm going to try fishor's modified kernel and see what that does.  (from the above URL)

Why can't the Ubuntu folks just release an updated Desktop Kernel with the USB Hybernate
disabled for the Desktop folks.  It would just be a simple compile and release.
What would be so hard?  Help me understand why?

Thanks.

lkraemer

Just booted Kernel 2.6.20-16-Generic and installed 2.6.20-15-124-386 and Rebooted on new kernel via GRUB.
I still have the same problems with any DPI over 300.  Will not scan....just locks up.

Booted 2.6.20-16-Generic and removed Test Kernel.

Any Ideas?

---

### Post by the dsc on 2007-08-24
> **HymnToLife said:**
> Oh, come *on*, this problem has been addressed countless times ! The reason why your LiDE is only displaying ablack image in Xsane is because of a ne in-kernel USB suspend feature, it has *nothing* to do with Ubuntu ! The issue is fixed in kernel 2.6.22, thus in Gutsy. Meanwhile, a workaround is to use scanbuttond to keep the USB connection active and preven the kernel's suspend feature from activating. Close xsane, do

```
sudo apt-get install scanbuttond
scanbuttond
```

then launch xsane again, you're there.

I have yet to try this scanbuttond thing, but, meanwhile, do you know "how" this issue was fixed in kernel 2.6.22? I would appreciate very much if you could answer in newbiese dialect.

I have found [this text](http://www.howtoforge.com/kernel_compilation_debian_etch) on compilling our own kernel, surprisingly it did not scary me so much, so I think I am going to try to customise a kernel of debian etch (which is what I am using right now) to solve that. (And if this whole thing of customising a kernel happen to be somewhat easy, I will also try to enable the support for NTFS-3g)

I think that the worst thing that could happen is to have a kernel that just does not work at all or does not solve the problem, then I would just have to boot from an older one from GRUB and uninstall the customised one.

... or could some failed attempt actually damage the scanner? :confused:

---

### Post by the dsc on 2007-08-26
Well, I did it, and it worked. Later maybe I'll install the button thing, but to actually use the scanner buttons...

However..... in order to use the scanner as a normal user, I've added the following line on fstab:

**none /dev/bus/usb usbfs defaults,devmode=0666 0 0**

This made possible to me use the scanner as a normal user, but I wonder if it is not the wrong way to do that.... is not it nearly the same  as using the scanner as root? Xsane warns emphatically that can be dangerous to use the scanner as root, so I'm a bit worried.... :confused:

---

### Post by deew on 2007-09-03
On my Lide25, the button fix is working, but is very hit and miss.  I have scanned two pictures today, but I restarted XSane about 15 times to do it.

---

### Post by gnoobie on 2007-09-09
I seem to be having some success but like the others can only scan once or twice without it reverting to black images

I have found that keeping a terminal window open and running scanbuttond when it seizes up seems to reopen it without having to reboot/ restart xsane. A slight hassle but bearable

huw

---

### Post by gnoobie on 2007-09-09
P S I am using a LIDE20  canon

---

### Post by babakan on 2007-09-10
I just started using Linux Mint (Ubuntu based) and ran into the scanner problem. After much effort I found this thread so at least I know what it is. It seems astounding this was not found before release and there still is no fix. 

Anyway, I tried the scanbuttond fix. Seems to work. However, by starting it from a console in background it will turn on the scanner light and leave it on whether you are running xsane or not. You have to reboot or kill the process if you know how. So rather, start scanbuttonx with the -f option to run it in foreground. Then when you close that console window it will exit. I am also going to try to write a script that does this, starts scanbuttond in foreground, opens xsane, then waits for xsane to be closed to exit the script and turn off the light.

I have to say I am very concerned about adopting Ubuntu or Mint after seeing how this is being handled (not). Somewhere in this thread someone questioned how Dell is handling this. Anyone know?

---

### Post by Stinger on 2007-09-19
The fix for the problem in Gutsy seems to be quite official now !
Have a look here:

[COLOR="Sienna"][bug/85488/comments/444]("https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488/comments/444")[/COLOR]

This is what its all about:
> linux-source-2.6.22 ([COLOR="DarkOrchid"]2.6.22-11.34[/COLOR]) gutsy; urgency=low

  [Alan Stern]

  * USB: disable autosuspend by default for non-hubs
    - LP: #85488

---

### Post by mikeescott on 2007-09-26
> **JimmyME said:**
> Anything new on the Feisty Scanner problems?


I got it working!!!!!

Open you package manager (System-Administration-Synaptic Package Manager)
install "libusb-dev 2:0.1.12-2"

If it does not work after that, go to [http://www.sane-project.org/](http://www.sane-project.org/) and find the "SANE-Backends-1.0.18" to download and install.

---

### Post by geraldm on 2007-09-27
the dsc wrote:
--snip--
none /dev/bus/usb usbfs defaults,devmode=0666 0 0

This made possible to me use the scanner as a normal user, but I wonder if it is not the wrong way to do that.... is not it nearly the same as using the scanner as root? Xsane warns emphatically that can be dangerous to use the scanner as root, so I'm a bit worried....
--end snip--

It is never a good idea to give "other" permission to access a device such as a scanner.
Damage to the scanner can occur if the scan head continues beyond the scan limit.
It is better to create a group, such as "scanner" and add selected users to that group
with read/write permissions.   "other" should NOT have write permissions.

On another note, those who are frustrated at their current kernel configured with
"CONFIG_USB_SUSPEND=y" should try compiling a custom kernel with that option
set to "=n".  Once you have compiled a custom kernel, you are over the hump.

Gerald

---

### Post by t2000kw on 2007-09-27
> **mikeescott said:**
> I got it working!!!!!

Open you package manager (System-Administration-Synaptic Package Manager)
install "libusb-dev 2:0.1.12-2"

If it does not work after that, go to [http://www.sane-project.org/](http://www.sane-project.org/) and find the "SANE-Backends-1.0.18" to download and install.

I installed the libusb file and it didn't work without using scanbuttond. However, if I run scanbuttond I can now do repeated scanning, and I'm no longer limited to Xsane. I can use Kooka without problems.

I went to the SANE-Backends page and they don't have binaries for Feisty posted (at least that I can't find, anyway). I don't wish to compile it from source so I'll just run scanbuttond when I'm going to need the scanner. 

I did try to add it as a startup command in system-preferences-session but it keeps disappearing. It "sticks" where it should in Dapper but in Feisty it disappears from the startup group. But it's not that difficult to run it once before doing any scanning, so I guess it's close to fixed for my purposes. The new libusb did something that allowed me to get more than one scan after running scanbuttond.

---

### Post by gewitty on 2007-09-28
I've been struggling with this one for months now, but with little success. My Epson Perfection 1670 refuses to work with any OS now, so I guess the firmware has got screwed up. Can anyone tell me how I can check/fix this?

And does anyone know if the scanner problems inherent in Feisty have been resolved in the forthcoming Gutsy release?

---

### Post by t2000kw on 2007-09-28
> **gewitty said:**
> I've been struggling with this one for months now, but with little success. My Epson Perfection 1670 refuses to work with any OS now, so I guess the firmware has got screwed up. Can anyone tell me how I can check/fix this?

And does anyone know if the scanner problems inherent in Feisty have been resolved in the forthcoming Gutsy release?

Is the firmware flashable? Your owner's manual (a copy of which would probably be on the Windows driver disk) should say so. Otherwise, you probably didn't screw up your firmware.

But if it's not working and still under warranty, I would suggest taking it to a service center. 

Also, check your USB port and try other things on it to see if it's the culprit if you haven't done so already.

---

### Post by gewitty on 2007-09-28
Yes, as far as I know, the firmware is flashable. When I boot Feisty at first, the scanner behaves as if it's OK - there is a brief movement of the scan bar and the green power light comes on. The problem only arises when I try to use XSane. It looks for available devices, then pops up an error message saying, "snapscan:libusb:004:005':Invalid argument". The power light goes out on the scanner at this point also. I've tried using scanbuttond, but this has no effect either.

---

### Post by crjackson on 2007-09-28
> **mikeescott said:**
> I got it working!!!!!

Open you package manager (System-Administration-Synaptic Package Manager)
install "libusb-dev 2:0.1.12-2"

If it does not work after that, go to [http://www.sane-project.org/](http://www.sane-project.org/) and find the "SANE-Backends-1.0.18" to download and install.

I can't find libusb-dev 2:0.1.12-2 in synaptic.  I'm using ubuntu 7.04 64-bit.  Where can I fine the package.  I do have all the extra repositories enabled.


NEVER MIND, I found it...

---

### Post by crjackson on 2007-09-28
> **crjackson said:**
> I can't find libusb-dev 2:0.1.12-2 in synaptic.  I'm using ubuntu 7.04 64-bit.  Where can I fine the package.  I do have all the extra repositories enabled.


NEVER MIND, I found it...

Well I found it and installed it.  Mine does the same old thing.  The scanner seems to be operating but the light never comes on and I only get a black image every time.

---

### Post by crjackson on 2007-09-28
Well, I thought it was scanning but the light wasn't coming on, but I was wrong.  Even though there is a progressively moving black scan on the screen there isn't any scanner activity at all.  Back to square 1.

---

### Post by gewitty on 2007-09-28
This may not go down well with the purists, but I got my Epson working today. I installed VirtualBox, then mounted WIn XP as a guest OS. With VirtualBox properly set up to recognise peripherals connected to the Ubuntu box, XP spotted the scanner as a new device and asked for the install disk. Once this was run, the scanner worked perfectly.

I know it's a long-winded solution - but when all else fails .........

---

### Post by crjackson on 2007-09-28
> **gewitty said:**
> This may not go down well with the purists, but I got my Epson working today. I installed VirtualBox, then mounted WIn XP as a guest OS. With VirtualBox properly set up to recognise peripherals connected to the Ubuntu box, XP spotted the scanner as a new device and asked for the install disk. Once this was run, the scanner worked perfectly.

I know it's a long-winded solution - but when all else fails .........

I would do that but I had other issues with VirtualBox and my floppy drive.  I've got 2 other scanners but they are BOTH usb, so I guess that means they too would have the same problem.

---

### Post by mikeescott on 2007-09-28
> **crjackson said:**
> Well, I thought it was scanning but the light wasn't coming on, but I was wrong.  Even though there is a progressively moving black scan on the screen there isn't any scanner activity at all.  Back to square 1.


Did you install the backends from Sane?

---

### Post by crjackson on 2007-09-28
> **mikeescott said:**
> Did you install the backends from Sane?

No I sure didn't, is that installable from synaptic?

---

### Post by crjackson on 2007-09-29
> **mikeescott said:**
> Did you install the backends from Sane?

Okay, I installed the backends.  Made no difference at all...

---

### Post by crjackson on 2007-09-29
> **parsim said:**
> A "me too" with a Canon LIDE 25. Just one scan from XSane. But "scanimage" works fine, so I've been doing all my scanning with:
```
scanimage -x 210 -y 290 --resolution 200 --mode Color > output.pmn
```
... and then edit in Gimp.

After installing the backends, I can actually use this command.  It's not very appealing but it is functional.

I wish I could get my dell 1600n multi-function laser printer/scanner to work.

---

### Post by gewitty on 2007-09-29
Following the successful installation of the Epson Perfection 1670 scanner using VirtualBox and Win XP, I discovered that it now also works with XSane (I still need to run scanbuttond first), so I guess that the firmware was corrupted and has now been reinstalled whilst running under XP.

It's not a perfect solution, but it will keep me going until the problem in Ubuntu gets sorted.

---

### Post by Unterseeboot_234 on 2007-10-09
Thanks Forum. I was sure I had originally a plug-n-play CanoScan LIDE 25. I now know it was Ubuntu Drake that made that possible. Reformatting my main drive and installing Feisty took away my scanner. The Forum had good patch ideas for the problem this time.

---

### Post by Snyper64 on 2007-10-23
Well I can confirm that my canoscan N650u now works in Gutsy(it didn't work in Fiesty) so it seem like they fixed the problem. Happy scanning.

---

### Post by gewitty on 2007-10-23
I just installed Gutsy and it seems to have resolved a number of hardware issues (my HP printer now works without having to use TurboPrint). However, I still can't get my scanner going. I don't think this is necessarily a problem with 7.10, I suspect that with all the messing around I've done trying to get it going with Feisty, I've screwed the firmware. I have the original Windows install disk for the machine, but have no idea how I can re-install the firmware using Ubuntu.

Anyone got a solution to this?

---

### Post by crjackson on 2007-10-23
My LiDE 20 scanner works perfectly under Gutsy.  My Dell 1600n printer works fine for printing but it's scanner isn't detected.

---

### Post by Seq83 on 2007-10-30
Is CanoScan LiDe25 workin now in Gutsy out of box?

---

### Post by t2000kw on 2007-10-30
Yes. At least it is for most people. I haven't seen complaints. It even set up my Canon i850 printer on a fresh install (not an upgrade). 

If you are upgrading and have a customized install, watch out for problems! Back up your /home partition (or directory) and if you have a separate partition for that, don't format it. If you don't, consider making one if you do a fresh install. 

I had enough problems trying to do the upgrade that I ended up just burning a disc and having a fresh installation.

If you used Automatix, you have a customized installation. If you used it a lot, that would qualify for a highly-customized installation and it probably won't work right, if it works at all, if you choose to upgrade rather than do a fresh install. 

That might have been part of my problem. I won't use Automatix again. If Automatix can do it, you can do it another way yourself that is cleaner and less of a problem for the system. If you do everything with deb package files, you shouldn't run into much of a problem. 

I can't say that upgrading Windows was always fun or less problematic, though, so I don't want to say "Windows does this better than Linux does" or even compare it with the MAC OSX. The latest fuss on OSX is that if you do an upgrade as a regular upgrade, it can leave you with a blank screen, at least for 6 or more hours, and it might not recover. 

Every OS has advantages and disadvantages, or there wouldn't be people using them. Ubuntu is a great Linux OS among Linux OS's, and Canonical doesn't charge for us to use it like a few of them do (Xandros is one example). But try to get a legal copy of OSX or MAC for free just for the asking and see how well you do.  :-)

Donald

---

