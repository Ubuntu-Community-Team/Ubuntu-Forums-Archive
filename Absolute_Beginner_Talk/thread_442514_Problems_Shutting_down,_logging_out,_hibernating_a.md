---
title: "Problems Shutting down, logging out, hibernating and suspending Edgy"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-05-13
It doesn't look like Edgy likes me turning it off.

When I click the red power button on the top-right corner and the window pops up with the log off, hibernate, etc options, the 'Shutdown' is conspicuously absent. For a couple weeks i'd been getting by with logging off and then choosing shutdown from the login screen, but recently even that stopped working. When I click log off it first just shows the default ubuntu background (with nothing else on the screen) and when I push the power button on my computer the screen turns orange with a white rectangle where the text box is supposed to be on the log in screen, and I have to force a shutdown on my pc.

Also, whenever I get it to hibernate it just turns the screen black and has a login window in the center (not the same as the login screen), goes to hibernate mode for a couple seconds and then comes back to the login window.  And when I tell the computer to sleep it turns on the screen saver and when I move the mouse it goes to what appears to be sleep mode except I cannot get out of it (I tried pushing the power button and everything).

This might have something to do with the theme I've switched to using the Beryl Theme Manager, but I can't figure how how I changed the themes in the first pace (I found the Beryl and the Ubuntu theme managers, but with the Beryl theme manager I had managed to change the default human theme a bit, but I can't figure out how to revert it)

Any help?
:confused:

---

### Post by Happy_Man on 2007-05-13
Beryl themes can be accessed by right-clicking on the gem icon and selecting "emerald theme manager." Of course, if you mean the version stocked with Ubuntu, go into System-->Preferences-->Themes and scroll to select "Human."

---

### Post by zhinker on 2007-05-13
Yeah, I've got the human theme selected in System-->Preferences-->Themes , but in the emerald theme manager I had changed the theme to change the colors a bit and I couldn't figure out how to change it back.  But that's irrelevant, I just threw that out because someone mentioned changing my theme might have caused my other problems

---

### Post by palmdoc on 2007-05-21
OK I have done a clean install of Ubuntu 7.04 on a Pentium 4 1.7 GHz system and 40 GB HD which previously had XP Pro but I have reformatted the disk and it's from scratch.
Nothing installed except Ubuntu updates as prompted by the system
When I try to shutdown, the system hangs at the Ubuntu Logo (the progress bar is black)

Please advise this newbie how to troubleshoot

Many thanks

---

### Post by palmdoc on 2007-05-23
Bump. Anyone?

---

### Post by vanadium on 2007-05-23
Ubuntu Feisty is known for issues with hibernation. On my Dell Latitude D800, I can properly hibernate. It worked properly with Ubuntu Edgy. Yet I do not have issues with shutting down, except for X-server not wanting to shut down after I have uses XMMS. I then need to kill X-sever using Contrl+Alt+Backspace to continue a normal shutdown.

Next to posting your question in this forum, search, search, search. Most of us are ordinary computer users and we do not always have a ready answer to particular problems.

To comfort you, as the graphical bar is completely black, the system probably shuts down properly, however the power is not turned off, i.e., the system is not properly halted.  Thus, pressing the power button yourself should not hurt.

Adding  "acpi=force" to the grub kernel start line is something you might try: see here:

[https://answers.launchpad.net/ubuntu/+question/6522](https://answers.launchpad.net/ubuntu/+question/6522)

---

### Post by palmdoc on 2007-05-25
Many thanks
The acpi=force did the trick for me
I did search and search the forums buts it's all quite disjointed and not easy to find
ANyway I finally also found this thread with the same solution

[http://ubuntuforums.org/showthread.php?t=422017](http://ubuntuforums.org/showthread.php?t=422017)

---

### Post by JesterGr on 2007-05-26
This acpi=force didn't solve my prob with hibernating. Got any suggestion in mind, or a place to look ?

---

