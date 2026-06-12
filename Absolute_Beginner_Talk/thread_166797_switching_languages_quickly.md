---
title: "switching languages quickly"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2006-04-27
I use ubuntu 5.10 and I often need to switch quickly from one keyboard input language to another during work. I know I can do this through keyboard layout settings, but that is not an easy way. Is there a special command for this?

---

### Post by Bloch on 2006-04-27
I'd like to know too.

---

### Post by mostwanted on 2006-04-27
This should work (replace .us with your desired locale):

xmodmap /usr/share/xmodmap/xmodmap.us

---

### Post by Sef on 2006-04-27
My keyboard is dual set up too.  I simply push both alt buttons at the same to switch languages.  I set it up when I set up the keyboard I believe.

---

### Post by 1002285 on 2006-04-27
Thank you for these answers.
mostwanted - sorry, I don't quite understand what it is that you suggest and what I would get.
Is this
xmodmap /usr/share/xmodmap/xmodmap.us
a command to type in the terminal? I don't have a folder named "share". And how does the switching then actually take place?
The best way for me would be to use sth like Sef described, but where would I set it up, may-be I'll have to go through the xserver-xorg configuration?
I use 5.10 and Gnome 2.12.1?

---

### Post by Sef on 2006-04-27
> The best way for me would be to use sth like Sef described, but where would I set it up, may-be I'll have to go through the xserver-xorg configuration?

I think it was when I did the keyboard set up.  First I checked the languages, then I checked the keyboard.

---

