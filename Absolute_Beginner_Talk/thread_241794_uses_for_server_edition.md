---
title: "uses for server edition"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by k94382 on 2006-08-22
what kind of things can u do with the ubuntu server edition?? i'm wondering cuz i heard that many ppl use their old and slow computers as servers and im wondering wat kinds of things u can actually do with a server. im a noobie in those kinds of things especially ubuntu

---

### Post by bodhi.zazen on 2006-08-22
1. Use as a server. A server stores and transfers data to other systems such as E-mail, this page, database, etc.

2. The server install itself is a minimal install of Ubnuntu. I use it myself to have a smaller, lighter install on my not so old box. Takes up less hard drive space and I install and customize only what applications I want, either from the Ubuntu repository of source. I do not run GNOME, KDE, or even XFCE rather preferring Fluxbox (or CLI). I use the command line (CLI) for sys admin and so sometimes do not run a GUI (window manager).

This leaves all my memory, CPU, etc to run applications rather then a large, resource intensive GUI. I use a few applications that are resource intensive and this allows optimal performance.

3. You can run a server on a network to serve data or programs (say openoffice and data) to other boxes that then act as terminals. You log onto the server and use the remote box to run X. Thus X does not need to run on the server, improving the security of the server (ie keeps out crackers who do not know how to manage without a GUI) and reducing the resource load on the server. Thus rather then updating each and every box with all the applications, I keep the server up to date with the lions share and the clients are up thus to date as well (lessens sys admin).

I do not do this with Ubuntu. No offense, Ubuntu is not secure enough for a server of this type.

---

### Post by k94382 on 2006-08-22
thx for the effort. so if i used my old laptop as a server, i could install openoffice on it and use it on my other computers, which dont have the program installed, at the same time??

---

### Post by bodhi.zazen on 2006-08-22
You can do this without the server install. It requires some knowledge of networking and firewalls.

The server install will NOT do this without the same configuration effort as the standard install. The features I mentioned are configured manually by the sys admin, in this case myself, and NOT by any type of GUI. The server install is smaller, CLI only, and, because there are less applications, more secure.

In order to maximize security you need to "harden" Ubuntu. You can start with the standard edition and strip away various features. This takes time. Or you can start with the Server install and add features, only the ones you need. The server install is very minimal and a faster route to a secure server. Many are of the opinion a server should not run X or a GUI of any type.

Once the server is hardened it is configured and networked.

I use a server install as a desktop because I am a control freak (read experienced Linux user). I would neither encourage or discourage a newbie to take this route, it takes more time but you will be forced to learn Linux very quickly if you must install and configure your box or network from the ground up.

---

### Post by k94382 on 2006-08-22
i think ill leave that project until im comfortable using ubuntu

---

### Post by bodhi.zazen on 2006-08-22
Find a free partition, do an Ubuntu server install, and configure it as your desktop. Will take some time, but you will rapidly learn the CLI. The Ubuntu forums will give you the guidence you seek.

What OS do you come from?

---

### Post by jimmygoon on 2006-08-22
Until then though... when you become a cli-pro (it doesn't take long)... you can try out Xubuntu. it works on lower end hardware... but you still get ubuntu/gtk goodness :)

---

### Post by bodhi.zazen on 2006-08-22
Try Fluxbox, Openbox, or IceWM. I would be happy to help you configure them, but they are "easy", esp IceWM.

They all use gtk. Openbox is as minimal as I go.

---

### Post by k94382 on 2006-08-22
so server edition is like desktop version except it almost has nothing preloaded with it?

and using the openoffice example again. would i be able to use openoffice from a windows xp computer??

---

### Post by Paul133 on 2006-08-22
I've been told that you can install the server OS and then open a terminal and type ```
 sudo apt-get install ubuntu-desktop 
``` and it'll be similar to refular Ubuntu but I can't install regular Ubuntu b/c it's way too slow on the LiveCD.

---

### Post by bodhi.zazen on 2006-08-23
> **k94382 said:**
> so server edition is like desktop version except it almost has nothing preloaded with it?

and using the openoffice example again. would i be able to use openoffice from a windows xp computer??

Yes on the first question.

Yes on the second question.

I learned to do this when learning Linux. It was a pain to dual boot, so I set up Ubuntu as a "server". Nothing special, a regular desktop install.

I then logged into the Ubuntu Bow from XP and "Learned the ropes" so to speak. No longer use Windows XP though.

I am willing to help you, but to outline each step in detail would be very long.

General steps (lots of options and variations).

1. Use ssh to log into the Ubutnu box. You need a Windows program to do this. I advise Putty:

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

On the same web page is:
PSCP (an SCP client, i.e. command-line secure file copy)

PSCP allows you to transfer files (2 way transfer) from windows to Ubuntu.

2. ssh gives you a CLI to Linux. To run say Firefox (surfing with the Security of a Linux box displaying firefox to Windows box) you need an X server for windows. There are several, I used Cygwin:

[http://www.cygwin.com/](http://www.cygwin.com/).

Cygwin gives you a bash shell in Windows, but more important an X Server.

3. To run Open office on a Linux box and display to windows:

On Ubuntu:
Allow ssh log in.
Allow X forwarding.


On the Windows box:
Start your X server.
Open Putty
Configure Putty (in the options check box) to allow X forwarding.
Log into Ubuntu.

This displays a "terminal" with a CLI to the Ubuntu box on the Windows box.

Log in to Ubuntu as your usual user.

At the CLI type:

openoffice & -> A window with open office will open on your Windows box. Otherwise looks like any other Window.

firefox & -> Opens Firefox.

startkde, gnome-session, xfce-session -> Projects the whole desktop (KED, Gnome, XFCE) to Windows box.

Now a days people do much the same thing with VPN.

You can log into Windows-> Ubuntu with VPN.
You can log into Ubuntu -> windows with RPC.

I found VPN slower then single applications via Cygwin.

This allows learning without dual booting.

Start on Windows -> Log onto Ubuntu.
Transition Ubuntu -> Log onto Windows.

Finish Ubuntu NO WINDOWS.

Sorry for the length.

---

### Post by k94382 on 2006-08-23
i appreciate your effort and i will look into it as soon as my lcd is repaired since using ubuntu takes a while for me and i dont want to keep starring into this electron cannon.

---

### Post by bodhi.zazen on 2006-08-23
[http://users.piuha.net/martti/comp/ubuntu/server.html](http://users.piuha.net/martti/comp/ubuntu/server.html)

---

### Post by 3rdalbum on 2006-08-23
The Server edition is also useful for making people think you're smart.

Just learn a few simple commands, get a few terminal-based programs like Links2 and MPlayer and run them with their output directly to the framebuffer. Your friends will think you're the biggest computer-whizz in the world!

---

### Post by k94382 on 2006-08-23
My first project I would like to attempt is to install aMSN from .deb file on a fresh installed server installation. Would it then be possible to run this program from my other computers with windows XP installed?

---

### Post by bodhi.zazen on 2006-08-23
Yes.

First configure your XP boxes with either an X server/vnc and ssh client.

SSH into Linux server.

Forward X to windows box.

run amsn from CLI.

Fastest and free would be Putty/Cygwin. VNC may be easire to configure, but slower.

---

### Post by k94382 on 2006-08-23
wat u just described sounds way too out of my league. are those steps described in the guides u provided me with?

---

### Post by bodhi.zazen on 2006-08-24
Sorry. This will take some time for you to learn, but do not be intimidated. Give yourself time and be willing to learn. In the end you will understand Linux and Windows a little better.

It would be a long post to give detailed instructions. If you start and have specific questions along the way, search the forums and post questions.

Start simple. Look at ssh, VNC, and RPC.

You can use RPC out of the box with Ubuntu to log into your Windows box. You will need to configure windows to accept a RPC connection.

ssh is also easy. Install Putty onto windows and log into Ubuntu. This will be CLI, but you can fix that.

VNC:
[http://www.tightvnc.com/](http://www.tightvnc.com/)
Install on Windows box.
Use synaptic to install VNC server into the Ubuntu server.

---

### Post by k94382 on 2006-08-24
now the first step has been done. i have installed the server edition on my laptop. i assume that installing amsn would be the next step. how do i approach this one with CLI?

---

### Post by bodhi.zazen on 2006-08-24
You will need to bear with me, I am not familiar with amsn

Try:
```

apt-get update
apt-get install aptitude
aptitude dist-upgrade
```

This will update your distro. Update may be down due to the problems ubuntu is having with X ? If so you will have to wait.

I prefer aptitude to apt-get.

Then:
```
aptitude install amsn
```

If this does not work here is a step-by-step guide (written for the CLI):
[http://www.ubuntuforums.org/showthread.php?t=216689](http://www.ubuntuforums.org/showthread.php?t=216689)

---

### Post by k94382 on 2006-08-24
that topic seems to be installing amsn with a graphical interface. i have downloaded the amsn .deb file on my win xp computer. how do i install it on the ubuntu laptop using CLI??

---

### Post by bodhi.zazen on 2006-08-24
Transfer the .deb file to the laptop. ? usb device, CD, floppy/

I would put the .deb file in your home directory in a folder SRC for future reference.

cd (cd <Enter> without anything else goes to your home directory)
mkdir SRC
cp /location_of_.deb_file/amsn-x.y.z.deb SRC/
cd SRC
sudo dpkg -i amsn-x.y.z.deb

If you run into errors (dependencies) you should "fall back" to the tread's instructions:

```


cd /home/user_name/SRC or cd ~/SRC if you are lazy.

wget http://www.doeweling.com/files/ubuntu/amsn/tcl8.5_8.5.0-1~neto3_i386.deb

wget http://www.doeweling.com/files/ubuntu/amsn/tk8.5_8.5.0-1~neto3_i386.deb

wget http://cablemodem.fibertel.com.ar/mnzk/amsn_0.97b_tcl0.95.deb

sudo dpkg -i tcl8.5_8.5.0-1~neto3_i386.deb tk8.5_8.5.0-1~neto3_i386.deb amsn_0.97b_tcl0.95.deb
```

Probably easier to do the second (which is why I boxed it) from the CLI in the server terminal.

Do you know how to use tab completion? Start to type a location, use <tab> key to complete.

Ex in the terminal type cd /ho <tab> and you get
> 
cd /home

Much easier then typing the long name of the .deb files.

ie sudo dpkg -i tk8<tab> will give you the file name "tk8.5_8.5.0-1~neto3_i386.deb".

Works for commands as well.

---

### Post by k94382 on 2006-08-24
wat does SRC stand for?? can u remind of the basic commands for copying files please?

---

### Post by bodhi.zazen on 2006-08-24
SRC is my own code for "source". You need to make the directory yourself.

mkdir SRC if you are in ~,
otherwise mkdir /home/user_name/SRC

If you install outside of apt-get/aptitude/synaptic it is nice to save the file somewhere you can find it again.

for example, your .deb file. What if you want to un-install or update? You will need to know where this file is.

If you install a package outside of apt-get/aptitude/synaptic it is up to you to maintain (find, download, and install updates).

To copy a file -> cp

to move -> mv

to delete -> rm (no undo, be careful).

For example cp <path_to_file/file> <where_to_copy>

On windows the path starts with C:\

In Linux it starts with /

"Full path" starts with /

"Relative path" starts with where you are now.

Ex Say you are in you home directory
Full path is /home/user_name

Your home directory is abbreviated with ~

Thus ~ = /home/user_name

to print your current working directory pwd (print working directory)

Assume a directory in ~ called SCR
Assume a file "file" in SRC
Assume you are in your home directory (cd ~) or (cd)

Full path to "file" is /home/user_name/SRC/file
Relative path SRC/file (no leading "/")

If you transfer your deb file you will need to look into mount as well.

Again, everyone feels overwhelmed with the CLI at first, but as you use it more and more it becomes very easy. Easier then a GUI for some.

---

