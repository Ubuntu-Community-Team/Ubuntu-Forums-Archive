---
title: "Issues with Apple Wireless Keyboard caps lock in Ubuntu 16.10"
date: 2017-03-02
forum: Apple Hardware Users
---

### Post by hedgeberg on 2017-03-02
Hey guys, this is a bit of a weird one. 
I've got an Apple bluetooth keyboard I use sometimes when I'm on the go. It connects fine to ubuntu, and I can do all normal functions without any issue, except that when I press the caps lock button, the keyboard appears to freeze. 

Caps lock will turn on on the laptop fine, and typing via any input system other than the apple keyboard will be capitalized as expected. However, the indicator LED on the apple keyboard will not turn on, while the indicator on the laptop does. I am then unable to type or send any kind of input from the keyboard to the laptop. The only resolution is to disconnect and reconnect the keyboard via the bluetooth notification item. 

I have a feeling this is because the keyboard is awaiting some kind of response indicating that caps lock has been set on the paired system which it isn't getting, but that's just my gut feeling. Would appreciate any help in debugging this. Dmesg, bluetoothctl, and google have all been pretty unhelpful so far. 

Thanks!

---

### Post by ajgreeny on 2017-03-02
*Thread moved to **Apple Hardware Users**.* which is more appropriate and a better fit.

---

### Post by hedgeberg on 2017-03-09
Posted it to hardware orginally since I figured it was less of an Apple issue since noone else had the same issue, and because I thought it would get more attention. That being said, since this has received no attention, thought I should ask if I'm allowed to recreate the post to give it another go at this.

---

### Post by QIII on 2017-03-09
No.  Do not create a duplicate post or we will remove it.

Generally, if you do not receive a response within 12 hours, you may feel free to bump your post back up to the top of the pile by simply adding a new post with the word "bump".

Allowing your post to go days without bumping means that it settles well out of sight in the sediment at tbe bottom of the sea.

---

### Post by horiafx on 2017-05-04
I am experiencing the same issue but I couldn't find a solution for this.

---

### Post by augustl on 2018-02-23
I have this same issue too. As soon as I hit caps lock on my apple wireless bluetooth keyboard, it stops working and I have to reconnect it in Bluetooth settings to make it work again.

---

### Post by aminbeiram on 2018-09-22
Here is how you can solve the problem:
reset the keyboard by pressing its switch key for 5 seconds,
go to Bluetooth setting of your ubuntu and remove the device
then press the switch button of your keyboard to turn it on without being paired with your ubuntu
press Fn+F6 twice, in order to turn off the caps lock
then pair it with your device
it should work now and caps lock should work too.

---

### Post by oldos2er on 2018-09-22
Old thread closed.

---

