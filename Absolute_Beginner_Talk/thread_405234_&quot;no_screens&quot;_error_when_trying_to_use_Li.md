---
title: "&quot;no screens&quot; error when trying to use LiveCD"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by AgelessDrifter on 2007-04-09
Hi there. I'm trying to install Ubunto edgy 10.6 on a Dell E510 that currently has WindowsXP on it.

Every time I run the LiveCD, I get through the "install/run ubuntu" menu screen, through the subsequent loading screen, and then an error message takes over. The screen that I receive the error on is text-based (the scroll bar is filled with strange characters and whatnot -- it basically looks like a malfunctioning NES). The error itself is something to the effect of (but unfortunately I'm not 100% on this) "Xserver, your graphic interface, failed to load. It is likely that it is not set up properly. Would you like to view [somethngorother] to diagnose the problem? Y/N"

When I select yes, it gives me a lot of jargon, but at the bottom, I remember that it says "fatal server error: no screens". Somewhere amidst the jargon it said "before filing an error report, make sure to check x.org to see that you have the latest version", but I don't know to the latest version of what, exactly, this message refers.

I perused the X.org forums and a few other places, using what I could remember of the error message as the search terms. I came up with a few results of people having the same problem, though most said that it had happened to them on a box that had already been running Linux for some time. Those in the know offered a number of command-line solutions, all of which I tried out, and seemed to illicit some promising feedback, but ultimately, when I rebooted, any progress I may or may not have made by using these commands seemed to have been lost.

I assume that's because the OS is running from the LiveCD, and therefor nothing in it's coding will remain altered after a reboot since it's not written to the disk. I dunno, though. And I don't know if the problem I'm having is exactly the same (though it truly seemed it) as the one I found solutions for. I don't know if my problem is a compatibility issue, or a problem with the specific version of ubuntu I got, or what. Anyway, it wound up becoming a huge mess with me trying a number of ill-informed routes to get around the problem, ultimately resulting in me having to reformat my original partition and re-install windows, which I have just finished doing. Does anyone have any suggestions? I thank you sincerely in advance.

---

### Post by mand0 on 2007-04-09
Try looking at [this]("http://ubuntuforums.org/showthread.php?t=293242") thread. If that doesn't help you there are many like it with the same problem.

---

### Post by AgelessDrifter on 2007-04-09
I'm embarrassed to say that's a little over my head, if only because "change the PCI part to where the video card is located" I don't have the foggiest idea how to find that out, or what the parameter would look like. 

Also, once I make those changes (mentioned in the thread you linked), how do I resume the installation without rebooting? It seems like when I reboot I lose any changes I've made, and I wind up starting from scratch.

Thanks again.

---

### Post by mand0 on 2007-04-09
Okay, let me try to explain this myself.  When you get to the menu list where you choose to install or not press alt+F1 to get to a prompt then type:

```
sudo dpkg-reconfigure xserver-xorg
```

Be sure to choose vesa as your graphics driver, instead of ati of nvidia.

---

### Post by AgelessDrifter on 2007-04-10
Well a few others had already recommended that, and I think it may well work, but the problem is that once I get to the end of all the prompts that the "reconfigure" command brings up (selecting video card, selecting keyboard layout etc), it returns me to the command prompt, but the installation does not resume, and the LiveCD doesn't run. How do I run the LiveCD from this point to see if the changes I've made through reconfigure actually make a difference? The only thing I could think to do was sudo reboot, and when I do that I basically throw all my changes out the window.

---

### Post by AgelessDrifter on 2007-04-10
Sorry for the double-post, but this is pretty much my last shot at getting an answer to this question.

---

