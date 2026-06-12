---
title: "Xubuntu can't find mouse?"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by pointyblue on 2007-08-01
I've just installed Xubuntu from the alternate install iso on a 150 mhz computer with 190 mb ram and a 10 gb hd.

Amazingly, Xubuntu seems to be loading as it should but it doesn't find my mouse!?!

It's a standard 2-button ball mouse with a scroll wheel. When I run DamnSmallLinux or PuppyLinux on the computer there's no problem with the mouse - it must be Xubuntu related.

Do any of you have an idea on how to make Xubuntu find the mouse?

---

### Post by FleetAdmiral74 on 2007-08-01
PS/2 or USB?

---

### Post by pointyblue on 2007-08-01
Ps/2

---

### Post by dannyboy79 on 2007-08-01
yeap, I had the same problem. I never solved it however and just used a usb mouse instead so I am sorry I can't be much help. I believe it has something to do with combination of the xorg.conf file as well as whether or not the hardware is even being seen. Did you check you dmesg output to see if it says anything about a pointing device?

---

### Post by asmoore82 on 2007-08-01
open your /etc/X11/xorg.conf file and search for 'psaux'

post that whole section or the entire file.

---

### Post by dannyboy79 on 2007-08-01
> **asmoore82 said:**
> open your /etc/X11/xorg.conf file and search for 'psaux'

post that whole section or the entire file.

faster way would be

cat /etc/X11/xorg.conf | grep psaux

then post the results that get spit out. No need to open the file and do a search.

---

### Post by asmoore82 on 2007-08-01
> **dannyboy79 said:**
> faster way would be

cat /etc/X11/xorg.conf | grep psaux

then post the results that get spit out. No need to open the file and do a search.

you have to do a search to post the Whole Section ...

I already know what grep will show
Option "Device" "/dev/psaux"
and nothing more... i.e. useless

P.S. 'grep psaux /etc/X11/xorg.conf' is **even faster** but still won't help. :P

---

### Post by pointyblue on 2007-08-01
Hmmm... How exactly do I open /etc/X11/xorg.conf ?

Remember I'm not able to use the mouse, so I can't access the terminal.

Do you know if and how it can be done if I start Xubuntu in text mode?

---

### Post by ugm6hr on 2007-08-01
> **pointyblue said:**
> Hmmm... How exactly do I open /etc/X11/xorg.conf ?

Remember I'm not able to use the mouse, so I can't access the terminal.


Press Alt+F2:
In the box that opens - type (followed by Enter):
> mousepad /etc/X11/xorg.conf

Remember, this is case sensitive.

If you need terminal:
Alt+F2: **xfce4-terminal**

And if you need to browse files:
Alt+F2:** thunar**
Then start typing the first few letters of the drive / file - it will select in alphabetical order.  Enter to open.  Alt+UpArrow to go to Parent directory. Ctrl+c to copy; Ctrl+v to paste (if you want to write it to a USB for viewing on your internet-connected computer).

For when you want to actually edit xorg:
Alt+F2: **gksudo mousepad /etc/X11/xorg.conf**

---

### Post by ugm6hr on 2007-08-01
Someone else with the exact same problem:
[http://ubuntuforums.org/showthread.php?t=514978](http://ubuntuforums.org/showthread.php?t=514978)

---

### Post by CautionaryX on 2007-08-01
I'm having the same problem on an old HP Pavilion 6343 - with the 7.04 live cd. I think I might try the 6.10 live cd later on tonight to see if that is the problem. 

Other than the mouse, xubuntu works great on it.

---

### Post by ugm6hr on 2007-08-01
It is bizarre that Xubuntu7.04 picks up Touchpads OK, but not PS2 mice?  I've not tried it on a desktop machine...

---

### Post by dannyboy79 on 2007-08-02
> **pointyblue said:**
> Hmmm... How exactly do I open /etc/X11/xorg.conf ?

Remember I'm not able to use the mouse, so I can't access the terminal.

Do you know if and how it can be done if I start Xubuntu in text mode?

if you're going to use text mode (command line only) then use nano as your text editor. I wouldn't suggest using gedit for this either only because you'll have to know what hte hotkeys are for saving it, closing it etc etc. Nano has all the commands written along the bottom of it so it's easier to use without a mouse.

I also find it hard to believe that you don't know anyone with a usb mouse?

---

### Post by dannyboy79 on 2007-08-02
> **CautionaryX said:**
> I'm having the same problem on an old HP Pavilion 6343 - with the 7.04 live cd. I think I might try the 6.10 live cd later on tonight to see if that is the problem. 

Other than the mouse, xubuntu works great on it.

i had the problem on dapper, edgy, and haven't tried feisty yet but obviously you guys have.

---

### Post by ugm6hr on 2007-08-07
Launchpad report: [https://bugs.launchpad.net/baltix/+source/linux-source-2.6.20/+bug/108221](https://bugs.launchpad.net/baltix/+source/linux-source-2.6.20/+bug/108221)

See this to resolve (hopefully): [http://ubuntuforums.org/showpost.php?p=3146190&postcount=4](http://ubuntuforums.org/showpost.php?p=3146190&postcount=4)

---

### Post by pointyblue on 2007-08-19
Solved!

I updated the kernel by

```
sudo apt-get install linux-image-generic
```

and everything works perfectly now.

Thanks for all the help!

---

