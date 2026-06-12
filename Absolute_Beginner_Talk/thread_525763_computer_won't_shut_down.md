---
title: "computer won't shut down"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by tommason on 2007-08-14
pretty much does what it says on the tin....I'm having issues with nvidia drivers and have had 'failed to start xserver' reconfigured it, to use vesa drivers (nv and nvidia don't seem to work with the old xserver thing) and now i have tried to turn the thing off to no avail... :( any advice?
Cheers!
Tom

---

### Post by Blutack on 2007-08-14
Holding the power button down for at least 10 seconds normally does the trick.

---

### Post by st33med on 2007-08-14
Try doing Ctrl-Alt-Backspace. It kills all processes with a harsh kill signal.

---

### Post by tommason on 2007-08-14
> **Blutack said:**
> Holding the power button down for at least 10 seconds normally does the trick.

spot on, that worked (i was stuck on the ubuntu logo with a completed task bar and so couldn't try the ctrl alt backspace manouvre) is there any reason why this is happening - and is there a fix?

---

### Post by p_quarles on 2007-08-14
Neither of those suggestions will do much to solve the problem. The first forces an unsafe shutdown, and the second will simply end the current session and bring up the login screen. 

Why don't you try shutting down from the terminal and seeing what happens that way:
```
sudo shutdown -P now
```
If it refuses to shutdown, it should provide you with some kind of error message that will point to the root of the problem.

---

### Post by st33med on 2007-08-14
> **p_quarles said:**
> Neither of those suggestions will do much to solve the problem. The first forces an unsafe shutdown, and the second will simply end the current session and bring up the login screen. 

Why don't you try shutting down from the terminal and seeing what happens that way:
```
sudo shutdown -P now
```
If it refuses to shutdown, it should provide you with some kind of error message that will point to the root of the problem.

Actually, if you tell Ubuntu to shutdown first, but it doesn't do that, Ctrl+Alt+Backspace kills all processes and shuts down. 

However, I do agree, this does nothing to solve the problem.

---

### Post by tommason on 2007-08-14
ok i'll give that a go...(here comes the noob) how do i get to the terminal? :D

---

### Post by p_quarles on 2007-08-14
Ctrl-f1

---

### Post by p_quarles on 2007-08-14
> **st33med said:**
> Actually, if you tell Ubuntu to shutdown first, but it doesn't do that, Ctrl+Alt+Backspace kills all processes and shuts down. 

However, I do agree, this does nothing to solve the problem.
Thanks, I didn't realize that.

---

### Post by tommason on 2007-08-14
ok tried:
 'sudo shutdown -p now' this did nothing - unknown command '-p'
tried:
 'sudo init 0' which shut down all processes and left me at the same screen - ubuntu logo task bar black underneath without actually turning the computer off.....

---

### Post by Blutack on 2007-08-14
sudo poweroff
normally works for me

---

### Post by brownknight on 2007-08-14
> **tommason said:**
> ok tried:
 'sudo shutdown -p now' this did nothing - unknown command '-p'


he said shutdown -P now  (with a capital P). I dont know it that makes a difference (noob here talking)

---

### Post by confused57 on 2007-08-14
You could try this:
```
sudo gedit /etc/modules
```

add a new line with the following statement:

apm power_off=1

---

### Post by p_quarles on 2007-08-14
> **brownknight said:**
> he said shutdown -P now  (with a capital P). I dont know it that makes a difference (noob here talking)
Yes, it does. Linux commands are all case sensitive, so whenever you try a command you see in the forums or from some other source, make sure you get the case of each character right.

---

### Post by tommason on 2007-08-14
cheers guys - 'sudo poweroff' works, but has the same affect, ie leaves me with a logo and a completed (black) task bar, will try the capital 'P' i'm sure it will work, but i assume this will leave me at the same screen? trying now....
if i try this:
add a new line with the following statement:

apm power_off=1
can i revert to what i had before using the same process but deleting the added line?

---

### Post by tommason on 2007-08-14
yeah, it does indeed work and leaves me in the same place...!
gonna crash now - thanks for all your help - i'll be here tomorrow trying the 'sudo gedit /etc/modules'.....! 
:)

---

### Post by p_quarles on 2007-08-14
> **tommason said:**
> yeah, it does indeed work and leaves me in the same place...!
gonna crash now - thanks for all your help - i'll be here tomorrow trying the 'sudo gedit /etc/modules'.....! 
:)
Cool. Hope you have some luck with that.

One note, though: never use "sudo" to run a graphical application. The correct way to run it is:
```
gksudo gedit /etc/modules
```
Most of the time, doing it the wrong way won't cause any problems. If it does, though, it can hose you.

---

### Post by VincentValentine on 2007-08-20
> Cool. Hope you have some luck with that.

One note, though: never use "sudo" to run a graphical application. The correct way to run it is:
Code:

gksudo gedit /etc/modules

Most of the time, doing it the wrong way won't cause any problems. If it does, though, it can hose you.

Hello... I am having the same issue with my Ubunto 7.04 machine... 

I tried the "gksudo gedit /ect/modules code and got this error:" (gksudo 5538) GTK-Warning **:cannot open display ... 

I was just wondering if anyone can tell me what the error means, or if anyone has any other solutions...

Thanks for your help!

---

### Post by yogo on 2007-08-20
I am not sure if this pertains to the issue, as I have this same problem on a desktop, but there are several pages on laptops hd continually spinning on shutdown, it is a problem to do with the kernel on feisty, I wonder if upgrading to the gutsy kernel will fix this?

Just a possible solution.

---

### Post by ubername on 2007-08-20
Hi

similar problems here, fixed by upgrading my Dell Bios to A12 (from A08 ). I did it through my XP install, don't know how to do it if you only have ubuntu.

(If you have an XP install, go to the Dell support site having set IE as your default browser and enter / find your service tag. Then select the 'Bios' update option.)

Good luck

---

