---
title: "problem with desktop settings"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by marsia on 2008-02-12
I posted in the morning saying that both my bottom and top toolbars were lost, and the only thing i could see on the screen was my desktop files / folders. Now, folders have also been disappeared. 
When I log in, i put my name and password and when I chose the normal session then I can click on the empty screen and it gives me options, among them "desktop settings". I can also access terminal via CTRL ALT F1, ...

I know all my files are still in there, i just cannot see anything on the desktop. 
how do I bring the very first settings back? what is the command I should give the terminal so I can see my folders on the desktop and the tool bars again? 

thanks for that.

please, take it slowly, I am a complete beginner

Marsia

---

### Post by smartboyathome on 2008-02-12
Try running "metacity --replace" (without the quotes) via alt+f2 and see if it fixes it. Did you change the desktop effects at all?

---

### Post by marsia on 2008-02-12
I tried 

Ctrl Alt F1
logged in

rm-rf .gnome .gnome2 .gconf .gconfd .metacity

Ctrl Alt F7

nothing happened. is it the same thing with what you just said? 

I may have changed the desktop effect accidentally.

---

### Post by marsia on 2008-02-12
no, metacity--replace does not fix it...

---

### Post by marsia on 2008-02-12
any more suggestions?

---

### Post by marsia on 2008-02-13
do i need to format and re-install?

---

### Post by overdrank on 2008-02-13
> **marsia said:**
> I tried 

Ctrl Alt F1
logged in

rm-rf .gnome .gnome2 .gconf .gconfd .metacity

Ctrl Alt F7

nothing happened. is it the same thing with what you just said? 

I may have changed the desktop effect accidentally.

HI and why would you remove these? When you use the command metacity --replace it will not work with you removing it. You can try the command ```
sudo apt-get install ubuntu-desktop
```

---

