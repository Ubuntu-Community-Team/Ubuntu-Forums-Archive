---
title: "Cannot start"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by ftathome on 2006-12-17
I've installed Automatix2 AND tje Nvidia update.
There was a message suggesting to use
sudo cp /etc/x11/xorg.conf_backup_206612171259 /etc/x11/xorg.conf
As suggested I rebooted the system.
I cannot boot anymore, normal or recovery or livecd (looks like CD drive is not working anymore)
Can anzbody help me to reach terminal to apply the changes as suggested during install?

Thank you from a very beginner of Ubuntu

---

### Post by bulldog on 2006-12-17
What happens if you boot and if you use recovery mode?
The message "I can't do this or that" isn't gonna help.

We need to know what happens and what error messages you get to help you with any thing.

So try again and give all the information you get.
Installing the nVidia driver from automatix2 shouldn't have to cause any crashes or malfunctioning of the cd-drive.

---

### Post by dannystaple on 2006-12-17
> **bulldog said:**
> What happens if you boot and if you use recovery mode?
The message "I can't do this or that" isn't gonna help.

We need to know what happens and what error messages you get to help you with any thing.

So try again and give all the information you get.
Installing the nVidia driver from automatix2 shouldn't have to cause any crashes or malfunctioning of the cd-drive.

In fact, I will add to that by saying that nothing from automatix should stop the liveCD from booting. Have you tried turning off (hard off - mains or switch at rear), then turning on and booting form the live CD?

---

### Post by ftathome on 2006-12-17
OK
I power up the pc and press Esc and 
select Ubuntu, kernel 2.6.17-10-generic (recovery mode)
Then "Starting up" appears shorlty and it starts booting, until the following line appears
[17179570.632000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1

The system hangs and nothing happens.

---

### Post by bulldog on 2006-12-17
Think you have a bad IDE controller on your mother board.
You can check if the cables are tight onto the IDE port,but I think your controller left this world.

This explains why you can't boot into the live cd as well because your cd player is attached to the same controller.

You can try to connect the devices [disk and cd-rom] to your secundary IDE port,maybe this one isn't affected by the malfunction of the first IDE.

Before fiddling with your hardware turn off the computer and disconnect it from the power outlet!!!!
Than discharge yourself from static electricity to avoid further damage to the motherboard.
Be very careful and don't force anything.

---

### Post by ftathome on 2006-12-17
I got it working by getting a new bus cable.
Now I could access terminal and everything is back to normal.

Thank you

---

