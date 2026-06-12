---
title: "I want to use Ubuntu"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by ButchSpeer on 2007-10-26
Hello all. I'm new to this forum & Ubuntu.I know my way around Windows pretty well but, don't know the first thing about Ubuntu. 

I tried to update my virus scanner & got the message that I couldn't because I'm not root. 

Can't install my HP printer. Tried to install w/ Wine. Got so far as to have my system checked then it disappeared.  Downloaded a HPLIP program like it says on the website. Can't install it.

Tried to use Free Download manager that I installed w/ Wine. Flashgot couldn't locate it.

There are some really good open GL programs out there ( Audacity, Amarok & 7 zip come to mind ) but some are pretty mediocre. I would like be able to use Windows type programs when I need them.  

Ubuntu is fast, slick looking & easy on the system but, it's all so new. Would really like to keep using it. Thumbing your nose at Bill Gates is kind of nice. Any help at all would be very appreciated.

Butch

---

### Post by Crafty Kisses on 2007-10-26
> **ButchSpeer said:**
> Hello all. I'm new to this forum & Ubuntu.I know my way around Windows pretty well but, don't know the first thing about Ubuntu. 

I tried to update my virus scanner & got the message that I couldn't because I'm not root. 

Can't install my HP printer. Tried to install w/ Wine. Got so far as to have my system checked then it disappeared.  Downloaded a HPLIP program like it says on the website. Can't install it.

Tried to use Free Download manager that I installed w/ Wine. Flashgot couldn't locate it.

There are some really good open GL programs out there ( Audacity, Amarok & 7 zip come to mind ) but some are pretty mediocre. I would like be able to use Windows type programs when I need them.  

Ubuntu is fast, slick looking & easy on the system but, it's all so new. Would really like to keep using it. Thumbing your nose at Bill Gates is kind of nice. Any help at all would be very appreciated.

Butch
To solve the root problem, before you enter the command type the following:
```
sudo -i
```

---

### Post by floke on 2007-10-26
1) You don't need a virus scanner = #1 problem solved
2) Try 7.10 for printing - it has an autosetupthingammydodahwatsit - apart from that - more details about how you tried to do it would help.

Oh yeah - and Welcome to Linux!

):P

---

### Post by LowSky on 2007-10-26
my hp printer works fine with the linux drivers

why do you need a download manager? Firefox has one by default?

What Windows apps do you need to use?

---

### Post by ButchSpeer on 2007-10-26
Codename,
Sorry, I don't know anything about code.

Floke,
It's just kind of hard to imagine not needing a virus scanner.
I just tried my printer. Works great.(that's a relief). I didn't realize I wouldn't need to install the drivers from the cd.

Lowsky,
I use a download manager to be able to schedule downloads. The download manager that comes with Firefox works great but it's pretty limited. No mirrors & no auto shut down. I use Guitar Pro & a few other odd programs.

Not complaining about Ubuntu. Grat set up. Just sure is different.

Thanks for the help.

Butch

---

### Post by ButchSpeer on 2007-10-26
Codename,
Sorry, I don't know anything about code.

Floke,
It's just kind of hard to imagine not needing a virus scanner.
I just tried my printer. Works great.(that's a relief). I didn't realize I wouldn't need to install the drivers from the cd.

Lowsky,
I use a download manager to be able to schedule downloads. The download manager that comes with Firefox works great but it's pretty limited. No mirrors & no auto shut down. I use Guitar Pro & a few other odd programs.

Not complaining about Ubuntu. Great set up. Just sure is different.

Thanks for the help.

Butch

---

### Post by floke on 2007-10-27
> **ButchSpeer said:**
> It's just kind of hard to imagine not needing a virus scanner.


it takes a while.

Actually every now and then I get paranoid and install clamav - it usually stays on my system for about 5 minutes!

Do some reading on Linux security to put your mind at ease.

And enjoy the freedom :)

---

### Post by markharding557 on 2007-10-27
ive found that gwet download manager does the trick
ther are also one or two that can be installed in firefox itsself from add ons

---

### Post by Smittysmit on 2007-10-27
I also am somewhat new to Linux.  These forums offer a WEALTH of info and are ours for the taking.  There are a LOT of differences from windoze and I'm working on doing the big plunge myself.  I have learned that you need to have patience and people in the forum will help.  BTW, Linux is designed so that it doesn't need a de-fragmenter?  

I'm a noob and like (love) what they have to offer.

---

### Post by Yes on 2007-10-27
To run a program as root, you would open a terminal (Applications -> Accesories -> Terminal), and run the command 'sudo <program>'.  So if you wanted to run update-manager as root, you would type

```
sudo update-manager
```

It will ask you for your root password, and when you type it, you won't see anthing being typed.  Don't worry, that's normal.  You can use sudo for any other terminal command as well to run the command as root.

---

### Post by sloggerkhan on 2007-10-27
> **ButchSpeer said:**
> 

I tried to update my virus scanner & got the message that I couldn't because I'm not root. 



You have to have admin rights to control sensitive things like virus scanning. In linux, the top level admin account on a system that has control over everything is always called root. To admin on an ubuntu system, you use a user account with sudo (super user) privilages to do things as though you were root. So try "sudo [program name]" to run it with admin privilages.

I also hope you didn't install a virus scanner using wine.

> 

Can't install my HP printer. Tried to install w/ Wine. Got so far as to have my system checked then it disappeared.  Downloaded a HPLIP program like it says on the website. Can't install it.



You shouldn't use wine to install printers ( I wouldn't think it'd work at all). The printer SHOULD be detected when you plug it in. If not, try system > admin > printers. Otherwise, post what model it is and maybe someone can help.


> 
Tried to use Free Download manager that I installed w/ Wine. Flashgot couldn't locate it.


There are linux download managers available in the repositories, or as firefox plugins. Look in Application > add/remove and browse through the internet category. 

> 
There are some really good open GL programs out there ( Audacity, Amarok & 7 zip come to mind ) but some are pretty mediocre. I would like be able to use Windows type programs when I need them.  


I'm not sure what you mean by this. (do you mean open source rather than open GL?) Odds are that you haven't heard of many great open source programs coming from windows. Explore the software in the add/remove menu. There's some great stuff there.

If you need to do a particular task and don't know the program, ask here. People will be more than willing to help, and nearly every windows program has a linux equivalent that's free.

---

