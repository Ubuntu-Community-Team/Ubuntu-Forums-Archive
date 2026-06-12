---
title: "Arch Linux - &quot;vanilla&quot; or LXDE?"
date: 2012-05-04
forum: Any Other OS
---

### Post by ratcheer on 2012-05-04
I have done a fresh installation of Arch Linux, this week. I am very happy with my progress, so far. The way I have it now, I boot to a text console, log in, and run startx to go into an OpenBox desktop with a tint2 panel. This is very nice, very simple, and very light on resources.

However, every time I want to do something new, it seems like I have to install something else and learn how to configure it. Yesterday, I discovered that LXDE is basically just OpenBox plus several more applications. The claim is that LXDE is also very light on resource consumption.

So, what is your take on this? Should I continue on my current tack, or add LXDE to maybe make things a little simpler? I want to hear the pros and cons of both approaches.

Tim

---

### Post by lykwydchykyn on 2012-05-04
It depends on what you like.  LXDE is pretty much a lightweight desktop ready-to-go out of the box.  I got bored with it after a while.

Some people enjoy the process of finding a new desktop component, configuring it just the way they want it, and ending up with something totally unique and personal.

Some just want a lightweight desktop with no hassle and don't care about customizing it much.

I eventually landed on awesome WM, which for me is a constant work-in-progress.

It hurts nothing to try it for a while.

---

### Post by wojox on 2012-05-04
You may want to check out Archbang. They have a great openbox distro on top of Arch.

I think the benifit of installing it a piece at a time, like your doing, is you broaden your scope of Linux a bit. 

Even if you install LXDE on Arch, you still have to deal with config files. :p

---

### Post by kelvin spratt on 2012-05-04
You can install lxpanel and lxmenu lxapearance gives better choice of gtk2 themes, Remove the panel you are using from auto start add lxpanel and you are ready to go uses about 10mb more ram for that you get a really nice desk top I preferred it to gnome2 myself.

---

### Post by ratcheer on 2012-05-04
@wojox, I used ArchBang for about six months, then I decided I wanted to try the real deal. Yes, I know that after installation and initial configuration ArchBang is just Arch, but don't try telling them that on the Arch Linux Forums. :p

I think I am answering my own question. It seems I am leaning toward being a configurator instead of an OOTB installer. But keep the comments coming.

Thanks,
Tim

---

### Post by ratcheer on 2012-05-04
> **lykwydchykyn said:**
> 

I eventually landed on awesome WM, which for me is a constant work-in-progress.

It hurts nothing to try it for a while.

I hear a lot of good things about Awesome. I need to take a look at it.

Thanks,
Tim

---

### Post by ratcheer on 2012-05-04
I did look at awesome wm and I like what I saw. However, when I tried to install it, pacman said it could not be found. I looked it up in the package database and found that it is in the testing repository. So I looked on the Wiki to see what that means, and they strongly recommend that you not install things from there unless you are an experienced user prepared to deal with "breakage".

I barely have my feet wet with Arch, so I will pass for now. Too bad.

Tim

---

### Post by ratcheer on 2012-05-04
[IMG]https://lh3.googleusercontent.com/-Szm7cOVwBTM/T6PiQgPm4bI/AAAAAAAAAWA/V_OcUT0bXT4/s250/screenshot_20120503_tn.jpg[/IMG]


[https://lh3.googleusercontent.com/-lPiuP6j900c/T6Lpvs8Mw0I/AAAAAAAAAVA/-zLySf8CHro/s914/screenshot_20120503.jpg](https://lh3.googleusercontent.com/-lPiuP6j900c/T6Lpvs8Mw0I/AAAAAAAAAVA/-zLySf8CHro/s914/screenshot_20120503.jpg)


Here is a screenshot of my OpenBox setup.

Tim[[IMG]https://lh3.googleusercontent.com/-Szm7cOVwBTM/T6PiQgPm4bI/AAAAAAAAAWA/V_OcUT0bXT4/s250/screenshot_20120503_tn.jpg%3C/a%3E[/IMG]]("https://lh3.googleusercontent.com/-lPiuP6j900c/T6Lpvs8Mw0I/AAAAAAAAAVA/-zLySf8CHro/s914/screenshot_20120503.jpg")

---

### Post by lykwydchykyn on 2012-05-04
> **ratcheer said:**
> I did look at awesome wm and I like what I saw. However, when I tried to install it, pacman said it could not be found. I looked it up in the package database and found that it is in the testing repository. So I looked on the Wiki to see what that means, and they strongly recommend that you not install things from there unless you are an experienced user prepared to deal with "breakage".

I barely have my feet wet with Arch, so I will pass for now. Too bad.

Tim

I don't blame you.  Probably the reason I've never cottoned to Arch is that I can't resist enabling testing repositories, and it always goes downhill from there.

Awesome has a pretty steep learning curve, TBH.  The configuration is all lua code; even changing the wallpaper requires hacking a script.  Once you get the hang of it, though, it's a blast.

---

### Post by ratcheer on 2012-05-05
Thanks. I suspect that, knowing Smalltalk and Ruby, Lua shouldn't be much of a learning curve. But I'm still going to stay away from that testing repo.

Tim

---

