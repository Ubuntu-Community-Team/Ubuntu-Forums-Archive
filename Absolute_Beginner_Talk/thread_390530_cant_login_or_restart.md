---
title: "cant login or restart"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by greenw40 on 2007-03-22
I just finished installing Ubuntu, and after rebooting for the first time I cant login anymore.  I type in my name and password and it flashes a blank screen then just goes right back the the login screen.  Then if I try to reboot or shutdown the Ubuntu shutdown screen appears but it hangs once the bar goes all the way down.  I tried using df -h and aptitude clean from another post but I didnt help.  Im not sure what to do since I cant even get into Gnome (although I can login from the command line interface).

Thanks for the help.

---

### Post by MrCheese on 2007-03-22
if you can log on from the command line as you say, do so then type "startx" and Gnome should fire up with you already logged on. From there you can run the User & Login managers to make sure all is well with your account settings.

I presume you are aware that your password is case-sensitive - check when you boot that caps-lock isn't on.

---

### Post by greenw40 on 2007-03-22
Yea, I know its case sensitive, because if I type a wrong password it tells me right away.  It only restarts the login screen if I get the password right.  So what can I do when I get into Gnome?  Do I have to upgrade something or download a patch?

---

### Post by greenw40 on 2007-03-22
Ok, I tried "startx" and it gave me this:

xauth: creating new authority file /home/chris/.serverauth.976
xauth: creating new authority file /home/chris/.Xauthority
xauth: creating new authority file /home/chris/.Xauthority

X: user not authorized to run the X server, aborting


Then it just brings me back to the command line.  I know im authorized because I logged in once before, and Im the only user.

Help

---

### Post by greenw40 on 2007-03-22
anybody?

---

### Post by cfgtech on 2007-03-23
can you log in as root?

---

### Post by greenw40 on 2007-03-24
from the command line I can startx, but not if im logged on under my name

---

### Post by P-Max on 2007-04-14
I have the same problem.
Only can login in the console.
startx only starts if im a # as well as every other program, even after im done startx every program run as #

---

### Post by ComplexNumber on 2007-04-14
my guess is one of the following:

-you have a separate home partition and you are short of memory on your home partition. type in **du -c ~ **on the commandline. a list of your own files will now scroll down the page with a figure(in kilobytes) for how much memory each file takes up. how much does it give you for the total?

-you may have been running graphical applications using sudo instead of gksudo. if so, you need to go into your home directory (after you've logged into the terminal failsafe session) amd delete a file called .ICEauthority. then exit to the login screen and see if you can now log in.

---

### Post by Muffin_man1356 on 2007-04-14
i'm having the same problem!  i installed gdesklets, put a few desklets on my computer, shut down.  and when i rebooted, it takes me to the desktop and before the icons load, it freezes and goes back to the login screen

so i took the advice and from the command line i logged in using 'startx' and i'm currently logged in as "root".  Now, how do i get to the user & login manager to wipe my   user clean (i dont have anything really stroed on it yet) or how do i just eliminate the problem with gdesklets?  i cant uninstall with root

---

