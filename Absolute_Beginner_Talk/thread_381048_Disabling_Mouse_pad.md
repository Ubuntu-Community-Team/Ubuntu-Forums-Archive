---
title: "Disabling Mouse pad?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Stevo0687 on 2007-03-10
Hey all,
    I have a Dell laptop.  I also have a wireless USB mouse.  On XP when I plugged the USB device in, I had it set up so it would disable the "touch pad" on the front of the computer so I could only use the mouse.  Can I do that for Ubuntu and how? I am constantly bumping it with my thumb when I type and it moves the curser around.  Thanks in advance.

---

### Post by Delvien on 2007-03-10
> **Stevo0687 said:**
> Hey all,
    I have a Dell laptop.  I also have a wireless USB mouse.  On XP when I plugged the USB device in, I had it set up so it would disable the "touch pad" on the front of the computer so I could only use the mouse.  Can I do that for Ubuntu and how? I am constantly bumping it with my thumb when I type and it moves the curser around.  Thanks in advance.

go into your Xorg by typeing the folloing 

```
 sudo gedit /etc/X11/xorg.conf 
```

then put "#" in front of every line of the section that states its your touch pad. save it and reboot, let us know.

---

### Post by mahy on 2007-03-10
> **Delvien said:**
> go into your Xorg by typeing the folloing 

```
 sudo gedit /etc/X11/xorg.conf 
```

then put "#" in front of every line of the section that states its your touch pad. save it and reboot, let us know.

Not a good idea!! This disables the touchpad permanently. What you want is to enable SHMConfig. Like this:

```
Option "SHMConfig" "on"
```

added into your /etc/X11/xorg.conf file, into the section named 'Synaptics Touchpad'.

---

### Post by Stevo0687 on 2007-03-10
Alright, thanks for the advice.  Mahy, you're right, I don't want to disable the touchpad permenently, just when I have the mouse plugged in. Is that possible?

Do I type what you told me into the terminal?  Or is option on my desktop or toolbar somewhere?  I tried it in the terminal and didn't get anything.  I am VERY new to Ubuntu.  I just got it installed today and have only used it one other time for a project in college.  If you can give me more details as to what I do I'd appricate it.  Thanks.

---

### Post by mahy on 2007-03-10
> **Stevo0687 said:**
> Alright, thanks for the advice.  Mahy, you're right, I don't want to disable the touchpad permenently, just when I have the mouse plugged in. Is that possible?

Do I type what you told me into the terminal?  Or is option on my desktop or toolbar somewhere?  I tried it in the terminal and didn't get anything.  I am VERY new to Ubuntu.  I just got it installed today and have only used it one other time for a project in college.  If you can give me more details as to what I do I'd appricate it.  Thanks.

Open the terminal and run:

```
sudo gedit /etc/X11/xorg.conf
```

Which will open the file named xorg.conf. Then add the line i showed you into the touchpad section. Xorg.conf is an extremely important file and you need to get familiar with it. Good luck.

---

### Post by Delvien on 2007-03-10
> **mahy said:**
> Not a good idea!! This disables the touchpad permanently. What you want is to enable SHMConfig. Like this:

```
Option "SHMConfig" "on"
```

added into your /etc/X11/xorg.conf file, into the section named 'Synaptics Touchpad'.

Not nec. permanently, all u have to do is take out the # and reboot, and bam, works again.


Guess i didnt read what he wanted, sorry, im at work, and doing this in between projects.

---

### Post by Stevo0687 on 2007-03-10
Alright, I was able to open xorg.conf  But I don't know where to go from there.  Where do I find Synaptics Touchpad section or whatever?  I can't seem to find out what to do.  In the box that opend I typed in the code you said and go nothing.

---

