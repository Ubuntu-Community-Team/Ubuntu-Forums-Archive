---
title: "3 computers, one moniter..."
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by ginko13 on 2007-08-10
I was asked a question about this idea, and had nowhere to post it, so here I am...

I was asked if it were possible to connect three computers to one monitor, and have each screen be displayed on a different virtual desktop.  Using beryl as an example, each of the three desktops would display their information on a different side of the cube at the same time.

is it possible?

---

### Post by bodhi.zazen on 2007-08-10
Yes, I do tis all the time with a hardware switch ...  

Belkin Omnicube 4 port for example

[http://www.linux-tested.com/results/belcube4.htm](http://www.linux-tested.com/results/belcube4.htm)

---

### Post by kavon89 on 2007-08-10
It most certianly is. You will need what is called a KVM switch. It means "Keyboard Video Mouse", you either press a keycombo like CTRL+ALT+F1 or hit the switch to change everything to another pc. You can even get large switches to control a whole bunch of PCs from one set of input devices.

---

### Post by Nuverde on 2007-08-10
Just to help you when searching online stores, sometimes these switches are called KVMs (for Keyboard Video Mouse).

---

### Post by eentonig on 2007-08-10
As already said. It is possible if you have a Hw device to interconnect them.

If you only want to share Keyboard and mouse across 3 PC's with each his own screen, you could use a software solution called 'synergy'

---

### Post by fastpakr on 2007-08-10
KVM is certainly the easiest solution.  I have to admit, though, that being able to Cube the system would be amazingly cool.

---

### Post by Ek0nomik on 2007-08-10
bodhi.zazen:  You have me intrigued by this now.  I have three computers (as you can see from my signature, exluding the laptop) and having them all hooked up to one monitor sounds adventerous.

Let's assume I have all three hooked into the KVM switch, on my box how would I go about switching from one monitor to the next?  They can't actually all have their own 'cube' using Compiz can they?  (I don't even use Compiz, but this would maybe lead me into installing it).

How do *you* go about switching from one computer visually to the next, and what are all the options available for switching from one to the next?

---

### Post by fastpakr on 2007-08-10
Typically you have a button on the switch box to move between them, as well as a hotkey on the keyboard (such as double tapping scroll lock, etc) that brings up a menu of the ports on the switch and you can move through them there.  Takes perhaps a second to go from one machine to another.  Very cool and convenient.

---

### Post by Calash on 2007-08-10
Could also do it with VNC, then drop one VNC window on each side of the cube.

Would be a bit slower but it would work...provided each system had network connectivity.

---

### Post by bodhi.zazen on 2007-08-10
> **Ek0nomik said:**
> bodhi.zazen:  You have me intrigued by this now.  I have three computers (as you can see from my signature, exluding the laptop) and having them all hooked up to one monitor sounds adventerous.

Let's assume I have all three hooked into the KVM switch, on my box how would I go about switching from one monitor to the next?  They can't actually all have their own 'cube' using Compiz can they?  (I don't even use Compiz, but this would maybe lead me into installing it).

How do *you* go about switching from one computer visually to the next, and what are all the options available for switching from one to the next?

They do not use the monitor/keyboard/mouse at the same time with this setup ...

But yes, they otherwise run independent, and each can run compiz if you like ...

On my setup I hit the "Scroll Lock" key twice to switch computers.

The 3 computers do not interact in any way, so using this you could not make a cube with one computer on each side of the cube (which is what I think you are wanting) :(

---

### Post by splintercellguy on 2007-08-10
Probably Calash's solution would be the closest you could get to having each machine's display on a side of the cube.

---

### Post by Ek0nomik on 2007-08-10
Yeah, I was just double checking bodhi.  :)  I figured something like that wasn't not developed yet, especially for Linux.

I know what VNC is, and I suppose that's a solution, but I usually stick to SSH instead of VNC these days.

Thanks for the input.

---

### Post by splintercellguy on 2007-08-10
*VNC over SSH :), last I checked, SSH doesn't show your desktop ;).

---

### Post by dutchman72 on 2007-08-10
> **splintercellguy said:**
> *VNC over SSH :), last I checked, SSH doesn't show your desktop ;).

GUI Desktop thru SSH is very much possible, just need -X in command and remote X ability running on the box your connecting to. Its usually a touch more work than most are willing to do to get it running right. 

When fully set up its like RDP on a Windows machine.

---

### Post by e1geo on 2007-08-24
Have you thought about using synergy (synergy package, [http://synergy2.sourceforge.net/](http://synergy2.sourceforge.net/))?

---

### Post by DaveAK on 2007-08-29
I'm going to set my computers up with VNC so I can have each one on a separate workspace.  I see no reason why this shouldn't work with the Beryl cube, (I don't actually use Beryl though).  I also don't see the need for SSH as these are all on my local and trusted network.  I use a KVM when I'm working on other computers besides mine so I can keep my work bench clear, but for my own computers VNC should do the trick, (especially since one computer is in another room).

---

