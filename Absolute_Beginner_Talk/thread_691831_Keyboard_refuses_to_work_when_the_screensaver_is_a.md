---
title: "Keyboard refuses to work when the screensaver is active."
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by saptarshi.roy on 2008-02-09
I am facing a weird issue with my keyboard. I have enabled 'lock screen when screen saver is active'. Now my issue is whenever I try to unlock the screen, my keyboard simply refuses to work, I can't enter my password. Every time this happens, I have to make an improper shutdown. I have the desktop effects disabled. Can someone give me a hint or a clue as to why this is happening?

---

### Post by randy78 on 2008-02-09
> **saptarshi.roy said:**
> I am facing a weird issue with my keyboard. I have enabled 'lock screen when screen saver is active'. Now my issue is whenever I try to unlock the screen, my keyboard simply refuses to work, I can't enter my password. Every time this happens, I have to make an improper shutdown. I have the desktop effects disabled. Can someone give me a hint or a clue as to why this is happening?

I was having some weird issues as well, so I disabled Desktop Effects and my computer has never ran smoother!

You might try disabling ALL of the Desktop Effects at first and then going to the next setting, one at a time, to troubleshoot it.

It sounds like it is freezing up and that happens quite a bit with Compiz enabled.

Let me know and take care :popcorn:

---

### Post by saptarshi.roy on 2008-02-09
Randy, thanks a ton again for your timely response, I really appreciate it. I am so sorry, I didn't gve you more information for troubleshooting it. I have compiz installed but I disabled the desktop effects due to frequent freezes.
Inspite of that my notebook freezes frequently and that's the reason I believe why I can't enter my password. What's interesing is that even while I was typing this message, my keyboard refused to work. With the help of my mouse I pasted the post and rebooted and now my keyboard starts working again. 
I have got no clue as to why this is happening.

---

### Post by randy78 on 2008-02-09
Hmm...

You might want to try:

sudo dpkg-reconfigure xserver-xorg 

Follow the defaults and reboot, and see what that gives you.

Take Care

---

### Post by saptarshi.roy on 2008-02-10
Hi Randy,
As you said, I ran
 > sudo dpkg-reconfigure xserver-xorg
Then I rebooted, I didn't find any keyboarded freezes till now.
Thanks a ton again for your timely assistance.

---

### Post by randy78 on 2008-02-10
Is it a Usb keyboard or a regular keyboard?

We'll get you straightened out ;)

---

