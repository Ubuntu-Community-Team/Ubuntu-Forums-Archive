---
title: "SATA Help. I certainly need it."
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by tylertilly on 2008-01-04
Okay, I guess this isn't exactly Ubuntu related, but since I'm going to be installing Ubuntu on this machine, I suppose in a roundabout way it is.

I just got done building a computer, and everything is working... sort of.

The only thing giving me problems is my Hard Drive and CD/DVD Drive.

I know for a fact my DVD drive works. I can even put my Ubuntu CD in and it loads up and all that. But the problem is, as soon as I plug in my Hard Drive, my DVD drive no longer works, and the hard drive just sort of spins and then turns off.

They're both SATA drives and I just want to know what the hell I'm doing wrong, because I'm sure it's something.

Thanks a lot,
Tyler

---

### Post by theRightNee on 2008-01-04
lost, you plug in your hard drive after you start your DVD drive? why not have them plugged in at the start? i am assuming you have tried to boot with both plugged in, and couldn't manage to get something going. please reply with more info. thanks!

---

### Post by tylertilly on 2008-01-04
Oh, sorry about that.

I've plugged in both at the same time before boot, and the DVD drive won't read the cd, and the hard drive will just sort of spin for a while, then stop. I can get through my bios screen, but after that nothing happens.

If I start with just my DVD drive plugged in, everything works fine, ubuntu cd starts up, starts installing, all that.

The only problem is I can't exactly install Ubuntu anywhere when my hard drive isn't connected (and when it is connected, not recognized or something).

Sorry if I'm still confusing :/
But thanks for helping :)

---

### Post by Paulmd on 2008-01-04
> **tylertilly said:**
> Okay, I guess this isn't exactly Ubuntu related, but since I'm going to be installing Ubuntu on this machine, I suppose in a roundabout way it is.

I just got done building a computer, and everything is working... sort of.

The only thing giving me problems is my Hard Drive and CD/DVD Drive.

I know for a fact my DVD drive works. I can even put my Ubuntu CD in and it loads up and all that. But the problem is, as soon as I plug in my Hard Drive, my DVD drive no longer works, and the hard drive just sort of spins and then turns off.

They're both SATA drives and I just want to know what the hell I'm doing wrong, because I'm sure it's something.

Thanks a lot,
Tyler

I think you have a bad Hard Drive.

---

### Post by tylertilly on 2008-01-04
Would a bad hard drive cease my DVD drive from working though?

I'm just wondering if I have to plug the sata cables in, in a certain order. Or like configure something that I'm missing. Cuz I figured if it was just a bad hard drive, my DVD drive would still work while they are both connected.

---

### Post by Paulmd on 2008-01-04
> **tylertilly said:**
> Would a bad hard drive cease my DVD drive from working though?

I'm just wondering if I have to plug the sata cables in, in a certain order. Or like configure something that I'm missing. Cuz I figured if it was just a bad hard drive, my DVD drive would still work while they are both connected.

Yes, depending on the computer. They can affect other drives when they go. I've even had cases where the computer won't even start.

The thing with SATA is there's nothing to screw up. One drive, one cable, one controller.  It doesn't actually matter which drives are plugged into which controller.

---

### Post by tylertilly on 2008-01-04
guess it is time to RMA. and i was so excited to get my computer going :(

---

### Post by shad0w_walker on 2008-01-04
The DVD drive will let you run the Ubuntu disc until you plugin the hard drive? Have you checked in your BIOS to make sure that the hard drive hasn't just taken boot priority. If it has then it is possible that the system will hang up looking for something to boot on the hard drive.

---

### Post by tylertilly on 2008-01-04
see that is what i thought too, but the thing is, on boot order, or whatever, in the bios, i have it set to > CD/DVDROM then HDDRIVE then REMOVABLE. i even got rid of HDDRIVE and REMOVABLE all together and just put CD/DVDROM, but that still happens.

---

### Post by shad0w_walker on 2008-01-04
That's really weird. Have you had a look around for a BIOS update? It maybe some some strange bug in your BIOS (Had one for my system and ACPI)
Also, have you got a spare DVD or hard drive just to test the setup with? Might be that it won't boot with all SATA but works fine with all SATA after you have managed to install it using a regular IDE drive.

---

### Post by tylertilly on 2008-01-04
maybe i could buy a cheap IDE drive and try that. i sort of don't want to deal with the hassle of RMA'ing.

---

### Post by tylertilly on 2008-01-04
Oh and I tried updating the bios, but it failed and I had to revert back to the CD Bios, which is even older than the bios the mobo came with. That's really aggravating, because now Ubuntu won't even load because the integrated graphics chip works shittier with the old bios. so i figured i'd just throw a video card in there, since i'm going to be needing one eventually anyway.

But yeah it's really odd that it works w/ a sata cd drive, but when i put in my HDD my cd won't boot. That's why I'm sort of nervous about RMA-ing, because what if my hard drive isn't bad and I just waited 1-2 weeks, spent 10 more dollars on shipping, all to no avail and my hard drive was actually fine. that's what bugs me the most.

---

### Post by Paulmd on 2008-01-04
> **tylertilly said:**
> Oh and I tried updating the bios, but it failed and I had to revert back to the CD Bios, which is even older than the bios the mobo came with. That's really aggravating, because now Ubuntu won't even load because the integrated graphics chip works shittier with the old bios. so i figured i'd just throw a video card in there, since i'm going to be needing one eventually anyway.

But yeah it's really odd that it works w/ a sata cd drive, but when i put in my HDD my cd won't boot. That's why I'm sort of nervous about RMA-ing, because what if my hard drive isn't bad and I just waited 1-2 weeks, spent 10 more dollars on shipping, all to no avail and my hard drive was actually fine. that's what bugs me the most.


You got access to another computer with SATA? You could try your hdd in it.

---

### Post by tylertilly on 2008-01-04
That's just it, the other two computers I have are laptops, and my friend's computers are all older than sin because we're just a bunch of broke college kids v_v.

basically im S.O.L.

All I can say is when I turn on my comp, the HD whirrs and spins, and the HD light turns on and is pretty much constant, then it just hangs for a while, and then stops spinning, and the comp goes into a blank screen (if i don't hit the bios button). but, take out the hard drive, pop in the ubuntu cd, and the comp turns right on and the ubuntu screen is there.

i'd be more sure it was just the hard drive and not some sort of bios/mobo problems if the damn thing wasn't making my dvd drive not work.

you can see why it's aggravating, since i sort of don't have a way to test it on another computer heh.

thanks for all the help by the way, everyone.

---

### Post by Paulmd on 2008-01-04
> **tylertilly said:**
> That's just it, the other two computers I have are laptops, and my friend's computers are all older than sin because we're just a bunch of broke college kids v_v.

basically im S.O.L.

All I can say is when I turn on my comp, the HD whirrs and spins, and the HD light turns on and is pretty much constant, then it just hangs for a while, and then stops spinning, and the comp goes into a blank screen (if i don't hit the bios button). but, take out the hard drive, pop in the ubuntu cd, and the comp turns right on and the ubuntu screen is there.

i'd be more sure it was just the hard drive and not some sort of bios/mobo problems if the damn thing wasn't making my dvd drive not work.

you can see why it's aggravating, since i sort of don't have a way to test it on another computer heh.

thanks for all the help by the way, everyone.


Here's the thing.  You can get into a lot of trouble trying to make something work, that just won't. 

You can try changing controllers (there are only so many) or  flipping the sata cable around end to end or plugging in the hard drive without the cd, and seeing if it shuts itself down.   If you have some sort of raid capabilities, you can check make sure that raid is not enabled.

Beyond which, it is virtually certain you have a bad hard drive.

If changing controllers actually works, you get to rma your motherboard instead of your hard drive (what fun).

---

### Post by tylertilly on 2008-01-04
Thank you very much for the reassurance. I have flipped cables, changed cables, and switched ports and still just get whirring then stopping.

When you say 'change controllers' do you just mean plug it into a different SATA slot/port/whatever? Because I've done that as well. If it means something else, then by all means explain :)

Well I have reason to believe it's not the motherboard since the SATA ports work on my CD/DVD drive.

Hopefully it's just a bad hard drive. I'll RMA.

Thank you very much for the hep, Paulmd.

---

### Post by Paulmd on 2008-01-04
> **tylertilly said:**
> Thank you very much for the reassurance. I have flipped cables, changed cables, and switched ports and still just get whirring then stopping.

When you say 'change controllers' do you just mean plug it into a different SATA slot/port/whatever? Because I've done that as well. If it means something else, then by all means explain :)

Well I have reason to believe it's not the motherboard since the SATA ports work on my CD/DVD drive.

Hopefully it's just a bad hard drive. I'll RMA.

Thank you very much for the hep, Paulmd.

Yes, I meant change sata ports.

---

### Post by pieterjanvu on 2008-01-04
Was just thinking of when i built my PC, i had to put in this little piece on the side of the hard drive to classify it as primary and not as slave, maybe thats the problem, not sure, its been quite a while ago maybe sata doesn't need it

---

### Post by tylertilly on 2008-01-04
As far as I know, SATA requires no jumpers, and there is no primary/slave, because its just one cable plugged into one port. That's why I got a SATA drive because I figured it would be super easy heh. So much for that :)

Oh well, I just got a newegg RMA number and I'll be driving to UPS to drop it off on Monday. Thanks :)

---

### Post by Paulmd on 2008-01-04
> **pieterjanvu said:**
> Was just thinking of when i built my PC, i had to put in this little piece on the side of the hard drive to classify it as primary and not as slave, maybe thats the problem, not sure, its been quite a while ago maybe sata doesn't need it

Sata drives to not need jumpers to ID them. There being only one drive per controller.

---

