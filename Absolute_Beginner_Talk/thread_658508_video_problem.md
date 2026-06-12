---
title: "video problem"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by mikejwburton on 2008-01-04
installed 7.10 all went well, screen said something about restricted video
tried to change resolution restarted program , looks like i got multiple screens in one .cant make out where i am to change the settings again, just wondering what my next option 
question , is there a option on the cd that will restore my video or do i have to reinstall everything

Thanks
Mike

---

### Post by taurus on 2008-01-04
Boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```
What graphic card do you have in that machine?

---

### Post by mikejwburton on 2008-01-04
complete newbee with linux so bear with me
not sure where is the recovery area
i tried to put the instllation disk in and did not find a boot area , i went to F6 there was a boot there wrote that line that was in your post but i dont think that did nothing because i got the same screen when i boot from the drive (multipage)

need moore instruction please

thanks 
Mike

---

### Post by taurus on 2008-01-04
When you first turn on your machine, you would see a message from the BIOS.  Then, GRUB will wait for three seconds to see if you press anything.  That's when you press Esc to bring up the menu.  The first one is highlight which is booting Ubuntu.  The second option is what's called recovery mode.  Use the down arrow key and highlight that option and hit Enter to boot from it.  Wait for it to finish booting and when you see a prompt, that's where you type in those two commands, one at a time.

The first command is to reconfigure your X server while the second command is to reboot your machine.  This time, just let it boot normal and see if everything is working fine now.

---

### Post by mikejwburton on 2008-01-04
Thank you so much , back up running. your question about my card is a 
nvidia accelerated graphics driver (legacy card)
currantly not enabled
Shouls i enable it and set up my graphics

Mike

---

### Post by taurus on 2008-01-04
You probably need the nvidia-glx-legacy (instead of nvidia-glx-new) since you have an older nvidia card.  You can search for it in System -> Administration -> Synaptic Package Manager -> Search.

---

### Post by PmDematagoda on 2008-01-04
Enable the driver in the Restricted Drivers Manager, since Nvidia VGA cards are usually compatible with Linux and most work out of the box, your card should be rather easy to setup.

---

### Post by mikejwburton on 2008-01-04
You Guys are great, Many thanks all working perfect

Mike Burton

---

### Post by lolo67 on 2008-01-05
> **taurus said:**
> Boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```
What graphic card do you have in that machine?

:) I had a video problem trying to add a second monitor or Lcd tv to my laptop,  I used your suggestion and it worked great, thanks taurus :)

---

