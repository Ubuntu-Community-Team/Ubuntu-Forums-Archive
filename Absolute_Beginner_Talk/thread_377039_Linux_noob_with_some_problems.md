---
title: "Linux noob with some problems"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Ozor Mox on 2007-03-05
I've been wanting to switch from Windows to Linux for quite a while now and at the weekend I finally did it by installing Ubuntu as the only operating system on my Dell Latitude D600 laptop. I actually found myself having more success than I thought I would, although I've had a number of problems...

1. I still don't entirely understand installing software on Ubuntu. I've got as far as Linux doesn't have exes or setup programs, but instead has the repositories or compiling for oneself. That's all fine, except all the applications I want are from several versions ago in the repositories, even with them all enabled, and apparently compiling is going to land me in all sorts of dependency trouble.

Are the repositories out of date because I am running Dapper? Should I be upgrading?

I understand that Linux has a different system of installing software to Windows, but why is it that I can download a nice easy package for Firefox 2.0.0.2 from the Mozilla website to install on Windows, and yet on the Ubuntu repository I get version 1.5.0.10 or something or I have to try and compile it myself? Again, is this because my version is out of date?

2. If I do upgrade, do I need to format? Will I need to burn a new CD?

3. My wireless card doesn't work. This is still a work in progress...I found a thread on getting it to work using Windows drivers that went on for about 6 pages. Is it really this difficult? I wasn't expecting an easy ride by any means, but if there's anything I can do to help myself out...maybe updating to a newer version would help with some hardware?

4. MP3s and videos don't play...can anyone point me towards codecs?

5. Does checking all the boxes in the repository settings enable me to all available software? (I found everything I wanted, just not at the latest versions)

I feel like I'm venting a bit here, I'm just feeling a bit of frustration as I'm sure is to be expected going from Windows-only heathen to Linux. I really like what I've seen of Ubuntu and I'm prepared to give it as good a go as I can as I am not looking to switch back to Windows unless I really can't get Ubuntu working as I want it.

---

### Post by Doomedelite on 2007-03-05
First of all, welcome to the club!

1) Don't worry about upgrading, it has long term support, all the packages are up-to-date. They only put software on their list that is tested.
2) You don't need to format or burn a new CD, it's done through your computer, and updates itself, with a simple machine restart at the end. All of your files will be untouched (not sure about config files, but anything else will remain the same)
3) Wireless is a big issue, not sure what has been updated with the Edgy Eft (6.10) release. I'm more or less new myself =P
4) In the Add/Remove Applications menu, search "mp3" and then some codecs/players will pop up. Read up about all of them to get a better idea of what they do.
5) I honestly don't know muhc about all the repositories, so take this with a huge grain of salt (Like ten grains stuck together), but anything that is not in the official repository *might* not work or might cause crashes/freezes etc. because it's not tested. It is all the available software that those repositories allow you to have, but keep in mind there are "third-party" repositories which you can add (I THINK). Try searching these forums, much information lies here.
I made the switch around a week ago, and I've learned much about how Ubuntu operates compared to windows. It takes time to get used to, but overall, I'm extremely happy that I've switched. And I'm a gamer!

---

### Post by annda on 2007-03-05
yes, dapper software is a little "behind". if you want to have an easy installation of FF2 & co. an upgrade to edgy is a good idea. you won't need to format or burn anything. i forgot how it can be done using a simple command but search or google for edgy upgrade.

mp3 is not open source. ubuntu wants to stay as close to that as possible (no longer with feisty), so you have to do it manually.

here's a good guide:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Codecs)

you may want to ckeck out automatix - it gives you extra repositories with extra applications including mulimedia support:
[www.getautomatix.com](www.getautomatix.com)

and stick around - it probably took months to learn how to windows, so give ubuntu a couple of weeks and you won't regret it.

when you have problems, post them here with as much info as you can give. some of us are experts, some are not. but we like to help as much as we can. i think this is the ubuntu way :-)

---

### Post by Gerard Barberi on 2007-03-05
> **Ozor Mox said:**
> 1. I still don't entirely understand installing software on Ubuntu. I've got as far as Linux doesn't have exes or setup programs, but instead has the repositories or compiling for oneself. That's all fine, except all the applications I want are from several versions ago in the repositories, even with them all enabled, and apparently compiling is going to land me in all sorts of dependency trouble.

Are the repositories out of date because I am running Dapper? Should I be upgrading?

Only if you want to upgrade.  Ubuntu can install packages from the repos, compile source packages, some binaries, and .deb packages(which are what is in the repo).  What apps are you looking for?

here some install guides:

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

> **Ozor Mox said:**
> I understand that Linux has a different system of installing software to Windows, but why is it that I can download a nice easy package for Firefox 2.0.0.2 from the Mozilla website to install on Windows, and yet on the Ubuntu repository I get version 1.5.0.10 or something or I have to try and compile it myself? Again, is this because my version is out of date?

Edgy runs with firefox 2.0, dapper runs a step behind with 1.5(more stable, my opinion).
If you want 2.0, try swiftfox.  Easy to install.

[http://getswiftfox.com/releases.htm](http://getswiftfox.com/releases.htm)

> **Ozor Mox said:**
> 2. If I do upgrade, do I need to format? Will I need to burn a new CD?

[http://ubuntuguide.org/wiki/Dapper#How_to_upgrade_from_Dapper_Drake_to_Edgy_Eft_.28experimental.29](http://ubuntuguide.org/wiki/Dapper#How_to_upgrade_from_Dapper_Drake_to_Edgy_Eft_.28experimental.29)
NOTE!!:  SUB aptitude for apt-get.

> **Ozor Mox said:**
> 3. My wireless card doesn't work. This is still a work in progress...I found a thread on getting it to work using Windows drivers that went on for about 6 pages. Is it really this difficult? I wasn't expecting an easy ride by any means, but if there's anything I can do to help myself out...maybe updating to a newer version would help with some hardware?

Try the ndiswrapper
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)


> **Ozor Mox said:**
> 4. MP3s and videos don't play...can anyone point me towards codecs?

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu](http://ubuntuguide.org/wiki/Dapper#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu)
Use automatix; it's a very easy way to install these codecs.  It is also a easy way of installing a lot of other good stuff.  Eventually, you'll want to learn how to do so manually.

> **Ozor Mox said:**
> 5. Does checking all the boxes in the repository settings enable me to all available software? (I found everything I wanted, just not at the latest versions)

Latest versions are by version of Ubuntu(6.06, 6.10).  Even when there all checked, there are still other repos, just not "official"

> **Ozor Mox said:**
> I feel like I'm venting a bit here, I'm just feeling a bit of frustration as I'm sure is to be expected going from Windows-only heathen to Linux. I really like what I've seen of Ubuntu and I'm prepared to give it as good a go as I can as I am not looking to switch back to Windows unless I really can't get Ubuntu working as I want it.

Give it time:)

---

### Post by mikewhatever on 2007-03-05
Firefox is regularly updated in 6.10, so perhaps you do need to upgrade.
[http://psychocats.net/ubuntu/firefox](http://psychocats.net/ubuntu/firefox)
Stuff like skype, opera etc can be downloaded and installed, who told you not to?
> 3. My wireless card doesn't work. This is still a work in progress...I found a thread on getting it to work using Windows drivers that went on for about 6 pages. Is it really this difficult? I wasn't expecting an easy ride by any means
Yes, and will remain difficult, until the manufacturers don't help with the drivers.

MP3: [https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29)

there are more repositories, infinite number, theoretically, but since you have found all you need...

[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

I'll reveal the secret and tell you that I took most of the stuff from the link above.

---

### Post by Dr. Nick on 2007-03-05
> **Ozor Mox said:**
> I've been wanting to switch from Windows to Linux for quite a while now and at the weekend I finally did it by installing Ubuntu as the only operating system on my Dell Latitude D600 laptop. I actually found myself having more success than I thought I would, although I've had a number of problems...
 
1. I still don't entirely understand installing software on Ubuntu. I've got as far as Linux doesn't have exes or setup programs, but instead has the repositories or compiling for oneself. That's all fine, except all the applications I want are from several versions ago in the repositories, even with them all enabled, and apparently compiling is going to land me in all sorts of dependency trouble.
 
The deal with compiling or installing them from outside of the repository is that other programs may not see them. Check the programs website and see if they offer a newer deb for ubuntu.
 
> Are the repositories out of date because I am running Dapper? Should I be upgrading?
 
The dapper repos will not get the newer versions of programs, You can upgrade to edgy to get newer applications
 
> I understand that Linux has a different system of installing software to Windows, but why is it that I can download a nice easy package for Firefox 2.0.0.2 from the Mozilla website to install on Windows, and yet on the Ubuntu repository I get version 1.5.0.10 or something or I have to try and compile it myself? Again, is this because my version is out of date?
 
Actullly with firefox you can download the tar file from mozilla for v2 and run it without needint to compile
 
> 2. If I do upgrade, do I need to format? Will I need to burn a new CD?
 
Depends, You can do a online update and will not need to format anything, online updates are fine every now and then, but if you try and make a single install last through 4 or 5 versions then things can get sloppy.
 
IF you set your /home on a different partition then you can use a cd to upgrade and format while keeping personal files saved.
 
I usually web update till it crashes, then start over off a newer cd.
 
> 3. My wireless card doesn't work. This is still a work in progress...I found a thread on getting it to work using Windows drivers that went on for about 6 pages. Is it really this difficult? I wasn't expecting an easy ride by any means, but if there's anything I can do to help myself out...maybe updating to a newer version would help with some hardware?
 
 
I assmume you are using ndiswrapper, it isnt to bad if your card is supported, this is hit or miss though. Youll have better luck dealing in the thread specific to your card
> 4. MP3s and videos don't play...can anyone point me towards codecs?
 
You can use easy ubuntu or automatix applications (more info can be found with search) to install the proper codecs or look here
 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
 
> 5. Does checking all the boxes in the repository settings enable me to all available software? (I found everything I wanted, just not at the latest versions)
 
Thier are other repos out their for certain apps that must be added manually, youll stumble upon them as you go
 
Thats a overview, if you have more specific questions feel free to ask

---

### Post by Dr. Nick on 2007-03-05
WOW alot of people jumped on this fast, 0 replies when I started typing

---

### Post by Ozor Mox on 2007-03-06
Wow thanks for the extremely fast and helpful replies! What a friendly community, really makes me feel good about being on Linux and want to do my best to keep it that way!

To update you on where I am...

I've now got MP3s to play, still working on videos and DVDs. Also WAVs and WMAs don't play. I hope that is just another package from the repository? That would be very nice if it was, although I have a suspicion that a proprietary Microsoft format such as WMA will not work on Linux.

I've been looking in to upgrading to Edgy, but I can only find information for downloading and burning an ISO to a CD. Is there some kind of upgrade from within Dapper? I haven't found this information yet if anyone can tell me how they got an upgrade without formatting.

On messing with my repositories, I somehow removed them all from the software preferences window and there was no way to cancel my changes! I re-added each one (LTS, LTS Updates, LTS Security Updates and LTS Backports) but now I only have four in my list and they are all binary and not source. Whoops! I don't expect Linux is very forgiving for idiotic things like that! Any way to restore the default list? I still seem to have all the packages in the repository. I may still add some third party ones as well.

As for wireless, with that I've now got as far as to realise that I have an open source driver installed for it but the device itself is disabled... network: DISABLED or whatever it says when you run that command for seeing hardware details in the command line. Does this mean I need to figure out how to enable my card, to override it being switched off somehow, or do I still need to use ndiswrapper?

Thanks for the help it is much appreciated, and I'm sorry I can't be more specific with some of these things but I have no access to my Ubuntu computer at the moment.

Edit: Oh one more question? Can Linux not write to NTFS, because I have an external hard drive that is read only to Ubuntu for some reason...

---

### Post by Ozor Mox on 2007-03-06
Oh and some people asked about the applications I'm looking for that I can't find...here are some examples...

Firefox
Windows 2.0.0.2
Ubuntu 1.5.0.10 (I think) or compile from source (I assume as nothing would work when I extracted the tar.gz)

Battle for Wesnoth
Windows 1.2.2
Ubuntu 1.1 (I think) or compile from source

Freeciv
Windows 2.0.9
Ubuntu 2.0.8 or compile from source

OpenOffice
Windows 2.1
Ubuntu 2.0.2

And so on...

What I've had trouble understanding as someone completely new to Linux is how, as far as I know, ALL of the above are designed for Linux yet I can't get the newest version. If, therefore, updating to Edgy is normal to get newer packages that's fine, but I did not know or understand this as a long time Windows user. If I do understand correctly, or possibly completely incorrectly, do please let me know :)

---

### Post by Dr. Nick on 2007-03-06
Some of the popular programs that undergo major changes make it into the backports after time so you wont have to do a full update, However to use the newest version of applications you typically neeed to run the latest version.

Linux just now gained ntfs write support with the newer versions, I have not used it though. But when Dapper was released NTFS was still readonly.

[This link]("http://ubuntuforums.org/showthread.php?t=227052")
Will help you update to edgy if you dont want to format, It was written when edgy was still testing phase but should still apply

For your wma look into w32codecs, You can find info on the forums or on google, just download a .deb and you can install it. 

If you are going to update to edgy I would do it before you get everything setup just incase you have to do it again, your wireless card may be bettter suported in edgy anyway depending on what it is.

---

### Post by jhenager on 2007-03-06
> **Ozor Mox said:**
> 
I've now got MP3s to play, still working on videos and DVDs. 

I can help you with that. Install Okle from Add/Remove Programs.

---

### Post by jkeyes0 on 2007-03-06
> **Ozor Mox said:**
> Edit: Oh one more question? Can Linux not write to NTFS, because I have an external hard drive that is read only to Ubuntu for some reason...

This how-to page might help you out:

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by Ozor Mox on 2007-03-07
Again, thanks for the replies.

I updated my version of Ubuntu to Edgy with the surprisingly painless procedure of doing it from within Dapper so I'm now running the latest version. This has certainly solved many of my out of date software problems. Firefox is now the newest version. Some other software are not quite as new as what is available from the website but I guess that is just some sort of lag time in it being approved and added to the repository as mentioned earlier.

I'm a little further along with my wireless card, which is a Broadcom BCM4309 according to the terminal. I have blacklisted the default driver so now I no longer get a wireless network option in the networking interface. I have also attempted to download a number of versions of the Broadcom driver, from Broadcom's website, from Dell's website, various different places. The problem is they are in EXE format, and the ndiswrapper asks for them to be in INF format. Google turns up absolutely nothing for this driver, so I'm still stuck. Does anyone know how or where I can find this driver? Maybe I should start a separate thread for this.

---

### Post by Dr. Nick on 2007-03-07
You may start a separate thread if this doesnt help, but you can use file-roller to extract some .exe files, or if possible get the exe onto a windows computer and try winzip to extract it and you can get the .inf files then copy them via usb ot other to the linux computer

The place I found the inf files without extracting was on teh driver cd that came with my card.


Feisty comes out in April and should get you back to newer program versions.

---

### Post by Ozor Mox on 2007-03-08
Thanks Dr. Nick. I do have a driver CD that was supplied with my computer by Dell that may have the INF file on it, but I read somewhere about a package available called something like cabextract, it definitely had cab in it, that would turn the EXE into a CAB file where the INF and SYS files would be that I could use with ndiswrapper. Do you know what I'm talking about or is it complete nonsense?

That's good to know about the updated software in Feisty. I will certainly be upgrading, as the upgrade from Dapper (provided on the Live CD I used for initial installation) to Edgy was well worth it just for the beautiful start-up screen! Possibly it will be worth burning some Feisty ISOs to save a double upgrade, as I have been warned against?

Of course this upgrade talk is providing I still have my head above water with Ubuntu by this point and haven't given in to the easy option when my Windows XP reinstallation disc has looked at me longingly :) 

I really want to stick with Ubuntu because I much prefer what I've seen of it so far to Windows and I hope that if I can pull through these initial problems I will have enough Linux knowledge to be able to fix them far quicker when they crop up again.

---

### Post by 3rdalbum on 2007-03-08
If you don't mind living "dangerously" (just an expression), you could use Autopackages. Just search Google for the program that you want along with the word "autopackage", download the file and follow the instructions. It's very easy. I mean, most of the time compiling is actually easy and safe, but Autopackage takes the easiness one step further. Using this method, you could have had Firefox 2 on Dapper - oh well, Edgy is good too!

Just remember to keep your wits about you, and if you don't feel that you trust the packager, don't install their package. If you have the only user account on your computer, then you should install all your Autopackages as "this account only" (the installer will give you that option) to minimise the security risks.

---

