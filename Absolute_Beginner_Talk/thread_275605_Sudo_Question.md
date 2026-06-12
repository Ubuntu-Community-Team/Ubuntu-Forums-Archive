---
title: "Sudo Question"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2006-10-11
I have a quick question about the concept of sudo. Sudo basically lets programs do root-ish operations temporarily, right? When I type my password into the sudo / gksudo box, it allows any program to do those root-ish operations for the next 5 minutes (or whatever I configure), right?

Just curious, but how is it safe to let any application do anything while under sudo? Could a program just sit there, wait until you give your computer sudo power, and do evil things?  Why doesn't it apply only to the program you let it gain access to?

Just trying to learn more about it. Thanks!

---

### Post by Brunellus on 2006-10-11
Nope.  your computer doesn't get sudo power for everything.  Sudo grants 'root' privileges to that USER for ONLY that command.

---

### Post by tonyr1988 on 2006-10-11
Okay, sounds good. :) Earlier I had just noticed that I ran a program that I needed sudo, and then I ran another one (that needed sudo) but it didn't ask me for my password, so I assumed that it gave sudo power to all programs within the 5 min period. Maybe I had ran the 2nd program less than 5 minutes before that and forgot. :P

Thanks

---

### Post by TheMono on 2006-10-11
It caches your password, yes. So if you issue the sudo command within the time frame again, it won't prompt for your password. But if you issue another command without the sudo option, it will not run as root.

Hope that clears that up.

---

### Post by ayoli on 2006-10-11
the password is cached for 15 min , if you want sudo to forget it type:
```
sudo -K
```

---

### Post by tonyr1988 on 2006-10-12
Okay, so when I type my password, any program can run as sudo for the next 15 minutes? What prevents a program from sitting and waiting until I type my password?

Then again, I guess if it tries to run as sudo and fails, it gets killed...

Thanks again for all your help!

---

### Post by yman on 2006-10-20
so why can't a program (virus?) do the same? it runs in the background, whaiting for you to use sudo, and then issues itself with sudo and your password?

or a program that listens for when you install a .deb and then installs a malicious .deb without needing a password?

---

### Post by aysiu on 2006-10-20
I just did a test of this.

I launched *kdesu konqueror*. I was prompted for my password. Then, five seconds later, I launched *kdesu kcontrol*. I was prompted for my password again.

Then I opened up a terminal and typed ```
sudo aptitude update
``` I was prompted for my password. Then, five seconds later, I opened a new terminal (the old terminal is still open in another window) and typed ```
sudo aptitude update
``` I was **not** prompted for a password in this second terminal window.

So, if what I've found is consistent (I haven't done extensive testing yet), then it would seem to indicate that for graphical applications, you are *always* required to enter your *sudo* password. For the terminal, there's a timeout, regardless of what command or what terminal you're in.

---

### Post by yman on 2006-10-20
> **aysiu said:**
> I just did a test of this.

I launched *kdesu konqueror*. I was prompted for my password. Then, five seconds later, I launched *kdesu kcontrol*. I was prompted for my password again.

Then I opened up a terminal and typed ```
sudo aptitude update
``` I was prompted for my password. Then, five seconds later, I opened a new terminal (the old terminal is still open in another window) and typed ```
sudo aptitude update
``` I was **not** prompted for a password in this second terminal window.

So, if what I've found is consistent (I haven't done extensive testing yet), then it would seem to indicate that for graphical applications, you are *always* required to enter your *sudo* password. For the terminal, there's a timeout, regardless of what command or what terminal you're in.
I would say you can't tell from that test. you launched 2 different graphical applications, but 1 command line application 2 times.

---

### Post by aysiu on 2006-10-20
That one command-line application was launched in two separate terminal windows.

**Edit**: Okay, that's weird. I tried it again. ```
sudo aptitude update
``` in one terminal window. Then I did the same command ```
sudo aptitude update
``` in another terminal window.

This time I was asked for a password both times.

Weird.

Interestingly enough, when I launched *gksudo nautilus*, I was prompted for a password, but when I launched *gksudo synaptic* five seconds later, I was not prompted for a password.

I wonder if *kdesu* and *gksudo* behave differently for some strange reason.

---

### Post by carloslosgrande on 2006-10-20
A little off the topic, but I've seen that there are apps for allow access to and from ubuntu and windows in dual boot mode. Isn't it possible for a virus to also make its way across?
and what about 'sudo su'?
Just a bit paranoid about Windoze.

---

### Post by tonyr1988 on 2006-10-20
carloslosgrande - what exactly do you mean? Bad Windows programs can't hurt Ubuntu even if it does "make its way across". There was a fairly popular virus a while ago that was non-dependent on the OS, but it was written in assembler and caused much less damage in Linux than Windows. Not a big deal.

I'm really interested about the sudo thing now. I know that sometimes I'll be prompted for a password when running two sudo programs back-to-back and other times I won't be. I never really thought much of it, though.

The quest continues...:P

---

### Post by yman on 2006-10-20
try two different apps with sudo in less than 5 minutes. if they both demand passwords, security is fine. if only the first, we got a problem.

---

### Post by tonyr1988 on 2006-10-20
Graphical (gksudo / kdesu) or terminal (sudo)? Or does it matter?

---

### Post by yman on 2006-10-20
> **tonyr1988 said:**
> Graphical (gksudo / kdesu) or terminal (sudo)? Or does it matter?

haven't got a clue, but I would try it in the terminal.

---

### Post by ayoli on 2006-10-20
> **aysiu said:**
> That one command-line application was launched in two separate terminal windows.

**Edit**: Okay, that's weird. I tried it again. ```
sudo aptitude update
``` in one terminal window. Then I did the same command ```
sudo aptitude update
``` in another terminal window.

This time I was asked for a password both times.

Weird.
that's normal, you are not in the same environement (not the same shell instance)
> **aysiu said:**
> 
Interestingly enough, when I launched *gksudo nautilus*, I was prompted for a password, but when I launched *gksudo synaptic* five seconds later, I was not prompted for a password.

I wonder if *kdesu* and *gksudo* behave differently for some strange reason.
i dunno for kdesu, but gksu(do) acts as sudo and keeps your password for a while unless you make it forget it (ie: with sudo -K)

---

### Post by pro003 on 2008-04-06
I do not want to get mess with you guys since am a newbie, but just to explain what am experiencing with this particular command, mighty "sudo"!

When I open a terminal I usually first type:

# sudo -s

and then I give my password and then am logged as root (excuse me  for my english)

i.e. 

# root@ubuntu


So anything I do later it does not require password, even when I close terminal and open another one am usually not prompted  for password, but only when time interval is short.

Truly, when you type

# sudo aptitude update 

in two different terminal window it requires a password in both cases, so I just wanted to add my contribute to this topic, and that is why I usually when I work in terminal I always first log in as root by typing 

# sudo -s

then password..

cheers

---

