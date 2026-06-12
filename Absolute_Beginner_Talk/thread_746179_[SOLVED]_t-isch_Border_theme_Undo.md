---
title: "[SOLVED] t-isch Border theme Undo"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Ohwii on 2008-04-05
Hi guys, 

well I guess this seems kind of obvious, but I can't get it to work. 

Yesterday I tried half the time to install a border theme for compiz and now I cannot undo it. 

I have compiz, emerald theme manger and the GL desktop installed. but now I want to go back to the human windows border them . 

Well every time when change the theme in System > Preferences > Appearance > Theme  
nothing changes. the border stays the same.

If you need more Info from some commands let me know. 

I just want it back to the Human style. :confused:

 Thanks in advance 

oh Wii

---

### Post by Michael.Godawski on 2008-04-05
When you go to
System > Preferences > Appearance > Theme 
and choose Human, what happens? Nothing? Something?

---

### Post by Ohwii on 2008-04-05
Nope nothing happens. just stays the same

---

### Post by sayakb on 2008-04-05
You need to remove emerald to use a GTK theme w/ compiz: 
 ```
sudo apt-get remove emerald
```

---

### Post by qamelian on 2008-04-05
> **LinuxIsInnovation said:**
> You need to remove emerald to use a GTK theme w/ compiz: 
 ```
sudo apt-get remove emerald
```
No, you don't. You can either turn off emerald by pressing Alt-F2 and typing:
```
gtk-window-decorator --replace
```
or you can edit the script /usr/bin/compiz and find the line that tells compiz to use emerald as the decorator and set the option to no rather than yes. A safer bet would be to install Simple-CCSM from the repos and use it to tell compiz which decorator to use.

---

### Post by sayakb on 2008-04-05
> **qamelian said:**
> No, you don't. You can either turn off emerald by pressing Alt-F2 and typing:
```
gtk-window-decorator --replace
```or you can edit the script /usr/bin/compiz and find the line that tells compiz to use emerald as the decorator and set the option to no rather than yes. A safer bet would be to install Simple-CCSM from the repos and use it to tell compiz which decorator to use.

 Wow.. I didn't know that .. Thanks :D (I'm still learning, just 6 months on linux, you see ;))

---

### Post by Ohwii on 2008-04-05
Thanks for the post.

I will check it out.

---

### Post by qamelian on 2008-04-05
> **LinuxIsInnovation said:**
> Wow.. I didn't know that .. Thanks :D (I'm still learning, just 6 months on linux, you see ;))
No problem. I've been using Linux for 11 years and there is always something else to learn.

---

