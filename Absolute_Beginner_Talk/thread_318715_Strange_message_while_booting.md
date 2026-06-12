---
title: "Strange message while booting"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by atarileaf on 2006-12-14
Hello everyone. I've finally installed Ubuntu 6.06, the AMD 64 flavor, on a second hard drive on my computer. When I turn the computer on, the GRUB menu comes up and I select the first Ubuntu and the OS starts to boot up. Then, after a few seconds, the screen goes black and I get some text on the screen and it halts, waiting for a command. The last string before the # is this:
[B]
/bin/sh: can't access tty; job control turned off[/B]

However, by just typing "exit" Ubuntu will boot normally. Its just an annoyance but why am I getting this message instead of it just booting and how can I get rid of it?

Also, I'm currently using plain VESA drivers which is giving me a headache but have no idea how to download drivers for my AGP Radeon 9800 PRO. Its not like downloading and installing drivers for Windows so as a newbie, I'm at a loss.

Thanks

---

### Post by dbd on 2006-12-14
Hmm, that first problem is really strange, no idea whats causing that!

As for drivers, there is a how to here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

And if that doesn't work, and you don't mind using propriety drivers (eeeugh!) have a look here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by atarileaf on 2006-12-14
Thanks, I'll try those links.

The fact that you don't know what the first problem was has me concerned. I'm a complete Linux newb and my problem is unique. :cry: 

I hope someone knows. [-o<

---

### Post by sailor2001 on 2006-12-14
> **atarileaf said:**
> Hello everyone. I've finally installed Ubuntu 6.06, the AMD 64 flavor, on a second hard drive on my computer. When I turn the computer on, the GRUB menu comes up and I select the first Ubuntu and the OS starts to boot up. Then, after a few seconds, the screen goes black and I get some text on the screen and it halts, waiting for a command. The last string before the # is this:
[B]
/bin/sh: can't access tty; job control turned off[/B]

However, by just typing "exit" Ubuntu will boot normally. Its just an annoyance but why am I getting this message instead of it just booting and how can I get rid of it?

Also, I'm currently using plain VESA drivers which is giving me a headache but have no idea how to download drivers for my AGP Radeon 9800 PRO. Its not like downloading and installing drivers for Windows so as a newbie, I'm at a loss.

Thanks
I believe at boot-up you can just hit ctrl/n (or is it c?) and bypass the tty... apparently you have installed tty.  you can remove that

---

### Post by doobit on 2006-12-14
> **atarileaf said:**
> Thanks, I'll try those links.

The fact that you don't know what the first problem was has me concerned. I'm a complete Linux newb and my problem is unique. :cry: 

I hope someone knows. [-o<

Nope, not unique :) The first problem and the second are related. It's trying to initialize the video drivers, and that's not happening. Once you ge the other drivers set up you won't have that error.

---

### Post by atarileaf on 2006-12-14
Ok thanks everyone for your help. I'm hitting the library soon and picking up every linux book I can get my grubby little hands on. Are there any good Ubuntu only books out there specifically designed for the absolute and total newb? The kind that needs complete and total handholding on every little step? :-D

---

### Post by dbd on 2006-12-14
Well, The Official Ubuntu Book would be a good if you can find it :)

However, libraries don't tend to have a good selection of Linux books and may not have it, also many of them may be out of date, or not 100% appropriate for your distribution. They should have at least 1 noob linux book though. Just be aware there will probably be a few differences between what it says and what you actually need to do. 

Good luck :)

---

### Post by dwblas on 2006-12-14
> Are there any good Ubuntu only books out thereSearching this forum is best thing to do to find an answer to a specific question.  You have Ubuntu installed, so now you would want to know specific things like how to install or change such-and-such.  Also, there is ample documentation on the net like The Linux Documentation Project [http://tldp.org](http://tldp.org)  Linux was created and grew up on the internet.  There are also free as in beer books available online [http://www.linux-books.us/ubuntu.php](http://www.linux-books.us/ubuntu.php)

---

