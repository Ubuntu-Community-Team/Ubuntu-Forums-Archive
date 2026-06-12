---
title: "Disable laptop WIFI"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-03-14
If you check out my signature, you'll see my computer specs.

I wanted to disable the wireless device on my laptop. It's an Acer Aspire laptop. I don't use the WiFi feature of my laptop at the same time, the orange color (which is used to activate wifi) is annoying.

How can I disable it? In windows, there's this Acer utility that will disable the WiFI of the laptop. So when I turn on my laptop, the orange button that represents WiFI is automatically disabled.

---

### Post by scottro on 2008-03-14
On the 4720z, there's a button above the keys which will turn it off.   Most Acers have either a switch or a button somewhere.  
It's ironic when there are so many posts on this forum about wireless on Acers not working.

---

### Post by karlo on 2008-03-16
> **scottro said:**
> On the 4720z, there's a button above the keys which will turn it off.   Most Acers have either a switch or a button somewhere.  
It's ironic when there are so many posts on this forum about wireless on Acers not working.

I want it to be **automatically disabled** when the computer starts up, not just by manually pressing the button to turn it off.

---

### Post by scottro on 2008-03-16
Just a few guesses--I'm only offering them because no one with more knowledge has posted.

I would think that once you have that button in the right position, it would be disabled at boot.

I'm not sure what happens if you simply disable it in network scripts.  If you do that in Fedora, the card won't activate till prompted, if you boot into textmode.  

If you boot into GUI, you should be able to uncheck wireless in NetworkManager and that should also keep it from activating on boot. 

I repeat, these are all guesses, just being offered as things to try.  

Hope this helps, but no guarantees.  My efforts have always been in the other direction, that is, to enable it.

---

### Post by karlo on 2008-03-16
> **scottro said:**
> Just a few guesses--I'm only offering them because no one with more knowledge has posted.

I would think that once you have that button in the right position, it would be disabled at boot.

I'm not sure what happens if you simply disable it in network scripts.  If you do that in Fedora, the card won't activate till prompted, if you boot into textmode.  

If you boot into GUI, you should be able to uncheck wireless in NetworkManager and that should also keep it from activating on boot. 

I repeat, these are all guesses, just being offered as things to try.  

Hope this helps, but no guarantees.  My efforts have always been in the other direction, that is, to enable it.

Thanks for trying to help me. Is there some script to disable it when the laptop is starting up to GUI?

---

