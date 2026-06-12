---
title: "how do i get rid of the network icon?"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by graigsmith on 2007-07-30
in the notification area, theres a network icon. i dont really want it there. is there any way i can remove that icon?

---

### Post by Inxsible on 2007-07-30
> **graigsmith said:**
> in the notification area, theres a network icon. i dont really want it there. is there any way i can remove that icon?

That helps you in selecting the wireless networks around you. Why would you wanna get rid of it?

Maybe you could uninstall nm-applet which is the network manager and install another application for your network management, which does not put an icon in the tray.

---

### Post by shagster_ on 2007-07-30
network manager was intended for mobile users....desktop pcs 99% don't care for this and it taking up 'space' in the tray.....

i'm gonna try uninstalling the package network-manager-gnome and its dependencies and see if that works 

i think the command would be
```

sudo apt-get autoremove network-manager-gnome

```

i'll confirm when i get home...but hopefully its not 'tied' to ubuntu-desktop package like everything else...

---

### Post by tajmox on 2007-07-30
I just remove it in my startup entries (Settings -> Sessions and Startup)
Just un-check the network manager.  Don't worry your network will still work.

---

### Post by tashmooclam on 2007-07-30
Put your cursor over the middle of the top panel. Right click.
You will see a menu
Click "Add to Panel" 
You will see the panel icons down there.

---

### Post by ron999 on 2007-07-30
> **tajmox said:**
> I just remove it in my startup entries (Settings -> Sessions and Startup)
Just un-check the network manager.  Don't worry your network will still work.
Smart thinking:D
I'm not even on a network,:lol:

---

### Post by graigsmith on 2007-07-30
i'd want to remove it because i dont have a wireless card. just a wired card here.

---

### Post by RomeReactor on 2007-07-30
Hi. I agree with **tajmox** and **ron999**:
> **tajmox said:**
> I just remove it in my startup entries (Settings -> Sessions and Startup)
Just un-check the network manager.  Don't worry your network will still work.
Just remove it from the **Startup Programs** list. No need to uninstall it.

System->Preferences->Sessions->Startup Programs, uncheck **Network Manager**.

---

