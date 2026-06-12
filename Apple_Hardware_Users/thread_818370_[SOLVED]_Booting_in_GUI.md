---
title: "[SOLVED] Booting in GUI"
date: 2008-06-04
forum: Apple Hardware Users
---

### Post by Scientia on 2008-06-04
Look, folks, i know this is really dumb.
I had problems with my xorg.conf, and after some tinkering around and stuff i did a Ctrl-Alt-F2 on startup. Whoops. Now i boot in CLI, and the ridiculously absurd thing is that i don't know how to boot back in GUI. Oh boy, if there was a shamefaced smiley i'd use it...

Help, Please? sorry for wastin y'alls time:(

---

### Post by avtolle on 2008-06-04
What happens when you do Ctrl+Alt+F7 from the CLI?

---

### Post by Scientia on 2008-06-04
Errm.. Nothing..? it shows me a blank screen with the blinking _ on top left.
Also the Ctrl-Alt-F_ keys just change the line above the command line login as in F1 will be what@whatblah blah tty1 then below blahblah-laptop login:
F2 tty2 and so on.

I just need to know hoe to switch back from CLI to GUI.

Thanks

---

### Post by hpp3 on 2008-06-04
I know some folks who would love to be able to boot to cli mode on Ubuntu. :p
It could be your X server is still borked.
List all your processes with
```

ps -A

```
and see if Xserver or Xorg or Xsomething is running.
If it is, you've got something weird going on.
If not, then
```

gdm

```
or 
```

startx

```
should either put you into a graphical mode until you get everything straightened out, or it will throw an error.
If you get an error, your X is borked and you'll have to figure out what is wrong.
I know there is a standard Ubuntu way to reset your Xorg.config, but my favorite is 
```

X -configure

```
which will automagically come up with an xorg config that will match your system, and give you instructions on how to test it.

Let us know what you come up with...

---

### Post by stream303 on 2008-06-04
What machine are you trying to boot, and which version of ubuntu?  Also, how much on-board ram does it have?  Is the hard drive original, or a replacement?

Once we know that, we can get that xorg.conf tweaked properly.

---

### Post by Scientia on 2008-06-05
I used this- [http://ubuntuforums.org/showthread.php?t=818049](http://ubuntuforums.org/showthread.php?t=818049) but instead edited the xorg.conf from the install cd. Then when i used ctrl-alt-f2 when booting, the thing started in CLI. I'm trying to boot a PowerPC iBook G3 700mhz, ATI Radeon Mobility 7500. RAM is 384MB, hard drive original. Worked perfectly before except for display brightness and Suspend probs which is why i tried editing xorg in the first place.

---

### Post by Scientia on 2008-06-05
It could be your X server is still borked.
List all your processes with
```

ps -A

```
and see if Xserver or Xorg or Xsomething is running.
If it is, you've got something weird going on.
If not, then
```

gdm

```
or 
```

startx

```
should either put you into a graphical mode until you get everything straightened out, or it will throw an error.
If you get an error, your X is borked and you'll have to figure out what is wrong.

I don't have any X's running. I did a startx and i got an error, my X IS borked.

I did X -configure, followed the steps to test. I got a grey screen(black with lots of tiny white dots) with an X. Moving my mouse moves the X.
How Now?
Please help, in bad state.

---

### Post by Scientia on 2008-06-05
I got it working with sudo dpkg-reconfigure xserver-xorg
Thanks people!!!

---

