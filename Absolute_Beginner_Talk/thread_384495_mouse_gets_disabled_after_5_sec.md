---
title: "mouse gets disabled after 5 sec"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by hooldus on 2007-03-14
Hello!

Yesterday I installed Xubuntu, and I have already one problem. After the system starts I can use mouse for 5 sec. After this, I think, my notebooks (FS L1310G) touchpad is recognized, and the mouse (Logitech, USB mouse) gets disabled. (though I can use touchpad, but not mouse).
How can I use mouse and touchpad simultaneously, because touchpad is less comfortable then mouse.

And one more question.
Can somebody recommend me some sites with tutorials and articles for newbies (smth like psychocats.net).

Thank you in advance.

---

### Post by glenndavy on 2007-03-15
hey there - I'm wondering what makes you think that the recognition of the touchpad suddenly kicks in and cuts out the mouse? I dont mean that in an obnoxious way, just have you seen something that hints at that, or is it just a hunch/guess?

in mean time, in /var/log there will be dozens of  files - I wonder if  you can find  Xorg.0.log and udev - compress them in someway and post a reply with them attached?

glenn

---

### Post by hooldus on 2007-03-16
**glenndavy**
Thanks for your response.

I just realized that I was a bit wrong :) The touchpad is recognized from the very beginning and it's still working after 5 sec. But mouse gets disabled after 5 sec of using the system (after the desktop appears).

---

### Post by glenndavy on 2007-03-16
ok - im sorry to say I couldnt find any hints there - I thought there might have been an error 'thrown' and available in log file at time mouse became unavaliable.

you could also try:
dmesg |grep -i mouse
to see if anything revealing appears

so before you login... do you use xdm/kdm/gdm? do both mouse and touchpad work correctly for an indefinite amount of time there... then is it only when you get in to xfce that you hit an issue?

---

