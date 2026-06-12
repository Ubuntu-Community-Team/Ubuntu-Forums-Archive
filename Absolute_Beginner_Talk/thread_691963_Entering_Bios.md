---
title: "Entering Bios"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by shoeshrimp on 2008-02-09
I'm trying to enter the bios on my Toshiba laptop. You have to press Esc on boot up, which I do, and it starts booting with text, so it clearly registers that I have pressed esc... However, then it just enters the normal Grub (I am dual booting), and I cannot enter the bios. Does anyone know what I am doing wrong?

Tom

---

### Post by hyper_ch on 2008-02-09
are you sure it's ESC?
Common other strokes would be:

DEL
Backspace
F2
F8

maybe try those.

---

### Post by Arwen on 2008-02-09
Or check out if your keybord has a button that changes the function of some F-buttons..Mine has one but I've never used it,although I had to press it so as to change back to normal functions and finally enter BIOS with F2 after driving me crazy:-)

---

### Post by Joeb454 on 2008-02-09
Keep hitting escape if that's the correct button. I can press escape to see text boot, but F12 is the button I have to press for Bios

---

### Post by shoeshrimp on 2008-02-09
Cheers guys. I press escape for text boot - but it says F12 is to select boot drive. Should I press F12 and then select something from there?

---

### Post by Paqman on 2008-02-09
Nope, F12 sounds like it's to select what drive to boot from. Try F2? F8? Del?

---

### Post by jou770d on 2008-02-09
It's F2 on my Toshiba Satellite A30.

---

### Post by wpshooter on 2008-02-09
> **shoeshrimp said:**
> I'm trying to enter the bios on my Toshiba laptop. You have to press Esc on boot up, which I do, and it starts booting with text, so it clearly registers that I have pressed esc... However, then it just enters the normal Grub (I am dual booting), and I cannot enter the bios. Does anyone know what I am doing wrong?

Tom

Why do you need to get into the BIOS ?

If you do not know how to get into the BIOS/setup of your machine, there is a likelyhood, that you should not be going into the BIOS.  Be careful.

Good luck.

---

### Post by brokenhachi on 2008-02-09
i think most toshibas use the same bios and im not sure if its connected though, but im also pretty sure most toshibas use F2 for going to bios..... atleast the ones that i see do.


and f12 wont take you to bios, it just brings up a small screen showing what drives you could possible boot from, life CDROM or external HDD or just plain old HDD

---

### Post by shoeshrimp on 2008-02-09
Thank you for your concern wpshooter...

F2 takes me into setup - but I need to prevent bios running my onboard modem - and i cannot find any way of doing this...

---

### Post by wpshooter on 2008-02-09
> **shoeshrimp said:**
> Thank you for your concern wpshooter...

F2 takes me into setup - but I need to prevent bios running my onboard modem - and i cannot find any way of doing this...

More than likely, there is a parameter in the BIOS for disabling the modem.  If not, there is the possibility that there may be a jumper on the motherboard to disable it there.  But opening up a laptop with out the proper knowledge, again, can be risky.

Would consult the computer's user manual or call Toshiba, I think you said, first.

Good luck.

---

### Post by brokenhachi on 2008-02-09
ok, assuming that you are running "phoenixBIOS setup utility" 


push right once to go to the tab marked "ADVANCED" 

go down to "Buit-in LAN [ENABLED]"  and push ENTER (i think) to change it to [DISABLED]

go right to the final tab and select "save changes and exit bios" and push enter, then select yes when it asks you if you want to save and quit.


it will automatically reboot.

---

### Post by shoeshrimp on 2008-02-10
> **brokenhachi said:**
> ok, assuming that you are running "phoenixBIOS setup utility" 


push right once to go to the tab marked "ADVANCED" 

go down to "Buit-in LAN [ENABLED]"  and push ENTER (i think) to change it to [DISABLED]

go right to the final tab and select "save changes and exit bios" and push enter, then select yes when it asks you if you want to save and quit.


it will automatically reboot.

aha! Thanks, I am running phoenix, but when I go to advanced there are only options related to the parallel port and the power management. Do I need a bios upgrade, and if so how!?

Thanks!

---

### Post by brokenhachi on 2008-02-11
if your computer came with a built in card, than there should be the option there from the start without having to update the bios. look around a bit more and see if you cant find it.


Edit: here is a view of my bios, showing the built in lan option... hope it helps. by the way.. what bios version do you have anyways... mine is 1.7

[IMG]http://img.photobucket.com/albums/v321/Brokeasshachi/bios.jpg[/IMG]

---

### Post by shoeshrimp on 2008-02-11
> **brokenhachi said:**
> if your computer came with a built in card, than there should be the option there from the start without having to update the bios. look around a bit more and see if you cant find it.


Edit: here is a view of my bios, showing the built in lan option... hope it helps. by the way.. what bios version do you have anyways... mine is 1.7

[IMG]http://img.photobucket.com/albums/v321/Brokeasshachi/bios.jpg[/IMG]

Thanks for going to the effort of taking a photo! My version is 1.7, and there's definitely  nothing about LAN in there. The only options are:

```
Parallel Port:
- Mode
- Base I/O Address
- Interrupt

Processor Power Management
```

I'm quite confused, it definitely has a built in modem (and many other things too!?)

Tom

---

### Post by NightwishFan on 2008-02-11
I have a bios that does not allow me to configure more than 15 options and none are very useful. :(

---

### Post by brokenhachi on 2008-02-11
i've noticed that the phoenix bios doesnt give you alot of options, but i do like it.. only because of the quick and easy boot menu though. but i dont get options for adjusting heat and overclocking th cpu blah blah.. so i guess it is restricting.


tom, the only thing i can say is that either the bios wont let you control it or the lan card is software controlled (from within the OS) but i dunno because im not a hardware specialist. all i know is that its on my list, as you can see...


what comp are you using? i will try and help by checking out the toshiba website. but i need the exact model number and name.

---

