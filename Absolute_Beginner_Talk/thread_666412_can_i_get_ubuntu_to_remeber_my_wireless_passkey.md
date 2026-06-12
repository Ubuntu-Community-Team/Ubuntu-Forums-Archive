---
title: "can i get ubuntu to remeber my wireless passkey?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by gruffwestern on 2008-01-13
Hi,

I have just installed Ubuntu (Its my first foray into Linux, and i must say if it works as well as it looks, i may well ditch Windows for good!), and all appears well, except that everytime i reboot it keeps asking me to re-input my wireless passkey?

Is this normal? is there any workaround? as i hoped my days of remembering hex were behind me................

Thanks in advance

---

### Post by Joeb454 on 2008-01-13
You say you installed it to the hard drive?

It should ask you for a second passkey to save the password (so nobody can change your wireless key without that 2nd passkey)

---

### Post by bagguley on 2008-01-13
Have you tried inputting the details manually? (right click over the network icon in the top right corner and select manual config)

---

### Post by gruffwestern on 2008-01-13
thanks for the quick reply!

  I have installed it to the hard drive.

It did not ask me for a second password, and hasn't done so at all, it just asks me to enter the hex passkey every time it boots up, although it does remember which wireless network i'm trying to connect to........

I haven't tried to connect manually as yet.

Please bare in mind that i'm not the greatest at configuring things manually!!

---

### Post by reinderien on 2008-01-13
If worse comes to worse, you can always write your own /etc/wpa_supplicant.conf to contain the SSID and password.

---

### Post by bagguley on 2008-01-13
1. Select Manual Configuration from the network menu (right click over the network symbol - top right hand corner.

2. Double Click on the wireless connection.

3. Click on the drop down menu next to network name and select your network

4. Input the password and encryption type

5. Make sure connection meathod is Automatic (DHCP)

Done

---

### Post by gruffwestern on 2008-01-13
> **bagguley said:**
> 1. Select Manual Configuration from the network menu (right click over the network symbol - top right hand corner.

2. Double Click on the wireless connection.

3. Click on the drop down menu next to network name and select your network

4. Input the password and encryption type

5. Make sure connection meathod is Automatic (DHCP)

Done

I get to step 3, but all the options are greyed out, There is a tick next to "Enable roaming" but if i uncheck this, all though the options become active, my network name is not listed...... in fact the drop down is blank. any ideas?

Thanks again!

---

### Post by bagguley on 2008-01-13
You dont have a button on the front of your laptop to turn your machines wifi on/off do you?? (Three days of fighting to realise Id hit this button by accident!)

---

### Post by gruffwestern on 2008-01-13
> **bagguley said:**
> You dont have a button on the front of your laptop to turn your machines wifi on/off do you?? (Three days of fighting to realise Id hit this button by accident!)

i do have a button, but the wireless is on........

well i hope so, otherwise i wouldn't be able to write this reply!

---

### Post by bagguley on 2008-01-13
Are you broadcasting your network name?

---

### Post by gruffwestern on 2008-01-13
pass.

How would i find that out?

My network appears in the list, as well as most of my neighbours, if that is what you mean?

---

### Post by bagguley on 2008-01-13
If you look at your router software (usually by typing something like 192.168.0.1 into a web browser) it'll have a box for broadcast name or SSID or ESSID. Alternatively if your network pops up on any computer then you are broadcasting your network, this is however a different conversation.

The reason I asked if you are broadcasting you network was because if you arnt then it wouldnt appear. If you are broadcasting then im unsure why it wouldnt appear..... Ill have a think and get back to you. Chances are you might need someone that understands linux better than I do (use bump if you dont get answer soon!

---

### Post by gruffwestern on 2008-01-14
bump

---

