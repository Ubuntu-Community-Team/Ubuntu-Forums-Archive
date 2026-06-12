---
title: "Dual-boot MacBook"
date: 2009-04-09
forum: Apple Hardware Users
---

### Post by oh n0es on 2009-04-09
Okay, I'm planning on setting up a dual-boot on my MacBook with my existing install of Mac OS X and either Ubuntu or CrunchBang, but first I have a few questions.

[LIST=1]
[*]Will it just be a case of inserting the disc and then it'll boot from there?
[*]After installation of the Linux distro, will I be given an option at every boot to choose which OS I want to install into out of OS X and Linux?
[/LIST]

If anybody has any useful links on this it would be appreciated, I've done some Google searches but didn't find anything of use.

Thanks for any help.

---

### Post by oh n0es on 2009-04-10
Sorry to double post but does anybody know about this?

---

### Post by coffeecat on 2009-04-10
Have a look at [this sticky]("http://ubuntuforums.org/showthread.php?t=1046568") in the Apple Users subforum. There's a link to a wiki page which you should find useful.

Also, you'll probably get better replies in the Apple subforum. If you want to have this thread moved, simply click on the report button: [IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG], and ask a moderator to move it for you. It's OK using the report facility for this. Don't be alarmed at the spam, harrassment, stuff. The staff are happy for you to use the report button to ask for a thread to be moved.

---

### Post by oh n0es on 2009-04-10
> **coffeecat said:**
> Have a look at [this sticky]("http://ubuntuforums.org/showthread.php?t=1046568") in the Apple Users subforum. There's a link to a wiki page which you should find useful.

Also, you'll probably get better replies in the Apple subforum. If you want to have this thread moved, simply click on the report button: [IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG], and ask a moderator to move it for you. It's OK using the report facility for this. Don't be alarmed at the spam, harrassment, stuff. The staff are happy for you to use the report button to ask for a thread to be moved.
Ah, thank you very much for the link, it looks pretty useful.

And thanks for pointing out the Apple sub-forum, I was not aware that there was one on this forum, I'll ask to have it moved.

---

### Post by coffeecat on 2009-04-10
Good luck! I'm actually posting from my Mac Mini atm. I haven't bothered setting up a dual-boot on this because I've got a Windows (hack, spit! :wink:) and Linux multi-booting machine as well. What I've done in MacOS is to install [VirtualBox]("http://www.virtualbox.org/") in MacOS and keep a couple of virtual Linuxes (Ubuntu Hardy and Mint6 atm) going. It's worth thinking about and certainly a good way of trying out other distros/releases. Two disadvantage of VirtualBox (actually, any virtualisation I believe): For technical reasons the guest OS has to use the vesa driver, so no wobbly windows, rotating cubes and all that stuff. Also the user experience in the guest OS is pretty grim until you install the guest additions. That can be a bit perplexing unless you're well used to Linux.

---

### Post by oh n0es on 2009-04-10
Yeah I've tried VirtualBox out before for trying out Ubuntu distros before now but I'm planning on setting up a dual-boot for my MacBook. The topic you linked me to looks pretty handy though.

On another note, I also have a dual-boot on my main PC with Ubuntu and XP, but I'm happy to say I haven't had any need to boot into XP for a long time :P

---

### Post by cyberdork33 on 2009-04-10
> **oh n0es said:**
> Okay, I'm planning on setting up a dual-boot on my MacBook with my existing install of Mac OS X and either Ubuntu or CrunchBang, but first I have a few questions.

[LIST=1]
[*]Will it just be a case of inserting the disc and then it'll boot from there?
[*]After installation of the Linux distro, will I be given an option at every boot to choose which OS I want to install into out of OS X and Linux?
[/LIST]

If anybody has any useful links on this it would be appreciated, I've done some Google searches but didn't find anything of use.

Thanks for any help.

Yes, you should be ale to boot directly from the Ubuntu disc.
You can use rEFIt to select your OS to boot each time.

For more detail on installing see:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

> **coffeecat said:**
> Two disadvantage of VirtualBox (actually, any virtualisation I believe): For technical reasons the guest OS has to use the vesa driver, so no wobbly windows, rotating cubes and all that stuff. 
The very latest version of VirtualBox now supports 3D acceleration in Linux.

---

### Post by coffeecat on 2009-04-10
> **cyberdork33 said:**
> The very latest version of VirtualBox now supports 3D acceleration in Linux.

Excellent! Thanks for the information. I'm on 2.1.4 atm, but downloading 2.2.0 even as I type.

---

### Post by cyberdork33 on 2009-04-10
> **coffeecat said:**
> Excellent! Thanks for the information. I'm on 2.1.4 atm, but downloading 2.2.0 even as I type.
Good Luck, I haven't tried it yet myself.

---

### Post by oh n0es on 2009-04-10
Alright, I've installed Ubuntu fine and the rEFIt menu comes up fine, but when I try and boot into Ubuntu I just get a flashing underscore in the top left corner of my screen and it just hangs there permanently. Any ideas what is happening there?

---

### Post by coffeecat on 2009-04-10
Edit: sorry, posted in error.

---

### Post by oh n0es on 2009-04-10
Alright, I've fixed the problem using the grub commands from this post;
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

Cheers for the help everyone.

---

### Post by ralphcab on 2009-04-10
Hello everybody,,i just became a member of the forums, and i've been using ubuntu for a while, I tried to dual boot my macbook 5,2 with ubuntu and it was a mess, does anybody knows if they are fixing all the issues that comes when trying ubuntu with MacBook 5,2 on the new release.

---

### Post by cyberdork33 on 2009-04-10
> **ralphcab said:**
> Hello everybody,,i just became a member of the forums, and i've been using ubuntu for a while, I tried to dual boot my macbook 5,2 with ubuntu and it was a mess, does anybody knows if they are fixing all the issues that comes when trying ubuntu with MacBook 5,2 on the new release.
people like you and me trying it out are how things get fixed. try it out, report bugs.

---

### Post by ralphcab on 2009-04-10
Yeah you are right i should keep trying and write  all the weird things that comes with this

---

