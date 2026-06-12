---
title: "Very very new, but liking it so far"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by sandeep108 on 2007-04-29
Hi, I have been looking at making the switch to Open Source since some time, using FF/TB since quite some time and also getting things setup in OO. Seeing that Vista does not seem the path for me and that linux has been evolving quite rapidly, I intend to (at least for my SOHO work environment) setup linux PCs. The new release of ubuntu/kubuntu seems very promising in this respect, especially for users like me who have long forgotten old DOS.

I downloaded and created the Live Ubuntu CD and have the following questions: Please bear with a noob.

1. I cannot for work related reasons attempt any dual boot of XP/Ubuntu as I do not want to take any chance of anything going wrong. I do have a second HDD spare. Can I disable the XP HDD from bios and install Ubuntu on the second one (and vice versa) as required? This will allow me to experiment and setup the required software / settings during when I have some spare time to help make a complete switch. I do not have the luxury of a spare PC with similar peripherals. Otherwise should I try installing it on a USB pendrive?
2. When I ran the live CD, it is not able to enable the nVidia driver through restricted driver manager. I have a 6600GT. I can try and enable as per a couple of guides here, once I set it up on the second HDD. Otherwise it correctly enables 1280x1024@60Hz for my 19” LCD.
3. I use foobar2000 as my music player (love it and its direct output / channel mixer sounds really great on my 5.1 HT system. Is the built it player / sound card drivers able to perform similarly? I have a creative audigy 2.
4. I use Outlook / Nokia PC suite for my symbian mobile phone. I sync calendar and contacts. What are the alternatives available to me on Ubuntu/Kubuntu? Can I use Evolution Calendar/ contacts? What about the rest of PC suite – e.g. installing programs, backups, firmware updates, etc. There does seem to be Gammu/Wammu, but it does seem quite limited. For backups / firmware, I can use my XP PC at home, but rest obviously is better done at work.
5. My connected printers show up when I search for connected printers, however there are 2 entries e.g. HP 930C and HP 930C QX115N or something similar. Which should I select? Do I need to install any HP linux drivers for this or a laserjet?
6. Can I get my multimedia KB special buttons to work? Can I get my Trackball explorer 4+clickable scroll wheel to work? 
7. I believe Firestarter is a good GUI firewall. What else do I need for security? I have 2 LAN cards – one connected to the Internet and one to my work LAN. None of the other PCs need Internet access.

Sorry for all the questions, if you feel I need to search more, just say so. TIA.

Also the bootable CD showed 1 file having an error - can I just go ahead and install and then update or re-burn the iso?

---

### Post by viciouslime on 2007-04-29
1. This should work fine.

2. It isn't possible to enable the restricted driver on the live cd as it requires a reboot :)

3. From what I have read the creative audigy 2 has excellent linux support, but I don't have one myself.

4. This is a little bit more tricky, I also have a nokia running symbian (6680) and getting it to sync with evolution wasn't the easiest thing in the world last time I tried, however, it is possible and getting better all the time. There are loads of guides on the forums and googling will produce plenty of results too. I'd post some links for you, but I can't remember any of them. Be assured though, there are plenty out there.

5. I have also noticed this with HP printers, I believe it is something to do with the HP driver that ships with ubuntu, basically you can choose to use it, or the gutenprint driver I think. The HP one probably has a few more features, so I would choose that. You won't need to install any additional drivers, as there are already two available for your printer :)

6. Almost certainly yes on the multimedia keyboard buttons. Go to System/Preferences/Keyboard Shortcuts and try setting it up there. if your key presses aren't detected it is probably still possible to get it working, but may require considerably more effort. We would need more info, keyboard make/model etc. as for the mouse, I'm afraid I don't know, but I shouldn't imagine it is too difficult a task.

7. Nothing really, I don't even use a firewall under linux, my router acts as a hardware firewall anyway and it is so much more secure than windows by fundamental design, that you don't really need anything installing additionally.

As for the error, I would check the md5sum of the ISO to make sure it isn't corrupt, then reburn.

Hope that's of some help :D

---

### Post by sandeep108 on 2007-04-29
Hey thanks, that was a pretty fast response and quite helpful/encouraging too. After my install, I am sure I will be back to bother you guys again...! In the meantime...:

1. I must make sure to disable the appropriate HDD, right? What if by mistake I leave both enabled? I hope it will not cause any permanent damage to either installation and just a sort of crash...?

2. Great, so on install the nVidia driver will be installed automatically, right?

3. Nice to hear. 

4. I need not necessarily sync with Evolution. It is just that Evolution was there already. In fact I may end up using what I am already using - T'bird. But then I will need another calendar program. How about Mozilla's Sun? Any other suggestions? 

5. Yes, but which one to choose? the one with the model name and other number on it or just the model name? I guess I can always uninstall and choose the other one if I do not get the same options / features. I can also share printers right? The LJ connected to my PC is shared on the LAN.

6. Ok on the KB. I did read somewhere about changing the xconf for a 4 button mouse. Will search some more.

7. No need of a firewall? I am on an ADSL ISP with a modem/router so yes, but I have been so used to Sygate Personal Firewall allowing me exact control of what can access the network or not that... Of course, just like with XP, with Ubuntu also I should run as a limited user, right? I should only log in as admin when I need to update/install programs, etc.?

What about kubuntu/ubuntu? I liked the ubuntu desktop also, but maybe I should look at kubuntu as well for my other assistants used to windows.

Edit: The md5sum is different, so I guess the iso file itself is corrupted...now to download again

---

### Post by thefoolisme on 2007-04-29
> **sandeep108 said:**
> Hey thanks, that was a pretty fast response and quite helpful/encouraging too. After my install, I am sure I will be back to bother you guys again...! In the meantime...:

1. I must make sure to disable the appropriate HDD, right? What if by mistake I leave both enabled? I hope it will not cause any permanent damage to either installation and just a sort of crash...?

7. No need of a firewall? I am on an ADSL ISP with a modem/router so yes, but I have been so used to Sygate Personal Firewall allowing me exact control of what can access the network or not that... Of course, just like with XP, with Ubuntu also I should run as a limited user, right? I should only log in as admin when I need to update/install programs, etc.?

What about kubuntu/ubuntu? I liked the ubuntu desktop also, but maybe I should look at kubuntu as well for my other assistants used to windows.

Edit: The md5sum is different, so I guess the iso file itself is corrupted...now to download again

In regards to #1, make sure you back up your important files.  That way if you make a mistake, you won't lose the files. :-)  

In regards to #7, yes, you would only log in as the root when you needed to make administrative changes.  Linux is built differently, and is much safer than XP.  You'll find that most don't even use an anti-virus here.  There's just no need.  Most routers have a hardware firewall to help protect you.  Do you know if your modem/router has one?  

If the MD5 is different, then the ISO itself has a problem.  Redownload, burn at the slowest speed possible (recommended is 4x, I got away with a 12x burn).  Before installing, also use the check disk option in the opening menu.  I had a live CD that worked fine, but had errors from the burn that would not allow it to install.  

The whole Ubuntu/Kubuntu question for former Windows users has been debated extensively on these forums and elsewhere.  Personally, as a life-time windows user, I had no issues using the Gnome desktop over KDE, but it's really a matter of preference.  Perhaps you should try them both out using live CDs and decide which desktop you like better.  Ive read that you can install the KDE desktop in Ubuntu, and vice-versa, but I haven't tried.  It might be a matter of whether you prefer the KDE software packages, but then, they say you can still run the KDE software in Gnome.  I've only run a couple of the KDE packages in Gnome, but I haven't had any issues.  

Youll find these forums are full of great people who will answer your questions quickly, as a rule.  Just remember to give them as much info as possible when asking, so they can help you more quickly.  

Good luck, and have fun!  Just expect a slight learning curve.  It is different, it's not Windows.  Don't expect it to be, and I think you'll really enjoy it.  I've been using Ubuntu for about a month or so now, and I absolutely love it.  :KS

---

### Post by viciouslime on 2007-04-29
> **thefoolisme said:**
> In regards to #1, make sure you back up your important files.  That way if you make a mistake, you won't lose the files. :-)  

In regards to #7, yes, you would only log in as the root when you needed to make administrative changes.  ...

Actually I'd have to disagree and say never log in as root. I never have in ubuntu, you don't need to thanks to sudo. Whenever you want to make an administrative change you will be prompted for your password, without your password it is impossible for you, or anyone/thing else for that matter, to make such a change.

The nvidia driver won't be installed automatically as it is proprietary, however, it is installed very easily by going to System/Administration/Restricted Drivers Manager Then all you do is tick the box and press ok.

As for the printer I think it is the one with the model name AND other number that uses the more advanced driver, so go with that. I can't be sure of that though.

As for kubuntu, personally I hate it, but linux is all about choice so yes, you should defo try it out, you might just like to try the live cd and see what you think. To be quite honest, I hate KDE all round, but kubuntu doesn't really do it justice, in my opinion it is one of the worst kde distros, it just isn't very well polished, it feels quite a way behind ubuntu, hopefully the gap will narrow with each future release though :)

---

### Post by sandeep108 on 2007-04-30
In regard to #7, yes NAT and Firewall are both enabled in my ADSL router/modem connection properties page. I quite liked the ubuntu live CD. If as you guys feel it is a bit behind ubuntu, maybe I will just stick with ubuntu. I hope I get some time next weekend. This one was more hectic than a workday!

---

### Post by rillip on 2007-04-30
In regards to Kubuntu, I haven't used another kde distroy, so I can't say as to how it compares.  I personally like it.

As for being "behind", keep in mind that they're just using a different application suite, kde apps by default instead of gnome.  The actual meat of Ubuntu/Kubuntu is exactly the same.  I think the "behind"ness that is being referred to is that it doesn't feel as "polished" as Gnome/Ubuntu feels to others.

If you have both HDD's enabled, you'll end up booting whichever one the Bios is set to use, which is most likely hd0, This would typically be the first drive you have plugged in, so your Windows boot.

---

### Post by SuperAndy on 2007-04-30
can i just say, about 1...

I tried doing this, well, i made the drive i was installing ubuntu on the primary, so the main boot partition was on this drive. although, ubuntu still installed grub on the drive that had the windows boot loader on. It did find windows fine though.

And if you have windows XP, and anything does go wrong, just put the CD in, go to the recovery console, and type FIXMBR.

that gets rid of grub, and allows you to boot straight back into windows.

---

### Post by sandeep108 on 2007-05-01
> **SuperAndy said:**
> can i just say, about 1...

I tried doing this, well, i made the drive i was installing ubuntu on the primary, so the main boot partition was on this drive. although, ubuntu still installed grub on the drive that had the windows boot loader on. It did find windows fine though.

And if you have windows XP, and anything does go wrong, just put the CD in, go to the recovery console, and type FIXMBR.

that gets rid of grub, and allows you to boot straight back into windows.
Thanks for the tip, but how would it find the drive if I disabled it in bios itself? As others have suggested in these forums, it may be better to run off the Live CD itself till one is comfortable making the switch. OO runs, FF runs, well I could use webmail for the time being, I can get at all my unencrypted files to work on in OO, but problem is installing the display, printer, etc. drivers, codecs for multimedia and quite important find a decent calendar program that will sync with my E50. This will require me to install it on a HDD, which I can enable during weekends or when I have a couple of spare hours to play with. 

From what I see, at least I have some reasonable easy alternative to MS Vista/Office 2007 for my next PCs at work. I intend to start my assistant(s) on OO, slowly weaning them away from MS Off97 (yes - see no need to pay MS to upgrade!)

---

### Post by sandeep108 on 2007-05-08
Well, finally I got the time and installed it switching HDDs in the bios - seems working ok, except for some minor (major?) issues.
1. On update it gave an error of network problems or incorrect address of repository index. It seems to have disappeared when I selected the main server in update preferences. Any other server I can use that may be less congested?
2. On enabling desktop effects of showing workspaces in cubes, once it hanged.
3. I tried to manually update using the code: "sudo aptitude update". After asking for the password it gave an error message: segmentation fault (core dumped). What is this and why should this happen? I think the CD may not be kosher.
4. Does this require an uninstall / reinstall of Feisty Fawn? If I need to uninstall Feisty Fawn what do I need to do?

---

### Post by ramjet_1953 on 2007-05-08
One point that hasn't been mentioned is that by default, Linux has a built-in firewall. It's called iptables and should not need any altering. It is very secure and no ports are left open. That is only one of the reasons why Linux is far more secure than Windows.

You will hear of people talking about a package called firestarter, as though it is a firewall. It is not. It is a GUI tool for configuring iptables. Unless you have very good reasons to do so, iptables is best left well alone.

Also others will want to set-up firestarter, so that it automatically loads on startup.
This is not a wise thing to do, as firestarter runs in root-mode and it is a security risk to run it continually.

Regards,
Roger :cool:

---

### Post by sandeep108 on 2007-05-08
Thanks for the tip about Firestarter. Yes, I did know that unlike Windows, by default all ports are closed in Linux.

I also did have some trouble getting sound to work - it seemed all I had to do was bump up the volume. Also for surround+sub, I had to enable the controls for Centre/Rear/LFE and increase them. That alsamixer is quite a neat piece of work! 

Now to resolve the segmentation fault issue.

If the CD is bad - I checked - one file shows an error, how can I check and replace that file? (similar to windows sfc/scannow instead of uninstalling, re-downloading and hoping - new CD, check and reinstall?

---

### Post by steve.horsley on 2007-05-08
Regards the firewall:
I have to comment on what ramjet_1953 said. Yes, iptables is installed by default, and it is **the** firewall, to which firestarter, guarddog and others are merely pretty front-end configuration tools. Also, yes, Linux has all ports closed by default. 

But the closed ports are nothing to do with iptables. The ports are closed because there are no network services enabled by default. In fact, the default iptables configuration is to allow everything, and I think that saying a firewall is installed by default, while literally true, is rather misleading.

I don't think I would trust an install from a bad CD - how cah you be sure other files weren't mis-read during the install. Sorry, but I would be inclined to reinstall. The easiest way would be to use the live installer CD, start gparted first, and delete the current Linux partitions, then tell the installer to install into the un-allocated space. BEWARE: the GRUB bootloader relies on files in the Linux system partition, so until you complete the re-install, the PC will not be bootable into either Linux or Windows.

---

### Post by sandeep108 on 2007-05-08
> **steve.horsley said:**
> Regards the firewall:
I have to comment on what ramjet_1953 said. Yes, iptables is installed by default, and it is **the** firewall, to which firestarter, guarddog and others are merely pretty front-end configuration tools. Also, yes, Linux has all ports closed by default. 

But the closed ports are nothing to do with iptables. The ports are closed because there are no network services enabled by default. In fact, the default iptables configuration is to allow everything, and I think that saying a firewall is installed by default, while literally true, is rather misleading.
Then do I need to install Firestarter? or have a firewall?

> **steve.horsley said:**
> I don't think I would trust an install from a bad CD - how cah you be sure other files weren't mis-read during the install. Sorry, but I would be inclined to reinstall. 
Sigh....
> **steve.horsley said:**
> The easiest way would be to use the live installer CD, start gparted first, and delete the current Linux partitions, then tell the installer to install into the un-allocated space. BEWARE: the GRUB bootloader relies on files in the Linux system partition, so until you complete the re-install, the PC will not be bootable into either Linux or Windows.
So from the Live CD splash screen I start gparted? Or do I just use the partition dialog during the install? Thanks for the warning, but it is in any case a spare HDD, but yes it would nice not to bother to re-install XP on it or my backed up data.

Maybe for now just for getting basic things working I may continue with the current installation and once I am ready to jump (or I bork things up badly), I will re-download/re-burn/re-install.

---

### Post by hyper_ch on 2007-05-08
You don't ahve to install firestarter... so far I've had no need for it...

Use the partitioner during install... it's simple... but it's up to you...

Make at least 3 partitions:

(1) Type: SWAP about twice the size of your ram
(2) Type: EXT3 / Mounting Point "/" about 10 GB
(3) Type: EXT3 / Mounting Point "/home" --> what's left over from your harddisk...

If you have a huge harddisk, you may want to extend the root ("/") partition a bit... it's a matter of taste... mine is set to 20 GB (out of my 500GB)

And regarding the appz... choose that distro (Dekstop Environment) that suits you best... I like simplicity and opted for Xfce (Xubuntu) however I do run quite a few KDE Appz...
They do run fine, they just are not optimized for a GTK2 environment and need to load more libraries... if you don't have a 5-year old computer then it shouldn't matter to you much either whether you use pure GTK2 or QT apps... Evolution is one PIM suite - I prefer Kontact...

---

### Post by sandeep108 on 2007-05-09
> **hyper_ch said:**
> You don't ahve to install firestarter... so far I've had no need for it...

If you have a huge harddisk, you may want to extend the root ("/") partition a bit... it's a matter of taste... mine is set to 20 GB (out of my 500GB)

And regarding the appz... choose that distro (Dekstop Environment) that suits you best... I like simplicity and opted for Xfce (Xubuntu) however I do run quite a few KDE Appz...
They do run fine, they just are not optimized for a GTK2 environment and need to load more libraries... if you don't have a 5-year old computer then it shouldn't matter to you much either whether you use pure GTK2 or QT apps... Evolution is one PIM suite - I prefer Kontact...
Thanks. About the apps - do you mean to say that I can install KDE apps on Gnome? I saw that Add/Remove programs had quite a list of KDE apps.

Another thing - it seems that apt-get works, aptitude does not. I cannot get DVDs to play. Gives me encrypted content error. After looking at the wiki guide, I did as instructed and everything went off ok, but no DVD. It said libdvdcss2 was the latest version already installed. I also installed gxine and xine-ui, but still no go. Should I add extra repositories as suggested by some sites to get a different version of the file?

I will have to search for setting up my LAN and 2 LAN cards (1 onboard nVidia chipset-LAN and 1 realtek-Internet ADSL) and access my other xp PCs...

---

### Post by hyper_ch on 2007-05-09
Yes, you can run KDE appz on Gnome... they will just load additional QT libs and hence use more ram/cpu... if you have not a 10-year-old machine you hardly won't notice a difference :)

Aptitude should also work if apt-get works... "aptitude install ..."

Dunno about the dvd...

---

### Post by BaffledMollusc on 2007-05-09
> **hyper_ch said:**
> You don't ahve to install firestarter... so far I've had no need for it...

Use the partitioner during install... it's simple... but it's up to you...

Make at least 3 partitions:

(1) Type: SWAP about twice the size of your ram
(2) Type: EXT2 / Mounting Point "/" about 10 GB
(3) Type: EXT3 / Mounting Point "/home" --> what's left over from your harddisk...

If you have a huge harddisk, you may want to extend the root ("/") partition a bit... it's a matter of taste... mine is set to 20 GB (out of my 500GB)

Why would you want EXT2 rather than EXT3 as the file system for the root?

---

### Post by hyper_ch on 2007-05-09
Oh, that's a typo... should be EXT3 :)

---

### Post by sandeep108 on 2007-05-10
> **hyper_ch said:**
> Yes, you can run KDE appz on Gnome... they will just load additional QT libs and hence use more ram/cpu... if you have not a 10-year-old machine you hardly won't notice a difference :)

Aptitude should also work if apt-get works... "aptitude install ..."

Dunno about the dvd...
Thanks for the heads up on the KDE apps. You mean I should have typed "sudo aptitude install update" instead of "sudo aptitude update"? The latter gives a segmentation fault, will try the former. 

Let me try the multimedia sticky in this forum for my DVD playback...

Would ubuntu recognise the nVidia chipset on board NIC? I saw in network manager two NICs, eth0 and eth1, so presumably it is recognised?

---

### Post by Sef on 2007-05-10
> You mean I should have typed "sudo aptitude install update" instead of "sudo aptitude update"? The latter gives a segmentation fault, will try the former.

Yes, type ```
sudo aptitude update
```.

> Would ubuntu recognise the nVidia chipset on board NIC?

Yes, they should be recognized.

---

### Post by sandeep108 on 2007-05-12
Things are looking nicer - literally - I never liked clear type for some reason on my LCD - it tended to blur more than clear - and I have been trying to get my screen and browser / open office looking like they did in XP. After a bit of searching, I could install ms core fonts and then complete the font settings much more to my liking.

I also got my trackball explorer all buttons working in FF for now it is ok. My multi media keys and some hot keys also work on my keyboard, so that is also fine. 

I got DVD playback also working with full 5.1 sound.

But Ubuntu does not like either hibernate or suspend and does not wake up from it. I have to restart the PC. It seems to leave the USB on for the KB/mouse. I can reproduce this if I log off and then at the log on screen select shutdown from the options. It does NOT shutdown, leaves KB/mouse on.

Now how do I get the following stuff working?

1. LAN. I have 4 PCs connected through a switch. I had given fixed IP addys and user names on each PC according to convenience. My PC was sort of acting like a server with the main Shared Docs on it, but I had removed the 'everyone' permissions, giving only specific users access. Similarly having set myself as a user on the other PCs, I could access them across the LAN, but nobody could locally (well if they had the Live CD they could I guess!). A second NIC connects me to the Internet using ADSL modem - auto config. I may need to enable internet connection sharing, but let us leave that out for now. It is also most likely that while on my PC I am using both, the other PCs will be switched to Ubuntu and I may continue to run XP.

How can I set up something like this on Ubuntu? I created a second user, but found that though I restricted the user (unchecked all the boxes) that user could access my files. Then in my user properties I disabled access, but then Shared Documents created there obviously cannot be accessed. It is not allowed me to create a folder anywhere other than my /home directory. Do I set up a 'Shared Docs' user?

I allowed sharing for windows networks and it installed samba, but now it only shows MSHOME in networks >Windows Network and does not allow any access to any of the other PCs. My windows workgroup is say ABC.

2. My pci card modem - D'link/motorola does not seem to be recognised. How can I install this hardware? and thereafter install basic fax software?

3. I used TB for e-mail and Outlook for calendar and syncing to my Nokia e50 symbian phone - mostly for calendar. Contacts is fine since I do not dial out from the PC, but a backup would be nice. Nokia PC Suite obviously will not work - will it work through Wine? Is Kontact a good choice or KOrganizer better? What else is available for Gnome? What would happen if I just connected the phone through the USB cable. Will ubuntu recognise it as a card reader?

I tried searching for #1 but only got confused. If I can get #1 and #3 setup, then I can make the ditch XP jump.

---

### Post by sandeep108 on 2007-05-19
bump - any ideas on how to proceed with No. 1 at least?

---

### Post by sandeep108 on 2007-06-23
Looking better and better..., somehow after the latest updates including .16 kernel, the network issues resolved themselves. I can easily browse the other windows computers on the LAN, but ironically am having problems accessing the shared folder on the ubuntu PC! The other PCs can also now 'see' the ubuntu PC (asks for a password to connect but that I guess I just need to set in samba).

Where should I create the shared folder? At present it is in my home folder since I am not able to create folders anywhere else.

Now to try and set up calendar/contacts/data sync with my Nokia e50...

---

