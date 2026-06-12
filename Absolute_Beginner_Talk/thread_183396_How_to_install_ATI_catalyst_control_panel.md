---
title: "How to install ATI catalyst control panel?"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by Rastareefer on 2006-05-27
Hi, folks and thanks for a great alternative OS.
All I need now is alternative brain patterns, ha!

I have an Acer AL1916 LCD monitor which unusually enough, is too bright and sort of washed out even with the brightness and contrast adjusted on the hardware.
This seems a common thing with this monitor and I really need to use the ATI drivers for my ATI RADEON 9500 card so that I can turn down the gamma on this thing.
I found what ATI claims are the Linux drivers but terminal just reports errors when trying to run them even with the code ATI lays out, the error is something about check the language encoding or something like that.

Is it possibly to install these drivers in Ubuntu somehow or is there some kind of control panel where I can actually setup my monitor already in the OS?

Thanks in advance

---

### Post by joshrobinson on 2006-05-27
you can try installing the fglrx driver for xorg, and the fglrx-control.. just do a search for fglrx in synaptic and they should pop up

when your done setting it up run

sudo aticonfig --initial

to set it to use the fglrx driver

if you have any problems run

sudo dpkg-reconfigure xserver-xorg

and pick the ati driver to get back to normal

the ati control panel has some adjustments you are looking for

---

### Post by Rastareefer on 2006-05-27
Thanks for the prompt advice.
I will give it a go right now but I will have to work out synaptec first.

This is my very first instalation of Linux and it is a bit confusing right now.
That said, I really want to find my way around it and get away from XP.

Thanks again

---

### Post by joshrobinson on 2006-05-27
[QUOTE=Rastareefer]Thanks for the prompt advice.
I will give it a go right now but I will have to work out synaptec first.

This is my very first instalation of Linux and it is a bit confusing right now.
That said, I really want to find my way around it and get away from XP.

Thanks again[/QUOTE]

click system > administration > synaptic package manager.. then click search type in fglrx then it should pop up with what it finds.. click the box next to what you want to install and it will say mark for installation.. do that for xorg-driver-fglrx and for fglrx-control

then click apply and install

when its done open a terminal in applications > accessories > terminal
type in the following code

sudo aticonfig --initial

then reboot

if you have problems and Xwindow wont come back up. when you boot up go to recovery mode
and login.. and type the following command, follow the onscreen dialog and when it asks what driver pick ati

sudo dpkg-reconfigure xserver-xorg

---

### Post by Rastareefer on 2006-05-28
Sorry to bother you guys with somthing as trivial as this but, I really need to get these drivers in to keep my mind at ease during this learning curve.

I did all the above as kindly described and after running terminal with the command, I am asked to enter the password. When entering the password for some reason I do not see anything being typed into the screen. I then hit enter and get this error message.
-------------------------------------------------------------------------------------------------------
sudo aticonfig --initial
Password:
sudo: aticonfig: command not found
-------------------------------------------------------------------------------------------------------
Is this something to do with not seeing anything being typed in the screen while entering the password or could it be something else?

Thanks in advance

---

### Post by kpolice on 2006-05-28
Try here if you use dapper:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

And for breezy:
[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)

---

### Post by Rastareefer on 2006-05-28
Sorry...All the terminology described on the sites with the information is Bumojumbo right now.:confused: ](*,) :confused:

---

### Post by joshrobinson on 2006-05-28
[QUOTE=Rastareefer]Sorry...All the terminology described on the sites with the information is Bumojumbo right now.:confused: ](*,) :confused:[/QUOTE]

did you install the fglrx-control package in synaptic?

in terminal

sudo apt-get install fglrx-control
then try your aticonfig --initial

---

### Post by Rastareefer on 2006-05-28
Yes, I installed everything with the commands provided.J
ust tried all the advice in the terminal window with the following results.
Please keep in mind that I could be screwing this up myself with my limited knowledge. As if I needed to say that. Ha.
---------------------------------------------------------------------
sudo apt-get install fglrx-control
Reading package lists... Done
Building dependency tree... Done
fglrx-control is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
---------------------------------------------------------------------
sudo aticonfig --initial
sudo: aticonfig: command not found
---------------------------------------------------------------------

---

### Post by Rackerz on 2006-05-28
Try just going into your xorg.conf and changing the device from 'ati' to 'fglrx'.

---

### Post by Rastareefer on 2006-05-28
Try just going into your xorg.conf and changing the device from 'ati' to 'fglrx'.
-------------------------------------------------------------------------
Is this done in terminal? Will one of the command lines as written in previous posts work? Sorry people, this is all so different.

---

### Post by Ryle on 2006-05-29
[QUOTE=Rastareefer]Try just going into your xorg.conf and changing the device from 'ati' to 'fglrx'.
-------------------------------------------------------------------------
Is this done in terminal? Will one of the command lines as written in previous posts work? Sorry people, this is all so different.[/QUOTE]

First backup your xorg.conf file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Then open it up with gedit;
```
sudo gedit /etc/X11/xorg.conf
```
Scroll down to the part that says
```
    Section "Device"
```
and change
```
Driver   "ati"
```
to 
```
Driver   "fglrx"
```

---

### Post by joshrobinson on 2006-05-29
as Ryle said, try that process.. that is what aticonfig --initial SHOULD be doing.. if it would run.. thats weird that it doesnt work mine does

when you do what Ryle said to run the ati control panel the command

fireglcontrol should open it

---

### Post by Rastareefer on 2006-05-29
Thanks folks..I am off to reboot and try to change the driver.

---

### Post by Rastareefer on 2006-05-29
It seems to work, however I get a window that says "Driver does not provide FireGL X extensions! Panel componenets will operate only partially."
The when I click on "OK" I get the ATI control panel with an Information tab and a TV Out tab. The information tab only has the driver information in it and the TV out tab has some adjustable stuff in it. However, I simply want to reduce the gamma on this display as it is killing my eyes and there appears to be no place to adjust this.

Is there not a component in Ubunto to adjust basic things like Gamma. brightness, contrast etc?

---

### Post by joshrobinson on 2006-05-29
your monitor has no settings for it? i dont think ive seen anything in ubuntu standard that you can change like that

---

### Post by Rastareefer on 2006-05-29
No unfortunately the Acer AL1916 does not have a gamma control which is ok in windows because one can turn it down with the ATI control panel but not on the monitor itself. This seems to be a common finding with this particular monitor. Thanks for the assistance everyone but it appears to be game over in this area.

Now, I have to try and get my mouse working like a mouse and not a snail as I have the motion turned right up in the control panel but it is still too slow without the Logitech drivers. Guess these sort of things are problems many face when moving from Windoze to Linux.

Thanks again

---

### Post by Rackerz on 2006-05-29
I tried this because all the other tutorials I used to install this driver didn't work, but this worked. The control see's my card and everything. One question, how can I find out if 3D acceleration is being used?

---

### Post by danoyoto on 2006-05-31
I am having a similar problem and am hoping someone can help me out!  

I followed the instructions in this post and now have a monitor that seems to bright?  The dark brown that I am used to in ubuntu is now a faded orange or very dull brown?  The TV displays colour but the screen is the wrong sixe(I video out to a 20" SONY TV)

I just tried the fireglcontrol and got the following:

dano@dano-desktop:~$ fireglcontrol
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Warning: Option 'DesktopSetup' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1
aticonfig : Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.
dano@dano-desktop:~$


Any help would be great as this is the last thing keeping me from having to boot into the dreaded Windows.....

Dano

---

### Post by morgengenuss on 2006-06-01
i have a ati x1400 and i have a problem with too bright display. well, actually it's a laptop display, so there's no option in sorting this out with the hardware.

as mentioned before by other people, i am looking for brightness and contrast adjustments.

i have tried just adjusting the gamma values with xgamma (e.g. "xgamma -gamma 0.6) and it looks better but not what it's supposed to be.

any help appreciated.

---

### Post by Rastareefer on 2006-06-01
Last night I installed Ubuntu 6.06 and to my surprise found that the washed out and too bright look has gone! Perhaps this is due to better drivers or better recognition of the hardware.

Thanks for another great distro folks.:-D :-D :-D

---

### Post by Rastareefer on 2006-06-11
Ooops...I thought the problem had been fixed but after a booting into Dapper and really looking at the screen brightness it doesn't seem to have worked.

I tried the xgamma 0.6 command as someone had suggested and it partially solves the problem but not entirely.

Booooo Hooooooo

I need my gamma settings......
Either that or another video card..But I only bought this one a month ago!](*,)

---

### Post by 3rdalbum on 2006-06-11
If you want to find out whether you're getting 3D acceleration, go into a terminal and type

```
glxgears
```

If the gears go round quickly, then you've got acceleration. If they go round sluggishly, you don't have acceleration.

If you want to make doubly sure, type glxinfo, and check the output to see whether Direct Rendering is turned on.

---

### Post by Rastareefer on 2006-06-11
No, my purpose was to get the gamma settings turned down as the Acer AL1916 monitor I am using was sort of washed out even with the brightness turned off on the monitor.
As there are no gamma settings on the monitor this was a problem without the control panel.


I managed to get the ATI control panel up with the gamma settings.
Had to set the three primary colors to move together and then adjust them slowly.
It works realy well now, but every time I reboot I have to call the ATI control panel up again as the settings get lost for some reason.
Is there any way to either get Dapper to retain the settings or at least add the control panle to the desktop?

---

### Post by Orixyu on 2006-06-12
I've got the same problem; as danoyoto

```
oliver@oliver-desktop:~$ fireglcontrol
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Warning: Option 'DesktopSetup' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1
aticonfig : Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

```

---

### Post by Rastareefer on 2006-06-13
Here is the screen shot of the ATI control panel.
For some reason even though I saved the session after adjusting the controls, they always go back to the default setting. Is there any way to make sure these settings get saved so that one doesn't have to mess around with them every time when booting into Dapper?

[IMG]http://img113.imageshack.us/img113/9695/screenshot4gi.png[/IMG]

---

### Post by Rastareefer on 2006-06-15
steve@steve-desktop:~$ fireglcontrol
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

------------------------------------------------------------------------------------------------------

That is odd as I get the same sort of error message but the control panel opens.

---

### Post by morgengenuss on 2006-06-15
well, i remember having had this problem with the aticonfig not remembering the gamma values...
anyways, i would suggest to put the command "xgamma -gamma 0.6" into "settings -> autostarted applications".
but i would agree that this is just a workaround and not the answer to why aticonfig does forget the gamma values.

---

### Post by leetcharmer on 2006-06-17
I, too, am I getting error messages, and it will not effectively save my settings.

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

