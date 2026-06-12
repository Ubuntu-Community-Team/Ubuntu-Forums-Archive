---
title: "Touchpad..."
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by mike_pasara on 2008-01-26
I just bought a Dell XPS M1530. I love it. Booted up with vista, decided it sucked too much and i'm with gutsy now.

I had my own thread up on the M1530 but wasn't receiving the help I needed because there were different issues all in one thread. So i'm dedicating this to the touchpad only.

My issue is that when i was in vista i was able to change the speed of the movement from the touchpad. I can't do this in ubuntu, it's stuck on slow so when i touch the left side and move to the right it doesn't move the pointer fast enough, i have to go over over it 4 times before it reaches the other side of the screen.

I don't know what I am doing i'm new to Ubuntu so I don't even understand the terminal or really all that familiar with the gui.

If anyone can give me a hand a dumbed down version to help me i'd appreciate it :D


EDIT: Now my touchpad goes crazy whenever i close the lid... anybody have a fix for this... it's super annoying.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-01-26
I did a quick Google search and i think i came up with a solution
we need to edit this file /etc/X11/xorg.conf
and its a good idea to back this file up first
so open a turminal and type 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkup
```
that was to back it up
and now to edit
```
gksudo gedit /etc/X11/xorg.conf
```
enter you pass
**worring be very carefull not to change anything in this file that you dont know about**
so now scroll down to where it says
Section "InputDevice"
and then sumthing like
 Identifier &#8220;Synaptics Touchpad&#8221;

it should look similar to this

Section "InputDevice"
Identifier &#8220;Synaptics Touchpad&#8221;
Driver &#8220;synaptics&#8221;
Option &#8220;SendCoreEvents&#8221; &#8220;true&#8221;
Option &#8220;Device&#8221; &#8220;/dev/input/mice&#8221;
Option &#8220;Protocol&#8221; &#8220;auto-dev&#8221;
Option &#8220;ZAxisMapping&#8221; &#8220;4 5&#8243;
Option &#8220;Emulate3Buttons&#8221; &#8220;on&#8221;
Option &#8220;SHMConfig&#8221; &#8220;on&#8221;
Option &#8220;LeftEdge&#8221; &#8220;85&#8243;
Option &#8220;RightEdge&#8221; &#8220;1010&#8243;
Option &#8220;TopEdge&#8221; &#8220;85&#8243;
Option &#8220;BottomEdge&#8221; &#8220;730&#8243;
Option &#8220;FingerLow&#8221; &#8220;25&#8243;
Option &#8220;FingerHigh&#8221; &#8220;30&#8243;
Option &#8220;MaxTapTime&#8221; &#8220;180&#8243;
Option &#8220;MaxTapMove&#8221; &#8220;220&#8243;
Option &#8220;VertScrollDelta&#8221; &#8220;100&#8243;
Option &#8220;MinSpeed&#8221; &#8220;0.10&#8243;
Option &#8220;MaxSpeed&#8221; &#8220;0.60&#8243;
Option &#8220;AccelFactor&#8221; &#8220;0.2&#8243;
Option &#8220;HorizScrollDelta&#8221; &#8220;0&#8243;
EndSection


He didnt say what he changed exactly to speed it up, but i would gess change the MinSpeed and the Maxspeed and make them higher

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-01-26
hahaha or just go here
[http://ubuntuforums.org/showthread.php?t=230197](http://ubuntuforums.org/showthread.php?t=230197)

---

### Post by Ub1476 on 2008-01-26
I thought there were a Mouse section in System>Preferences?

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-01-26
or 
Another way to do it is to just add this to xorg.conf
Option "SHMConfig" "on" 

Then apt-get install gsynaptics/qsynaptics/ksynaptics.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-01-26
> **Ub1476 said:**
> I thought there were a Mouse section in System>Preferences?

ummm ya good point i woner if that works with his touch pad

---

### Post by Ptero-4 on 2008-01-26
You probably need to install gsynaptics (a touchpad config GUI). You can do that from synaptic (the package manager GUI)

---

### Post by mike_pasara on 2008-01-26
changed my xorg.conf to different settings... they work good now... i'm going to write an install guide for myself and this is going in there.

---

### Post by mike_pasara on 2008-01-29
I am now having issue with the touchpad going all squirrely when i close the lid... any help with this?

---

### Post by mike_pasara on 2008-02-03
bump.. anyone??

---

