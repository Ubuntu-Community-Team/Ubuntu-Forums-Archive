---
title: "twinview/meta mode"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by davidwrocklage on 2008-01-16
I have uploaded the Nvidia drivers, twinview enabled, everything was fine.  Unfortunately I'm curious, I found under system>administration>screens and graphics... so I thought what could I hurt. I managed to change my settings to separate x screen but I didn't like it so I wanted to go back to twinview. trying to go back screwed up everything with resolutions so I uninstalled and re-installed Nvidia from restricted drivers like I did before, this fixed my resolution on my default monitor, then I went to set up twinview and when I tried to apply I got this message

Failed to set MetaMode (3) 'CRT-0: 1280x1024@60 @1280x1024 +1024+0, CRT-1: 1024x768 @1024x768 +0+0' (Mode 2304x1024, id: 96) on X screen 0

Would you like to remove this MetaMode?

could someone please help me un-fubar this situation.

I'm very new to Linux, about 3 days so please be gentle

I tried to find a similar situation on the forums, but most solutions pointed to what I had already done.

I also have the problem that I have no idea how to make the changes to my screen setup permanent, whenever I restart my box, the second monitor is off and I have to reconfigure nvidia. I'm sure there is a step I'm missing.

if this has anything to do with "save to x configuration file" I'm recieving this message

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

lastly I have seen some people request to have a forum set to "solved" I would like to be able to do this to conform to the way this forum is set up, but have no idea how to do so.

Thanks in advance

btw so far I'm very impressed with Ubuntu 7.10 and don't regret leaving xp behind

---

### Post by amo-ej1 on 2008-01-16
I'm assuming you're using the 'nvidia-settings' tool to configure your x-server. Well you get the error that it is unable to save the file because you're running that tool as your standard user which isn't allowed to write that file. So you could open a terminal window and type 

```

sudo nvidia-settings

```
Then enter your use password, configure your display as you did before and then you'll notice that the tool will be able to save the configuration file.

---

### Post by Hospadar on 2008-01-16
I had all kinds of effin wierd issues with those stupid nvidia meta-modes, the way I finally resolved it was by wiping my xorg.conf with "sudo dpkg-reconfigure xserver-xorg" (make sure you select "nvidia" instead of "nv" on the first page!) and then going to nvidia-settings and setting them up exactly the way I wanted the first try.

If you're feeling daring you could go into your xorg.conf and delete the extra meta-modes manually, but I think that's the hard way personally, and more work than needed.

On a side note, if you are running "nvidia-settings" manually (either from a terminal window, or by Alt-F2 and typing "nvidia-settings" you'll need to prepend it with "sudo" (for a terminal) or "gksu" (for Alt-F2) so that the command looks like "sudo nvidia-settings" or "gksu nvidia-settings" this will allow the settings manager to edit system files like xorg.conf (which it needs to be able to do) by giving it root privilege. that should clear any "unable to write to xorg.conf" issues

As for setting to solved, just edit the title of your post to include "solved"

---

