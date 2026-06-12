---
title: "New kernel updates"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by jmasgalas on 2007-05-28
OK so I just installed a dual boot setup. Had Ubuntu workijng perfectly yesterday with the nvidia drivers and beryl. Configured everything the way I wanted it and was really liking everything. Today I was prompted for an update. I take the updates and reboot. A blank screen comes up. So I restart in recovery mode. Uninstall the Nvidia drivers. Take Beryl out of startup. This gets me able to log into my desktop. However now everytime I install the Nvidia drivers I get to the blank screen when I reload xdesktop. Can anyone help me? Will I have to go through this with every kernel update? Thanks!

---

### Post by daverich on 2007-05-28
I seem to remember that sometimes (depending on how you install them) you need to redo the video drivers after every kernel update.

Kind regards

Dave Rich

---

### Post by starcraft.man on 2007-05-28
> **jmasgalas said:**
> OK so I just installed a dual boot setup. Had Ubuntu workijng perfectly yesterday with the nvidia drivers and beryl. Configured everything the way I wanted it and was really liking everything. Today I was prompted for an update. I take the updates and reboot. A blank screen comes up. So I restart in recovery mode. Uninstall the Nvidia drivers. Take Beryl out of startup. This gets me able to log into my desktop. However now everytime I install the Nvidia drivers I get to the blank screen when I reload xdesktop. Can anyone help me? Will I have to go through this with every kernel update? Thanks!

Right, I installed that update today too. It was a new linux kernel image. I am not sure exactly what was changed in the new kernel we got (I would like to know if someone can point to where I might find out), however, the old kernel is always left installed and in the GRUB menu. It is usualy right under, the top two in your menu should be the new one ending in 16, the old one is right under 15. You can boot up in that one and it is your old kernel, that should fix any problems you are having.

I assume that some changes made in the new kernel have unexpected effects on your hardware. We'd have to know more about your specific set up and I'd have to know what was changed to be of more help. So boot up in the old version and reinstall nvidia and beryl, it should work.

You can edit the boot list later, assuming it gets working. Hope that helps :).

Edit: Oh and if i remember correctly, this command gets you to open up the boot list, you can then comment out the bad kernel until you find a way to fix it.

```
gksudo gedit /boot/grub/menu.lst
```

Be careful when editing the GRUB, if you mess it up bad you'll need the live CD to fix it.

Oh and [here]("http://ubuntuforums.org/showthread.php?t=456702&highlight=edit+boot") is a link to other people having issues with latest kernel.

---

### Post by bloodniece on 2007-05-28
Try doing the kernel update, then reconfigure xserver-xorg using dpkg-reconfigure.  You should not have to this for every kernel update.

```
sudo dpkg-reconfigure xserver-xorg
```  

Or you could use the Envy installer script for Nvidia and ATI drivers
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by shavenlunatic on 2007-05-28
i agree .. envy is the way forward.. although saying that.. I didn't have any issues this kernel update.

but, if you have installed envy, and you find yourself stuck at the command line, just log in.. type 

```
envy -t
```

and the option is there to sort your video drivers out :)

---

