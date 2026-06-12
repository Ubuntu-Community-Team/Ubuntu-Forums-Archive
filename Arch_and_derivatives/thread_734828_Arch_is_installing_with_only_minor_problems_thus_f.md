---
title: "Arch is installing with only minor problems thus far..."
date: 2008-03-25
forum: Arch and derivatives
---

### Post by handy on 2008-03-25
Gnome is downloading at the moment, I'll see what problems arrive when I try to start it up.

---

### Post by Lord Illidan on 2008-03-25
You shouldn't have any problems if X installed correctly. Are you using the Beginner's Guide? It's extremely helpful! Oh, and btw, there's Gnome 2.22 in the testing repositories, I am using it right now on Arch.

---

### Post by jgrabham on 2008-03-25
Yeah, Arch rocks... now if only I hadn't dropped my laptop and cracked the screen Id still have it running XD

Oh, and Lord Illian, you cant use bloated rubbish like GNOME in Arch, you gotta use xfce...  runs so fast its unreal =b

---

### Post by LaRoza on 2008-03-25
> **jgrabham said:**
> 
Oh, and Lord Illian, you cant use bloated rubbish like GNOME in Arch, you gotta use xfce...  runs so fast its unreal =b

What? You can't use bloated GUI's in Arch, it is so much faster and better without them.

---

### Post by odiseo77 on 2008-03-25
> **handy said:**
> Gnome is downloading at the moment, I'll see what problems arrive when I try to start it up.

If you got to the point where you're downloading Gnome, you shouldn't have any problems as long as you've installed and set up your X server properly, as Lord Illidan said. Arch is one of the most versatile and customizable distros I've tried; hope you enjoy it as much as I do :)

---

### Post by handy on 2008-03-25
> **Lord Illidan said:**
> You shouldn't have any problems if X installed correctly. Are you using the Beginner's Guide? It's extremely helpful! Oh, and btw, there's Gnome 2.22 in the testing repositories, I am using it right now on Arch.

I think X installed ok, I had the *bloated* Gnome running on the nv free drivers, though I need the proprietary nvidia drivers, which didn't work for me, & have me at the moment trying to find a way to get a command prompt before the screen goes black & stays that way. Again... :-)

***[Edit:]** Will I have to use a LiveCD & chroot to be able to edit my xorg.conf?*

---

### Post by handy on 2008-03-25
> **jgrabham said:**
> 
Oh, and Lord Illian, you cant use bloated rubbish like GNOME in Arch, you gotta use xfce...  runs so fast its unreal =b

I can use what ever I want on Arch! :lolflag:

So, can you, aren't we fortunate?

---

### Post by handy on 2008-03-25
> **odiseo77 said:**
> If you got to the point where you're downloading Gnome, you shouldn't have any problems as long as you've installed and set up your X server properly, as Lord Illidan said. Arch is one of the most versatile and customizable distros I've tried; hope you enjoy it as much as I do :)

Thanks!

I like pacman, & the whole process was so much quicker & easier than my brief experience with Gentoo, yet as you say, you only get what you want in your OS.

---

### Post by odiseo77 on 2008-03-25
> **handy said:**
> I think X installed ok, I had the *bloated* Gnome running on the nv free drivers, though I need the proprietary nvidia drivers, which didn't work for me, & have me at the moment trying to find a way to get a command prompt before the screen goes black & stays that way. Again... :-)

***[Edit:]** Will I have to use a LiveCD & chroot to be able to edit my xorg.conf?*

You can edit your xorg.conf either from a live cd or directly from Arch with ***vi*** or ***nano*** (as you prefer), but I think you can't test your X server from a live cd (obviously). 

As for the nvidia driver, there are 3 different proprietary drivers on the repos (it depends on which type of nvidia graphic card you're using).

---

### Post by handy on 2008-03-25
> **odiseo77 said:**
> You can edit your xorg.conf either from a live cd or directly from Arch with ***vi*** or ***nano*** (as you prefer), but I think you can't test your X server from a live cd (obviously). 

As for the nvidia driver, there are 3 different proprietary drivers on the repos (it depends on which type of nvidia graphic card you're using).

I installed the right driver. 

How do I get root access to edit the xorg.conf?  Do I have to it via chroot, as I have tried with knoppix DVD & can't get write privileges.

I'm about to start the battle again, will let you know what I had to do when I work it out! :lolflag:

---

### Post by Lord Illidan on 2008-03-25
Well, I like Gnome, heh :D And tbh, I find XFCE to be a touch too bland, I like some eyecandy. And Gnome doesn't take up too much RAM, too. Also, thanks to the compositing, I am now using AWN without packing Compiz Fusion into it. All said and done, I'm a happy camper. I haven't been on Ubuntu for months :S

Oh, and do try out [yaourt]("http://archlinux.fr/yaourt-en"). It's incredibly useful.

Oh and as for the root access?? Well, if you're doing it in Arch, you have to use su, and use root directly. Later, you can setup sudoers to work like it does on Ubuntu.

---

### Post by odiseo77 on 2008-03-25
> **handy said:**
> How do I get root access to edit the xorg.conf?  Do I have to it via chroot, as I have tried with knoppix DVD & can't get write privileges.

Sorry if I misunderstand you here, but you're trying to chroot Arch from the knoppix LiveDVD, right? I think from knoppix you have to type ***sudo su*** to gain root access. However, if you have another linux installation on this machine, it's more comfortable to chroot and do the remaining tasks from there.

Greetings.

---

### Post by mips on 2008-03-25
> **handy said:**
> I installed the right driver. 

How do I get root access to edit the xorg.conf?  Do I have to it via chroot, as I have tried with knoppix DVD & can't get write privileges.

I'm about to start the battle again, will let you know what I had to do when I work it out! :lolflag:

Handy,

Read the beginners or official install guide.

To get root access simplly type 'su' from cli followed by the password you selected and then enter the commands you want to access as root.

---

### Post by handy on 2008-03-25
> **mips said:**
> Handy,

Read the beginners or official install guide.

To get root access simplly type 'su' from cli followed by the password you selected and then enter the commands you want to access as root.

I can't halt the boot process (I tried ctrl + c, ctrl + d) before I get an xorg.conf caused black screen (no flashing cursor) of death.

I have been using the beginners install guide.

I just accessed the xorg.conf via booting the core install disk & using chroot.  My changes didn't work, (not that I really expected them to) but now I can continue sorting it out.  I have a variety of xorg.conf files that will work, but won't give me the nvidia closed drivers.  I may try the xorg.conf that worked so well in Sabayon & see what happens with that in Arch, it is the same machine.

---

### Post by handy on 2008-03-25
> **Lord Illidan said:**
> Well, I like Gnome, heh :D And tbh, I find XFCE to be a touch too bland, I like some eyecandy. And Gnome doesn't take up too much RAM, too. Also, thanks to the compositing, I am now using AWN without packing Compiz Fusion into it. All said and done, I'm a happy camper. I haven't been on Ubuntu for months :S

Oh, and do try out [yaourt]("http://archlinux.fr/yaourt-en"). It's incredibly useful.

Oh and as for the root access?? Well, if you're doing it in Arch, you have to use su, and use root directly. Later, you can setup sudoers to work like it does on Ubuntu.

Yes, I am obviously happy with Gnome, I've tried KDE, it is great too, but offers more than I need, KISS suits me.

I have already set up Yaourt, though I haven't had the chance to try it out yet.

I also set up sudoers, too, haven't got around to deleting the root user as yet though.

As you will see from my post above to mips, my problem has been getting past a black screen of death caused by xorg.conf.  Anyway, I'm in via chroot, so now I can continue the good fight.

---

### Post by Rumor on 2008-03-25
Try ctrl+alt+F1 to get to a virtual console. Login as root and then either nano or vi /etc/X11/xorg.conf or, ```
pacman -S hwd
hwd -u
hwd -xa
``` and then see if you can startx. hwd does a very good job at detecting and configuring your X for you.

For more info on hwd for Arch: [http://user-contributions.org/projects/hwd/hwd.html](http://user-contributions.org/projects/hwd/hwd.html)

---

### Post by handy on 2008-03-25
> **odiseo77 said:**
> Sorry if I misunderstand you here, but you're trying to chroot Arch from the knoppix LiveDVD, right? I think from knoppix you have to type ***sudo su*** to gain root access. However, if you have another linux installation on this machine, it's more comfortable to chroot and do the remaining tasks from there.

Greetings.

Knoppix does not have its own root password, it makes it difficult to write to anything.  It says how you can change the permissions on drives so you can write to them, I copied pasted & edited the correct drive into the code, but it did not work.

Anyway it is really easy to do from the Arch core install disk, so I'm past that problem now, thanks for your reply though.

---

### Post by handy on 2008-03-25
> **Rumor said:**
> Try ctrl+alt+F1 to get to a virtual console. Login as root and then either nano or vi /etc/X11/xorg.conf or, ```
pacman -S hwd
hwd -u
hwd -xa
``` and then see if you can startx. hwd does a very good job at detecting and configuring your X for you.

For more info on hwd for Arch: [http://user-contributions.org/projects/hwd/hwd.html](http://user-contributions.org/projects/hwd/hwd.html)

Thanks for your reply, but no keyboard input works to either interrupt the boot process, or to escape the black screen of death! :lolflag:

Yes I have used hwd, it works nicely, but still leaves me without functioning proprietary nvidia drivers.

I'll change back to a known bootable xorg.conf & see what I can come up with?

---

### Post by MisfitI38 on 2008-03-25
> **handy said:**
> Thanks for your reply, but no keyboard input works to either interrupt the boot process, or to escape the black screen of death! :lolflag:

Yes I have used hwd, it works nicely, but still leaves me without functioning proprietary nvidia drivers.

I'll change back to a known bootable xorg.conf & see what I can come up with?

If X is causing issues, simply boot into runlevel 3,  instead of chrooting into your Arch system.

Remove your GDM or KDM from the DAEMONS= array in /etc/rc.conf, assuming you followed the B.G.
You may also append 'single' to your GRUB kernel line, to boot into runlevel 1, if you wish.

---

### Post by handy on 2008-03-25
> **MisfitI38 said:**
> If X is causing issues, simply boot into runlevel 3,  instead of chrooting into your Arch system.

Remove your GDM or KDM from the DAEMONS= array in /etc/rc.conf, assuming you followed the B.G.
You may also append 'single' to your GRUB kernel line, to boot into runlevel 1, if you wish.

Thanks, I'll edit GRUB so the option is there for future troubles that I'm sure to make for myself. :lolflag:

---

### Post by handy on 2008-03-26
I am using an nVidia, AGP graphics card by XFX, the 7950GT.  It is a pig to setup under Linux, Ubuntu can't handle it, & I tried the restricted driver manager, using synaptic, envy & manually.

The only OS that gets it right, that I have tried is Sabayon. So I just tried transplanting the xorg.conf from Sabayon, it doesn't work either?

---

### Post by kpkeerthi on 2008-03-26
I had some trouble configuring my USB mouse with Arch (I run it on a laptop). I just booted with Ubuntu Live CD, copied xorg.conf over to flash drive and then replaced it over Arch's. Worked a charm.

---

### Post by handy on 2008-03-26
I like Arch, & really have no other problem at this stage than the graphics card, which is a shame, because my monitor's display has the tremors & I can't use the graphics card for a game that my Mac is not powerful enough to run.

Eventually this problem will be history, though I must admit to being over it at the moment, I have easily spent over 6 hours today, mostly on it.

---

### Post by finferflu on 2008-03-26
Glad to see you on Arch, handy :D

I suggest you to post your problems on the Arch forums (if you haven't already), it will be much easier to get replies. Not that the users here are not knowledgeable enough, but there you'll eventually get the devs to help you :)

As for me, I have never had anything to do with Nvidia cards, so I can't be of much help.

---

### Post by Lord Illidan on 2008-03-27
Hmm, I merely ported over Ubuntu's xorg.conf and edited it a bit. Shouldn't be hard to do so.

---

### Post by handy on 2008-03-28
As previously stated, nothing I did (& I tried everything I am aware of)  could get the card to work under Gutsy.  Even though it works straight up in multiple versions of Sabayon!?

---

### Post by fwojciec on 2008-03-28
For those people who ported the xorg.conf file from their Ubuntu install -- have a look at /var/log/Xorg.0.log file and check for warnings (WW) and/or errors (EE).  I'm pretty sure that you'll need to adjust the font paths in your xorg.conf, at least, to make everything work like it should in Arch.

---

### Post by handy on 2008-03-28
> **fwojciec said:**
> For those people who ported the xorg.conf file from their Ubuntu install -- have a look at /var/log/Xorg.0.log file and check for warnings (WW) and/or errors (EE).  I'm pretty sure that you'll need to adjust the font paths in your xorg.conf, at least, to make everything work like it should in Arch.

Yes, that thought did occur to me.  At stage of the game I was tired of the problem & left it alone.  When I go back to it I'll do some editing of the xorg.conf from Sabayon, & see if I get lucky.

---

### Post by Iandefor on 2008-03-29
Out of curiosity, Handy, how did you install the nvidia kernel module?

---

### Post by handy on 2008-03-29
> **Iandefor said:**
> Out of curiosity, Handy, how did you install the nvidia kernel module?

In Arch I followed the instructions on the beginners installation page; for the nVidia proprietary drivers they give the following command:

***depmod -a***

---

### Post by Lord Illidan on 2008-03-29
> **fwojciec said:**
> For those people who ported the xorg.conf file from their Ubuntu install -- have a look at /var/log/Xorg.0.log file and check for warnings (WW) and/or errors (EE).  I'm pretty sure that you'll need to adjust the font paths in your xorg.conf, at least, to make everything work like it should in Arch.

Yes, of course.. But it's still quite trivial to do.

> In Arch I followed the instructions on the beginners installation page; for the nVidia proprietary drivers they give the following command:

***depmod -a***

[http://wiki.archlinux.org/index.php/How_to_install_NVIDIA_driver](http://wiki.archlinux.org/index.php/How_to_install_NVIDIA_driver)

---

### Post by Iandefor on 2008-03-29
> **handy said:**
> In Arch I followed the instructions on the beginners installation page; for the nVidia proprietary drivers they give the following command:

***depmod -a***Did you do the instruction immediately before that, too? Installing the nvidia drivers?

---

### Post by handy on 2008-03-29
> **Iandefor said:**
> Did you do the instruction immediately before that, too? Installing the nvidia drivers?

Yes, but I did not worry about following the tweaking options below:
_____________

[I]It also has several options which will further specify the contents and options of the xorg.conf file. For example,

nvidia-xconfig --composite --add-argb-glx-visuals

For more detailed information, see nvidia-xconfig(1).

Some useful tweaking options in the device section are (beware that these may not work on your system):

       Option          "RenderAccel" "true"
       Option          "NoLogo" "true"
       Option          "AGPFastWrite" "true"
       Option          "EnablePageFlip" "true" [/I]
_____________________

I considered the above unnecessary or inappropriate at least to my initial install.

---

### Post by Iandefor on 2008-03-29
I've never configured an AGP card before, and don't know if there's anything special you *have* to do to make an AGP card work.

However, NVIDIA devoted [Chapter 12]("ftp://download.nvidia.com/XFree86/Linux-x86/169.12/README/chapter-12.html") of the driver's README to "Configuring AGP" and may be worth a read.

---

### Post by handy on 2008-03-29
> **Iandefor said:**
> I've never configured an AGP card before, and don't know if there's anything special you *have* to do to make an AGP card work.

However, NVIDIA [Chapter 12]("ftp://download.nvidia.com/XFree86/Linux-x86/169.12/README/chapter-12.html") of the driver's README to "Configuring AGP" and may be worth a read.

Thanks for your interest in Iandefor, I appreciate it.

I expect to enter into battle against the machine most likely tomorrow.  I will edit my font paths in the xorg.conf from Sabayon, & see if that has any effect, if not I will pursue modifying it with anything that I have learned in this thread & get seriously involved in the Arch & other documentation.  

If all else fails I'll then post in the Arch forums, whilst, (by then) all that stuff is still fresh in my mind & cross my fingers! :lolflag:

---

### Post by fwojciec on 2008-03-30
> **handy said:**
> I will edit my font paths in the xorg.conf from Sabayon, & see if that has any effect, if not I will pursue modifying it with anything that I have learned in this thread & get seriously involved in the Arch & other documentation.

Arch keeps the fonts in the /usr/share/fonts/ directory by default so the trick is to navigate to that directory and to make sure that every directory inside that directory is listed in xorg.conf.  The fonts section in my xorg.conf looks like this, for example:
> Section "Files"
	FontPath	"/usr/share/fonts/misc"
	FontPath	"/usr/share/fonts/cyrillic"
	FontPath	"/usr/share/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/Type1"
	FontPath	"/usr/share/fonts/100dpi"
	FontPath	"/usr/share/fonts/75dpi"
	FontPath	"/usr/share/fonts/TTF"
	FontPath	"/usr/share/fonts/OTF"
    FontPath	"/usr/share/fonts/artwiz-fonts"
	FontPath	"/usr/share/fonts/local"
EndSection
You may not need all of those in your xorg.conf, but this should get you an idea of what it should look like...  You might also need to navigate to some of those directories and to run "mkfontdir" command (as root) inside them if there are messages in the Xorg.0.log file that tell you to do that.

---

### Post by handy on 2008-03-30
> **fwojciec said:**
> Arch keeps the fonts in the /usr/share/fonts/ directory by default so the trick is to navigate to that directory and to make sure that every directory inside that directory is listed in xorg.conf.  The fonts section in my xorg.conf looks like this, for example:

You may not need all of those in your xorg.conf, but this should get you an idea of what it should look like...  You might also need to navigate to some of those directories and to run "mkfontdir" command (as root) inside them if there are messages in the Xorg.0.log file that tell you to do that.

Thanks fwojciec, I'm going through the fonts in my xorg.conf that runs (the non nvidia driver one) & had to do only one mkfondir.

My Xorg.0.log file now has only one EE in it & that's for ACPI which perhaps needs to be installed, but is inconsequential at the moment.

So now I'm going to modify this good xorg.conf to run the installed nvidia driver, I'll undoubtedly be reporting back no matter what the result. :-)

---

### Post by handy on 2008-03-30
Black screen of death again!

I'm looking at the Xorg.0.log & find interestingly enough that I have a ***WW warning that "the directory /usr/share/fonts/Type1" does not exist*** first thing before anything else to do with the fonts is recorded.

Then scrolling down the log, I find in the loading modules section see that I have an ***EE error on loading module "type1", which also does not exist?***

Apart from the inconsequential ACPI error there are no others, so to my very ignorant of the in depth workings of Linux mind, this module could be where its at.

Now I will endeavor to discover what a type1 module does & how to get one so I can load it.

---

### Post by handy on 2008-03-31
Hmmm, the type1 module is just a red herring, there is no need for it to be in the xorg.conf load modules section, it is redundant.

So it looks like I'll have to post in the Arch forums I think, I'm sure this is so easy to fix once you know how too...

---

### Post by handy on 2008-03-31
Having looked in the Arch forums, people have been having this problem with arch at least since 2006.  Many could never get their machines to run the proprietary nVidia drivers & had to go elsewhere.

It would seem that it is a kernel problem?

I have not given up, but I can't post on the Arch forum because even though I can log in it looses my login by the time I'm back to where I want to post.

Anyway, history is the perfect place to store problems. ;-)

---

### Post by handy on 2008-03-31
Just for fun I changed the Option "NvAgp" "1" to 2, thinking I'll go through them from 0 to 3, after reading someone on the Arch forums recommendation.

Anyway, from root, I did a startx & got a my first flash of the nVidia logo start screen which then went to 3 xterm windows.

I'm looking at the Xorg.0.log & see a warning I have not seen before, it may mean something to one of you? :

(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-1

(WW) NVIDIA(0): Unable to get diplay device CRT-1's EDID; cannot compute DPI from CRT-1's EDID.

It then says that it is setting DPI to (75, 75) 

Though it is just as likely from an error of mine in the xorg.conf, but it has not been seen before.

---

### Post by handy on 2008-03-31
[CENTER]:guitar: [SIZE="3"]SUCCESS!!![/SIZE] :guitar:[/CENTER]

My AGP nVidia 7950 GT needed the following (the bold line) in the xorg.conf:

[I]Section "Device"
    Identifier    "VideoCard0"
    Driver        "nvidia"
    VendorName    "NVIDIA Corporation"
    BoardName    "Geforce 7950 GT"
***    Option     "NvAgp"     "_0_"***
    Option    "NoLogo"    "true"
EndSection[/I]

None of the tools that I used to create the xorg.conf even put the critical ***NvAgp*** line in the file.  Then when I did see it in someone else's xorg.conf I gathered that AGP should be number "1".  Perhaps incorrectly?  Though that is the number they were successfully using on an 8x AGP nVidia card.

Someone may be able to tell me where the responsibility for this problem lies? Is due to graphics card manufacture, the nVidia driver, or  is it involved in the kernel?

Really it should not take 12 hours to find such a simple answer.  Though I'm sure many of you would have sorted it out a great deal quicker than I did.

Anyway, I'm happy, I CAN now use Arch, it has taught me a few things during the installation & dealing with this ***minor*** problem... :lolflag:

Thanks to everyone for taking the time to offer your assistance, I learned from all of you.

---

### Post by Lord Illidan on 2008-03-31
Good for you mate. 

Seems rather funny, you disabled AGP over there!!

[ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-d.html](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-d.html)

---

### Post by handy on 2008-03-31
> **Lord Illidan said:**
> Good for you mate. 

Seems rather funny, you disabled AGP over there!!

[ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-d.html](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-d.html)

Hey, thanks! :-)

Thanks for that great link also, I need that knowledge.

Perhaps the reason may be that the 7950gt was initially intended to be a PCE-X GPU that XFX hacked together as an AGP card for those of us that don't want to buy a new motherboard, CPU, RAM just to be able to get a graphics card good enough to play a game or two.

I tend to think that this card being AGP may be a big part of the problem,  I have talked to others on the forums here who have the PCI-X version & don't have any trouble installing the proprietary nVidia drivers on Ubuntu for it.

---

### Post by mips on 2008-03-31
handy,

Your above explanation sounds very plausible to me seeing it was never intended to be an AGP card.

The good thing is you found a solution! As far as I remember you also had the same problem with some other distros? As least in future you know how to get around this problem if it ever occurs again.

Welcome to the Arch club, I think you will stay for a long time.

>   - Option "NvAGP" "0"       Disable AGP
  - Option "NvAGP" "1"       Use NVIDIA's AGP GART Driver
  - Option "NvAGP" "2"       Use the OS AGP GART driver (agp.ko)
  - Option "NvAGP" "3"       Attempt "2", fall back to "1"

---

### Post by handy on 2008-03-31
Thanks mips! :)

Yes, at this early stage I have found so many things that I like about Arch.  I obviously have a lot to learn, though I think it may be an excellent teacher of Linux.

Last night I wanted to install NeroLinux (it is still the most reliable for my hardware) so I tried pacman, no go, then I tried yaourt & the latest version only a day or so old was available & easily installed!  Very impressive.

Regarding the graphics card, yes you are right it has given me a lot of trouble with all but Sabayon.  The interesting thing is that Sabayon don't have that Option line that turns off AGP in the xorg.conf??  

Perhaps Sabayon has something in the kernel or a module to handle the problem.  It is a mystery that I doubt Fabio has the time or interest in to explain it to me.  I have Gutsy in a drive draw that I will get around to booting up & testing the NvAGP 0 line on. 

I just thought that I may try to run this one past TSEliot, he may benefit from the knowledge & he may even have an explanation?

I will attempt to install CrossOver Games on Arch today & see if I can get DVDShrink to run on it.  I suspect that I will have to install lib32 or whatever it/they are called for CrossOver?  Time will tell.

Talk to you later mips.

---

### Post by mips on 2008-04-01
Yes, running it by Fabio and Alberto is probably a good idea, hopefully they could explain it. Hmm, I just relalised they are both Italian :)

---

### Post by handy on 2008-04-01
Wine & DVDShrink went on beautifully.

I have just installed CrossOver Games, & am fiddling around to get Guild Wars to run.

The only thing I haven't sorted out is my TCP ports, I tried adapting frodon's how-to but things are quite a bit different under the skin between a Debian base & Arch.  

I looked at firewall builder, great software, though it seems like it is far more than I need to just open a port for torrents.  I'll use it if I ever build a machine as a firewall/poxy for the house, but really I think that is overkill for a LAN that usually has no more than 4 nodes. 

I can't log into the Arch forum for some reason I've notified them so its just a matter of time.

I'm thinking I might have a go at installing Arch on my iMac tomorrow, it should be interesting, it will be nice to see how fast the Mac can go!   Provided the Mac & Arch are compatible.

***[Edit:] ** I was writing this & doing other stuff, when you posted mips, yes I'll try to communicate with Fabio, I'm sure Alberto will be much easier & hopefully less time stressed than Fabio.*

---

### Post by mips on 2008-04-01
For firewalls see:
[http://wiki.archlinux.org/index.php/Firewalls](http://wiki.archlinux.org/index.php/Firewalls)
[http://wiki.archlinux.org/index.php/Simple_stateful_firewall_HOWTO](http://wiki.archlinux.org/index.php/Simple_stateful_firewall_HOWTO)


Dunno if your Mac is intel or PPC but this is for PPC:
[http://www.archlinuxppc.org/](http://www.archlinuxppc.org/)
[http://wiki.archlinux.org/index.php/Category:PowerPC_(English](http://wiki.archlinux.org/index.php/Category:PowerPC_(English))

---

### Post by handy on 2008-04-01
> **mips said:**
> For firewalls see:
[http://wiki.archlinux.org/index.php/Firewalls](http://wiki.archlinux.org/index.php/Firewalls)
[http://wiki.archlinux.org/index.php/Simple_stateful_firewall_HOWTO](http://wiki.archlinux.org/index.php/Simple_stateful_firewall_HOWTO)


Dunno if your Mac is intel or PPC but this is for PPC:
[http://www.archlinuxppc.org/](http://www.archlinuxppc.org/)
[http://wiki.archlinux.org/index.php/Category:PowerPC_(English](http://wiki.archlinux.org/index.php/Category:PowerPC_(English))

Thanks mips, I've just been scanning all the how-to's on the Arch wiki. I saw that there is plenty for me to get into there, found the firewall page too.  Thanks for posting the link, I'll check it out after I sleep.

My iMac is intel core2duo.

---

### Post by mips on 2008-04-02
> **handy said:**
> 
My iMac is intel core2duo.

Then you should be just fine.

---

### Post by handy on 2008-05-19
Here is a link to a guide I wrote that is now in the Arch wiki, it is about installing & setting up Arch, Gnome, essential software, graphics drivers & sound on the first model (07) aluminium iMacs:

***_[http://wiki.archlinux.org/index.php/IMac_Aluminium](http://wiki.archlinux.org/index.php/IMac_Aluminium)_***

---

