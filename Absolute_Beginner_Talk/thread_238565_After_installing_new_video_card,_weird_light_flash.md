---
title: "After installing new video card, weird light flashes and won't let me turn on the PC!"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-08-17
okay so I had a radeon 9800 pro 128 mb card, which I installed a zalman VF700 Al-Cu fan/heatsink on. the 9800 pro ended up not working (it got scratched) so i bought a new card, a radeon x1600 pro 512 mb. i installed the VF700 Al-Cu fan on it (so yes i took it off of the 9800 card) before installing it in the computer. so, finally i installed the card (and is it me or does this card not have a power slot?) but i cannot turn on the computer! it won't let me! the little tiny light on the back of the computer, the one next to the power supply's fan thing, keeps on flashing, even though it's normal behavior is to be constant.

wtf??????!!!!!!!!

edit:  here are the system requirements from the ati website:[LIST]
[*]AGP 8X or 4X graphics slot available on the motherboard
[*]Connection         to the system power supply is required (Adapter Included)
[*] 350-Watt power supply or greater recommended (assumes fully loaded         system)
[*] 512MB of system memory
[*] Installation software requires CD-ROM         drive
[*] DVD playback requires DVD drive and decoder software             (not included)[/LIST]I have an AGP 8X/4X slot, and that's where i installed it. 

Connection to the power supply?  i don't see anyplace on the card that could possibly connect to the power supply!

ionly have a 250 W power supply, but the requirement says "recommended" not requirement.

i have a Gig of RAM, so no problem there.

i can just download drivers online (btw, i have my 9800 pro drivers installed on the machine, but its the same driver for my new card (ati catalyst software)

and yes i have a dvd-rom

and yea i posted this thread in three different places, not to be a pain in the butt, but because of my urgency.

---

### Post by daou on 2006-08-17
AArgh... I wrote a reply so long that the browser at work logged me out and ctrl-c somehow didn't copy the contents of the textbox. :( Let's try again.

Anyway, there a couple different possibilities. When you say it doesn't turn on, does that mean no motherboard LEDs (including the power-on LED) are turning on?

If for example the power-LED turns on at some point, it probably means there is a problem with the video card. Check to make sure its firmly in the AGP slot and if you have notches to secure it, make sure they are closed. You might even want to take it out and put it back in to make sure. If this doesn't help ask a friend if you can put your card in their AGP slot to see if their computer will turn on.

If no LEDs are turning on, its probably a motherboard or power supply issue. Make sure you didn't accidentally bump into any power supply wires inside the comp when changing video cards.

One thing that worries me is the 250W rating on your supply. It might not be enough. When the manufacturer recommends a certain amount, it might mean you need that much or just about. I bet they didn't specify a minimum ;-). Different computers have different power needs and there is no way that the manufacturer will know exactly how much you need. Different processors, memory, motherboards, etc take different amounts of power. It also depends on the number of your hard drives and other peripherals. If your components are sucking the max amount of current your supply can give, then some components might not be getting enough to function properly. A computer is not a lamp. It either works or it doesn't. There are no in betweens, like different intensities on a lamp depending on the driving voltage.

If you have a voltmeter and know how to use it, you could check that the power supply is indeed working (this will not establish whether its rating is high enough, just whether it works or not). Or you could ask a friend over to bring his mega power supply and see if your system works with it :D .

---

### Post by daou on 2006-08-17
You mentioned you couldn't find the power connection... perhaps that is the problem after all.

[IMG]http://www.mvktech.net/images/reviews/pcx16proagp/pc-x16agp-bg-17.jpg[/IMG]

See the white thing at the bottom corner. Try that if you have one.

---

### Post by arsenic23 on 2006-08-17
Ok, yeah, your more then likely need a slightly meaner/sturdier power supply.  But not necessarily.  First off if you could post the make and model of your power supply I might be able to make a more educated guess in that direction.

Also on an AGP x1600 pro 512mb the power connector to the card should look something like one of these:
[IMG]http://img220.imageshack.us/img220/2510/untitledon8.jpg[/IMG]

There should be one, and if it's not connected I'm fairly certain it would/could prevent you from booting.  Otherwise the power supply should more then likely be replaced.  But I've seen some good 250PSUs that pull and act much better then their numbers.

---

### Post by user1397 on 2006-08-21
okay i have solved this issue, it was a PSU issue after all.  i went to a used PC parts vendor, got me a 400W PSU, installed it, and everything works fine.  I was able to connect my graphics card and my graphics card's fan to the power supply, so no worries.  everything's running fine (though a bit noisy :p)

---

