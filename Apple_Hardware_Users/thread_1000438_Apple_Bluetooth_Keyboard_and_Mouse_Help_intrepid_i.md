---
title: "Apple Bluetooth Keyboard and Mouse Help intrepid ibex"
date: 2008-12-02
forum: Apple Hardware Users
---

### Post by brucem91 on 2008-12-02
Hello. I have a question. I use the Apple Wireless Keyboard and Mouse in Intrepid Ibex. Syncing works just fine, but when I shut my mouse off, turning it back on doesnt seem to work. In Hardy it worked just fine, I would turn it off, go do whatever I needed to, come back, turn it on, and get to work. Now turning the mouse back on doesnt work. Hmm. Also, the extended keys dont seem to work on my keyboard, such as
fn+delete
fn+volume controls(volume controls are viewed as single button, for example, their is no difference in hitting fn+f8 and simply f8, and I dont want to set play to f8 in cause I need it interferes with another shortcut)
Please Help
Thanks
Bruce

---

### Post by hyperboloid on 2008-12-03
I had a problem with my Mighty Mouse pairing getting lost after suspend or reboot, and it drove me crazy until I found a workaround in the following thread. 

[http://ubuntuforums.org/showthread.php?t=966436]("http://ubuntuforums.org/showthread.php?t=966436") 

The workaround suggested is to click on "Hidden" and then select "Always Visible" in Bluetooth Preferences (right-click on BT icon, or use System -> Preferences -> Bluetooth), then the mouse pairing survives cold boots and suspends. This worked for me with the BT Mighty Mouse.

---

### Post by HyRax on 2008-12-26
There is a current issue in Intrepid that is causing this by not scanning for devices to reconnect. In the meantime [this workaround](http://ubuntuforums.org/showpost.php?p=6438656&postcount=6) has worked for me - as simple as power-cycling your mouse/keyboard.

---

