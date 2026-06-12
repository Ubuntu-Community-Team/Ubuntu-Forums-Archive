---
title: "ubuntu crashed! I had to turn off the power!"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-03
I had just started Planet Penguin Racer, I was looking through the different races when my screen suddenly started to get dark. Oh, no, the screensaver I thought. So I moved the mouse and nothing and then pressed the keyboard.

At this stage the screen became bright but my mouse was permanently stuck with the hand. It moved but that was it. The keyboard worked and that was useless as I don't know any commands which might have helped.

ctrl-alt-del may have helped on XP but it was a no show here. So off with the power.
Then an extra long start-up as ubuntu "Checking all filesystems..."

I have just turned OFF my screensaver.

What are the keyboard commands to close programs and also reboot in cases such as this?

Also is there any software so I can use to check the state of my HDDs?

I'll give Planet Pengiun Racer another try.

Thanks.

](*,)  @ crash

---

### Post by durand on 2006-06-03
> What are the keyboard commands to close programs and also reboot in cases such as this?

If you press CTRL+ALT+F1 , you can get a simple terminal where you can type any commands. You will have to login there and then u can kill planet penguin racer and most other programs if u know the name of the program. EG. for planet penguin racer, the name of the program is ppracer so u can do ```
killall -9 ppracer
```If you don't know the name of ur program, you can run the command "top" in the terminal. this shows running porgrams in order of CPU usage.

To reboot, you can type ```
sudo reboot
```, providing you know the root password.
ps. when you type in the password for sudo, it doesn't show anything, not even ***

---

### Post by NiceGuy on 2006-06-03
One which I've always found helpfull is Ctrl + Alt + Backspace (note **not** delete). What that does is it kills the X server (the graphical part of linux) and it should drop you back at the login screen. Occasionally it will drop you at a command login. If it does that then login, and type startx to start the X server or sudo reboot to... well... reboot! :D

---

### Post by u.b.u.n.t.u on 2006-06-03
Thanks. add/remove froze. So I tired ctrl-alt-F1 and then "top" but I didn't see anything to remove so I rebooted. Add/remove works now.

I've installed xfce4-taskmanager.  Like ctrl-alt-del :)

---

### Post by rocka on 2006-07-02
Hi all,

I just had the same problem - it went to the screensaver and promptly locked up! VLC media player just started stuttering on the bit of the song it was playing at the time. CTRL-ALT-F1 did nothing, neither did CTRL-ALT-Backspace.

Any ideas how to assess/repair this problem?

TIA :)

---

### Post by MaximB on 2006-07-02
NOTE : some of your crashes may have been caused b/z you haven't installed your video card and you are trying to run 3d applications
that's happen to me several times until I fixed it. (I mean installed my ATI video card).

---

