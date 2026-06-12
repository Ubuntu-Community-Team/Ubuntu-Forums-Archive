---
title: "Almost at the end PCI USB"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by catch2two on 2008-03-19
Been using ubuntu for 1 year on my desktop, little less on my wifes lap top, and fedora for my server. No dual boot just straight linux.

After the constant arguments with my wife, and numerous issues along the way. Turning a blind eye to things i really wanted, but lived without am i nearly at the end of my linux days?

I actually had wireless once on my lap top did the upgrade to gutsy and no more. It all looks to work it just does not. My wife has been amazing she has actually given up wireless and we have a cord across the lounge so i can use linux. 

I also once had a super cool 3 d cube on dual screens, but alas it just one day decided not to work and no more cool cube.

**The Actual  Issue**

So it seems all my usb ports stopped working after using an ipod (i think linux may not have been unmounting the dives properly) Anyways i have tried a live version of linux and still no usb. This leads me to believe that are toast. 

I just purchased a pci usb hub is this something i can get to work???

Help it does not just auto detect it.

If anyone can let me know if this is going to be easy or should i start looking to replace my new mobo???

Thanks,

Catch2two

---

### Post by Hospadar on 2008-03-19
Probably that pci card needs specific drivers which (it would seem) linux does not have.  If the manufacturer does not provide linux drivers, I would suggest you:

Find a manufacturer that does provide linux drivers, and exchange your card for one of theirs.  I just installed a rosewill pci serial port adapter which did have linux drivers on it's driver cd.  So maybe look into them.

Do you know if your usb ports will run in windows? how about a different distro's livecd?

Your motherboard may already have some jumpers (not actually jumpers, they just look like jumper pins for extra usb ports.  look around on your motherboard (probably somewhere on the south end, near the pci slots, it should say "usb" on the board near the jumper panel).  These are generally designed to connect front-panel usb ports, although often they go unused or there are extras.  You will need a usb connector like this:
[http://www.silverpcs.com/images/front_usb_connector_a.jpg](http://www.silverpcs.com/images/front_usb_connector_a.jpg)
on the mobo it will look something like this:
[http://www.windowsdevcenter.com/windows/2005/02/23/graphics/figure14.jpg](http://www.windowsdevcenter.com/windows/2005/02/23/graphics/figure14.jpg) (after you plug in the connector)
This could work, but if the usb controller on the mobo somehow got fried, it probably won't.  If you need a usb connector like this for cheap, try ripping one out of an old case, any case with front panel USB should have a connector like this.
Ask around, check the communtiy documents, etc, and see if anyone can confirm a specific model of pci usb connector working with their machine, then try to get your hands on that model.

it might be possible that your usb ports are just burned out on the mobo, it happened to a friend of mine after plugging his power supply into the aux power out for a video card.

I'm also not totally sure about this, but it may be that pci usb ports are controlled by the mobo usb controller, in which case a pci card wouldn't help, if you have the opportunity you might try using your pci usb card in a different tower w/ a livecd.  If this turns out to be the problem, the only thing to do I think would be to get a new mobo.

Also, it might be helpful if you could post the output of the "lspci" command with the pci usb plugged in

---

