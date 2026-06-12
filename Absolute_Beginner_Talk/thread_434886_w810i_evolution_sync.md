---
title: "w810i evolution sync"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by jvc26 on 2007-05-06
Hi there, I have done numerous reading about on the forums trying to find a possible solution to the problem. Since feisty, I have been able to plug in my phone (a sony ericsson w810i) and transfer files to and from it with no problems. The issue comes when I am trying to sync it with Evolution and my calendar.

I got the multisync packages following instructions [here]("http://www.williambrownstreet.net/wordpress/?p=27#more-27") which was all well and good, but once I get to actually syncing the two, I have to do it via cable as my pc doesnt have bluetooth. Looking [here]("http://ubuntuforums.org/showthread.php?t=242932&highlight=wammu") someone mentioned:
> 

What version of multisync are you using? I'm current using 0.82 and am able to sync without problems with either cable, IR or bluetooth. Although bluetooth sometimes can be a pain with the security...

In the plugin, select IrMC Mobile Device, then click "Options", in the connection type, you can choose the method you want to connect via. For IR or Bluetooth, let Multisync search for the device. For Cable, my device is /dev/ttyACM0 - I can't remember how you find out which device it is connected as... maybe someone can help you with that.

Then for the other plugin, select Ximan Evolution 2.

How do I find which device my phone is attached to? That would solve the problem I believe. Thanks very much,
Il

---

### Post by Turgon on 2007-06-20
Your phone is connected to either /dev/ttyACM0 or /dev/ttyACM1 , problaby the last one.

---

### Post by Kevanx on 2007-07-27
I'm having this same problem - the Test Connection button doesn't seem to work... could someone explain how to determine where your device (in this case - my cell phone) is connected? Any help appreciated.

---

### Post by Kevanx on 2007-07-27
Solved - sort of...

I'm having trouble syncing, but Multisync recognizes the phone (Sony Ericsson w810i) beautifully now. Just like in windows,
*****the phone requires any syncing to be done while in PHONE MODE, not in FILE TRANSFER MODE*****

Try starting up in USB mode, and in MultiSync, use a sync pair of Ximian Evolution 2 and IrMC Mobile Device in either order.
Click "options" on the latter , and choose "other device", then type in /dev/ttyACM1
notably, /dev/ttyACM0 worked for me as well. Either way, really.

I hope this helps other non-bluetooth, cable syncers out there with a variety of phones!

---

### Post by danysl on 2007-12-21
> **Kevanx said:**
> Solved - sort of...

I'm having trouble syncing, but Multisync recognizes the phone (Sony Ericsson w810i) beautifully now. Just like in windows,
*****the phone requires any syncing to be done while in PHONE MODE, not in FILE TRANSFER MODE*****

Try starting up in USB mode, and in MultiSync, use a sync pair of Ximian Evolution 2 and IrMC Mobile Device in either order.
Click "options" on the latter , and choose "other device", then type in /dev/ttyACM1
notably, /dev/ttyACM0 worked for me as well. Either way, really.

I hope this helps other non-bluetooth, cable syncers out there with a variety of phones!

Thanks! after searching the net this is the only thing that worked flawlessly and easy too. :)

---

