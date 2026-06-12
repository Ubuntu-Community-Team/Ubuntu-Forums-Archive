---
title: "Ubuntu running slow on WUBI"
date: 2011-01-23
forum: Apple Hardware Users
---

### Post by Wunala Dreaming on 2011-01-23
Hello everyone! Before I installed Ubuntu (10.04) on my MacBook Pro, I had two partitions (Boot Camp), Windows 7 and OSX. I decided to install Ubuntu via Wubi on the Windows partition and after following one of your tutorials I got almost everything working (keyboard brightness, display brightness, Wifi, etc.

The problem is that everything seems to be running very (VERY) slow on Ubuntu, if I click something it takes the OS a few seconds to react. Do you know what might be causing this problem?

On the other hand, I followed this tutorial: [https://help.ubuntu.com/community/MacBookPro6-2/Lucid](https://help.ubuntu.com/community/MacBookPro6-2/Lucid)
but I still can't get the speakers and bluetooth to work. Do you know of any other possible solution?

Thanks for your help.

---

### Post by stephan.brubaker on 2011-02-11
Don't know if you will see this but I'm fairly certain the problem more than likely is being caused because you installed via WUBI. All wubi does is allocate a sizable chunk of your windows partition and runs Ubuntu from there. If you install Ubuntu onto it's own partition it will run amazingly smooth.

---

### Post by Wunala Dreaming on 2011-02-11
Nope, I didn't install it via WUBI, but I have corrected the problem. I just installed Windows 7 again on it's own partition and then Ubuntu into it's own partition and this time I made sure I selected the correct partition for the boot loader and now I'm just seeing the 3 normal icons (Ubuntu, Windows and Mac OSX).

Thanks!

---

