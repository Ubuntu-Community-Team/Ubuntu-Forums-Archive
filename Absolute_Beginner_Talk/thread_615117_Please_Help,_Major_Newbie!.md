---
title: "Please Help, Major Newbie!"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by mzdawg on 2007-11-16
I installed Ubuntu on my computer, and when I rebooted it, the terminal appeared, and being a TOTAL newbie to terminal stuff, I don`t know how to get out. I logged in, but now what? I just want to get to my desktop and actually USE my computer. I don`t care about the terminal. Please help. :(:confused:

---

### Post by taurus on 2007-11-16
Did you install from the desktop CD (LiveCD) or the server CD?  

What happens if you type this command from a prompt?

```
startx
```

---

### Post by dstew on 2007-11-16
Did you have an Ubuntu desktop working before? If you are in a terminal window, type **exit**. if you booted into a terminal, you can try **startx** to see if you can get the xserver to give you a graphical interface. If you don't get anything with startx, post the response to the forum.

---

### Post by Inxsible on 2007-11-16
Did you download and install the server version by any chance? Server versions dont have GUI.
Try this:

 ```
startx
```

---

### Post by mzdawg on 2007-11-16
I used the "Alternate CD"

---

### Post by init1 on 2007-11-16
> **mzdawg said:**
> I used the "Alternate CD"
If you installed the desktop, type
```

startx

```
to start it.

---

### Post by mzdawg on 2007-11-16
It said I already have a display being used by the X server or something like that.

---

### Post by mzdawg on 2007-11-16
I also got the Display error that siad, " The display has been shut off 6 times, etc.

---

### Post by taurus on 2007-11-16
Sounds like there is something wrong with the graphic card?  What is it anyway?  Try reconfigure X again with

```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
startx
```
If you're not sure about a question, just use the default.  And try using **vesa** driver for now until you get X up and running.  Then, you can install a driver for your graphic card.

---

### Post by mzdawg on 2007-11-16
Oh, and when my screen flickers, I catch a glimpse of the orange desktop, so maybe its my monitor causing all the trouble. It is a sharp 26"

---

### Post by Sims2789 on 2007-11-16
> **mzdawg said:**
> I installed Ubuntu on my computer, and when I rebooted it, the terminal appeared, and being a TOTAL newbie to terminal stuff, I don`t know how to get out. I logged in, but now what? I just want to get to my desktop and actually USE my computer. I don`t care about the terminal. Please help. :(:confused:

> **mzdawg said:**
> Oh, and when my screen flickers, I catch a glimpse of the orange desktop, so maybe its my monitor causing all the trouble. It is a sharp 26"

Modern desktop operating systems intended for use by everyday people don't require terminal use. Since Ubuntu's one of these* it shouldn't do this. Chances are, you have an old (but not too old) graphics card. NVIDIA and ATI write drivers for newer cards, and generic drivers tend to work with older cards, but there's a middle range where they don't work out-of-the-box.

So, if your computer has built-in graphics, turn it off and plug your monitor into your built-in graphics card. There should be a plug that's identical to the one your monitor's already plugged into; this is the one you want.

When you boot up Ubuntu, there should be something in the upper right-hand corner called the Restricted Drivers Manager, and it should ask you if you want to install the restricted (proprietary) driver for your graphics card. If this doesn't appear, go to System -> Administration -> Restricted Drivers Manager, and install your graphics card's driver from there. You may need to know what type of graphics card you have before you do this.

*Unfortunately, many Linux nerds still distribute programs without automatic installers, or deceive users into thinking they must use the command line for editing configuration files. Most of them don't purposefully make it difficult (to them it's easy), and hard-to-use distributions are perfect for some people (just like easy-to-use ones like Ubuntu are perfect for us people), but it's still a pain in the butt to most Linux users.

---

### Post by mzdawg on 2007-11-16
when the display setup asked to xhoose the bit color, it wanted me to type something, what do i type. It says, overwriting possibly customized configuration

---

