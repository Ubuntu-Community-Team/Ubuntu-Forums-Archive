---
title: "Just installed ubuntu, locks on startup"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by virgilnilson on 2007-05-26
Hi, I just finished installing ubuntu 7.04 alternate x86 on my other computer (AMD64, x850 video card) and upon first attempt to boot up after the install, I got to the menu that asks me to enter my username, i had a sound play, then when i tried to move my mouse or type, neither would respond and I concluded that my computer had frozen up.

So I tried again and this time after the loading splash all I got was a black screen.

I followed all of the directions in the ATI Xxxx sticky, all seemed to go without a hitch. I rebooted, once again black screen. I rebooted again twice more and both times I got to an orange backdrop with a little white circle in the middle and it would then just hang there indefinitely.

Anyone know how I can fix this? Thanks in advance.

---

### Post by BOOBOOJS on 2007-05-26
Without complete system specs I'll have to take a guess.
Seems similar to my laptop(also AMD based)
Mine has a faulty bios try booting with noapic.

1. Just highlight the standard boot option in grub when your computer starts up and hit e
2. If you have a grub password set them you must hit p and give your password before using e
3. find the line that starts with kernel and add noapic to the and of it
4. hit enter to save and press b for boot

If that works do the following after your system boots

1. log in and press alt + f2 to open the run dialouge 
2. type gksu gedit /boot/grub/menu.lst
3. find the same line as before and add noapic there as well
4. save and your done

If this does not work then reply with more info and me or someone else in this forum will help you

---

### Post by virgilnilson on 2007-05-26
Thank you for the response, I did as you suggested and once again I got through the splash and then was just greeted by a frozen orange backdrop and loading mouse cursor in the middle.

As for more information I'm not sure what you would need. I am running an nforce 3 motherboard, AMD 64 +3200 processor, ATI x850 video card, two hard drives (the slave has not yet been formatted and is still fat32), 1 gig of ram.

Thank you again for taking the time to help me.

---

### Post by virgilnilson on 2007-05-26
I have now tried the suggestions in this bug report

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853")

(the ones in the original message regarding xserver reconfig and using a vesa driver)

and the problem remains apparently exactly the same.

---

### Post by virgilnilson on 2007-05-26
After unplugging my slave drive it seems that I now make it all the way to the "username" screen every time, I see the prompt pulse once or twice in the box, am even able to move my mouse for the first two or three seconds, then I hear the sound, and then it all freezes.

I am running onboard realtek ac97 for my sound, if this could possibly be another part of the puzzle.

Edit: I take this back, after 3 or 4 consecutive boots all the way to the username entry, I am now back to freezing at just an orange background and loading cursor.

---

### Post by virgilnilson on 2007-05-26
As I was typing the last message, my other computer was off. I went back and tried once again to boot, this time intent on trying to log in before it froze, the first time it simply froze at the loading cursor again, the second time however i managed to log all the way in. Sitting there, ecstastic, I waited for it to freeze any second but everything seemed to be running fine.

So I started checking everything out and tried to fiddle with the resolution (the maximum was 1024, although I have a widescreen monitor capable of 1680x1050) I clicked help and searched around there to see if there was any information on how to raise this limit. Finding nothing I closed the window and it then suddenly froze.

I estimate the total usage time after logging in was around a minute or a little more.

---

### Post by virgilnilson on 2007-05-26
Trying again and again with different approaches, I now unplugged my printer and speakers and tried again to log in before a freeze. This time I made it halfway through typing my password before it froze and then something that had not ever happened before, did, a blue checkered bar appeared across the top of the screen, roughly 1/10-1/15th of the total monitor height wide.

Sorry if this is spammy, I'm just trying to keep this thread up to date with all of my attempts so people could possibly better understand my problem.

---

### Post by virgilnilson on 2007-05-26
My computer may just be haunted.

Two more reboot attempts yielded freezes during the actual splash screen, something that had not happened before.

During the second one I left to go take care of something, came back and it was still frozen and decided to try to reset my cpu clock to its factory setting (it was slightly overclocked), so i unplugged my USB keyboard and as I did so the splash screen suddenly started again and finished, only to freeze again at the orange background/loading cursor.

So anyway I proceed to reset the clock to normal and this has not fixed the problem.

---

### Post by alienexplorers on 2007-05-26
You may have downloaded a faulty iso file.  My suggestion would be to redownload the iso and reburn it at 4x.  See if that helps.

---

### Post by virgilnilson on 2007-05-27
SOLUTION: AMD K8 Cool N Quiet must be disabled in bios.

---

