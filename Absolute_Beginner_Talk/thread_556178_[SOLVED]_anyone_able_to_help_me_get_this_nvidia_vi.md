---
title: "[SOLVED] anyone able to help me get this nvidia video card updated."
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by computergeek13 on 2007-09-21
Finally, with the help of this forum, got feisty installed.

Now i am in the process of updating the video card and wireless card.

I have been reading that nvidia doesnt release open source drivers, and the resolution on my screen is locked at 800 x 600 atm.  

So some threads say to install and run nvidia glx, some list other means.  Can anyone offer some advice. 

I am extremely new to linux and am sort of tossed into the pool this quarter at school with my first linux class. And another scheduled for winter.

I have the latest driver downloaded for my card.. Nvidia-Linux-x86-100.14.09-pk1.run  downloaded from nvidia site.

Unfortuneatly attempting to run from a terminal doesnt work... get an error and the install closes.

Im searching for other solutions and looking for a GLX download.

thanks.

---

### Post by mysticmatrix on 2007-09-21
> **computergeek13 said:**
> Finally, with the help of this forum, got feisty installed.

Now i am in the process of updating the video card and wireless card.

I have been reading that nvidia doesnt release open source drivers, and the resolution on my screen is locked at 800 x 600 atm.  

So some threads say to install and run nvidia glx, some list other means.  Can anyone offer some advice. 

I am extremely new to linux and am sort of tossed into the pool this quarter at school with my first linux class. And another scheduled for winter.

I have the latest driver downloaded for my card.. Nvidia-Linux-x86-100.14.09-pk1.run  downloaded from nvidia site.

Unfortuneatly attempting to run from a terminal doesnt work... get an error and the install closes.

Im searching for other solutions and looking for a GLX download.

thanks.

Which video card are you trying to deal with?
If its in supported card list, restricted manager would be able to handle it easily. [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

If it is not listed there, (or you want to try latesst beta drivers at your own risk), try Envy.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by computergeek13 on 2007-09-21
sorry its an nvidia 8400m GT - on a sony laptop fz-190.

i have the driver downloaded for it - just need help with the commands and procedure.

---

### Post by bodhi.zazen on 2007-09-21
My advice for that nvidia card is to use the nvidia driver.

Envy is typically the easiest and fastest way to get it installed, later you might want to look at how to install the driver manually.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by computergeek13 on 2007-09-21
> **mysticmatrix said:**
> Which video card are you trying to deal with?
If its in supported card list, restricted manager would be able to handle it easily. [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

its not supported. I am attempting to install it manually. but the link you offered says installing nvidia graphic drivers maunally is bad. lol

Im still reading into it. if anyone has done this before im open to suggestions.

---

### Post by alienexplorers on 2007-09-21
Envy should be able to load the drivers for your card.  Just remember that you have to remove the old drivers first before adding the new drivers or you could have trouble.

---

### Post by mysticmatrix on 2007-09-21
> **computergeek13 said:**
> its not supported. I am attempting to install it manually. but the link you offered says installing nvidia graphic drivers maunally is bad. lol

Im still reading into it. if anyone has done this before im open to suggestions.

Yes, the link says "BAD" as in having headaches dealing with compiling. loads of command line stuff, and still no guarantee that you got it right. :)

SO better go with Envy, manages all headaches for you. When you think you have reached to expertise level, install drivers manually. BTW, there is link at end of that page which will tell you how to install manually

---

### Post by computergeek13 on 2007-09-21
> **mysticmatrix said:**
> Yes, the link says "BAD" as in having headaches dealing with compiling. loads of command line stuff, and still no guarantee that you got it right. :)

SO better go with Envy, manages all headaches for you. When you think you have reached to expertise level, install drivers manually. BTW, there is link at end of that page which will tell you how to install manually

gotcha  :) thanks for the help -  i downloaded envy attempting install now

---

### Post by computergeek13 on 2007-09-21
heh stuck on first step.. I have the debian package of envy (0.9.7) downloaded - i double click to install envy - and it flashes error --- DEPENDENCY is not satisfiable - build-essential.

Feisty fawn was listed as supported OS on the envy page - why is it flashing error?

---

### Post by Maestro23 on 2007-09-21
> **computergeek13 said:**
> heh stuck on first step.. I have the debian package of envy (0.9.7) downloaded - i double click to install envy - and it flashes error --- DEPENDENCY is not satisfiable - build-essential.

Feisty fawn was listed as supported OS on the envy page - why is it flashing error?

In a terminal:

> sudo apt-get install build-essential

---

### Post by computergeek13 on 2007-09-21
yea when i saw build essential i thought it was not liking the OS version heh. not missing a package :P

got it and thanks

---

### Post by computergeek13 on 2007-09-21
success = driver is installed and working. sorry for the long posts but thanks for the help!

---

### Post by Maestro23 on 2007-09-21
Good deal man.  Don't forget to mark this thread SOLVED.

---

### Post by nicklikesfire on 2007-10-07
This is my first day with linux, I'm using unbuntu 6.06.

I'm trying to get envy to work, and I'm having all the same problems.


Quote:
Originally Posted by computergeek13 View Post
heh stuck on first step.. I have the debian package of envy (0.9.7) downloaded - i double click to install envy - and it flashes error --- DEPENDENCY is not satisfiable - build-essential.

Feisty fawn was listed as supported OS on the envy page - why is it flashing error?
In a terminal:

Quote:
sudo apt-get install build-essential

I've done all this, and the terminal says:

Quote:
Reading package lists... Done
Building dependency tree... Done
Package build-essential is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

I have no Idea what that means. Any help out there?

---

### Post by bodhi.zazen on 2007-10-07
> **nicklikesfire said:**
> This is my first day with linux, I'm using unbuntu 6.06.

I'm trying to get envy to work, and I'm having all the same problems.


Quote:
Originally Posted by computergeek13 View Post
heh stuck on first step.. I have the debian package of envy (0.9.7) downloaded - i double click to install envy - and it flashes error --- DEPENDENCY is not satisfiable - build-essential.

Feisty fawn was listed as supported OS on the envy page - why is it flashing error?
In a terminal:

Quote:
sudo apt-get install build-essential

I've done all this, and the terminal says:

Quote:
Reading package lists... Done
Building dependency tree... Done
Package build-essential is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

I have no Idea what that means. Any help out there?

My guess is you need to enable a few repositories :

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by nicklikesfire on 2007-10-07
Thanks for the help, yeah, like I said, I'm still very new and bad at this.

so I enabled all the repositories, and then tried that line in the terminal again, and it installed a bunch of stuff. but now when I try to run envy I get:
quote:

Error: Dependency is not satisfiable: module-assistant

any idea where to go from here?

Thanks again.

---

### Post by aktiwers on 2007-10-07
Wont this work you ?

Go here and download the latest driver:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Save it on Desktop.

Log out.

Hit CTRL+ALT+F1

Log in.
type:
```
cd Desktop
```And then 
```
sudo ./Nvidia-Linux-x86-100.14.09-pk1.run
```when done.. type:
```
sudo reboot
```

---

### Post by nicklikesfire on 2007-10-07
well, I wen't ahead and did that, but I have no idea what it accomplished, if anything. I still can't set a high moniter resolution (above 1280 x 1024)

Thanks though. Maybe I should really be starting somewhere more basic?

---

### Post by aktiwers on 2007-10-07
This should install your Nvidia drivers.
Did an Nvidia screen show up on login?

What output does this give you, if you type:
```
glxinfo
```

in terminal?

I just want to make sure your Drivers are installed currect. Post the output here, then I will have a look.

---

### Post by bodhi.zazen on 2007-10-07
You should now see the nvidia logo when you start X or re-boot.

If not, then the drivers are not installed.

If so, you can set your resolution (and other things) with :

```
gksu nvidia-settings
```

Once you get it the way you like, save the settings ....



@aktiwers You have to stop X to install the nvidia driver 

```
sudo /etc/init.d/gdm stop
```

Now install the nvidia driver, then re-start X

```
sudo /etc/init.d/gdm start
```

---

### Post by aktiwers on 2007-10-07
Ahh sorry.. thought my solution was ok..  thanks for currecting that.

---

