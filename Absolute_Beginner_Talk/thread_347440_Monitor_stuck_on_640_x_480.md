---
title: "Monitor stuck on 640 x 480"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Mrich1976 on 2007-01-27
All:

Please forgive my ignorance, as I am new to the world of Linux. I have a HP Pavilion that I converted to Hoary, then upgraded to Breezy, and now to Edgy (I even covered the Windows sticker with a Tux one).

I'd love to use the box more (I'm primarily a MS guy, working in the IT industry, but I want to learn to utilize Linux as well to help my career), but I am unable to adjust my monitor resolution beyond 640 x 480.

I've tried all the avenues I can think of, and Google wasn't helpful. I did, however, discover that it has something to do with the XConfig86-4 file, and one other file.

Any command I can use from the terminal, or any update I can get to fix this? I know this monitor and graphics card is capable of 1024 x 768.

Thanks for any advice you may be able to provide!

**ISSUE RESOLVED**

---

### Post by dbbolton on 2007-01-27
what does your /etc/X11/xorg.conf  have set as the resolution ?


if you want to reconfigure X with a wizard:
```
sudo dpkg-reconfigure  xserver-xorg
```

---

### Post by Mrich1976 on 2007-01-27
Thanks for the quick reply. I used the sudo command you suggested, and it went through the configuration, but I don't think it changed anything. Do I need to reboot or anything?

The xorg file had a number of resolutions listed, and I don't think it had any of them as a "default".

The refresh rate on the monitor seems flaky, as well. It's stuck on 60Hz. That could be part of the issue as well.

I'd love to get this monitor to a minimum of 800 x 600, but 1024 x 768 would be ideal. It's only a 15" monitor.

---

### Post by bugster on 2007-01-27
What happens to your monitor when you boot from the edgy cd?

---

### Post by Mrich1976 on 2007-01-27
I don't have one. I have one for Hoary (I believe), but I don't have one for Edgy.

I'm running 6.10, though, if that helps.

---

### Post by bugster on 2007-01-27
I'm a newbie who had a similar problem when I started a few weeks ago.  Eventually solved it by googling my monitor and getting the makers settings for H and V rates.  I entered them in sudo dpkg-reconfigure xserver-xorg and that solved it.  Hope this helps.

---

### Post by Mrich1976 on 2007-01-27
Ok, now I feel like an idiot...the console command did work (??). I had some updates going on, as well, but when I rebooted it came up as 1280 x 1024.

Thanks for your assistance. Consider this issue closed.

---

### Post by Tomosaur on 2007-01-27
Please add [resolved] to the thread title by editing your first post, so people with similar problems know which threads to look in :)

---

