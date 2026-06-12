---
title: "using ubuntu the first time"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by anirudhbsg on 2008-04-13
Hi there, after a workshop of open source in my college i decided to turn completely to open source .......
I decided to use ubuntu as my os although i cannot remove windows from my pc because of some family problems,now when i am using the live cd of ubuntu after working for about 2-3 minutes the system goes into the hang state.The next time time it always shows that a system application has failed .
Its not with just one cd, i have used more than 3 cd's.Now its frustrating as i cant even work for five minutes . I found some booting related problems already present on the forum but probably i did not understand them.Please can some one help me with this problem.

---

### Post by Mick8882003 on 2008-04-13
You can checksum the cds, i will try finding the link... I assume you mean the installation cds?

take a look at my sig for an outline of the proccess

---

### Post by emergingtechnologies on 2008-04-13
So... someone in your family loves Windows... that's fine -- their eyes will open soon enough -- here is a solution to one aspect of your problem.

I confess I am not really a computer expert -- but I do know that dual boots and running off the CD is no way to really experience this fine family of OSs.

You have to pull out some older system and set it back up.  Ubuntu's little brother is called Xubuntu -- some Xubuntu fans are going to go crazy on me for saying that but bear with me -- Xubuntu will allow you to take your OLD 600mghz system out of the closet and start surfing the Internet faster than your 2.6 gig Vista box -- this is the truth!  

I have a source in my town where I am buying these older boxes for as low as $25 -- all you have to do is look in the yellowpages for Computer Recycling -- you will find a source for an incredibly cheap box -- and probably cheap monitor, keyboard etc etc -- 

Now -- just download the most recent xubuntu iso and load that badboy on there -- plug into the network and you will show these family members who live Vista so much that there is NOTHING at all to fear.

Hope this helps.

ET

---

### Post by philinux on 2008-04-13
> **anirudhbsg said:**
> Hi there, after a workshop of open source in my college i decided to turn completely to open source .......
I decided to use ubuntu as my os although i cannot remove windows from my pc because of some family problems,now when i am using the live cd of ubuntu after working for about 2-3 minutes the system goes into the hang state.The next time time it always shows that a system application has failed .
Its not with just one cd, i have used more than 3 cd's.Now its frustrating as i cant even work for five minutes . I found some booting related problems already present on the forum but probably i did not understand them.Please can some one help me with this problem.

Use cdrw's if you have any, then no more coasters.

at the menu choose check cd for defects.

---

### Post by linuxlizard on 2008-04-13
My advice is just to relax and wait another week until Hardy Heron comes out. It has a special installer for first time users where you can install the entire OS from within windows just like any other windows application (and uninstall it just like any windows application).

Of just partition your hard drive and duel boot with two os installed. That's better than installing within windows because the within windows install doesn't let you use your graphics card.

---

### Post by erginemr on 2008-04-13
If after all CD checks, you get confident that it is not a faulty CD, which is responsible, then please read:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

and try removing the words "quiet splash" from the boot parameters, follow the messages run by, track down error when the bootup stalls and report back here.

Depending on the error message issued, using one of the following boot parameters: 
**acpi=off**, **irqpoll**, **noapic **and **nolapic**
either one by one or in combinations, may help.

---

### Post by setamym on 2008-04-13
When Hardy Heron (Ubuntu 8.04) will be released ? When I see ShipIt! the release not yet come.

---

### Post by kwacka on 2008-04-13
Shipit will be weeks away. Hardy download from Ubuntu mirrors at the end of this week, I understand.

---

### Post by farsight on 2008-04-13
Hey there

I'm pretty much new to all this too. If you're having trouble with the CDs how about giving the USB flash drive way a whirl.

There is a guide here:
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

I managed to make a total mess of my computer the other night by deleting the ubuntu partition in Windows only to find that once i'd turned off the comp. i was then unable to access windows. 
I'd premade a USB version of 7.10 and that allowed me to get sorted.

Using the USB option also allows you to save all your work you do and just plug it back in next time and carry on. 

Regards, Farsight

---

### Post by chrisdugdale on 2008-04-15
Why not try Wubi from [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php) It just installs as a Windows application and will then install Ubuntu for you so it runs just like any other application in Windows? Haven't tried it myself. Also you could wait 8 days and download the release version of Ubuntu 8.04 Hardy Heron (it's only available as a beta till then). That may solve the problem.

---

