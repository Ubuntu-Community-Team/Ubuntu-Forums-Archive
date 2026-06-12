---
title: "How do i get this away?"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-05-26
How do i get this away [[img]http://bildr.no/thumb/69636.jpeg[/img]](http://bildr.no/view/69636) ? 

And the screens seems to not fit, or is it just me not being used to Ubuntu Studio look?

---

### Post by Pizzarth on 2007-05-26
I'm using ubuntustudio too, and that's what it's supposed to look like. except I'm using a bigger resolution

you mean the driver thing? that' another question. maybe edit that post to make it a little moer clear what you're asking

---

### Post by ajmannen on 2007-05-26
I set it to 1400x 900x . I have a 17" laptop screen, is that the right resolution?

---

### Post by taurus on 2007-05-26
Unless you have a widescreen.  Otherwise, use 1024x768 or 1280x1024.

---

### Post by ajmannen on 2007-05-26
I think i have a wide screen ( Acer CrystalBright LCD) how do i change to 1280x1024

---

### Post by Pizzarth on 2007-05-26
no that's not the right resolution. it's at 1024x768, at most. I didn't bother checking, sorry. But with a 17 inch  you could easily have it at 1280x1024. my cousin's 17" goes higher. I guess when it came to the stage of the installation where you check off what resolutions you wanted to be able to use, you just left it alone, right? that'll set it to the default max of 1024x768. either install it again, or change the xorg.conf file, adding on the resolutions, but I havent tried doing that, so I can't guarentee it's safety. make a backup of the file first, then do it. and remember to operate in root or sudo when doing it.

---

### Post by ajmannen on 2007-05-26
Umm... i made it 1440x 900x , anny guids to how to change it in x-org.confg

---

### Post by zettberlin on 2007-05-26
Just install the proprietary NVIDIA-drivr or reenable it, then set the correct resolution for your screen - 1400x900 sounds OK, but check you manual first...

BTW: that you set the corrrect resolution does not mean, it shows up in any case. The driver must support it - the NVIDIA does for sure, on the screenshot is no sane resolution for any computer of the last 3 years...

---

### Post by ajmannen on 2007-05-26
To...darm.....complicated. I'll just re-install the whole thing whit resolution 1280x1024 or 1024x768 i'm not sure what to use....WHAT SHOULD I USE! 
and how do i get those restricted drivers away?

---

### Post by nonewmsgs on 2007-05-26
omg is that a gorgeous look.  how can i get that?

---

### Post by Happy_Man on 2007-05-26
Dude... I really think you need to calm down. If you want the restricted driver window to go away, click "close." For your xorg.conf problem... open up a terminal (applications -> Accessories --> Terminal). Then type
```
gksudo gedit /etc/X11/xorg.conf
```

Go down to the section that lists all the resolutions, and add "1280x1024" (quotes and all) to the end of each line w/ resolutions on it. Then log out, and log back in. Hopefully, you will be able to change to 1280x1024.

---

### Post by taurus on 2007-05-26
You also need to restart X again after you log out with <Ctrl><Alt>Backspace.

---

### Post by ajmannen on 2007-05-27
Ok, now i'm calm (to manny red bulls) should i rename  every one that says 1440x900 (sorry for being stupid but i scared of braking something) 
[[img]http://bildr.no/thumb/69665.jpeg[/img]](http://bildr.no/view/69665)

I'm going to try and use Envy on the restricted drivers

---

### Post by ajmannen on 2007-05-27
Envy made one of the restricted drivers go away, but should i change all of the 1400x900, and what dos it mean that this driver, or whatever it is, is un supported? [[img]http://bildr.no/thumb/69686.jpeg[/img]](http://bildr.no/view/69686)

---

### Post by Happy_Man on 2007-05-27
It just means that the Ubuntu team aren't the people updating it.... so don't sue them if everything goes belly-up. A disclaimer, really. Not to worry, though; they all work fine. Now, as for your xorg.conf, that looks ok to me.... try it out like me and taurus said above.

---

