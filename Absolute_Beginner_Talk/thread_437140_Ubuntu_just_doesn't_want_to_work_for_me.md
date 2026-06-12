---
title: "Ubuntu just doesn't want to work for me?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Meizulo on 2007-05-08
I ran the live CD on my Toshiba laptop which worked fine. I then installed Ubuntu. The installation went perfect. After I entered my User Name and Password, Ubuntu loads correctly. The problem is after it has loaded I get the Ubuntu background but no Task bars on top or on the bottom. Also, my right click does nothing. Basically I cannot do anything but look at the cool Ubuntu Background wallpaper and wait for the screen to automatically shut off after x amount of time.

I am running a P4 3.0MHz with 447MB of ram on a Toshiba Laptop with Ubuntu 6.10 i386

---

### Post by LaRoza on 2007-05-08
That's odd. Did your hardware work with the live disk?

---

### Post by mejy on 2007-05-08
To fix the gnome-panel (the taskbar type things) issue, try switching to VT1 by pressing Ctrl + Alt + F1, logging in, typing 'killall gnome-panel' and the pressing Ctrl + Alt + F7 to switch back to the display.  If the right click is with a touchpad, look into installing gsynaptic.  It's also worth trying as many external mice as you have lieing around, and checking all your USB ports.

---

### Post by Meizulo on 2007-05-08
Everything seems to be working fine with the live CD.

---

### Post by Meizulo on 2007-05-08
I switched to VT1, then logged in using my User Name and Password. When I type "killall gnome-panel' and press enter is says " -bash: killall gnome-panel: command not found'

---

### Post by annda on 2007-05-08
> **Meizulo said:**
> I switched to VT1, then logged in using my User Name and Password. When I type "killall gnome-panel' and press enter is says " -bash: killall gnome-panel: command not found'

this is very strange. are you sure you typed "'killall' correctly?

also, you don't really have to change the console: you can hit Alt+F2 and a window will pop up with a field to enter a command. you can try the killall command here. or try starting the panel:

```
gnome-panel
```

if you have internet connectivity (check for example with firefox as a command), you will be able to install the touchpad driver. it's possible that it is already installed - type

```
gnome-control-center
```
 to see if you can modify the settings.

---

### Post by Meizulo on 2007-05-08
alt F2 does not work and I keep getting 'cannot open display' when I type 'gnome-panel' if i'm in VT1. Also when I type 'gnome-control-center' I get '(gnome-control-center:4467): Gtk-WARNING **:cannot open display:

---

### Post by mdwuznik on 2007-05-08
In VT1 try issuing " DISPLAY=:0 xterm" Than get back to X.


Happy bughunting
Michal

---

### Post by annda on 2007-05-08
this does not look good. it looks like at least GNOME is not installed correctly (killall missing from bash?!). before you reinstall, maybe try this from the console (Ctrl + Alt + F1)
```

gnome-panel --display=:0
```

if nothing happens, switch back to GUI (Ctrl + Alt +F7) and see if you get a message - or better yet, your panels.

---

### Post by Meizulo on 2007-05-08
Just to let you know this is not the first time I have installed Ubuntu. I have tried reinstalling it about three different times with two different CD's. 

I went to the (ctrl+atl+F1) console typed in 'gnome-panel --display=:0' and nothing happened. So I switched back to (ctrl+alt+F7) and a blank message box appeared - no panels though.

---

### Post by earobinson on 2007-05-08
well maybe you can still use open source software on windows.

---

### Post by Panzor on 2007-05-08
If it was my problem, I would reinstall feisty. I've had a few issues with the partition aspect of my live disks and have had other errors. You can do it the long way (see above) or you can reinstall. Also, check to see if your live cd has errors before reinstalling if you feel that it won't work. There should be an option around the boot screen that has the "run live CD" option.

---

### Post by Meizulo on 2007-05-08
thank you guys for all the help. I just really wanted to get into Linux. It sucx that Ubuntu will not work for me. Do you know of any other good Linux OS's out there I can try?

---

### Post by Ozeuss on 2007-05-08
first try to install KDE or XFCE through apt-get (for kde, "sudo apt-get install kubuntu-desktop" if im not mistaken). it might be just a gnome problem. it might be easier to bughunt the problem from there, or reinstall gnome.

---

### Post by annda on 2007-05-08
i reaaly would give Ubuntu another try/install. it is one of the nicest distributions out there, and the live CD worked...

but of course Ubuntu is not all there is. you can try Mandriva, openSUSE, PCLinuxOS, MEPIS...

take a look here to read reviews:
[http://distrowatch.com/](http://distrowatch.com/)

if you feel like exploring, this is a nice collection of screenshots:
[http://www.thecodingstudio.com/opensource/linux/screenshots/index.php](http://www.thecodingstudio.com/opensource/linux/screenshots/index.php)

---

### Post by JLHenry on 2007-05-08
I'm having problems getting the LiveCD to run on my laptop (Inspiron 6000, 256 meg, Intel 9154g graphics, Dell wireless 1370 [miniPCI card]).  But the Latest TR of PCLinuxOS boots right up (TR4).  Download that and try it.  It uses KDE instead of Gnome, but other than that, everything is there.

The Issue with My Laptop is disturbing, because Ubuntu works GREAT on my Desktop, which a MUCH older PC!!!

In fact, once I "convince" my daughter that she doesn't need THAT many iTunes songs, I'm going to install Feisty on on the Desktop as a dual boot . . .

---

### Post by Meizulo on 2007-05-08
i tried the 'sudo apt-get jubuntu-desktop' and it said 'E: Invalid operation kubuntu-desktop'. If I wanted to try to re-install the gnome how would I do that? I have tried re-installing the whole OS from scratch many times now after checking the CD for errors.

---

### Post by mattva01 on 2007-05-08
The command is : sudo apt-get **install** kubuntu-desktop

---

### Post by annda on 2007-05-08
it should be:
sudo apt-get **install** kubuntu-desktop

as to reinstalling gnome, it is difficult without a GUI... but you should be able to do it with KDE's Adept package manager.

---

### Post by mejy on 2007-05-08
> **annda said:**
> it should be:
sudo apt-get **install** kubuntu-desktop

as to reinstalling gnome, it is difficult without a GUI... but you should be able to do it with KDE's Adept package manager.

Not so - 'sudo apt-get install ubuntu-desktop' will do it just fine.  I think perhaps we should lay off the installing software before we over complicate things...

---

### Post by Meizulo on 2007-05-08
I ran 'sudo apt-get install ubuntu-desktop' and it said that I had the latest version already

---

### Post by annda on 2007-05-08
yep, that's why you need to install another window manager to repair gnome - sorry.

you can try aptitude (this command-line tool can reinstall)

```
sudo aptitude reinstall ubuntu-desktop
```

but most probably it will complain, because the gnome package was not installed using aptitude.

if you have a good internet connection, i would recommend KDE. it takes some time to install, but it's good.

after it's installed, reboot and choose 'change session' in the login window (it should be in the options menu) and boot to KDE.

good luck and stick around!

---

### Post by Meizulo on 2007-05-08
This is the message i got when i tried to reinstall

'E: I wasn't able to locate file for the ubuntu-desktop package. this might mean you need to manually fix this package'
'E: couldn't lock list directory.. are you root?'

---

### Post by icechen1 on 2007-05-08
> **Meizulo said:**
> This is the message i got when i tried to reinstall

'E: I wasn't able to locate file for the ubuntu-desktop package. this might mean you need to manually fix this package'
'E: couldn't lock list directory.. are you root?'

add sudo before that command\
sudo aptitude reinstall ubuntu-desktop

---

### Post by Meizulo on 2007-05-08
I added sudo to the command

---

### Post by Toontwnca on 2007-05-08
Had the same problem with every distro of Ubuntu.
The solution that works for me is;

sudo apt-get remove powernowd.


> **Meizulo said:**
> I ran the live CD on my Toshiba laptop which worked fine. I then installed Ubuntu. The installation went perfect. After I entered my User Name and Password, Ubuntu loads correctly. The problem is after it has loaded I get the Ubuntu background but no Task bars on top or on the bottom. Also, my right click does nothing. Basically I cannot do anything but look at the cool Ubuntu Background wallpaper and wait for the screen to automatically shut off after x amount of time.

I am running a P4 3.0MHz with 447MB of ram on a Toshiba Laptop with Ubuntu 6.10 i386

---

### Post by Meizulo on 2007-05-08
OMG!!! that worked!!! Thank you soooo much. I have been trying to fix this problem for like a month now. What was the problem if I can ask?

---

### Post by Toontwnca on 2007-05-11
Well I'm not real sure what the problem was. All I know is it worked.
It has been documented elsewhere in this forum as far back as Breezy, I think.

Part of what powernowd does (I think) is control the cpu speed when using your battery. Other than that I'm not sure. I rarely use my battery.

---

