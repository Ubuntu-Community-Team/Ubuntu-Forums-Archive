---
title: "Help with setting display resolution on Fujitsu P7010"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by pastashop on 2006-10-16
Hello there! 

I'm looking for some very basic, step-by-step help in setting the display resolution to 1280x768 on a Fujitsu P7010, running Ubuntu Dapper Drake. All the pages I've seen thus far require a rather complicated - I'm a complete beginner - sequence of steps. Any help would be much appreciated! 

-P

---

### Post by ReaderRat on 2006-10-16
> **pastashop said:**
> Hello there! 

I'm looking for some very basic, step-by-step help in setting the display resolution to 1280x768 on a Fujitsu P7010, running Ubuntu Dapper Drake. All the pages I've seen thus far require a rather complicated - I'm a complete beginner -** sequence of steps**. Any help would be much appreciated! 

-P

Try Here:....
Resolution (& Refresh Rate) HOWTO Change
         [http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

---

### Post by ebutton on 2006-10-16
Try'd "System/Preferences/Screen Resolution"?  

Ed

---

### Post by bodhi.zazen on 2006-10-16
> **ReaderRat said:**
> Try Here:....
Resolution (& Refresh Rate) HOWTO Change
         [http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

That is a nice guide.

I need to add this resolution stuff to the UDSF...

I tried to write one more newbie friendly. NOT AS COMPLETE but it gets the job done:

[[color=blue]bodhi's resolution solution[/color]](http://ubuntuforums.org/showthread.php?p=1566609#post1566609)

---

### Post by bodhi.zazen on 2006-10-16
> **ebutton said:**
> Try'd "System/Preferences/Screen Resolution"?  

Ed

LOL :lol: That is ever easier ! I will add that to my guide.

We always assue this has been tried prior to a post like this....

---

### Post by pastashop on 2006-10-16
Many thanks... 

I have tried the first logical thing - change the Resolution preference from the System dropdown. The choices there are limited, with the highest 1024x768 (I'm looking for 1280x768). 

After that, I tried to follow the step-by-step instructions you kindly provided. One of the simplest ones was along the lines of: 

  sudo aptitude install 915resolution 

Unfortunately, my computer couldn't find that package. 

Next, I tried inserting a new "Modeline" into the xorg file. I went to one of the links that allows me to get the modeline for my monitor resolution (I'm assuming that this will work): 

 # 1280x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 80.14 MHz
  Modeline "1280x768_60.00"  80.14  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync 

However, I seem to be having trouble even finding a way to edit the right ("xorg.*"?) file. Every time I try to do so, the system pops me into a semi-graphical (dos-looking, mouse disabled) interface, from which I can't easily exit. 

Would anyone be so kind as to give me some very very very basic step-by-step instructions?

Many thanks in advance.

-P

---

### Post by bodhi.zazen on 2006-10-16
First for 915resolution, [How to enable repositories](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then refresh in synaptic, search and install 915resolution.

to open synaptic, in a terminal:```
sudo synaptic
```

to edit xorg.congf, in a terminal type```
sudo gedit /etc/X11/xorg.conf
```

Edit & save.

---

### Post by pastashop on 2006-10-16
Success! 

Many many thanks for that! 

I basically followed the guide on adding repositories: 
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

The 915resolution package appeared, I installed it, then entered in the Terminal window: 

sudo 915resolution 50 1280 768

...then I restarted the computer (Ctrl+Alt+SpaceBar didn't work), and the current resolution is 1280x768. 

(One caveat: Previously, I did manage to edit the xorg file to contain the Modeline, but I've no idea if that made any difference.) 

Many thanks for your patience and help!

---

