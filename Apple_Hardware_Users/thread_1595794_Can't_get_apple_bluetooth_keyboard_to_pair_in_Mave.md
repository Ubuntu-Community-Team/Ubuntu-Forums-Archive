---
title: "Can't get apple bluetooth keyboard to pair in Maverick"
date: 2010-10-13
forum: Apple Hardware Users
---

### Post by crazygoose on 2010-10-13
Hi All,

I think my computer must be haunted, as I've so far failed at 3 different ways of installing Maverick on my 2007 aluminium imac! I've written off using a VM, and I'm currently stuck trying to make a dual boot setup.

So I've followed the guide at [https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac), and got as far as rebooting with the CD in, and selecting Ubuntu, but then when everything loads I'm left at the screen where I can select try or install, with no way of selecting either as my mouse (apple bluetooth mighty mouse) and keyboard (apple bluetooth wireless aluminium keyboard) don't seem to be connected. I've got past this point by hitting random keys after booting and selecting the CD - this takes me into a more basic looking menu where the keyboard does still work and I can select install, try etc.

So I can get as far as selecting try, and get a working Ubuntu desktop. However, when the desktop loads, my keyboard and mouse are again not working. By connecting a USB keyboard and mouse, I'm able to get my mouse to pair, using the bluetooth menu and going through the setup. However, I'm stuck trying to get my keyboard to pair.

Going into set up new device and searching initially shows up my keyboard, then it disappears. If I wait it randomly comes back and disappears again. If I click on next whilst it is available, I can get as far as putting in a pin, but when I press enter it says Failed..

Sorry for the rambling post - I basically have 2 questions:
1- Is it expected that bluetooth keyboards and mice won't work during the installation menus? Half my problem is that I don't know what should be working and when (should I have to boot into the trial installation and setup the keyboard and mouse, or should it be set up automatically?).

2- Has anyone else seen the same problem with the apple wireless keyboard failing to pair? I've searched the forums and google, and found lots of people with problems with bluetooth keyboards, but none which seem to match what I'm seeing. I don't know if there's any point in pressing on with the installation using the USB keyboard and mouse in the hope that things will work in the full install, or if they don't work in the trial install then thats my lot.

Thanks in advance,
Max

---

### Post by pc_michael on 2010-10-13
It took a couple of tries for me to get my Apple Wireless Keyboard to pair as well.  Try turning it off, waiting ten seconds or so and turning it back on so that it's definitely discoverable.  Same goes for the mouse.

Note that once you do successfully pair it with Ubuntu, you'll have to pair it again with Mac OS X next time you boot into Mac.  But that will only happen the initial time.

---

### Post by crazygoose on 2010-10-15
Hi,

Thanks for the advice. I ploughed on with the install, and have got everything working now in my full install :D. I think it was just being fiddly, as you suggested - initially I had the same problems, but I kept going and it worked eventually. I think the trick was to wait a while after the keyboard was found before clicking next.

Thanks for the help - glad my computer isn't actually haunted!

---

### Post by pc_michael on 2010-10-15
Sounds good.  Have fun!

---

### Post by whoawilly on 2010-10-21
> **crazygoose said:**
> 
I'm stuck trying to get my keyboard to pair...

Going into set up new device and searching initially shows up my keyboard, then it disappears. If I wait it randomly comes back and disappears again. If I click on next whilst it is available, I can get as far as putting in a pin, but when I press enter it says Failed...


Hi,
This is happening to me too. Except, Ubuntu is installed. I add /etc/init.d/bluetooth to the startup applications and my magicmouse started working but my keyboard still won't pair.

thanks for your help.

---

### Post by smoors on 2010-10-22
Hi!

I had the same problems with the wireless keyboard, it just kept disconnecting after pairing. The problem was that i entered the key the wrong way. IIRC, you have to enter a key first with your *wireless keyboard* and finish it with "enter". Then, a dialog should appear which says that you should enter the key again. Now take your built-in keyboard(if you're doing this on a laptop) and enter the same key that you entered on the wireless one. I did that some month ago, since then it works totally flawless, like in OS X.
Hope that helps!!
- Sebastian

---

### Post by whoawilly on 2010-10-22
That worked!
thank you!

---

