---
title: "Duel monitors"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-03-05
Ok, I have a Intel 965 Chip set in my laptop. 

I would like to use an external monitor as well as my laptop screen. 

The external monitor is an LCD 1280x1024 resolution. My laptop is 1280x800

When I plug in my external, nothing happens. I've looked under screen and graphics and nothing there either :\
How do I get it to work?

Also, can I have one monitor with one workspace on and another with the other work space on?

Thanks,
Tom

---

### Post by saj0577 on 2008-03-05
On the screen and graphics Preferneces you need to enable the second monitor.

If you need screenshots on how i will do so but if you look again you should see it is possible.

Saj

---

### Post by Tom--d on 2008-03-05
When I go on screen and graphics.. It shows my current screen (laptop) but when I click on  'Screen 2' There is nothing. I can't tick the secondary monitor.

---

### Post by madcow72 on 2008-03-05
What is your graphics card, and do you have the driver installed?

The reason I ask is, primarily, if it's NVidia, it's very easy.  You just use do
```
sudo nvidia-settings
```
and then use their GUI to configure your dual monitors, save it to xorg.conf, reboot X and you're done.

---

### Post by saj0577 on 2008-03-05
> **Tom--d said:**
> When I go on screen and graphics.. It shows my current screen (laptop) but when I click on  'Screen 2' There is nothing. I can't tick the secondary monitor.

Does it let you click default screen on the second screen?

Have you told ubuntu what make and model your screen is?

Saj

---

### Post by Tom--d on 2008-03-05
> What is your graphics card, and do you have the driver installed?

The reason I ask is, primarily, if it's NVidia, it's very easy. You just use do
```


sudo nvidia-settings

```
and then use their GUI to configure your dual monitors, save it to xorg.conf, reboot X and you're done.

I have an Intel 965 Chip set internal. 

> Does it let you click default screen on the second screen?

Have you told ubuntu what make and model your screen is?

Saj

No, the secondary screen is blocked on my default screen. 
I've looked for the make of the Monitor but its not there. The make is GNR. All I know its 17" and the model is... TS700

---

### Post by saj0577 on 2008-03-05
> **Tom--d said:**
> I have an Intel 965 Chip set internal. 



No, the secondary screen is blocked on my default screen. 
I've looked for the make of the Monitor but its not there. The make is GNR. All I know its 17" and the model is... TS700

Il see what i can find for you, as mine worked near enough straight away.

Saj

---

### Post by Tom--d on 2008-03-05
Thanks :)
Really appreciate it!

---

### Post by saj0577 on 2008-03-05
From first searching take a look at 
[http://wiki.linuxquestions.org/wiki/Using_multiple_monitors_with_XFree86]("http://wiki.linuxquestions.org/wiki/Using_multiple_monitors_with_XFree86")

Do you want the second monitor to display exactly the same or not?

Saj

---

### Post by Tom--d on 2008-03-05
I would like one to show one of my workspaces and the other monitor shows the other workspace (I have 2 all together)

---

### Post by saj0577 on 2008-03-05
Okay. Il have a look :)

Saj

---

### Post by saj0577 on 2008-03-05
[Link]("http://www.zulustips.com/2007/04/01/dual-monitors-howto.html")

If you want we could sort it out over msn step by step,and im sure we would get it sorted.

Saj

---

### Post by Tom--d on 2008-03-05
Yeah, sure :)

*Sending a mail*

---

