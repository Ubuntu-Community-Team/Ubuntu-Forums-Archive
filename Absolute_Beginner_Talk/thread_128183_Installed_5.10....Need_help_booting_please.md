---
title: "Installed 5.10....Need help booting please"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by gordong11 on 2006-02-10
Hello,

I just installed 5.10 for my first linux install ever using the standard install by pressing enter only, so pardon my newbness. 

Ok my problem is, when I boot my PC it asks me for my username and password, then does not boot into the GUI, just a DOS like console. Is this normal? if so what command do I give to boot the GUI?

I"m sorry I just can't seem to find any info on this.

Godo

PS-It did NOT ask me for my display resolutions during install, is this normal?

---

### Post by vt8 on 2006-02-10
I have the some problem! is this a bug or have i done something wrong?
I am logged in, now what? where is the gui my last installation had?

---

### Post by gordong11 on 2006-02-10
I know this weird, I have never used linux before, but the live CD just went right into the gui. I wonder if there is a way bypass this console permanently?

---

### Post by bluevoodoo1 on 2006-02-10
Is "X" running? if not, that command is "startx"

To get you to the graphical login try:

```

sudo /etc/init.d/gdm start

```

if that doesn't work, might be... sudo /etc/init.d/gdm restart


EDIT:

[QUOTE=gordong11]I know this weird, I have never used linux before, but the live CD just went right into the gui. I wonder if there is a way bypass this console permanently?[/QUOTE]

Do you have "gdm" installed?

---

### Post by Mustard on 2006-02-10
There may have been some issue with your graphics card at the start and the installer might have failed to configure your display.  That would be my guess.  What graphics cards are you both using?

---

### Post by gordong11 on 2006-02-10
Honestly I'm not sure if I have GDM installed. I went through the install, took out the CD, rebooted...then completed the install by selecting timezone, username and password. Then I rebooted again, then it took me to that console.

I havent installed anything that is not included in the typical install. I"m running 64 bit edition of 5.10. My system is AMD sempron 2800, 512 meg ram, WD 80 gig Caviar SATA and a Lite-On DVD recorder all on a MSI MS482M-IL Mobo.

All I want to do, is when I start my PC it goes into the GUI. I just want this for web and DVD burning uses. I have no plans of doing much more until I get more experience with Linux. Will this GDM help me? how do I install? Thanks

---

### Post by bluevoodoo1 on 2006-02-10
[QUOTE=gordong11]
All I want to do, is when I start my PC it goes into the GUI. I just want this for web and DVD burning uses. I have no plans of doing much more until I get more experience with Linux. Will this GDM help me? how do I install? Thanks[/QUOTE]

after you're logged in, try typing the things I mentioned:

sudo /etc/init.d/gdm start

(or like i said it might be.... sudo /etc/init.d/gdm restart) 

see if that does anything.

---

### Post by gordong11 on 2006-02-10
[QUOTE=Mustard]There may have been some issue with your graphics card at the start and the installer might have failed to configure your display.  That would be my guess.  What graphics cards are you both using?[/QUOTE]

Ah!!! yes it did not ask me for the resolutions my monitor supports. This cant be normal. I;m running built in ATI, from my MSI- RS482M-IL mobo.

Will I have to re-install? See I tried install earlier, and it asked me for resolutions...but I pressed enter by mistake, on the highest resolution you can opt for, so I re-installed.....but it never asked me for a resolution when I re-installed. Hmmm...I bet I need to re-install again 8(...any ideas?

I'll try your sudo command firest though.

---

### Post by dcast on 2006-02-10
sudo dpkg-reconfigure xserver-org

---

### Post by Mustard on 2006-02-10
[QUOTE=dcast]sudo dpkg-reconfigure xserver-org[/QUOTE]

Entering the above command will go through a configuration dialog for your display, among other things.  Choose the default answers for anything you don't know what the answer is to.  If 'ati' doesn't work for any reason, I would try configuring with 'vesa' drivers.  ATI has pretty patchy support for linux, so there are often problems with installing ubuntu on systems using ATI graphics.

---

### Post by vt8 on 2006-02-10
I typed startx and got file not found.

I typed sudo /etc/init.d/gdm start and sudo /etc/init.d/gdm restart it asked me for a password after entering reponded file not found.

I typed sudo dpkg-reconfigure xserver-org and got xserver is not installed.

I also hav a ATI graphics card -asus ati radeon x300

all this worked ok in last version.
where from here?

---

### Post by Mustard on 2006-02-10
[QUOTE=vt8]I typed startx and got file not found.

I typed sudo /etc/init.d/gdm start and sudo /etc/init.d/gdm restart it asked me for a password after entering reponded file not found.

I typed sudo dpkg-reconfigure xserver-org and got xserver is not installed.

I also hav a ATI graphics card -asus ati radeon x300

all this worked ok in last version.
where from here?[/QUOTE]

It sounds like gnome wasnt even installed! :)

I would try this (assuming you have an active internet connection, if not it might prompt for the install CD)....

```
sudo apt-get install ubuntu-desktop
```

This should finish the installation of all the relevant packages to get gnome up and running.

---

### Post by vt8 on 2006-02-11
thankyou mustard and others,
install all files then typed startx all worked ok, I got a great surprise when i was told new updates were available meaning it recognised my network card and put me straight on the net, this has never happenened in the past so this is the first time on the net using linux, 
thanks again!!!!!!!!!!!!!!!

---

### Post by bluevoodoo1 on 2006-02-11
[QUOTE=vt8]thankyou mustard and others,
install all files then typed startx all worked ok, I got a great surprise when i was told new updates were available meaning it recognised my network card and put me straight on the net, this has never happenened in the past so this is the first time on the net using linux, 
thanks again!!!!!!!!!!!!!!![/QUOTE]

Good good!!

---

### Post by gordong11 on 2006-02-11
[QUOTE=Mustard]Entering the above command will go through a configuration dialog for your display, among other things.  Choose the default answers for anything you don't know what the answer is to.  If 'ati' doesn't work for any reason, I would try configuring with 'vesa' drivers.  ATI has pretty patchy support for linux, so there are often problems with installing ubuntu on systems using ATI graphics.[/QUOTE]


I have tried this and I get XServer-Xorg not installed, not found error. How weird. Please HElp! LOL

Maybe re-install.....or is it because when I boot X-Server is being exited because of an error? Thanks

I also tried Suo Apt-get install ubuntu-desktop...but I got already exists, no upgrade needed, or something similar.

I'm trying a re-install.

---

### Post by Mustard on 2006-02-11
[QUOTE=gordong11]I have tried this and I get XServer-Xorg not installed, not found error. How weird. Please HElp! LOL

Maybe re-install.....or is it because when I boot X-Server is being exited because of an error? Thanks

I also tried Suo Apt-get install ubuntu-desktop...but I got already exists, no upgrade needed, or something similar.

I'm trying a re-install.[/QUOTE]

Those two messages are a bit confusing really.  If you have installed ubuntu-desktop, then xserver-xorg should be installed too.  My first thought would be maybe you typed the command in incorrectly, so I would try it again typing it out exactly as you see below.  Better yet just copy and paste it directly to your command line....

```
sudo dpkg-reconfigure xserver-xorg
```

If that still comes up with an error, then I'll need you to paste the exact error message you receive (including the command you entered), into this thread and try to find some clues in the error message to determine how to proceed.

-edit-

Just a thought...what version of ubuntu are you installing?  Does the CD say 5.10 or 5.04?

---

### Post by gordong11 on 2006-02-11
Thanks,

I finally got it to install. I used the OEM mode, and then the dpkg-reconfigure and changed the settings to VESA. The only thing was it guided me through a series of questions I was not prepared for. Like amount of memory, keyboard and other things. For my video memory, it is ATI onboard my mobo...so I chose 64 magabytes of my system 512, I have no plans to game....so I was conservative...i hope not too much, is there a way to alter it? 

Also, it again asked to choose resolutions, the bottom 3 were already chosen for me and I could not figure how to choose other resolutions. Can anyone tell me? ie *, but asterick did not work for me.

Also I'm having issues playing DVD+R videos I have burned on my other machine. I cant seem to get it to work

---

### Post by Mustard on 2006-02-11
Now that you have it all up and running there are probably a ton of questions you will have. :)

The asterisk thing (*) can be selected usually by using the **tab key** to go to selection you want to make, and the **space bar** toggles the asterisk on and off, if I recall correctly.

There is a little bit of configuring to do before the system will be up an running the way you like it.  I would suggest you look over this links below, as many of the questions you might have will be answered there...
[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)
[http://help.ubuntu.com/starterguide/C/index.html](http://help.ubuntu.com/starterguide/C/index.html)

Specifically with regard to DVD playback, you might need to look at this link below, which covers many proprietory formats that can't be included in Ubuntu by default, as they have restrictive licences...
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

If you have any problems these forums are a good place to find answers.  Also there is an IRC support channel.  Instructions for IRC are below if you need them...

The X-Chat client is installed by default in Ubuntu and can be found in the Applications>Accessories>Internet menu.

When you open the X-Chat client you will be presented with a choice of servers to join.  Select the 'Ubuntu Servers' and then press the 'Connect' button.  X-Chat will automatically join the #ubuntu support channel on the irc server irc.freenode.net .

---

