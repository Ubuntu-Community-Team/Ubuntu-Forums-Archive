---
title: "Problems with wireless internet"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by say592 on 2007-04-08
I am having a problem getting the wifi to work. I use a generic wifi card, so I wasnt sure it would, but it worked fine in the live CD. 

When I installed it though, it has yet to work, and it doesnt pick it up as a network device.

I know it may be loose, so dont say that. I am checking it, and will post whether that was the solution. 

Im relatively sure that it is driver related, so if know of a driver pack that might work, I will give that a try provided you can walk me through what to do after I burn it to a CD from my windows machine.

---

### Post by mand0 on 2007-04-08
One way to check if Ubuntu detects your wireless card is to type this in Terminal:

```
lshw
```

Paste the output.

---

### Post by jimrz on 2007-04-08
> **say592 said:**
> I am having a problem getting the wifi to work. I use a generic wifi card, so I wasnt sure it would, but it worked fine in the live CD. 

When I installed it though, it has yet to work, and it doesnt pick it up as a network device.

I know it may be loose, so dont say that. I am checking it, and will post whether that was the solution. 

Im relatively sure that it is driver related, so if know of a driver pack that might work, I will give that a try provided you can walk me through what to do after I burn it to a CD from my windows machine.

check in Synaptic and make sure you have the "restricted modules" package installed. if it is installed we will need more info on your card (make/model/chipset) in order to help you get it working. if you do not know this info, try booting the "live" cd again and looking in Device Manager to see how it is listed and in /etc/Xorg/xorg.conf to see what driver is being uused in your "live" sessions.

---

### Post by say592 on 2007-04-08
> **jimrz said:**
> check in Synaptic and make sure you have the "restricted modules" package installed. if it is installed we will need more info on your card (make/model/chipset) in order to help you get it working. if you do not know this info, try booting the "live" cd again and looking in Device Manager to see how it is listed and in /etc/Xorg/xorg.conf to see what driver is being uused in your "live" sessions.

Ok, so how would I go about checking synaptic. I am relatively new, and I just dont recognize what you are saying by that. Im sure I can do it if i get a little bit of hint lol

---

### Post by Maestro23 on 2007-04-08
> **say592 said:**
> Ok, so how would I go about checking synaptic. I am relatively new, and I just dont recognize what you are saying by that. Im sure I can do it if i get a little bit of hint lol

Open up Synaptic(GUI) and search "restricted modules".  Anything with a green box is installed.  If it is not installed, you need to mark it for install and apply.

System>>>Admin>>>Synaptic

*Some links to help you down the road w/Ubuntu:

Useful Links:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Managing Repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

Community Docs: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Graphic Card Drivers
ATI supported cards: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
Installing ATI Drivers: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Installing Nvidia Drivers:[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Super Grub Disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)


Welcome and Good luck.

---

### Post by jimrz on 2007-04-08
> **say592 said:**
> Ok, so how would I go about checking synaptic. I am relatively new, and I just dont recognize what you are saying by that. Im sure I can do it if i get a little bit of hint lol

on your top panel go to Sytem > Administration > Synaptic Package Manager (you will need to enter your password) then search for "restricted" and scrol down to linux-restricted-modules entries and check that the version for your kernel is installed. if not install them, restart and you should be in business. if they are already installed we will need further info on your card.

---

### Post by say592 on 2007-04-08
heh....It seems the simplest solution is always the best solution.

When I checked to see if it was loose earlier, I didnt remember that I had to remove the antenae to open the case. So it was no longer loose, but it wasnt functioning correctly without the antenae.

When I saw this, I promptly plugged it back in, and what do you know, it worked! lol

Thanks for the help though!

---

### Post by jimrz on 2007-04-08
> **say592 said:**
> heh....It seems the simplest solution is always the best solution.

When I checked to see if it was loose earlier, I didnt remember that I had to remove the antenae to open the case. So it was no longer loose, but it wasnt functioning correctly without the antenae.

When I saw this, I promptly plugged it back in, and what do you know, it worked! lol

Thanks for the help though!

no prob ...  glad you got'er going ... simplest is always the best, indeed

---

