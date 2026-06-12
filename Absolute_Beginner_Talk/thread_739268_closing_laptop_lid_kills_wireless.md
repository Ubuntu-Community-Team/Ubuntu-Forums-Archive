---
title: "closing laptop lid kills wireless"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2008-03-29
Dell 1525 with the intel wireless card in it. 
Everything seems to work fine until I close the lid. 
When I re-open it, it seems to have a real hard time coming back to life, and when it does, the wireless is non functional until I re-boot. 

I honestly have no clue as to where to begin to try to resolve this... It's not like the wireless doesn't work... It's flawless and was so right out of the box. I use WICD to manage the wireless, and it has always seemed to work. (It still does, I guess, because when this happens, no other interface works to get it running either...)

---

### Post by AKPAKP on 2008-03-29
Even i have this problem i use a DELL Latitude...when i close the lid the wired lan connection gets hanged & i'm forced to reboot ....the same thing happens when i remove the lan wire without disconnecting it....

---

### Post by FuturePilot on 2008-03-29
Do you have it set to Suspend when you close the lid? This could be the issue. I've seen problems where people don't have wireless after suspending.

---

### Post by Papa-san on 2008-03-29
It was set to hibernate. 
I set it to blank screen, but that isn't a really good option when it is on battery power...

---

### Post by FuturePilot on 2008-03-29
Perhaps you could try reloading the kernel module after waking it up. I'm not sure what wireless card you have but if you can find out the module it uses you could try
```
sudo modprobe -r <module-name>
sudo modprobe <module-name>
```
after hibernating and see if it brings the wireless back.

---

### Post by Papa-san on 2008-03-29
OK.

So, how do I find out what module it uses?

---

### Post by ImNeat on 2008-03-30
My wireless breaks after being resumed from hibernate, but restarting the network process fixes it for me.

```
sudo /etc/init.d/networking restart
```

---

### Post by louieb on 2008-03-30
> **ImNeat said:**
> My wireless breaks after being resumed from hibernate, but restarting the network process fixes it for me.

```
sudo /etc/init.d/networking restart
```
IBM T30 here network does not come back to life after suspend or hibernate. This also works for me. ```
sudo dhclient
```

---

### Post by hazey_night on 2008-05-02
I just got my wife a Dell 1525 and she has been having the same exact problem. I think I have fixed it. I tried once and it worked, time will tell though. 

Ok, so what I did was actually really simple. This is with Vista. Go to Network and Internet setting under the control panel. Then go to Network and Sharing Center. And then Manage Wireless Networks... and then adapter properties... 

Once the window comes up go to config and Power Management... Uncheck Allow the Computer to turn off this device... I'm sure there is some quicker way to get to this, I just happen across it.

Now then this might not be the best for battery life, but don't know yet. Now there is the option to manualy turn it off (if you have that option) that could save battery life....

---

