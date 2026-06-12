---
title: "Keyboard Issues on MacBook Pro"
date: 2009-06-12
forum: Apple Hardware Users
---

### Post by tomreid on 2009-06-12
Hi

I've been running 9.04 on a MacBook Pro 4.1. It's been running well, but today has started exhibiting some strange behaviors. 

When I was typing into Evolution, sending e-mails, I noticed the keyboard was hanging for a few seconds, then if i clicked the mouse in the space where I was typing, I could type again. 

I Initially thought this may be an Evolution problem, so I switched to Firefox, but the same problem arose. 

At it's most extreme, the keyboard hung altogether when I was using Thunderbird , then seemed to develop a life of it's own and (without my hands even being on the keyboard), it types "nnnnnnnnn" without me being able to stop it. It didn't respond to any other command (I was clicking the mouse to try to open the terminal to run an Xkill command on Thunderbird. I just had to hit the power button to stop the process. 

Even typing in this box, it has hung around 6 or 7 times and if I  stop typing for a second or two and start again, or click the mouse in the box, it starts again. 

Please can someone help, I am new to linux, was hoping to wean myself off my Apple habit by using a free Unix based OS, but this fault makes the machine almost too difficult to use. 

cheers

Tom.

---

### Post by cyberdork33 on 2009-06-15
I have not seen this behavior exhibited before. Do you have another keyboard (non-apple?) that you can test for the same thing? it may be that this is just some package update gone wrong...

---

### Post by alexmurray on 2009-06-15
Have you got tap to click on for the trackpad? I wonder if you are tapping the trackpad accidentally as you type and inadvertently 'clicking' outside of the text region you are typing into? Try disabling tap to click and see if that helps - which I think you should be able to do by changing any lines like: 

> <merge key="input.x11_options.TapButton1" type="string">1</merge>
<merge key="input.x11_options.TapButton2" type="string">3</merge>
<merge key="input.x11_options.TapButton3" type="string">2</merge>


to

> <merge key="input.x11_options.TapButton1" type="string">0</merge>
<merge key="input.x11_options.TapButton2" type="string">0</merge>
<merge key="input.x11_options.TapButton3" type="string">0</merge>


(ie make all TapButtonX as 0) in /etc/hal/fdi/policy/11-x11-synaptics.fdi (assuming you set up the trackpad following the [instructions on the wiki]("https://help.ubuntu.com/community/MacBook5-1/Jaunty#Trackpad"))

---

### Post by tomreid on 2009-06-22
Yes that is indeed possible and explains a lot, I'll check that out thanks.

---

### Post by tiagobt on 2009-06-22
If you still like the tapping behavior, you could disable it only while typing.

Add the following line to /etc/hal/fdi/policy/11-x11-synaptics.fdi:
```
<merge key="input.x11_options.SHMConfig" type="string">true</merge>
```

Go to System &#9656; Preferences &#9656; Session and add a new startup program configured with the following command:
```
syndaemon -d -t -K
```

To have the changes take effect immediately (without requiring a reboot), run the following in a terminal window:
```
syndaemon -d -t -K
```

If the command above doesn't work, you could pass the argument **-S** to force syndaemon to use SHMConfig.

For more information, read the following page:
[https://help.ubuntu.com/community/SynapticsTouchpad#Disabling%20the%20Touchpad%20Temporarily%20While%20Typing](https://help.ubuntu.com/community/SynapticsTouchpad#Disabling%20the%20Touchpad%20Temporarily%20While%20Typing)

---

### Post by tomreid on 2009-06-30
Thanks Alex, that was exactly what was happening, I was leaning on the trackpad whilst typing. As I'm using an external mouse, I think I forgot the trackpad was there!

cheers

---

