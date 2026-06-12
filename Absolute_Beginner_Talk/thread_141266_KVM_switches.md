---
title: "KVM switches"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by Garbageman on 2006-03-07
Does anyone know if it's possible to get a switch to work with ubuntu? or of a particular switch that would work with it?  I want to be able to use the same mouse/keyboard for my regular windows PC and my linux box.  Being the optimist that i am, i went out and bought one and can't get it to work.  Any suggestions?

---

### Post by aysiu on 2006-03-07
IOGear's KVM switches are Linux-compatible.
I'm using one right now!

[http://www.iogear.com/guide/KVM%20Comparison%20Guide%20final.pdf](http://www.iogear.com/guide/KVM%20Comparison%20Guide%20final.pdf)

---

### Post by Garbageman on 2006-03-07
that's what i have and it's not working
any idea why?

---

### Post by aysiu on 2006-03-07
No idea.

Can you describe *what* isn't working exactly? Is it the screen flickering? Does Ubuntu just not acknowledge your mouse or keyboard? What's the problem?

---

### Post by bobpur on 2006-03-07
Hello, 
  I've been stumbling around here trying to fix some of my problems with v5.10 and came across your problem. I'm a Linux newbie but; I do know a little about KVM switches. 
  First of all, I could never get one to work. 
                 1). Picture quality would suffer on the moniter
                 2). Mouse would function poorly.
                 3). If yours has audio support, Sound quality suffered as well.
  I figured that the problem was signal degradation due to the longer wiring. I have two KVM switches. One is a D-Link and the other is a Belkin. Both are USB connected all the way around.
  I tried different moniters, different mice(?), and different Keyboards and different drivers(Just in case). 
  I've read reviews off of the Internet that didn't have much good to say about KVM switches. Sorry, But that has been my experience with them.

---

### Post by aysiu on 2006-03-07
That hasn't been everyone's experience:
[http://www.ubuntuforums.org/showthread.php?t=132799](http://www.ubuntuforums.org/showthread.php?t=132799)

---

### Post by bobpur on 2006-03-08
OK, I read the thread. I just think they bring about more problems than they fix. My fix? Two complete computer setups, an "L" shaped desk and a swivel chair.

---

### Post by dtfinch on 2006-03-08
Mine has worked out pretty well. If there's ghosting or blurring, I can't see it. I just looked around until I found a cheap one with positive reviews about sharpness and no negative reviews about ghosting or other technical problems. I use it to switch between my two main desktops. It's a 2 port TrendNet, probably $23 on TigerDirect. Can't say much more without taking a closer look.

A Linux-incompatible KVM to me sounds about as unusual as a Linux-incompatible extension chord.

---

### Post by Garbageman on 2006-03-08
for me, it just won't recognize my linux computer. if i could get anything to work i'd be fine(i'm using a PS/2 one btw).  I just need keyboard and mouse.  i was going to buy a DVI one but...not for 150 dollars :)

---

### Post by Garbageman on 2006-03-08
okay...i guess i'm just slightly dumb.  Apparently i put my keyboard together wrong waaay back when i cleaned it, so using the scroll lock(which wasn't the scroll lock) to change between the two wouldn't work. heh...thanks everyone for the help...

---

### Post by aysiu on 2006-03-08
[QUOTE=Garbageman]okay...i guess i'm just slightly dumb.  Apparently i put my keyboard together wrong waaay back when i cleaned it, so using the scroll lock(which wasn't the scroll lock) to change between the two wouldn't work. heh...thanks everyone for the help...[/QUOTE] So it works now?

---

### Post by ubu_dynamite on 2006-04-18
i both a Sweex 2 ports ps/2 kvm switch with audio support today
first it woudnt work manual seth press 2 times CTRL and than ESC
after a few times i tried googling and prest enter than my screen
switcht suddenly only thing i had to do wash
Press 2 times CTRL than ENTER and ESC to chose the screen i wanted to use.

Works fine now.

---

### Post by jacksonz123z on 2006-05-07
I am sorry to admit that after trying 2 KVM switches and experiencing ALL the noted problems I bought a switch box (mechanical rotary switch).  This has solved the problem.  Perhaps the screen images are a little dulled, however the KVM experiments have ended!

---

### Post by NeoGreen on 2006-05-07
I had the same problem with a IOGear KVM switch (keyboard, or mouse sometimes didn't work), so I invested on a Switch box.  The switch box is for a four port connection, which I has a 4 port connection, the only problem I have on the switch box is the resolution on my monitor.  Sometimes it takes a while for it to adjust from when I switch from on computer to another.   Anyone recommend a good KVM switch that is relaible?

---

### Post by confused57 on 2006-05-07
My 2 port Trendnet works pretty well, someone else had mentioned it earlier in this thread, also.

One thing I forgot to mention was that when I install Ubuntu, I connect the monitor, keyboard, and mouse directly to the computer.  After installation, I hook up the KVM & haven't had any problems using the switch.

---

### Post by jason.b.c on 2006-05-08
> IOGear's KVM switches are Linux-compatible.
I'm using one right now!

I don't understand how something like that **wouldn't be** linux compatible, What is it there to be compatible with..????:confused:

---

### Post by aysiu on 2006-05-08
[QUOTE=jason.b.c]I don't understand how something like that **wouldn't be** linux compatible, What is it there to be compatible with..????:confused:[/QUOTE] I don't know either, but if you look at the original PDF I linked to, all the KVM switches are compatible with Mac, Windows, and Linux, but only certain models are compatible with Sun Solaris, so I would assume that compatibility is something that could be there... or not there.

---

### Post by aineko on 2006-05-10
Unfortunately, software does affect KVM behavior.  I have a Belkin OmniView 4-port PS2/USB KVM, which worked perfectly for a year (no ghosting, no loss of mouse/keyboard when switching.)

However, since the May xorg upgrade with the xserver-xorg-input-mouse package, the slightest mouse movement sends the mouse flying across the screen randomly with random button presses.  The mouse works fine until I perform a KVM switch, but is broken in the manner described above afterward.  Any ideas?

---

