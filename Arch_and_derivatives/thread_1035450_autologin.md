---
title: "autologin"
date: 2009-01-09
forum: Arch and derivatives
---

### Post by kerry_s on 2009-01-09
hey all, i would like to know what auto login method your using to log in **without** a dm/login manager?

please only put if it's different from everyone else's.

i'll start, i'm using:

```
c1:2345:respawn:/bin/login -f user tty1 < /dev/tty1 > /dev/tty1 2>&1
```

---

### Post by Dr Small on 2009-01-09
Autologin is anti-security, so I don't practice it :p

---

### Post by Amranu on 2009-01-09
> **Dr Small said:**
> Autologin is anti-security, so I don't practice it :psame

---

### Post by kerry_s on 2009-01-09
it's on a computer that never leaves the house, so security is not a issue. i need it to just turn on and go straight to the desktop so grandma can do her mail, then she just turns it off. thanks anyways, but not what i asked.

---

### Post by Dr Small on 2009-01-09
> **kerry_s said:**
> it's on a computer that never leaves the house, so security is not a issue. i need it to just turn on and go straight to the desktop so grandma can do her mail, then she just turns it off. thanks anyways, but not what i asked.
I know. No need to be so serious about it, though ;)
Actually, I've never needed autologin, so I've never attempted it.

---

### Post by K.Mandla on 2009-01-09
I usually edit inittab like the wiki suggests.

[http://wiki.archlinux.org/index.php/Start_X_at_boot](http://wiki.archlinux.org/index.php/Start_X_at_boot)

I think there are better ways, but I prefer that one because it also works for me in Crux, and I am, at my core, terribly lazy. :mrgreen:

---

### Post by kerry_s on 2009-01-09
> **K.Mandla said:**
> I usually edit inittab like the wiki suggests.

[http://wiki.archlinux.org/index.php/Start_X_at_boot](http://wiki.archlinux.org/index.php/Start_X_at_boot)

I think there are better ways, but I prefer that one because it also works for me in Crux, and I am, at my core, terribly lazy. :mrgreen:

got to try that 1, i used the top part:

```
if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/vc/1 ]]; then
  startx
  logout
fi

```

i had just "exec startx". earlier i tried what i use in debian and it did not work:

```
if [ $(tty) == "/dev/tty1" ]; then
 exec startx > /dev/null 2>&1
 logout
fi

```

i didn't bother to try to figure out why it didn't work yet. i'll play with it later.

thanks

---

### Post by qpieus on 2009-01-10
kerry_s - what happens when you exit your desktop environment? Do you get kicked out to console but still logged in to your account, or do you get completely logged out and you end up in console at a login prompt?

The reason I ask is that I (for a short time) used one of the autologin methods from the arch wiki (I don't remember the exact details, but it did involve editing inittab). What I hated about it was that when I exited KDE, I got completely logged out. So when I wanted to shut down the pc, I had to log back in to the console so I could poweroff. PITA.

I currently use method 3 from [http://wiki.archlinux.org/index.php/Start_X_at_boot](http://wiki.archlinux.org/index.php/Start_X_at_boot)
It doesn't autologin, but it does start KDE automatically after I log in at the console, no login manager needed. And when I exit KDE I end up back in the console still logged in.

---

### Post by kerry_s on 2009-01-10
just remove the "logout" part and it won't log you out when you quit X.

example:

```
if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/vc/1 ]]; then
  startx
fi

```

it will still work as usual, but when you log out of X you don't have to log back in.

the way i have mine setup when you logout it brings you right back to the gui, i use tty2 if i need console.

---

### Post by smartboyathome on 2009-01-10
I just use [this meathod]("http://wiki.archlinux.org/index.php/Start_X_at_boot#Starting_X_as_preferred_user_without_logging_in") to autologin on my laptop (I'm not worried about security, it is not leaving the house much). Really nice imo, doesn't take a VT.

---

### Post by handy on 2009-01-10
I don't use autologin either.

I edited inittab so after entering user name & password Xfce starts, when I log out, I land back at the console prompt, I have to hit <alt> <F2> from where I can shut down or reboot.

It is automated enough for my uses.

---

### Post by wolfvorkian1 on 2009-01-10
I edited  /etc/inittab. Start the WM in .xinitrc and use sudo with no passwd. I think that is it. 

```
c1:2345:respawn:/sbin/mingetty --autologin mike vc/1 linux
#c1:2345:respawn:/sbin/agetty -8 38400 vc/1 linux
```

---

### Post by kerry_s on 2009-01-11
> **wolfvorkian1 said:**
> I edited  /etc/inittab. Start the WM in .xinitrc and use sudo with no passwd. I think that is it. 

```
c1:2345:respawn:/sbin/mingetty --autologin mike vc/1 linux
#c1:2345:respawn:/sbin/agetty -8 38400 vc/1 linux
```

for mingetty you have to get it out side the repo right?

---

### Post by wolfvorkian1 on 2009-01-11
> **kerry_s said:**
> for mingetty you have to get it out side the repo right?
  
Correct. I'm glad you brought this up because I played around later trying to get it back to where I could just login normally and then use startx and I haven't been able to figure out exactly how it is done. 

I turn the computer on and go straight to a desktop state without doing anything else normally but I've thought about maybe being able to get to a prompt if a problem should arise would be beneficial.  I tried to do this last night and was able to get to a  login but after l login, I went straight to a desktop without stopping at prompt. 

I think what it is, Is I also created and modified .bash_profile per the Arch Wiki to something like this.

```
. $HOME/.bashrc
if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/vc/1 ]]; then
  startx
  logout
fi
```

Once I get woke up good, I'm going to experiment some more. If it turns out this isn't it, I'll post later because now you've got me wondering exactly how I accomplished this in the first place and i want to make sure I know how to reverse it if needed.

---

### Post by wolfvorkian1 on 2009-01-11
> **kerry_s said:**
> for mingetty you have to get it out side the repo right?

mingetty per the arch wiki ....[http://tinyurl.com/2v7huh](http://tinyurl.com/2v7huh)

---

### Post by kerry_s on 2009-01-11
> **wolfvorkian1 said:**
> Correct. I'm glad you brought this up because I played around later trying to get it back to where I could just login normally and then use startx and I haven't been able to figure out exactly how it is done. 

I turn the computer on and go straight to a desktop state without doing anything else normally but I've thought about maybe being able to get to a prompt if a problem should arise would be beneficial.  I tried to do this last night and was able to get to a  login but after l login, I went straight to a desktop without stopping at prompt. 

I think what it is, Is I also created and modified .bash_profile per the Arch Wiki to something like this.

```
. $HOME/.bashrc
if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/vc/1 ]]; then
  startx
  logout
fi
```

Once I get woke up good, I'm going to experiment some more. If it turns out this isn't it, I'll post later because now you've got me wondering exactly how I accomplished this in the first place and i want to make sure I know how to reverse it if needed.

:lolflag:

> mingetty per the arch wiki ....[http://tinyurl.com/2v7huh](http://tinyurl.com/2v7huh)  

thanks, but like debian i don't want to go outside the repo.

you could try mine if you want, i like to make it as simple as possible, with as little calls and checks to make it as fast as possible:

```
if [ $(tty) == "/dev/vc/1" ]; then
 exec xinit > /dev/null 2>&1
 logout
fi

```

here's all i use:

---

### Post by wolfvorkian1 on 2009-01-11
You are right. That eliminates mingetty. I'm sure glad you brought this up though because I really did need to refresh my mind on this in case X ever crashes, etc. I do everything by trial and error and am often too lazy to take any notes or too confused to remember exactly how I did accomplish something after I finally do get it working. 

It is all mandla's fault. Even thinking about running half marathons all uphill tires me out to where note taking even is a chore.

---

### Post by markp1989 on 2009-01-11
i have 
```
su -- mark -c 'source /etc/profile;xinit' &
```

in my rc.local

of course you would have to replace mark with your user name

---

### Post by kerry_s on 2009-01-11
> **markp1989 said:**
> i have 
```
su -- mark -c 'source /etc/profile;xinit' &
```

in my rc.local

of course you would have to replace mark with your user name


that 1's new to me, never even thought about using rc.local, much appreciated. ):P
you my friend think outside the box. :lolflag:

---

### Post by handy on 2009-01-11
> **wolfvorkian1 said:**
> You are right. That eliminates mingetty. I'm sure glad you brought this up though because I really did need to refresh my mind on this in case X ever crashes, etc. I do everything by trial and error and am often too lazy to take any notes or too confused to remember exactly how I did accomplish something after I finally do get it working. 

My memory is failing as time goes by, so what I've found is a good solution for complex tasks that we manage to find our way through, is to write a how-to.  It provides others with helpful information & also allows us to retrace our steps in the future, without having to reinvent the wheel.  

I'm sure that the day is coming where my mind will find it too hard to go where I have easily traveled in the past.  Actually it has already arrived, but I will stave off this mental problem for as long as I can.

That's my theory on the subject anyway. :-)

---

### Post by kerry_s on 2009-01-12
:lolflag: i was messing around and locked myself out.
i forgot to change the single login so it don't ask for a root password, i have already locked the root. #-o

---

### Post by handy on 2009-01-12
The auto-lockout.

Bummer.

Can you go to a LiveCD & edit our way out of this problem?

I know that I can do that in IPCop at least.

---

### Post by kerry_s on 2009-01-12
> **handy said:**
> The auto-lockout.

Bummer.

Can you go to a LiveCD & edit our way out of this problem?

I know that I can do that in IPCop at least.

no need, its easy to get around, only takes a reboot(ctrl+alt+delete), i just couldn't believe i did it. :lolflag:

if it ever happens to you just use the "e" to edit the line add "init=/bin/sh" you'll get a root shell, no password.

i made sure i changed it in inittab and added "single" to that failsafe line so i don't need to edit it, so it won't happen again. rooky mistakes happen from time to time. i was trying to get my suspend to work, all i get is the infamous BOD(blink of death) common problem with t20's.

---

### Post by kerry_s on 2009-01-14
i tried that way most was using:

```
x:5:wait:/bin/su user -l -c "/bin/bash --login -c startx >/dev/null 2>&1"
```

but man that way is slow, i went back to my way, the debian way, but modified for arch:

```
c1:2345:respawn:/bin/login -f user vc/1 </dev/vc/1 >/dev/vc/1 2>&1
```

auto logs me in.
this starts my X from .bash_profile:

```
if [ $(tty) = /dev/vc/1 ]; then
  xinit >/dev/null 2>&1
  logout
fi
```

it's much faster than all the others i tried and it has the add benefit if you logout it will bring you right back to X.

---

### Post by markp1989 on 2009-01-14
> **kerry_s said:**
> i tried that way most was using:

```
x:5:wait:/bin/su user -l -c "/bin/bash --login -c startx >/dev/null 2>&1"
```

but man that way is slow, i went back to my way, the debian way, but modified for arch:

```
c1:2345:respawn:/bin/login -f user vc/1 </dev/vc/1 >/dev/vc/1 2>&1
```

auto logs me in.
this starts my X from .bash_profile:

```
if [ $(tty) = /dev/vc/1 ]; then
  xinit >/dev/null 2>&1
  logout
fi
```

it's much faster than all the others i tried and it has the add benefit if you logout it will bring you right back to X.

i have just changed to that method, its alot faster, thanks:D:

---

### Post by kerry_s on 2009-01-14
> **markp1989 said:**
> i have just changed to that method, its alot faster, thanks:D:

your welcome, if i find a faster way i'll let you guys know. i'm still fairly new to the way arch works, but i been learning. ;)

---

### Post by smartboyathome on 2009-01-14
> **markp1989 said:**
> i have just changed to that method, its alot faster, thanks:D:

I changed to that meathod before you two posted, but after I posted my first post. I did it mainly because I also wanted to have my system log displayed in a terminal. Works great for both. ;)

---

### Post by kerry_s on 2009-01-14
> **smartboyathome said:**
> I changed to that meathod before you two posted, but after I posted my first post. I did it mainly because I also wanted to have my system log displayed in a terminal. Works great for both. ;)

you mean the garbage on the tty if you don't use ">/dev/null 2>&1" ?
i try and keep logs to a minimum, wasted space, i disabled the system log to.

---

### Post by smartboyathome on 2009-01-15
> **kerry_s said:**
> you mean the garbage on the tty if you don't use ">/dev/null 2>&1" ?
i try and keep logs to a minimum, wasted space, i disabled the system log to.

No, I mean it displays the output of dmesg so I don't have to open up a new terminal and look at it all the time. Basically, what I run is this:
```
if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/vc/5 ]]; then
  dmesg
  sleep 30
  logout
fi
```

There is probably a more efficient way of doing this, but I don't know what it is. :P

---

### Post by kerry_s on 2009-01-15
> **smartboyathome said:**
> No, I mean it displays the output of dmesg so I don't have to open up a new terminal and look at it all the time. Basically, what I run is this:
```
if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/vc/5 ]]; then
  dmesg
  sleep 30
  logout
fi
```

There is probably a more efficient way of doing this, but I don't know what it is. :P

yeah, i just go to /var/log/ and look at it if i need to, which is rare, because it's always the same. :lolflag:

in terminal it's-> sudo cat /var/log/dmesg

---

### Post by smartboyathome on 2009-01-15
> **kerry_s said:**
> yeah, i just go to /var/log/ and look at it if i need to, which is rare, because it's always the same. :lolflag:

in terminal it's-> sudo cat /var/log/dmesg

That is basically the same thing that dmesg does. I will just stick with what I have now. ;)

---

