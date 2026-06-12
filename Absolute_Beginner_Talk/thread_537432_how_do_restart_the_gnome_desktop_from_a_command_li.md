---
title: "how do restart the gnome desktop from a command line"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by 99bluefoxx on 2007-08-28
im running off the live boot disk[my psu cant support a hdd very long n e mor] and my desktop icons and taskbars keep freezing up. i dont wanna reboot and lose all my settings so how can i fix this?i tried 
```
sudo /etc/init.d/gdm restart
```
but when i did that the terminal gace me this:
```

ubuntu@ubuntu:~$ sudo /etc/init.d/gdm restart
 * Stopping GNOME Display Manager...                                     [ ok ] 
 * Starting GNOME Display Manager...                                     [fail] 

```
what other command lines can i remedy this with?

---

### Post by st33med on 2007-08-28
Try Control Alt Backspace. It returns to... actually, I don't know with the LIVE CD. Possibly the main menu?

---

### Post by Hobo Joe on 2007-08-28
ALT + CTRL + Backspace.

---

### Post by 99bluefoxx on 2007-08-28
did the ctrl alt bkspc
kinda worked nut now the panels are gone, and it gave me an error message saying"I've detected that another panel is allready running, now im going to exit
now what?

---

### Post by st33med on 2007-08-28
Does it do anything else, like, does it return to the menu, or remain frozen there?

---

### Post by 99bluefoxx on 2007-08-28
yes it returns to the logon screen
then i log back into the defualt account
then it tells me the message

---

### Post by st33med on 2007-08-28
And stays there?

You could also reboot and try Safe Graphics mode.

---

### Post by 99bluefoxx on 2007-08-28
like i said
i dont wanna roboot cause i will lose all the settings
and it takes me a few hours to get everything working like i have it

---

### Post by st33med on 2007-08-28
Hmmmm... does Ctrl Alt F1 result in a username prompt in a shell?

400th post

---

### Post by 99bluefoxx on 2007-08-28
yes
edit:gratz on post 400 ^^

---

### Post by st33med on 2007-08-28
Great!After you login, Do:
```
xstart
```

---

### Post by dhobbs on 2007-08-28
I don't mean to pry but why on earth would you want to tweak an operating system that won't persist when the computer turns off?  That's not the intention of the Live CD.

---

### Post by dhobbs on 2007-08-28
```
startx
```

---

### Post by 99bluefoxx on 2007-08-28
i add the mp3 decoder and amsn, as well as bmp to listen to media streams[my mp3 broke, the the tape i backuped to broke, and then the memstick i had them on got snapped in half]
i also customize the desktop backgruond and change the theme
the defualt theme is a bit hard to see for me and im on a cheap net connection so it takes a while to download depending on the time of day and how many ppl in the building are online

---

### Post by st33med on 2007-08-28
Why not get another Hard Drive?

---

### Post by 99bluefoxx on 2007-08-28
my power supply is too weak[power hungry nvidia and celeron d 3.5 ghz processor] at 200 watts and ive got no funds to buy a new harddrive right now, and i also got to replace a breaking keyboard{i dont have a mouse right now either]
so the psu is about 50$, hdd 120$ and they keyboard im gonna buy tomorrow is about 70$
i only got 40$ in my pocket and i get the 30 that a neighbor owes me tomorrow. as for getting a job ive been trying, but itt'l be my first if i get hired anywhear, and all the places want a resume

---

### Post by dhobbs on 2007-08-28
That's fine as long as you understand that nothing you do in the Live CD environment will be saved, so any documents or games or whatever you decide to do, it will all disappear every time you restart the computer.

And your system will always get sluggish and unresponsive, a side effect of having everything loaded in RAM.

Good luck with the job hunt.

---

### Post by reset3x on 2007-08-29
```
killall gnome-panel
```

or ctrl-alt-backspace

---

