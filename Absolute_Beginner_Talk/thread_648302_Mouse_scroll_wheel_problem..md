---
title: "Mouse scroll wheel problem."
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by jmail524 on 2007-12-23
Hello everyone,

I still trying to lean Ubuntu and always seem to get weird issues.  I had been using Gutsy AMD64, but I too many programs I needed to use didn't have a 64-bit version available so I decided to move back to Gutsy 32-bit.

I now have a really weirs problem.  When I use the scroll wheel on my mouse to scroll the screen, it will move the screen up a little and then display a menu.  It displays the same menu that I get when I use the 'RIGHT' mouse button. The occurs in everything: Firefox, Nautilus, Rhythmbox, etc...  Scrolling down doesn't have any problems.  The odd thing is that this did not occur in the 64-bit version of Gutsy.

If anyone has any good ideas, I would be very appreciative.

---

### Post by Joeb454 on 2007-12-23
Are you sure you're not clicking the wheel button down?

Also check the settings of your mouse (should be somewhere under System > Administration)

---

### Post by FreewheelinFrank on 2007-12-23
Run this command in a terminal:

```
xev
```

A little widow appear plus a slightly larger window.

Position the cursor over the small window and click the mouse buttons and rotate the wheel: the mouse output will appear in the larger window. (Try to keep the mouse still as mouse movement also appears.)

The right mouse button and forward/backward movement should all have a different button number.

If the right button and up screen rotation somehow have the same function, use Xbindkeys to reassign functions to buttons:

[http://ubuntuforums.org/showthread.php?t=65471](http://ubuntuforums.org/showthread.php?t=65471)

I used this method to get the side buttons on my mouse working- I hope it'll work to fix your problem.

---

### Post by jmail524 on 2007-12-23
When I scroll the mouse up I get 2 events: (I think I summarized the relevant information.)

     ConfigureNotify  event
          state 0x10, button 5

     ConfigureNotify event
          state 0x01010, button 5

When I scroll down I get 7 events total:

     ConfigureNotify event
          event 0x2e00001

     ConfigureNotify event
          event 0x2e00001

     ButtonPress event
          state 0x10, button 2

     ButtonPress event
          state 0x210, button 4

     ButtonRelease event
          state 0xa10, button 4

     ConfigureNotify event
          event 0x2e00001

     ButtonPress event
          state 0x210, button 3

I do not think I am pressing the wheel down of accidentally hitting the right mouse button, I am being very careful.  Besides, I have been using 64-bit Gutsy for about 6 months and never had this issue, I don't think my mouse habits  have changed.

I am having this issue when running the 32-bit Gutsy Live CD, but with the 64-bit Gutsy Live CD the mouse works fine.  I am using a Logitech mouse.

---

### Post by FreewheelinFrank on 2007-12-23
Have you tried using a different mouse?

I had a problem with right clicks of my mouse being registered as double clicks and assumed it was a problem with Ubuntu because the mouse was a) not that old and b)a good brand, but it turned out to be a problem with the mouse.

What are the outputs of the following commands as described in the link below?

```
cat /proc/bus/input/devices
```

```
sudo gedit /etc/X11/xorg.conf
```

[http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)

I had to manually configurel evdev to get Gutsy to autodetect my mouse as described here:

[http://ubuntuforums.org/showpost.php?p=3881090&postcount=589](http://ubuntuforums.org/showpost.php?p=3881090&postcount=589)

The mouse worked before with generic detection but I think it behaves better now.

---

