---
title: "setting up a touchpad on a laptop?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-08-06
I did a quick search in the repository for drivers for my touchpad (Synaptic Touchpad) and found these:

ksynaptics
qsynaptics
tpconfig
xfree86-driver-synaptics

And this one is already installed: xserver-xorg-input-synaptics

Anyone know which I need, or if the one I have already is appropriate? I can't find where it is.

Thanks.

---

### Post by Ziox on 2006-08-06
> **JohnJSal said:**
> I did a quick search in the repository for drivers for my touchpad (Synaptic Touchpad) and found these:

ksynaptics
qsynaptics
tpconfig
xfree86-driver-synaptics

And this one is already installed: xserver-xorg-input-synaptics

Anyone know which I need, or if the one I have already is appropriate? I can't find where it is.

Thanks.

try qsynaptics

sudo aptitude install qsynaptics

But before you do that, add this line ot your touchpad "inputdevice" section:

Option "SHMConfig" "on"

---

### Post by JohnJSal on 2006-08-06
Thanks. That's the one I was thinking of. What does that extra line do? And where can I find the "inputdevice" section?

---

### Post by Ziox on 2006-08-06
> **JohnJSal said:**
> Thanks. That's the one I was thinking of. What does that extra line do? And where can I find the "inputdevice" section?

that line allows the touchpad to be configured by a GUI application

and the inputdevice section is in your xorg.conf file...sorry, i'm assuming everyone knows where that is...(i should remember how ignorant I was...lol)...anyhow,

gksu gedit /etc/X11/xorg.conf

then locate the "inputsection" There are couple input sections, so look for the one with the "Identifier "Synaptics Touchpad"

If you need help, just post your xorg.conf file, and I'll see how I can be of an assistant

---

### Post by JohnJSal on 2006-08-07
Is it normal for this file to be empty? Mine was, and I also did a whereis and it came up with another file path, but that was also empty (so I'm not sure if it really even existed, or if I created it just then).

---

### Post by Ziox on 2006-08-07
> **JohnJSal said:**
> Is it normal for this file to be empty? Mine was, and I also did a whereis and it came up with another file path, but that was also empty (so I'm not sure if it really even existed, or if I created it just then).

It isn't possible to have that file missing and still have a working system...I'm sure there's just some missing typing...copy and paste:

gksu gedit /etc/X11/xorg.conf

that X11 is X-el-el, not X-one-one

---

### Post by JohnJSal on 2006-08-08
What's the difference between gksu and sudo? I thought maybe gksu was graphical, but I've tried sudo gedit and it still opens it normally.

---

### Post by JohnJSal on 2006-08-08
I tried this but I got error messages. It said "SHMConfig disabled?" and "can't access shared memory".

---

### Post by McTek on 2006-08-08
Where is qsynaptics installed. I used apt-get install and it did but now I can't find it to set up my icon.

---

### Post by McTek on 2006-08-08
I tried using the script and got the same blank page you did. Went to Place, Computer, etc, X11 (one one),xorg.conf. Opened a terminal and typed in "sudo gedit" and then dragged xorg.conf into the terminal window and the file opened. BTW I'm running Ubuntu 6.06

---

