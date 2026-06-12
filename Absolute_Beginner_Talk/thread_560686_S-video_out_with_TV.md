---
title: "S-video out with TV"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by holdie on 2007-09-26
I just received my S-video cable in the mail, and I'd like to set up my computer so that I can dual-monitor or even just switch screens to the TV...

I was wondering how I could go about accomplishing this

I'm using an ATI x300 graphics card on a Dell Inspiron 6000

thanks

---

### Post by Linux_Man on 2007-09-26
Which ATI drivers do you have propriatary or free? Have you tried just plugging the S-Video into your computer and TV and seeing what happens? I have seen someone (using a mac though) simply do that and it works.

---

### Post by holdie on 2007-09-26
I'm pretty sure I'm currently using the open source "radeon" driver for my card

and no, just plugging it in doesn't seem to do anything

---

### Post by Jonnothin on 2007-09-26
I have this problem as well. I'm wondering if there isn't some kind of software. I know it's been done though because a friend of mine has done it, he's even played movies off another TV, but I don't remember if it was S-video.
Sorry though, I've got the same problem, but a different computer and Graphics card. I do know though that ATI cards are not very well supported. I know that's not what you want to hear, but if you have a driver (which you probably do unless your computer doesn't do 3D graphics or things like that very well) then you should be ok in that department.

---

### Post by holdie on 2007-09-27
yeah 3-D graphics aren't the greatest with linux and ATI, makes me sad to have to watch google earth crawl to a halt, but i haven't had the willpower to search for a better driver and this one works with compiz sooooo...

weren't they starting to get some better support from graphics cards?  I'd think that s-video out would be a relatively common want for most users, someone has to have thought something up

---

### Post by crav on 2007-09-27
the driver on ati's website claims to enable s-video out, but i haven't checked it out.
If you choose to go that route, please post an update!

---

### Post by ellkae on 2007-09-27
For s-video, after your video drivers are installed, all you have to do it plug in the s-video and restart X (ctrl+alt+backspace).

---

### Post by snake444 on 2007-09-27
you can wait to gutsy there is a window for configuring it in System->Administartion->Screens and Graphics and you can do there dual monitor.. and not configure some X files :)

---

### Post by holdie on 2007-09-27
hmmm I checked the ati website and it looks like you're right...so I switched back to the ati driver (just replacing "radeon" with "ati" under xorg, I think that's all I have to do right?) and there's still no output going to the TV, so I'm wondering if theres something I need to switch on after doing this..

---

### Post by Dr Small on 2007-09-27
[http://ubuntuforums.org/showthread.php?t=554095](http://ubuntuforums.org/showthread.php?t=554095)

---

### Post by holdie on 2007-09-27
I tried installing the program in the thread you referenced, atitvout...

using atitvout detect, it sees that a TV is connected via s-video, however when I try to use
atitvout t

it gives me this

sudo atitvout t
VBE call failed.
Maybe this command is not supported by your graphics adapter?
Did your parameters (if you specified some) really make sense?
Please try all other available commands before complaining!

I tried using the ati driver, the radeon driver, and the vega driver that was mentioned in the wiki, and they all turned up the same response from the machine...any ideas?

---

### Post by Dr Small on 2007-09-27
Did you follow everything to the letter on this page ?
[https://wiki.ubuntu.com/Radeon7500TVOut?highlight=%28s-video%29](https://wiki.ubuntu.com/Radeon7500TVOut?highlight=%28s-video%29)

---

### Post by JBAlaska on 2007-09-27
According to that guide, you forgot a switch. The command should be:
sudo atitvout -f t

If that works (and your happy with only one screen on at a time)...great.
If that didn't work, or like most ppl, you want output on both monitors, you might try reverting to the ati non-free drivers and starting ati catalyst control center, I think there's a setting in there to clone your displays (sorry I can't check it as i'm using the restricted drivers in a xgl session)

---

### Post by holdie on 2007-09-27
I followed everything that page says, except that I'd already had atitvout installed before changing to the vesa driver...

and yeah, I'd tried it with the -f addition first and that didn't work either...

what are the non-free drivers?  I'm currently back to using the radeon open-source one...

---

