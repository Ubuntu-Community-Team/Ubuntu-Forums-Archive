---
title: "ubuntu wont let me go back to vista"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by internetishere on 2008-03-01
ubuntu is keeping me from going back to windows vista
i been having so many errors with ubuntu lately....  cant kill process cant shutdown error code ... etc, but now when i boot up my comp im always automatically takin to boot menu but now when im there i cant use any key on my keyboard so it waits 10 seconds then goes to ubuntu and when i reboot i have to press the sleep button on my keyboard to make my screen appear then i cant use and keys. now how do i get back to vista?

p.s.  i didn't not install ubuntu over vista i was able to get back to it before but now that ubuntu is making me press the sleep key on my keyboard i can only go into ubuntu

sincerely,
internetishere

---

### Post by spiderbatdad on 2008-03-01
This isn't officially a Vista support site, but I can tell you "Ubuntu" isn't preventing you from doing anything. You should have used Vista's partitioning tool prior to the installation of Ubuntu, and you should have burned a Vista recovery disk. Hopefully you did those things. Boot into recovery with your Vista disk, and follow the instructions for recovering your system.

---

### Post by internetishere on 2008-03-01
> **spiderbatdad said:**
> This isn't officially a Vista support site, but I can tell you "Ubuntu" isn't preventing you from doing anything. You should have used Vista's partitioning tool prior to the installation of Ubuntu, and you should have burned a Vista recovery disk. Hopefully you did those things. Boot into recovery with your Vista disk, and follow the instructions for recovering your system.

Umm i dont have a vista recovery disc i bought my comp from circuit city they just gave me the vista os but i think its probably something wrong with my keyboard maybe because it works fine once im in ubuntu but at the boot menu it doesnt work? *scratches head* any other way to fix this?

---

### Post by gary0 on 2008-03-01
Is your keyboard USB? If it is, try a PS2 one. USB hasn't been loaded yet (at the boot menu that is). I had a similar problem and the ps2 keyboard works at boot up.

Gary.

---

### Post by lolzlolz on 2008-03-01
umm i have vista and ubuntu and i dont have any problems, vista causes every problem i have not ubuntu ubuntu hasnt caused one vista has, so dont start blaming ubuntu, u can use the vista disk to recover and it will overwrite the grub menu, so u should be able to stick that in if u bought ur comp it should have come with this disk, then choose to boot from disc then choose the recovery option and follow the resulting steps and it should fix vista's problems

also i have a usb keyboard and it works fine at the boot menu

---

### Post by internetishere on 2008-03-01
Ok first of all id like to say sorry i was just abit peeved
my keyboard is ps2 not usb and i have only tried this ps2 maybe i should try usb then?

---

### Post by glennric on 2008-03-01
> **internetishere said:**
> ...

if YOU HAD READ what i said before the problem is not that vista wont start its once i installed ubuntu everything started to get ****** up you see as i have said i used to be able to get into vista but now its as if my keyboard is completely frozen at the boot menu plus wtf is with haveing to push th sleep ley to see my screen when i reboot now dont get me wrong i admit ubuntu IS BETTER in all ways you see i rarely would need to get back to vista its just occasionally i get a program and wine wont emulate it properly and for specific information i was trying to install Halo1 but when i enter my cd-key it says cant load PitGen.dll and whenever i tryed to install it on windows vista it worked just fine all i was trying to do is get back to vista so i can install it properly but after a while of haveing ubuntu it has just completely f_____ up my comp i mean seriously wtf so now everytime i reboot i gotta press my sleep key and after that i gotta never go back into vista just wtf i didnt think ubuntu could get virus's it was wrkin fine i could always switch back to vista by rebootin my comp but now everything as i said before is f_ _ _e_d up.

You do know that periods are for ending sentences and not paragraphs don't you?

---

### Post by internetishere on 2008-03-01
> **glennric said:**
> You do know that periods are for ending sentences and not paragraphs don't you?

as i said when i posted that big wall of text i shouldnt have i was just mad so i changed it to this

 Umm i dont have a vista recovery disc i bought my comp from circuit city they just gave me the vista os but i think its probably something wrong with my keyboard maybe because it works fine once im in ubuntu but at the boot menu it doesnt work? *scratches head* any other way to fix this?

anyone got any ideas on how to fix this problem though?

---

### Post by mrsteveman1 on 2008-03-01
This thread is a bit hard to read but here goes


So the main problem is that you cant use your keyboard to select a boot entry, and thus can't boot into Vista?

When grub is loading, as far as i remember, it uses BIOS drivers up until the point that the kernel loads, so if your keyboard works in the bios menus it should work in grub.

If you can boot into ubuntu you can always just change the default boot entry to the vista one to boot into it for now. Edit /etc/fstab and change the default to the vista entry

Also sounds like the ubuntu installation is a bit screwed as well

---

### Post by internetishere on 2008-03-01
sounds good but how? im not very skilled lol what do i type in terminal to edit that? and also what in that document do i edit?? maybe a screenshot please? lol

---

### Post by mrsteveman1 on 2008-03-01
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS")

---

### Post by Derviansoul on 2008-03-08
hello
can you tell me something??
can u use the bios and the keyboard after?

Usually on usb keyboards there is an option for that on the bios usually . on my abit aw9dmax award bios i go to


Integrated Peripherals>>>On-Chip PCI Device>>USB Keyboard Support Via  the option there should be BIOS

i would advise you to try first another ps2 keyboard and if it works there is something wrong with your keyboard, if not u should have a look on your bios settings, could u go before to vista when with the grub installed??

regards

---

### Post by halitech on 2008-03-08
> **internetishere said:**
> Ok first of all id like to say sorry i was just abit peeved
my keyboard is ps2 not usb and i have only tried this ps2 maybe i should try usb then?

if you have a ps2 keyboard, enabling USB keyboard support won't do anything. Do you have another keyboard you can try? maybe something is going on with your keyboard

---

### Post by Duck2006 on 2008-03-08
In your BOIS do you have a USB KB legacy support?

---

