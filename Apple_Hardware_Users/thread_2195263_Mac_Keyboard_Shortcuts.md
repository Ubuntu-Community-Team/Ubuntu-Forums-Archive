---
title: "Mac Keyboard Shortcuts"
date: 2013-12-23
forum: Apple Hardware Users
---

### Post by b3n0 on 2013-12-23
Hey everyone,

I haven't used Ubuntu seriously in over three years. It's now time to come on back! In the last three years I've been using MacOS exclusively. I've dual booted MacOS with Ubuntu 13.10. It's working really nicely. There's a couple of tweaks I need to make. The biggest thing is the keyboard shortcuts. I'd like to be able to use CMD + C (copy) and CMD + V (paste)... etc.

I'm sure there has to be a way to do a system wide change.

I found these articles:
[https://help.ubuntu.com/community/AppleKeyboard]("https://help.ubuntu.com/community/AppleKeyboard")
[http://askubuntu.com/questions/10008/how-to-make-keyboard-work-like-osx-system-wide]("http://askubuntu.com/questions/10008/how-to-make-keyboard-work-like-osx-system-wide")

But I can't seem to see any changes.

Can anyone offer some step by step advice?

---

### Post by ankurgupta1985 on 2014-04-02
I am going through the same problem. I actually started a blog about it. I have Lubuntu 13.10 though. See this: [http://perfectlyrandom.org/?p=66](http://perfectlyrandom.org/?p=66) (shameless self-promotion)
I think the autokey solution might work for you.

---

### Post by Lazar_Milicic on 2014-06-10
[COLOR=#213C51][FONT=Arial]Hey I took this course - **Productivity for Mac Users: Shortcuts and Tools to 10x Your Productivity on the Computer**, it was really good and thought I'd share a free coupon here. 

Coupon link - [/FONT][/COLOR]https://www.udemy.com/mac-keyboard-shortcuts/?couponCode=productiveyou[COLOR=#213C51][FONT=Arial]

I hope you will like it as much as I did.[/FONT][/COLOR]

---

### Post by MikeBraxner on 2014-06-10
Have a look at [https://help.ubuntu.com/community/AppleKeyboard#Mapping_keys_.28Insert.2C_Alt.2C_Cmd.2C_etc..29](https://help.ubuntu.com/community/AppleKeyboard#Mapping_keys_.28Insert.2C_Alt.2C_Cmd.2C_etc..29).

What it boils down to is a small adjustment in an [COLOR=#333333][FONT=Ubuntu]xmodmap init file (e.g. ~/.Xmodmap) along the lines of ...
[/FONT][/COLOR]```
clear control
clear mod5
clear mod4


keycode 64 = Alt_L
keycode 108 = Alt_R
keycode 133 = Control_L
keycode 134 = Control_R

add control = Control_L Control_R
```[COLOR=#333333][FONT=Ubuntu]

[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Now simple have this called when needed, say from */etc/rc.local* via [/FONT][/COLOR]***xmodmap /home/[your user id]/.Xmodmap &***, and you should be all set.

---

### Post by Patricia_Konarski_ on 2014-06-23
Welcome back to Ubuntu, B3n0.  Mike has got a good link, so I just you take a look at that.  All the best.

Patricia Konarski Tucson
--Freelance editor and owner of Patricia Konarski Literary Services of Tucson

---

