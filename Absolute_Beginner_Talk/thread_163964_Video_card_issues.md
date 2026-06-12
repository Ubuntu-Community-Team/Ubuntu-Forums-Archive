---
title: "Video card issues"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by Justin Holt on 2006-04-21
Jaton Geforce 2 MX400 64Mb pci card

My problem is that this card can get me up to where ubuntu gets through its initial boot up (aka the long list of things) and after that, i get a cursor that doesn't blink and it is frozen. By the way if it helps, i am using Dapper Beta if that makes any difference.

I really just want to use linux on my tv so i am just wondering why it doesn't work

Computer Specs:
800 MHZ Celeron Processor
196 MB of RAM
30 GB hard drive

Thats about it...

---

### Post by dermotti on 2006-04-21
run **sudo dpkg-reconfigure xserver-xorg **and select **vesa** as your driver, then reboot or restart X

---

### Post by Justin Holt on 2006-04-21
So then by using this command you are telling me to then insert my video card after starting and then going into the terminal and make it startx?

---

### Post by Jason_25 on 2006-04-21
Never mess with a video card while the computer is running.  To enter those commands, press ctrl-alt-f1 to get to a virtual terminal.  Once you have finished reconfiguring. type:
```

sudo /etc/init.d/gdm restart

```

---

### Post by Justin Holt on 2006-04-21
well first i have to reboot and get that far...it will probably get to the point where i will reinstall ubuntu tomorrow afternoon...wish me luck

---

### Post by Justin Holt on 2006-04-21
Well I Screwed Up Pretty Good, Sorry By The Way If This Is All In Caps, I Am Using Lynx To Browse Around, But Um, Well I Got An Error, It Would Be Greatly Appreciated If I Could Get Some Help Reverting Back To What My Previous Settings Were

---

### Post by Jason_25 on 2006-04-21
Congratulations on posting with a text browser.  Could you elaborate on what you did and what the error said?

---

### Post by Justin Holt on 2006-04-22
it said something like the x server was not configured correctly and can not start, i could not start gdm by putting in gdm either.

---

### Post by Jason_25 on 2006-04-22
Ok you'll need to be a little more specific or post the contents of your Xorg.0.log and your xorg.conf.

---

### Post by Justin Holt on 2006-04-22
seems to me i will probably just reinstall dapper, and then attempt to get to the full screen terminal and use lynx if it doesnt work...but i will deffiantly let you know what i can find

---

