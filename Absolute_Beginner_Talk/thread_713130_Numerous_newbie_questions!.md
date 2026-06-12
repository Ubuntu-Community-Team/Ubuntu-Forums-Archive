---
title: "Numerous newbie questions!"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Wobbley on 2008-03-02
Hey

Instead of making tons of threads i decided to shove it all into one thread with several questions :) First of all i would like to point out that i have NEVER used linux until now so bear with me please.

System specs:
8800GTX 768mb
E6600 2.4 @ 2,7
4gb RAM
Disc is split into 4 with Vista (NTFS), Linux (ext3), Sideswap, Storage(NTFS)

1. I managed to dual head on ubuntu, but it seems the primary monitor takes a while longer to open the "Applications" "Places" and "System" tabs (actually any tabs like that), or for example when i right click something it takes longer for the square thingi with the options to open compared to the secondary screen. (Could this be due to the difference to the refresh rate on the 2 screens? Primary is 60 secondary is 75) Also on the secondary screen i am unable to move anything, when a windows opens its stuck there.

[Answered by TheExplorer] 2. Is there an option to quickly switch the keyboard language like in Windows you have Alt   + Shift button, This comes in handy since i juggle between languages.

[Answered by kpkeerthi] 3. Just making sure: Creative X-Fi cards are NOT supported right? Since creative are being stingy :(

[Answered by Mazza558] 4. I have a Razer Tarantula keyboard, I am really used to being able to use the multimedia keys on it (i doubt i can get the macro keys to work) anyway to do that in ubuntu?

[Answered by realmerx] 5. Any advice for "must have" software for linux? Also whats a good software for monitoring hardware and network? 

[Answered by warbird and ringi] 6. VLC "Always on top" is not working, vlc on top is a must! :(

[Answered by Mazza558] 7. I love eyecandy, i got beryl or whatever its called that comes with ubuntu, any places i could find themes or cursors skins that dont look like their made by 5 year olds and sparkle my eyes to death?

Hope you guys can help me out! :D

---

### Post by TheExplorer on 2008-03-02
> 2. Is there an option to quickly switch the keyboard language like in Windows you have Alt + Shift button, This comes in handy since i juggle between languages.
Yes, go to System - Prefs - Keyboard - Layout Opts (Tab) - Group Shift behavior.

---

### Post by Mazza558 on 2008-03-02
> 7. I love eyecandy, i got beryl or whatever its called that comes with ubuntu, any places i could find themes or cursors skins that dont look like their made by 5 year olds and sparkle my eyes to death?

Try [THESE]("http://www.gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=100") for actual window themes and[HERE]("http://www.gnome-look.org/index.php?xcontentmode=101") for window title themes. I like using Aurora myself (the top theme for the first link)

---

### Post by Mazza558 on 2008-03-02
> **Wobbley said:**
> 


4. I have a Razer Tarantula keyboard, I am really used to being able to use the multimedia keys on it (i doubt i can get the macro keys to work) anyway to do that in ubuntu?


I just did a search and found that this keyboard is pretty badly supported in ubuntu - it'll probably work but not the special functions.

---

### Post by Wobbley on 2008-03-02
wooo thanks guys :)

Second link was broken >)

---

### Post by Mazza558 on 2008-03-02
> **Wobbley said:**
> 

Second link was broken >)

Fixed it. Try again :)

---

### Post by vamsibethapudy on 2008-03-02
> **Wobbley said:**
> 
5. Any advice for "must have" software for linux? Also whats a good software for monitoring hardware and network? 


conky is a great desktop monitoring software.it is customizable.
[http://ubuntuforums.org/showthread.php?t=281865&highlight=start-up+programs](http://ubuntuforums.org/showthread.php?t=281865&highlight=start-up+programs)
is a great link.
i still have some questions on conky & its functionality.
but you too try it anyway.
there seems to be another software for this purpose. dont know its name.

scribus is a publishing software.
miro is an internet tv software like real & windows media player
its still being improved.
k3b is a great cd / dvd writing software.
wine is a must if you want to run windows programs.
these are the very basic ones.

---

### Post by Wobbley on 2008-03-03
Thanks alot guys gotten alot of answers and most of my kinks and questions have been answered. Except the first one. Could anyone help me out with that one?

---

### Post by MegaJim on 2008-03-03
I havent had that problem myself, but you could try launching the nvidia-settings X server config tool and play around with it a little.

```
sudo nvidia-settings
```

---

### Post by warbird on 2008-03-03
6: This is a problem with VLC AFAIK, and its been bothering me too. For now, use totem to play back if you need always on top (Movie Player under Applications -> sound & video). In Totem, go to edit -> plugins and enable always on top (or you can rightclick on the top window border and enable always on top there, which is easier :))

---

### Post by kpkeerthi on 2008-03-03
> 3. Just making sure: Creative X-Fi cards are NOT supported right? Since creative are being stingy 

[http://opensource.creative.com/soundcard.html#X-FI](http://opensource.creative.com/soundcard.html#X-FI)

---

### Post by kpkeerthi on 2008-03-03
> 5. Any advice for "must have" software for linux? Also whats a good software for monitoring hardware and network? 
```
netstat -antp
```
Lists out all active TCP connections (port, IP and the programs currently using/listening on it)

---

### Post by xc3RnbFO8P on 2008-03-03
VLC on top: switch interface to wxwidgets , then rigth click on VLC border and check on top.

---

### Post by Wobbley on 2008-03-03
woooo thanks guys! =D>

I bet i can check myself when i get home but how do i change the interface to wxwidgets?

oh right this aint ubuntu directly but might give it a shot here:

How do i tile chat windows in xchat?

---

### Post by xc3RnbFO8P on 2008-03-03
> **Wobbley said:**
> woooo thanks guys! =D>

I bet i can check myself when i get home but how do i change the interface to wxwidgets?

Settings>Switch Interface

---

### Post by Wobbley on 2008-03-05
hmmm anyone got an answer to that first question?

Also the screen gets "pushed down" by like 1/5 if my hertz is any higher then 60 (the monitor goes to 75) it also gets detected as a CRT.

Should i try posting that question only under multimedia and video? or hardware? :S

---

