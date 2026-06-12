---
title: "Ubuntu Installation Issue (HELP!)"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by kyle.hall on 2008-04-20
Hi.

I am new to LINUX and Ubuntu and fairly comfortable with computers.  

I have downloaded and burned and installed Ubuntu with no issues.  I even set up Flash and was very proud of myself, with help from a website of course.  My problem arises when I shut down my computer.  When I come back to use it, I turn it on and get the Ubuntu screen with the progress bar and then nothing.  Black screen of death in Windows terms.  Can anyone point out to me what I am doing wrong?

I have 7.10-desktop-i386, IBM ThinkPad, Pentium III 800 MHz, not sure about RAM, at least 256?  and 20 Gig hard drive.  I have completely wiped Windows off this machine.

Like I said, Ubuntu installs fine, asks to reboot, asks me to remove CD and hit enter, reboots, and works great.  If I turn it off after this point I can not get it to come back up.  

I reset my BIOS to boot from hard drive and know that the battery is weak but I use an AC adapter.   

I appreciate any insight you may have and thank you in advance for you expertise.

Kyle

---

### Post by meborc on 2008-04-20
try to boot to the recovery mode (choose the 2nd line in grub menu... you might need to hit esc while booting to see the grub menu)

you should now be able to see the text flying by when you boot... see if there are any error messages... do you get to login, or does it hang before that... what is the last thing you see on screen?

the problem might be in the graphics driver, what card does your computer have?

---

### Post by martrn on 2008-04-20
Like above the problem maybe with your graphics driver although it may also be :-

Not the correct/best  kernel try
```
uname -r
sudo apt-get install linux-386
sudo apt-get install linux-generic
sudo apt-get install linux-server
sudo apt-get install linux-ume
```
If you need to istall other defualt kernels.

It could be something else causing a problem during boot up eg.
In your  /etc/init.d  startup.

---

### Post by kyle.hall on 2008-04-20
meborc,

OK.  I started in recovery mode.  A lot of stuff flashes by, everything ending in [OK] from what I could tell.  I then get this line:

root#kyle-tPadLaptop:~# followed by a cursor.

Yep, I'm a noob.  Now what?  I assume I can log in from here.  How?  I am certian you already know this but kyle-tPadLaptop is the name of my machine.

Please excuse my ignorance, I really do want to learn this!

---

### Post by meborc on 2008-04-20
when booting into recovery mode, you are automatically logged in as root... so this name@name# means you are now logged in as root

which means that the problem might be in the graphics part... try to type```
startx
```in the command line and hit enter, does the gnome desktop appear? if not try```
dpkg-reconfigure xserver-xorg
```whenever you do not know the correct answer, just choose the default one.. .the important ones are the questions about the resolution and graphics card

---

### Post by martrn on 2008-04-20
try   init2   or init3 or init4

you need to change your runlevel, 
or type login to login to run level1.

When you login you might need to configure x
Check to see if there is an error log I think it should be at   ... /var/log/XFree86.0.log I believe.

If you need to reconfigure x11 try
```
sudo dpkg-reconfigure xserver-xorg
```]

---

### Post by kyle.hall on 2008-04-20
This is definitely a monitor or graphics driver issue.  I have played with some of the resolutions but have not got it working yet.  I will do some internet searching and try to see what others did.

Thank you for the push in the right direction. 

Kyle

---

### Post by kyle.hall on 2008-04-20
Problem Solved.  The auto detected screen size and refresh frequency were wrong.

Thank you again.

Kyle

---

