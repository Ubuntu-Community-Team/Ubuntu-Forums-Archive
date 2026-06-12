---
title: "Kubuntu doesn't display properly"
date: 2011-02-26
forum: Apple Hardware Users
---

### Post by wweeks on 2011-02-26
I have an Apple iBook  (ancient I know) and whenever I boot from the Live CD (Kubuntu 10.10) it boots up in 800x600 (as far as I can tell that's what it is). This would be a problem however it simplely leaves a huge black column on the right side and has a partially duplicated desktop below it. 
When I go to display settings it won't let me change to a higher resolution (1024x768 is what the iBook natively runs at).
This is an iBook G3.
I'd appreciate any help you could give me! Thanks!

---

### Post by Untitled_No4 on 2011-02-28
Please open Konsole, type
```
xrandr
```
and post the output here?

---

### Post by wweeks on 2011-02-28
> xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 x 0mm
800x600   60.0* 56.0
640x480 60.0
I also tested a live CD of Ubuntu 10.10 and it has the same result.

---

### Post by Untitled_No4 on 2011-03-01
As you can see from the xrandr output, your graphic card isn't recognised as having this mode (1024x768)

Fire up konsole again and run the following commands
1. 
```
cvt 1024 768
```
This will output the information regarding your screen with this resolution. The second line will begin with "Modeline". Copy the contents of the second line beginning with the resolution (so, anything after the word Modeline.
Just in case: ctrl+c/ctrl+v don't work console. Instead you have to use ctrl+insert/shift+insert or the mouse).

2. Create the new mode using the information from step one and the command "xrandr --newmode". For example:
```
xrandr --newmode "1680x1050_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
```

3. Add the new mode:
```
xrandr --addmode default 1024x768_60.00
```

4. Now try to use the new mode:
```
xrandr --output default --mode 1024x768_60.00
```

and hopefully your screen will change to the correct resolution. This is only temporary until you restart X. There are ways to make it permanent, but let's make sure it works first.

---

### Post by wweeks on 2011-03-01
Thanks for the quick reply!

I keep getting the error:
> xrandr: Failed to get size of gamma for output default

Note: I'm running out of a LiveCD and I ran this out of the console in Ubuntu LiveCD 10.10. Should be the same right?

---

### Post by wweeks on 2011-03-01
I tried again and I got this error message which seems to add some details:
> xrandr: Failed to get size of gamma for output default
X Error of failed request: BadName (named color or font does not exist)
Major opcode of failed request: 151 (RANDR)
Minor opcode of failed request: 16 (RRCreateMode)
Serial number of failed request 19
Current serial number of output stream:19

---

### Post by linuxopjemac on 2011-03-01
what exact model do you have? Link in everymac.com please.

---

### Post by wweeks on 2011-03-01
[http://www.everymac.com/systems/apple/ibook/stats/ibook_600.html](http://www.everymac.com/systems/apple/ibook/stats/ibook_600.html)
It's got 384 MB RAM though.

---

### Post by linuxopjemac on 2011-03-01
in a terminal:
```
wget http://mac.linux.be/files/xorg/ibook1.txt
sudo mv ibook1.txt /etc/X11/xorg.conf
```
reboot

---

### Post by wweeks on 2011-03-01
That will require that I first install it right? I'm still testing from a LiveCD to see if it works. 

I'm really not wanting to end up with dead machine but if thats what it takes thats what it takes.

Thanks so much for working with me on this. :)

---

### Post by linuxopjemac on 2011-03-01
no you don't need to install, you can also do it in a live environment.

After the mv command, do 
CTRL-Alt-F1 and go into a terminal
type:
```
sudo /etc/init.d/gdm restart
```

---

### Post by wweeks on 2011-03-02
Perfect! If I install and run this again will it be permanent?

---

### Post by linuxopjemac on 2011-03-02
I don't understand your question.

---

### Post by wweeks on 2011-03-02
I mean if I install Ubuntu from the LiveCD to my hard drive and go through that process again will the screen resolution stay the right size permanently?

---

### Post by linuxopjemac on 2011-03-02
If you intall it to your hard drive and you set the correct xorg.conf file on your disk, it will be permanent.

---

### Post by wweeks on 2011-03-02
And what you told me to do is how I would set the correct xorg.conf? Sorry, I'm slow but I really don't wanna end up with a dead machine.

---

### Post by linuxopjemac on 2011-03-03
read post #9

---

### Post by Untitled_No4 on 2011-03-03
wweeks:
Linuxopjemac's solution in #9 was to set an xorg.conf file that matches your machine. Once you install Kubuntu and repeat this procedure, this change will be permanent.

---

### Post by wweeks on 2011-03-03
Ok thanks for clarifying that for me  Untitled_No4 and all your ideas.

And thank you to linuxopjemac for finding me a solution. I ended up installing Ubuntu because it seemed less buggy. Thanks so much!

---

