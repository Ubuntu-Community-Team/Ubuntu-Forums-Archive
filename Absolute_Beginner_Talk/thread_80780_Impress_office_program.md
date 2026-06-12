---
title: "Impress office program"
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by danrkeva on 2005-10-23
Trying to use this to make a Power Point presention and can't get the projector to show the slides anyone know the trick to get the projector to show the slides for the Impress program.  My laptop with powerpoint messed up and won't run the power point program.  I can get the program on the computer screen and go through it but can't figure out how to get the slides to show up on the projector.
Thanks
Danny

---

### Post by raghav_p on 2005-10-23
I'm not sure I understand your problem. Are you connecting your laptop to an external projector? If so, is the laptop screen displaying on the projector screen?

---

### Post by danrkeva on 2005-10-23
Yes I have a external projector, the program shows up on the laptop screen, and I can do a slide show there  but I can't get it to work on the projected screen.There must be some way to toggle the screen I know in windows there is one of the F buttons that sends the single to the projector.
Thanks
Danny

---

### Post by adriantry on 2005-10-23
[QUOTE=danrkeva]here must be some way to toggle the screen I know in windows there is one of the F buttons that sends the single to the projector.[/QUOTE]

Hi Danny

That's not a function of Windows, it's a function of your laptop. The same key should work in Linux.

If it helps, the key on my Sony Vaio laptop is Fn-F7.

Adrian

---

### Post by raghav_p on 2005-10-23
We'll need more information. What make/model is your laptop? What video card does it use?

---

### Post by danrkeva on 2005-10-23
Laptop is Dell Latitude CP running Ubuntu and Open Office Have no idea what type of card it has in it.  program show up fine on screen of laptop but won't show up on the projected screen.  I can go through the whole slide show on the computer screen but nothing seems to get it to show up on the projector screen.
thanks
danny

---

### Post by raghav_p on 2005-10-23
Does any part of the computer screen show up on the external screen?

---

### Post by adriantry on 2005-10-23
[QUOTE=adriantry]That's not a function of Windows, it's a function of your laptop. The same key should work in Linux.[/QUOTE]

Sorry, looks like it's more complicated than I thought.

I just came across a thread that may help:

[http://www.ubuntuforums.org/showthread.php?t=78570](http://www.ubuntuforums.org/showthread.php?t=78570)

---

### Post by raghav_p on 2005-10-23
[QUOTE=adriantry]Sorry, looks like it's more complicated than I thought.

I just came across a thread that may help:

[http://www.ubuntuforums.org/showthread.php?t=78570](http://www.ubuntuforums.org/showthread.php?t=78570)[/QUOTE]

That would only work of course if you have the same make and video card which is highly doubtful. 

I'm sure you'll need your video card make/model before proceeding. I'm not sure how to garner that info though : (

---

### Post by danrkeva on 2005-10-23
Know this sounds really dumb but what is the Fn button.  I have no idea what it is.  know about using Ctrl and Alt and the Shift to change things but have no idea what the Fn button is.
Danny

---

### Post by adriantry on 2005-10-23
[QUOTE=danrkeva]Know this sounds really dumb but what is the Fn button.  I have no idea what it is.  know about using Ctrl and Alt and the Shift to change things but have no idea what the Fn button is.
Danny[/QUOTE]

It's an extra "Function" button that a lot of laptops have. In conjuction with the function keys, they give access to functions like volume, brightness and contrast, and external monitor. They also often work with the buried numeric keyboard to allow you to type numbers without the number lock being activated.

But I have to apologise - the Fn key doesn't seem to be working for me in Ubuntu. I have to admit that I'm not an expert, and I'm still learning.

In an earlier message, I referred to another thread that recommends using the following command when the projector is plugged in:

sudo dpkg-reconfigure -phigh xserver-xorg

Another poster (raghav) said that command wouldn't work unless you had the same video card used in the other thread. I'm sure that raghav knows more about this than I do, but I can't see what that command has to do with the video card used. Maybe there were other steps taken that I missed. For what it's worth, the original poster in the other thread used a Dell Latitude c800 laptop.

Anyway, I hope you get it all worked out.

---

