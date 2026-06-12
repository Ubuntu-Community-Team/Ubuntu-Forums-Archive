---
title: "recently developped wireless problem."
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by medicatedlain on 2007-12-27
My computer is a dual boot(windows vista, ubuntu gutsy 7.10).  Nothing has changed recently related to anything with the package manager or anything.  But yesterday, my SCIM program was showing the keyboard application twice on the bar at the top, so I decided to close one of them(wireless was working fine).  When the one keyboard disappeared, so did every icon on the top except for volume.  I figured when I restarted, everything would be there again.  Today my connection was randomly last, so I decided to restart.

When I restarted, the symbols still weren't, there, so I went to "add to panel," and added "network monitor," but even though it looks to be the same icon, it doesn't do what the old one did.  The old icon showed a list of wired and wireless connections available, the new icon only gives connection properties.  

So ok, I figure I can live without it if I can still connect.  Go to the terminal... (I always use a wireless connection)
```
sudo dhclient eth1
```

network is sleeping...

```
ifconfig
```

just a bunch of 0s... so i hooked in a wire, and checked ifconfig, and that read fine, so now I'm connected through 
```
sudo dhclient eth0
```

But I still get nothing for wireless.  Any ideas?

---

### Post by tgalati4 on 2007-12-27
One of three things:

1.  Your neighbors got a new 2.4 GHz wireless phone for Christmas and it clobbered your network.

2.  Your wireless card died.

3.  None of the first two options.

Seriously, remove the battery and let the computer set for a while.  Try to reset or update the firmware.  Sometimes wireless chipsets have persistent memory as part of the digital tuning.  When it gets messed up, you need to reset it, and it's difficult if it's built-in.  If it's removable, then remove it for a while.  If it's really warm then it could be a heat issue.

---

### Post by llamakc on 2007-12-27
You want to add "nm-applet" to your panel.

---

### Post by medicatedlain on 2007-12-28
I tried looking on the list for "nm-applet," but didn't see, so I searched for it, and couldn't find it.  Still haven't been able to figure it out.

---

### Post by medicatedlain on 2007-12-28
I just looked closer at "ifconfig," kind of weird.  It shows me listings for:
eth0 (wired connection i am using)
eth1 (all 0s just about, exept where it says dropped 7)
lo (what?)
I've never seen this lo thing before, any ideas what it is?

---

### Post by walkerk on 2007-12-28
> **llamakc said:**
> You want to add "nm-applet" to your panel.

1. In terminal run this
```
nm-applet --sm-disable
```

If that works make sure to add that command to Session Manager.

2. If not, install it.
```
sudo apt-get install network-manager network-manager-gnome
```

Then revert back to 1.

---

### Post by medicatedlain on 2007-12-28
I tried the first command, but it didn't fix it, and at that point the terminal stopped takng nay requests until I restarted it, so when I openned the terminal again, I entered the second command first, which worked just fine, but the first command continued to not change anything, and stop the terminal from taking commands.  

One friend has suggested(since all of my icons except volume are missing) that systray isn't getting loaded.

---

### Post by walkerk on 2007-12-28
> **medicatedlain said:**
> I tried the first command, but it didn't fix it, and at that point the terminal stopped takng nay requests until I restarted it, so when I openned the terminal again, I entered the second command first, which worked just fine, but the first command continued to not change anything, and stop the terminal from taking commands.  

One friend has suggested(since all of my icons except volume are missing) that systray isn't getting loaded.

right click the panel and select > Add to Panel ... look through and select Systray and Add

---

### Post by medicatedlain on 2007-12-28
It was systray... I just added "notification area" to panel, and all is better now.  It spots my wireless and everything.

---

