---
title: "Bluetooth keyboard pin entry?"
date: 2010-07-19
forum: Apple Hardware Users
---

### Post by robacarp on 2010-07-19
I have spent quite some time reading forums and howtos and such on connecting the Apple Bluetooth keyboard to Ubuntu through a dongle.

I have gotten so far as to get the device registered on the computer, but when I type anything on the keyboard I get a popup that says:

"Device 'Apple Wireless Keyboard' wants to pair with this computer"  Please enter the PIN mentioned on the device 'Apple Wireless Keyboard' (<address>)

But I have no pin on the keyboard.  I've tried entering 0000, 1234, abcd, etc in the popup and also on the keyboard (then enter) just before entering them in the popup.

I am running Ubuntu 10.04.

I feel like I'm missing an obvious "press the any key" type thing here.

---

### Post by kostkon on 2010-07-19
You could check your keyboard's manual for this. Anyway, just leave the pin text field blank and press OK (or whatever label the button has).

---

### Post by robacarp on 2010-07-19
> **kostkon said:**
> You could check your keyboard's manual for this. Anyway, just leave the pin text field blank and press OK (or whatever label the button has).

Thanks, and good suggestion. The manual has nothing in the way of pin numbers.  And the box won't let you press 'OK' until you've typed something.

---

### Post by robacarp on 2010-07-20
Bump

---

### Post by valbaca on 2010-07-20
[http://blueman-project.org/wiki/Howto_Apple_Wireless_keyboard](http://blueman-project.org/wiki/Howto_Apple_Wireless_keyboard)
 
You may have to remove the batteries for the keyboard to become discoverable again:
[http://support.apple.com/kb/HT1809](http://support.apple.com/kb/HT1809)
[https://fedoraproject.org/wiki/Documentation/Bluetooth](https://fedoraproject.org/wiki/Documentation/Bluetooth)

---

### Post by robacarp on 2010-07-20
> **valbaca said:**
> [http://blueman-project.org/wiki/Howto_Apple_Wireless_keyboard](http://blueman-project.org/wiki/Howto_Apple_Wireless_keyboard)


Okay, so the big trick was that I was doing it backwards.  The docs I had read previously seemed to say that I needed to type the pin on the keyboard *first* then type the same pin on the computer.  The correct sequence is the reverse: input pin on computer and then on the keyboard.  

I did not, however, see the 'pairing notification' that it says will come up.  Regardless, I'm now typing on my fancy schmancy new keyboard!

Thanks a ton!

---

### Post by valbaca on 2010-07-20
If this worked, please help other users by marking this thread as [Solved].
 
To do this, go to [COLOR=red]_Thread Tools _[/COLOR][COLOR=black]in the top right and click on "Mark thread as solved"[/COLOR]
 
Thank you

---

