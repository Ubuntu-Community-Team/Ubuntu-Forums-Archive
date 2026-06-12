---
title: "Can't get Ubuntu 6.06 installed. HELP PLEASE!"
date: 2007-05-09
forum: Apple PPC Users
---

### Post by wildazndude on 2007-05-09
Greetings. My name is William. I am a Mac/Linux newbie. Been using x86/Windows all of my life. I recently purchased an iMac indigo G3 500MHz with 256MB RAM, 20GB HDD, and a slot-loading CD-ROM drive. It has Mac OS X 10.1 installed. So far, it's been a hoot for me, owning a Mac, even if it's a legacy system.

I have never used Ubuntu, so this will be all new to me. Here's the problem at hand.

I requsted for a copy of Ubuntu for the PowerPC via [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

I received the Ubuntu version 6.06.1 LTS for your Mac.

I followed the instructions as stated on this post...
[http://ubuntuforums.org/showthread.php?t=377942](http://ubuntuforums.org/showthread.php?t=377942)

Here is a snip of the instructions...
1. Boot up live CD holding down the C until the screen goes black and you hear the cd running. In your post you were having problems booting from the CD. I had a defective keyboard the first time I had this problem. Try switching keyboards if possible. (By the way, I'm using both a windows keyboard and mouse on my imac). I used a CD-RW disc that I recorded in Windows and finalized and didn't have any problems.)
2. At prompt type: live-powerpc
3. After loading everything the screen goes blank and you hear the CD running for about 2 - 3 minutes before you hear it stop,
4. Press CRTL-ALT-F1. This brings up the command line.

So, everything is loaded, the screen goes blank, I do hear the CD running for roughly 2 minutes, and before I hear it stop, I press the CONTROL key, the ALT/OPTION key, and the F1 key.

The screen remains blank for about a minute. Then, the following message is displayed:

Authentication token is no longer valid; new one required.
You are required to change your password immediately (root enforced)

Authentication token is no longer valid; new one required.
You are required to change your password immediately (root enforced)

Authentication token is no longer valid; new one required.
You are required to change your password immediately (root enforced)

Authentication token is no longer valid; new one required.
You are required to change your password immediately (root enforced)

Authentication token is no longer valid; new one required.
You are required to change your password immediately (root enforced)

And it sits there. I press the ENTER key. The press the ESC key. Nothing. I press CTRL+ALT+F1 again. Nothing.

Then it says...

Authentication token is no longer valid; new one required.
 * INIT: Id "1" respawning too fast: disabled for 5 minutes
 * INIT: Id "2" respawning too fast: disabled for 5 minutes
 * INIT: Id "3" respawning too fast: disabled for 5 minutes
 * INIT: Id "5" respawning too fast: disabled for 5 minutes
 * INIT: Id "6" respawning too fast: disabled for 5 minutes
You are required to change your password immediately (root enforced)


Authentication token is no longer valid; new one required.
 * INIT: Id "4" respawning too fast: disabled for 5 minutes
 * INIT: Id "2" respawning too fast: disabled for 5 minutes
You are required to change your password immediately (root enforced)

So... I sit here, waiting for something to happen. CTRL+ALT+F1 again. Nothing.

Now it says...

Authentication token is no longer valid; new one required.
 * INIT: Id "1" respawning too fast: disabled for 5 minutes
 * INIT: Id "3" respawning too fast: disabled for 5 minutes
 * INIT: Id "5" respawning too fast: disabled for 5 minutes
 * INIT: Id "6" respawning too fast: disabled for 5 minutes

Sigh. I downloaded the Alternate CD from [http://releases.ubuntu.com/6.06/ubuntu-6.06.1-alternate-powerpc.iso](http://releases.ubuntu.com/6.06/ubuntu-6.06.1-alternate-powerpc.iso)

I used Nero to burn the Alternate CD ISO to a blank 700MB CD-R.

I inserted the copy of the Alternate CD into the slot-loading drive on the iMac and it keeps rejecting it. Insert, it spins for roughly 10 to 20 seconds, and it spits it back out.

So I used a different CD-R, burned the ISO to this new CD-R, insert it into the iMac slot-loading drive, and it does the same thing. Rejects my CD-Rs.

When I insert the copy of Ubuntu version 6.06.1 LTS for your Mac into the slot-loading drive, it stays there. I restart the computer, press C, type live-powerpc at the boot prompt, it goes through the loading screen, screen goes blank, wait 2 minutes, press the CTRL+ALT+F1, and those weird messages show up. 

Authentication token is no longer valid; new one required.
You are required to change your password immediately (root enforced)

What is happening?

---

### Post by wildazndude on 2007-05-09
I found the solution. Looks like the DATE and TIME setting for the iMac is wrong. All I did was set the date and time to the correct and current date and time and it worked perfectly. Thank you, Jazzman, for the proper instructions.

---

### Post by stmiller on 2007-05-09
Be sure to check out the PPCFAQs at the link below. Lots of other PowerPC tidbits. Welcome!

---

