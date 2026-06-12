---
title: "Three small ?s Please"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-04-28
I'm starting to get the hang of this now but I have to ask what am I supposed to enter in terminal after installing a program? I succeded in the installation but my user and the cursor are just sitting there waiting for something.

?-2 is there a way shutting the update manager off. Every time I boot it pops up telling me there are updates which are the same ones I have refused before as they are un-needed.

Saved the easy one for last: As I am the only user of this PC why is it necessary for me to enter my password every time I try to do something? Am not on any network, have remote sharing off, just sitting here surfing.


Thanks for any insight,

Jon

---

### Post by [S|G] on 2007-04-28
After installing something, you're ready to run it. Usually you start the program by typing its name.

---

### Post by raul_ on 2007-04-28
Ususally the name of the program it's the name of the package. 

You can lock package versions through synaptic, by searching fot the package name and then in options, choose "lock version" or something like that.

You need to type a password because that's how Linux works.

:)

---

### Post by Roadrunner777 on 2007-04-28
1.  Longish answer because there are different scenerios.  Typing the name of the program works, mostly.  But, that gets to be a drag after a while. So, you can create a desktop icon, right-click on desktop and 'Create Launcher', pretty obvious from there.  You can drag the launcher into a toolbar or whatever.

2. I recommend installing all updates, even if you don't think you need them.

3. Automatic Login: Go to System > Administration > login window, then on the security tab you can enable automatic login.

3. Revised: I see what you are asking now.  Raul is right.  It's pretty much the same thing in any other distro of LInux, Apple, and Windows Vista.  It's the right way to go to prevent malicious code and viruses from causing problems.

---

### Post by tophatandy on 2007-04-28
after a programs finishes downloading it should run through a brief install screen, then it should say something like "Installation Complete!" and then you simply click close, it should be added to the application menu (or other menus, depending on what you installed). If you think that you have installed the program, but cant find it try typing ```
locate x
``` where x would be the name of the package or program you installed. An example would be if I installed the firestarter firewall and couldn't find it, I would type ```
locate firestarter
``` in the terminal..
or to run the program I would type ```
firestarter
``` in the terminal to run the program.

as for turning off automatic updates, sorry.. I will look around the forums and post the answer if I can find one..

and your final problem..
I dont think you can shut off passwords..
unless you log in and run the operating system as root..
which can be very dangerous even if you are the only user..

BUT.. if it really bothers you that bad I could find the way to log in as root user every time.
I would really not suggest it though..

good luck.

---

### Post by Romin-1 on 2007-04-28
Thanks for all the info folks,

I cannot find GDebi or Wine anywhere so will try the calls in Terminal and endeavor to put an icon somewhere.

Once again, thanks

Jon

---

### Post by kittyhawk63 on 2007-04-28
> **Romin-1 said:**
> I'm starting to get the hang of this now but I have to ask what am I supposed to enter in terminal after installing a program? I succeded in the installation but my user and the cursor are just sitting there waiting for something.

?-2 is there a way shutting the update manager off. Every time I boot it pops up telling me there are updates which are the same ones I have refused before as they are un-needed.

Saved the easy one for last: As I am the only user of this PC why is it necessary for me to enter my password every time I try to do something? Am not on any network, have remote sharing off, just sitting here surfing.
Thanks for any insight,
Jon

If you turn off updates, you will not see ones they add later. Those may be important ones.
kh

---

