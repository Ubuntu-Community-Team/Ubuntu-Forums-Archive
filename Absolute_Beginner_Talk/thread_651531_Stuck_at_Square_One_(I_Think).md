---
title: "Stuck at Square One (I Think)"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by jeffk14 on 2007-12-27
Hello everyone. I've got an old emachines T1100 with only 128MB of RAM, so I downloaded the alternate install-only version of Xubuntu & burned it to CD. My old HDD was fried, so I got a new-used one, installed it & now I've got the old-timey "c-prompt" with flashing cursor looking at me after I start the computer. How do I proceed from here? BTW, I don't have any recovery CD's for this machine & I assume the "new" HDD is empty. I used the search feature & read over the documentation, but didn't find anything explaining what to do in my situation. Any help would be greatly appreciated.

P.S., please be gentle, as I'm an old %art & not at all what you could call "savvy" when it comes to computers.

---

### Post by LaRoza on 2007-12-27
> **jeffk14 said:**
> Hello everyone. I've got an old emachines T1100 with only 128MB of RAM, so I downloaded the alternate install-only version of Xubuntu & burned it to CD. My old HDD was fried, so I got a new-used one, installed it & now I've got the old-timey "c-prompt" with flashing cursor looking at me after I start the computer. How do I proceed from here? BTW, I don't have any recovery CD's for this machine & I assume the "new" HDD is empty. I used the search feature & read over the documentation, but didn't find anything explaining what to do in my situation. Any help would be greatly appreciated.

P.S., please be gentle, as I'm an old %art & not at all what you could call "savvy" when it comes to computers.

If the CD is burned as an ISO, put it in the cd drive, close it, reboot.

Hope that helps.

I guess you can proceed from there, if you have problems with the questions asked during the install (which I doubt, they are simple) don't hesitate to ask.

---

### Post by jeffk14 on 2007-12-27
The CD is not the "live" CD. It's not bootable. I have the alternate "install only" CD due to my lack of RAM.

---

### Post by LaRoza on 2007-12-27
> **jeffk14 said:**
> The CD is not the "live" CD. It's not bootable. I have the alternate "install only" CD due to my lack of RAM.

Live means that the distro will run, the install cd means that you won't get the Ubuntu desktop (or *buntu), but you will get the install procedure when you boot.

It is bootable, if burned correctly.

---

### Post by jeffk14 on 2007-12-28
> **LaRoza said:**
> Live means that the distro will run, the install cd means that you won't get the Ubuntu desktop (or *buntu), but you will get the install procedure when you boot.

It is bootable, if burned correctly.

Thanks for clearing that up. As I said before, I'm no whiz. I think my copy may be messed up. Wen I put it in a working comp, all I get is the Windows-based thing that pops up and asks what you want to do with the CD, then I can't open it. Numerous attempts to download another copy have been unsuccessful. File transfer gets interrupted about 1/3 of the way and terminates. I would be willing to pay a few bucks for a good copy, but that does not seem to be available on the Xubuntu site.

---

### Post by Niniel on 2007-12-28
But you can order Ubuntu CDs, even free ones.

Just go to the [Get Ubuntu]("http://www.ubuntu.com/getubuntu") page. 

Oh, and you'll also need to change your BIOS to boot from CD. You sound like you are booting into Windows and then the autoplay function asks you what you want to do with the CD. So your CD may actually be ok.

---

### Post by sloggerkhan on 2007-12-28
With the alternate install CD, you still have to set your BIOS to boot from CD and restart with the CD in the CD drive.
If it's burned correctly, it will take you to a series of text dialogs to set up and install xubuntu.
You may need to use something like the free program imgburn on windows to correctly burn the iso to disk.

---

### Post by jeffk14 on 2007-12-29
O.K., I got the install-only Xubuntu CD to work. It was a loose cable on the back of the CD drive. Everything appears to have installed on the HDD. Booted up again & now can't get past the login/password screen. Please help. I set up a "host" name during installation & also set up a password where it said to. Now nothing works. Thanks.

---

### Post by jeffk14 on 2007-12-30
Well. after much fumbling around, I've got a working desktop of Xubuntu installed & running. I'm now trying to do what everyone refers to as "opening a terminal". I go to applications>accessories>terminal, enter my password when asked, then the computer reboots back to the desktop instead of giving me a terminal to work from. I know my ultra-newbie questions are probably a pain to anyone (which is probably about everybody on here) who is far more advanced than me, but any help would be greatly appreciated. Thanks again to everyone who has helped so far.

---

### Post by doorknob60 on 2007-12-30
What do you mean by reboots back to the desktop? Do you mean the terminal window closes?

---

### Post by mandrill on 2007-12-30
your terminal should not ask for a password unless the command you are trying to run needs permissions.....are you perhaps logged on as root? 

try this in terminal :  yourname@yourcomputername:~$ sudo evolution - should open the evolution email client....

trust me, it gets easier!

---

### Post by Don1500 on 2007-12-30
>  I know my ultra-newbie questions are probably a pain to anyone (which is probably about everybody on here) who is far more advanced than me, but any help would be greatly appreciated. Thanks again to everyone who has helped so far.

That's what this forum is for, The absolute beginner. I have not even tried another section yet. (BTW I'm waiting for this answer so I'll know what to do if it happens to me.)

---

### Post by mandrill on 2007-12-30
can you copy and paste what you get when you do: applications>accessories>terminal?

---

### Post by jeffk14 on 2007-12-30
> **doorknob60 said:**
> What do you mean by reboots back to the desktop? Do you mean the terminal window closes?

When you click on terminal, it goes to the sign-in screen, the same as when Xubuntu starts. You sign in, then the desktop comes up, the same as when Xubuntu starts

---

### Post by jeffk14 on 2007-12-30
To be more clear, when you click on "terminal", the computer boots & goes to the sign-in screen, THEN to the desktop once you sign in.

---

### Post by jeffk14 on 2007-12-30
> **mandrill said:**
> can you copy and paste what you get when you do: applications>accessories>terminal?

I can't copy & paste because I'm on a different comp. The Xubuntu machine isn't hooked to the internet. I go; applictions>accessories>terminal. Immediately when I click on terminal, the computer reboots and takes me to the sign-in screen for the desktop.

---

### Post by JoshuaRL on 2007-12-30
So basically you're saying that when you try to run terminal it crashes Xserver?  Have you tried running anything in either rescue mode or failsafe?  Are you able to run any simple commands like the evolution one suggested?

Are you running the program Terminal, or Super-User Terminal?

BTW Xserver is the application that allows you to load your chosen desktop manager.  Yours is XFCE, thereby Xubuntu.

---

### Post by ByteJuggler on 2007-12-30
> **jeffk14 said:**
> I can't copy & paste because I'm on a different comp. The Xubuntu machine isn't hooked to the internet. I go; applictions>accessories>terminal. Immediately when I click on terminal, the computer reboots and takes me to the sign-in screen for the desktop.

That doesn't sound right/normal... Can you open up any other applications?  Do they start normally?

---

### Post by jeffk14 on 2007-12-30
> **JoshuaRL said:**
> So basically you're saying that when you try to run terminal it crashes Xserver?  Have you tried running anything in either rescue mode or failsafe?  Are you able to run any simple commands like the evolution one suggested?

Are you running the program Terminal, or Super-User Terminal?

BTW Xserver is the application that allows you to load your chosen desktop manager.  Yours is XFCE, thereby Xubuntu.

I cant't access the terminl at all. When I click on the icon for "terminal" (in the accessories drop-down menu), the computer reboots to the same sign-in screen just like when Xubuntu first starts. As for the other stuff, I don't know. I'm too new at this to give you a good answer. Thanks.

---

### Post by JoshuaRL on 2007-12-30
Don't worry man, just ask and we're more than willing to help.

Alright try this:
When logging in, click the Session button and choose to go into Failsafe Terminal.  Then see if

```

sudo evolution

```

works for you.  If not, restart the machine and when it says that GRUB is loading hit escape and choose rescue mode.  It should run through a lot of stuff and finally sit there at the console when it reads:

```

you@yourcomputer $

```

then try running evolution again and see if it runs.  Let us know what happens.

---

### Post by jeffk14 on 2007-12-30
Hey, thanks to everyone for helping. The problem is solved. It was a bug that effects older hardware. Th way to fix it is to go to a failsafe terminal, then go to xorg-something and change the default depth setting from 24 to 16, then reboot. It worked! Thanks again.

---

### Post by JoshuaRL on 2007-12-30
Dude, that makes sense now.  Well, as much as bugs do.  Glad you got it working.

Just for anyone that has the same problem in the future, what hardware do you have?

---

### Post by bwtranch on 2007-12-30
Well, I'm not exactly understanding why you would need a password just to open a terminal. You should just be opening a terminal just as a regular user and that doesn't require a password once you are logged on. That is, once you have booted up your system. I'll use mine as an example, once you on the Desktop and go to Applications -> Accessories -> Terminal  do you see something that looks like jim@jim-desktop:~$
with a blinking cursor after it? Let us know.

---

### Post by jeffk14 on 2007-12-31
Well, I was tired last night, so I forgot to give credit where credit is due. A fellow who goes by the name of ozar over on another board helped me out. He found the reference to the bug and posted it for me. In case anyone else has this problem, here's the link:

[https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/114124](https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/114124)

---

