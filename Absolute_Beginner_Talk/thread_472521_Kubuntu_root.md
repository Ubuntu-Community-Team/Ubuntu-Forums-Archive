---
title: "Kubuntu root"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by HybridTheory on 2007-06-13
How the crap do I use root in Kubuntu in terminal to install stuff like sudo in ubuntu what do you use in kubuntu? because sudo isn't working...thanks...

---

### Post by blue_shift on 2007-06-13
What are you typing at the command prompt (konsole)?

---

### Post by HybridTheory on 2007-06-13
> **blue_shift said:**
> What are you typing at the command prompt (konsole)?

trying to install beryl with a script in KATE 

travis@travis-laptop:~$ sudo ./beryl-install-script
&#8220;You must run this script as root.

---

### Post by blue_shift on 2007-06-13
That's weird - do you get the error with all sudo commands eg ```
travis@travis-laptop:~$ sudo -i
```
A script in kate? as in you wrote the script in kate? as long as you're not entering commands into kate :P

Have you set up several users on your laptop - maybe you're not on the sudoers list?

---

### Post by HybridTheory on 2007-06-13
> **blue_shift said:**
> That's weird - do you get the error with all sudo commands eg ```
travis@travis-laptop:~$ sudo -i
```
A script in kate? as in you wrote the script in kate? as long as you're not entering commands into kate :P

Have you set up several users on your laptop - maybe you're not on the sudoers list?

Lmao no I'm not doing it in kate that didnt work btw does sudo work in kubuntu? O_o
I'm just trying to add beryl to kubuntu that i just installed to dual boot with vista and i think I already freaking broke it..........

---

### Post by HybridTheory on 2007-06-13
I can't even open my list

travis@travis-laptop:~$ sudo /etc/apt/sources.list
sudo: /etc/apt/sources.list: command not found

---

### Post by Outrunner on 2007-06-13
> **HybridTheory said:**
> I can't even open my list

travis@travis-laptop:~$ sudo /etc/apt/sources.list
sudo: /etc/apt/sources.list: command not found

That's right, you don't do it like that...

```
kdesu kate /etc/apt/sources.list
```

---

### Post by blue_shift on 2007-06-13
when all is well and good sudo certainly works.

---

### Post by HybridTheory on 2007-06-13
> **Outrunner said:**
> That's right, you don't do it like that...

```
kdesu kate /etc/apt/sources.list
```

Thank you kind sir lmao thats one prob down about 399 more to go

---

### Post by HybridTheory on 2007-06-13
> **HybridTheory said:**
> Thank you kind sir lmao thats one prob down about 399 more to go

I lied that added about 20 more probs

travis@travis-laptop:~$ kdesu kate /etc/apt/sources.list
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0

The crap? :(

---

### Post by Outrunner on 2007-06-13
> **HybridTheory said:**
> I lied that added about 20 more probs

travis@travis-laptop:~$ kdesu kate /etc/apt/sources.list
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0

The crap? :(

It really doesn't mean anything. I get it too.

---

### Post by laura_glow on 2007-06-19
yeah, i'm getting those messages too, when typing 
kdesu konqueror

but then, sometimes konqueror starts, and sometimes not.

if i press alt-f2 and type there kdesu konqueror, it starts.

another question:


if i type su in konsole, and then i enter my password when prompted, why do i get a "authentication failed, sorry" message? sudo works well for command line tasks, like cp. but i can't become superuser in my konsole, which is very unnerving.

---

### Post by gigaferz on 2007-06-19
if you really want super cow powers, type sudo su press enter then itll prompt for your password

---

### Post by Happy_Man on 2007-06-19
Yes, sudo does put a whole new spin on superuser... you get used to it after a bit..... here are some basics: 

For Superuser rights: ```
sudo su
``` or ```
sudo -i
```

To open a *_graphical_* application using sudo: ```
kdesu <app name here>
```

To open a text file: ```
kdesu kate <path to file>
```

Those are the basics that everybody should memorize. Hope this helps!

---

### Post by Bachstelze on 2007-06-19
> **Happy_Man said:**
> Yes, sudo does put a whole new spin on superuser...

New ? Sudo has been the preferred way of running stuff as root since way before Ubuntu existed...

---

### Post by Happy_Man on 2007-06-19
Yeah, but in all the other distros, it was never quite as convoluted (or so it seemed to me at the time.)

---

