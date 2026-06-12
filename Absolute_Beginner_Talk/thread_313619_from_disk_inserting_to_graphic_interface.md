---
title: "from disk inserting to graphic interface"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by spooky_paul on 2006-12-06
hi, just had my first taste of linux after yrs and yrs of windows, but it seems i can`t get to the graphical interface.. :(

i`ve been typing "sudo aptitude install ubuntu-desktop" but with no result...

i`m sure it`s been asked many times and answered time and time again... but bare with me and pls help me out as i`m not really comfortable with the command line environment

so... how do i get from disk inserting to a graphical interface?

thanks

---

### Post by apjone on 2006-12-06
have you just download the iso file and burnt it to disk?

---

### Post by taurus on 2006-12-06
You need to download the desktop CD (LiveCD).  Burn it as an ISO image file to a CD.  Set your BIOS to boot from a CD first.  Boot the CD...

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by spooky_paul on 2006-12-06
yes. i`ve dled and burnt "ubuntu-6.10-desktop-i386.iso"

---

### Post by Kieranties on 2006-12-06
Er.... not totally clear on where you are graphically

Are you at a command prompt?
Have you actually installed linux?

If you boot from the livecd, and then select the first option it will start the X server, (the gui) and then you can double click the install option on the desktop.

EDIT: You say you have the disk, leave it in the drive, restart your machine, if you need to, change the bios setting to boot from the cd/dvd drive.

If you have installed already then it should boot up with X anyway.

If you are at the command line eg 
```
root@computername#>
```

then type
```
startx
```

and the gui should start up

if your trying 'sudo aptitude install ubuntu-dekstop' what is the output of the command?

---

### Post by taurus on 2006-12-06
> **spooky_paul said:**
> yes. i`ve dled and burnt "ubuntu-6.10-desktop-i386.iso"
Have you set your BIOS to boot from the CD first?  How did you burn it anyway, as a image file not data file?

---

### Post by steve.horsley on 2006-12-06
Oops - already answered.

---

### Post by Kieranties on 2006-12-06
> **steve.horsley said:**
> 
One thing - sometimes the graphical installer doesn't work. I always recommend the "alternate" isntaller CD. It's text mode only but it's easy to use ant less trouble prone than the GUI one.

Really? I have never had a problem with the graphical install! <crosses fingers and hopes it works tonight/>

---

### Post by spooky_paul on 2006-12-06
what i did `till now:

dled, burnt, rr the pc, got to a menu and chose install/run ubuntu (not sure this is the way it`s called)
then got to a command line... then just typed "sudo  aptitude install ubuntu-desktop" and in didn`t install.. gave a reply like "0 packets installed"

well that`s about it

---

### Post by Kieranties on 2006-12-06
tried "startx"?

I assume you have the alternate cd, I have never used that.  As I said, the liveCD will boot up in a virtual ubuntu desktop environment

---

### Post by spooky_paul on 2006-12-06
> **Kieranties said:**
> tried "startx"?

I assume you have the alternate cd, I have never used that.  As I said, the liveCD will boot up in a virtual ubuntu desktop environment

i only have the liveCD ... i will reboot now and see if startx works

---

### Post by Kieranties on 2006-12-06
> **spooky_paul said:**
> i only have the liveCD ... i will reboot now and see if startx works

Hmmmm, Guess that is all you can do at the moment.  Reboot select the first option, and leave it to do its thing.  It should display "ubuntu" and a marquee like bar which will fill up as it sets itself up.

I am at work at the moment, and am afraid I can't help out much more then what I can think off the top of my head!

---

### Post by taurus on 2006-12-06
If you have a LiveCD and it doesn't boot into Gnome, then it means that there is something wrong with the graphic card...

---

### Post by spooky_paul on 2006-12-06
> **taurus said:**
> If you have a LiveCD and it doesn't boot into Gnome, then it means that there is something wrong with the graphic card...
i kinda have an ancient gpu... nvidia`s fx5200

with "startx" i only got errors :(

---

### Post by taurus on 2006-12-06
So you insert the LiveCD and boot from it.  You pick the first option from the CD and it boots up but somehow drops you into a commandline!  Is that what you mean?  Do you see any flickering on the monitor when it boots?

---

### Post by spooky_paul on 2006-12-06
> **taurus said:**
> So you insert the LiveCD and boot from it.  You pick the first option from the CD and it boots up but somehow drops you into a commandline!  Is that what you mean?  Do you see any flickering on the monitor when it boots?

that`s exactly what i mean :D

---

### Post by taurus on 2006-12-06
Do you plan to install Edgy on your machine?  you can use the alternate CD if you want.  Otherwise, see if you can configure your X again with

```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by houstonbofh on 2006-12-06
All of the stuff you are leaving out is the stuff we need.  Lets start with the CD.  What menue option do you pick?  Have you tried both "Start Ubuntu" and "Start Ubuntu in safe graphics mode" from the boot menue?  Do you get the graphical boot menue?
[IMG]http://img138.imageshack.us/img138/7134/w2u198sn.png[/IMG]
How far do you get in this screen?
[IMG]http://img144.imageshack.us/img144/9720/w2u218vo.png[/IMG]
What errors do you see when it dumps you to terminal?

---

### Post by spooky_paul on 2006-12-06
@ taurus

after reconfiguring i still get errors(errno111 & errno3)

@houstonbofh

when i chose start/install it loaded but i didn`t get those messages on the bottom while loading (loading essential messages... & ...)

after loading i got a command line style interface with some messages already on them about sudo and & stuff

when i chose Start Ubuntu in safe graphics mode

it loaded, still no messages. after that the screen became black and it had a just cursor blinking but no ability to write

---

### Post by taurus on 2006-12-06
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by spooky_paul on 2006-12-06
> **taurus said:**
> ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

i got this back:

xserver-xorg postinst warning: not updating /etc/X11/X; file has been costumised

xserver-xorg postinst warning: overwriting possibility-customised configuration file; backup in /etc/x11/xorg.conf.20061206191455

that`s it

---

### Post by bodhi.zazen on 2006-12-06
This is OK

Restart x```
sudo gdm
```

---

### Post by spooky_paul on 2006-12-06
@ bodhi.zazen

after sudo gdm i got this:

gdm: error while loading shared libraries /usd/lib/libretype.so.6: invalid ELF header

:(

---

### Post by spooky_paul on 2006-12-06
hey guys i still can`t get to the graphic interface...

pls help me out

---

### Post by bodhi.zazen on 2006-12-06
That is an interesting error message you have found :p

I have no idea what it may mean.

My only feeble thought would be to check the integrity (md5sum) of your .iso and CD in the hopes you have a bad burn.

[How to check md5sum](http://ubuntuforums.org/showthread.php?&t=290339)

---

### Post by taurus on 2006-12-06
And how fast did you burn it anyway?  Make sure you don't burn it faster than 4x (although I didn't have any problem with 8x on my crappy HP laptop)...

---

### Post by spooky_paul on 2006-12-06
i burnt it @ 16x :D

i`ll burn it again

... or i`m just gonna order one of those live cds...

i`m curious.... how long will it take to get to romania? :D

---

### Post by taurus on 2006-12-06
Usually 4 weeks from ShipIt!

---

