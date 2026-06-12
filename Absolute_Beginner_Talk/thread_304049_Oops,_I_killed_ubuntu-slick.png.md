---
title: "Oops, I killed ubuntu-slick.png"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by twrock on 2006-11-21
I was messing around trying to make some changes in my splash screen and I succeeded copying over my ubuntu-slick.png file (the original brown Ubuntu splash screen). I tried to find the file via search engine and here as well, but hey, who could possibly need the original splash screen that comes pre-installed in every system? :oops: Is it available as a stand-alone file somewhere, or can someone post it somewhere for me?

The file is in /usr/share/pixmaps/splash/.

Thanks

---

### Post by Ben Sprinkle on 2006-11-21
Just switch the themes, you can find the application to change it in the menu.

---

### Post by twrock on 2006-11-21
I'm not sure what you mean. My problem isn't because I changed the theme, I actually copied another file over the ubuntu-slick.png file, so I no longer have the original file to revert to.

---

### Post by Ben Sprinkle on 2006-11-21
I know, but change themes quick or next reboot it will mess up. It's temp so you can recover the file from someone here. I would attach but I am not at linux right now.

---

### Post by maximouse on 2006-11-21
Here it is.

---

### Post by twrock on 2006-11-21
Too late. I've already rebooted. However, I didn't encounter any problems. Ok, here's what I did (or at least what I think I did).

I was toying around with changing my whole desktop look, including Grub splash, Ubuntu splash and login screens. As part of that process, I downloaded ubuntu-splash-blue.png. Using terminal, I "sudo cp ubuntu-splash-blue.png /usr/share/pixmaps/splash/ubuntu-splash.png". What I hadn't noticed was that ubuntu-splash.png was only a shortcut to ubuntu-slick.png. (I couldn't see the little arrow on my 1280x1024 resolution screen because it is so small and sits right in the middle of the word "ubuntu", making it even harder to see.) So instead of just copying over the ubuntu-splash.png file, I copied over both at the same time. So now, ubuntu-splash.png and ubuntu-slick.png and ubuntu-splash-blue.png all look exactly the same: blue.

I hope that makes sense.

---

### Post by twrock on 2006-11-21
Yep, that's it maximouse. Thanks.

---

