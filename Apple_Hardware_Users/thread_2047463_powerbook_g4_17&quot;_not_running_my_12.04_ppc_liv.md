---
title: "powerbook g4 17&quot; not running my 12.04 ppc live disc."
date: 2012-08-24
forum: Apple Hardware Users
---

### Post by boneskid1 on 2012-08-24
well after looking at a powerbook g4 that was on a shelf i decided i might try to run ubuntu off of the live disk  just to see how well it works, but i was stopped because it never goes past the black ubuntu 12.04 screen it freezes and i have to reboot the computer.

so what i am wondering is ........ is 12.04 even compatible with the ppc cpu?

i got the .iso from here
[http://cdimage.ubuntu.com/releases/precise/release/](http://cdimage.ubuntu.com/releases/precise/release/)
and i did the desktop cd

Thanks ahead of time,
Boneskid1

---

### Post by 2F4U on 2012-08-25
I assume that you took the desktop cd for PPC ([http://cdimage.ubuntu.com/releases/precise/release/ubuntu-12.04-desktop-powerpc.iso](http://cdimage.ubuntu.com/releases/precise/release/ubuntu-12.04-desktop-powerpc.iso)) and not the other desktop cd on the site.
In general, Ubuntu supports the PPC architecture:

[https://help.ubuntu.com/12.04/installation-guide/powerpc/hardware-supported.html](https://help.ubuntu.com/12.04/installation-guide/powerpc/hardware-supported.html)

And there is also quite some help available:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
[https://wiki.edubuntu.org/PowerPCFAQ](https://wiki.edubuntu.org/PowerPCFAQ)
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
[]("http://cdimage.ubuntu.com/releases/precise/release/ubuntu-12.04-desktop-powerpc.iso")

---

### Post by 2blue on 2012-08-25
Powerbooks have rather low specs so, perhaps xubuntu or lubuntu. However, Ubuntu should boot just as well but maybe run a bit slow compared to the others. To run live CD there is a minum of RAM needed, but I cannot remember exact number at the moment. My iBook G4 runs fine with 512MB.

---

### Post by boneskid1 on 2012-08-25
i have 1.5gb of ram and it requires at least 348mb so i figured that is not the problem but i will do some more trouble shooting today

---

### Post by 2blue on 2012-08-25
More than eough ram then. I had trouble booting 12.04, but I cannot remember what the exact trouble was. I had to run a blacklist-command in the pre-booting stage or otherwise it haulted at a certain point. I think it had to do with wireless drivers. How quickly you forget :rolleyes: , and probably not the case with your G4, but if you get any messages during bootup, it might be worth posting them.

---

### Post by boneskid1 on 2012-08-25
yeah when i boot from the disc it takes me to a black command like screen where i hit return and it boots sending it to the ubuntu loading screen but after it sits for a bit it says something like firmware not configured and it gives a url to go to for a wireless firmware, but i have the powerbook plugged in to my Ethernet.

---

### Post by rsavage on 2012-08-25
Hi, your problem and solution is documented in the wikis that you've already been given.  

I'm interested to know how people use the FAQ (so I can make it better), clearly it is different to how I would.

This is how I would do it:

Start with the FAQ.  See there is a troubleshooting section.  See there is a question "Ubuntu boots to a command line, hangs during boot, or blank screen etc.".  Read that answer.  See it suggests the Known Issues Page.  Look down the list of 12.04.  See it mentions a problem "b43 (Airport Extreme) hangs".  Sounds like my problem.  Follow the link.

Did you do any of that?

If you can tell me how it can be improved let me know!

---

### Post by 2blue on 2012-08-25
Hmm...

If it is the same trouble I had, you have to type "live b43.blacklist=yes" in the first stage of booting when you come to a termial like screen (before CD loads any further). Later after install you have to type "Linux b43.blacklist=yes" to be able to boot fully.  The bug sorts its` self out as soon as you do the updates. [Here]("http://ubuntuforums.org/showthread.php?t=2020131") is the thread on the help I was given, and it worked fine. I have an iBook G4 from 2005, not sure how much the G4s differed in hardware.

---

### Post by boneskid1 on 2012-08-25
> **rsavage said:**
> Hi, your problem and solution is documented in the wikis that you've already been given.  

I'm interested to know how people use the FAQ (so I can make it better), clearly it is different to how I would.

This is how I would do it:

Start with the FAQ.  See there is a troubleshooting section.  See there is a question "Ubuntu boots to a command line, hangs during boot, or blank screen etc.".  Read that answer.  See it suggests the Known Issues Page.  Look down the list of 12.04.  See it mentions a problem "b43 (Airport Extreme) hangs".  Sounds like my problem.  Follow the link.

Did you do any of that?

If you can tell me how it can be improved let me know!

no but i did not see a troubleshooting option, and i was posting what 2blue said might help figure my issue out.
also i will not have acess to 2 computers tonight so i can do this but i will do it in the morning, also does the Linux b43.blacklist=yes command work on the live disc?
i am not quite sure if i am going to fully install ubuntu just yet

---

### Post by 2blue on 2012-08-25
I remember when I was all new to Ubuntu, I read wikis up and down, and still didnt get half of what I was reading. With some posting on the forum, reading, trying, testing, asking..., I gradually have become a bit better at it, even reading the FAQ pages. With the iBook it was sort of all new again for a while, and still stuff that needs sorting out. The ppc FAQ page is very good, but it needs a bit more than just reading it for a beginner at least.

...and no, for the live CD it has to be: live b43.blacklist=yes

---

### Post by rsavage on 2012-08-25
@2blue The b43.blacklist=yes is an interesting one.  That indeed would work, but it doesn't do what people think.  The implication is it blacklists b43.  It doesn't.  "blacklist" is an unknown parameter and this is what stops the b43 module loading.  You could write
```

live b43.aloadofrubbish=yes 

```and it would do the same thing.  That is why (up until now) it is not in the KnownIssues page (although the link is provided) because I've tried to purge the PowerPC documentation  of any dodgey or misleading advice.

*EDIT: I've updated the KnownIssues page to hopefully make it clearer.*

---

### Post by 2blue on 2012-08-25
LOL, I have no idea what I am doing at times, mostly copy & paste. Just as long as *aloadofrubbish *works !!

---

### Post by boneskid1 on 2012-08-25
I installed but after rebooting it won't boot and I tired linux b43.blacklist=yes upon boot and it says un-avaliable

---

### Post by 2blue on 2012-08-25
It has to be capitol L:  Linux b43.blacklist=yes

---

### Post by boneskid1 on 2012-08-25
That worked but did It fix it? And my wi-fi won't config
I know I am asking tons of questions but I am new to this and can use all the help I can get.

---

### Post by 2blue on 2012-08-25
The trick is to get a wired connection, do the updates and the booting issue will be fixed. You might have to install a few things for the wireless to work, but a lot will be working on your first bootup after doing the updates. Until you have done the update, you will need to run the blaclist command on each bootup. 

Updates are done from menu-system tools-update manager. 

There are ways about it if you only have wireless connection, but wired is easiest.

---

### Post by boneskid1 on 2012-08-25
Ok I will try to wait til tomorrow but I would like it to run tonight, how do I go about the wi-fi updates

---

### Post by 2blue on 2012-08-25
I think my wireless card might have activated its` self after the first updates and reboot. It took a few minutes and the system detected a list of networks. I ran this command in terminal too though: "sudo apt-get install firmware-b43-installer",  and it has worked ever since.  You might have to reboot after the last command.

---

### Post by boneskid1 on 2012-08-26
home now posting this from the powerbook and i am running the updater, i do have a question or 2 for you 2blue.

does your ibook go to sleep/hibernate when you close the lid?
and can you change your brightness settings at all via hardware keys or in system settings?

thank you for all the help i now have a better performing device than when i started.

EDIT: after the reboot and updater the brightness and wi-fi works and i am getting ready to check out the sleep issue.

---

### Post by 2blue on 2012-08-26
My iBook G4 only shutdown and suspends properly. I`m not all sure about the hibernate mode. (What is suppose to be the difference between suspend and hibernate?) So far I haven`t payed much attention to this. In suspend mode screen turns completely of, no heat or sounds from the comptuer that I have noticed. The battery light in front is on though. Computer goes in suspend mode when left alone for some time and when lid is closed. I have chosen hibernate manually but it seems to be like regular shutdown.  I have to investigate this further too really.

Do you have regular Ubuntu? I went straight for lubuntu thinking it was the lightest, but I might try xubuntu too. They have different default media players and applications, not just different desktop environment.

---

### Post by 2blue on 2012-08-26
I just tested hibernation; left browser open and manually chose hibernation mode. It seems to work fine. Computer seems to almost shut down and I have to press start button to get any reaction from system. It seems very much like a regular bootup, but when I got as far as desktop screen browser was open. A full shutdown kills all running applications.  It`s  a question of settings to get computer to suspend or hibernate when closing lid, and are to be found in: menu-preferences-power manager.

---

### Post by boneskid1 on 2012-08-26
my powerbook gives me no option for hibernate now, it ran another update and that fixed the sleep when the lid is shut. i am running regular ubuntu as i prefer the desktop environment over lubuntu's desktop environment.

---

### Post by 2blue on 2012-08-26
I can`t remember power manager for gnome, but it is probably there. At least in the lxde version it works fine. You need a minimal swap to make suspend and hibernation work, it is often suggested 1.5GB or twice your RAM, and  seems to be a loosely estimated number depending on your system. 

Does Ubuntu and Unity work fine on a G4? How large is the processor? And Totem, does it stream in browser?

---

