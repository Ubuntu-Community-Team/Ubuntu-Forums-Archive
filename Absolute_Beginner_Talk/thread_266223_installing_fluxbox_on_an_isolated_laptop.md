---
title: "installing fluxbox on an isolated laptop"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by k94382 on 2006-09-27
So I want to install fluxbox on a laptop without any way to connect to the internet. I also have installed the server edition of ubuntu and now when I try to install fluxbox, the last line of installation tells me that I need Xorg. How do I install Xorg??? Do I download the source from their website and somehow compile and if so, how???

Thanks.

---

### Post by k94382 on 2006-09-27
Please help. How do you install Xorg or Xserver or whichever one you need without internet access??? I have internet access to another computer and could download stuff there.

---

### Post by Sef on 2006-09-27
Please have some patience.  Almost all questions are answered within 24 hours.  

Not sure if you could download and put it on a cd.  Check out doing that.  Not sure if it will work or not.

---

### Post by k94382 on 2006-09-27
Hey, I'm just a little excited. I have downloaded it but haven't found anything about installing or compiling it.

---

### Post by k94382 on 2006-09-27
bump bump

---

### Post by bodhi.zazen on 2006-09-27
If you downloaded the .deb package:
```
sudo dpkg -i fluxbox.xyz.deb
```

To install x:```
sudo aptitude update
sudo aptitude install x-window-system-core
```

---

### Post by k94382 on 2006-09-27
Thanks, but remember that I don't have access to the internet where I want to install fluxbox.

---

### Post by bodhi.zazen on 2006-09-27
You will have to download the deb package and dependencies on another box and transfer them to your laptop.

[[color=blue]Fluxbox[/color]](http://packages.ubuntu.com/breezy/x11/fluxbox)

Download the fluxbox and dependencies and save them on a usb drive, CD-ROM, whatever.

Install with```
sudo dpkg -i package_name-xyz.deb
```

If they are all in 1 directory you can try ```
dpkg -i *.deb
```

Install each dependency. You may run into other dependencies..... ie dependency hell....

---

### Post by k94382 on 2006-09-27
Thanks again, but I'm already at that step. I plan on compiling fluxbox from source but the problem I have is that I NEED AN XSERVER or Xorg or something like that. How do I install that??? I was thinking of somehow adding that program to aptitude from a regular ubuntu CD. Any help???

---

### Post by bodhi.zazen on 2006-09-27
Perhaps this is what you seek?

[[color=blue]x-window-system-core[/color]](http://packages.ubuntulinux.org/edgy/x11/x-window-system-core)

If you are going to compile Fluxbox on the Laptop, you should also look into build-essential and checkinstall.

I'll leave the google search to your competent hands.

---

### Post by k94382 on 2006-09-27
Thanks, I managed to install build-essential by adding the repositories from the CD. I know that it works because I managed to install ndiswrapper with it but now I'm stuck and I just want to install fluxbox.

---

### Post by k94382 on 2006-09-27
Thanks a lot, hell has just started. It doesn't seem that bad once you get a spreadsheet done on what needs to be installed. Thanks again for helping me out again.

---

### Post by bodhi.zazen on 2006-09-27
> **k94382 said:**
> Thanks a lot, hell has just started. It doesn't seem that bad once you get a spreadsheet done on what needs to be installed. Thanks again for helping me out again.

:lol: =D>

No time like the present. I am envious, all that learning. There are few on Ubuntu who know hell like you.... :biggrin:

Let me know if you get stuck.

A spread sheet is a good idea. Keep it safe.

Also, if you are compiling, you will need those configuration files. Keep them organized somewhere.

I use ~/src with a separate directory in src for each proggie.

I'm sure you have a more efficient method, but just in case... :twisted:

---

### Post by k94382 on 2006-09-29
Just to test I've tried on another computer with internet and installed x-window-system-core via aptitude. I still get the same message when I type

> sudo ./configure

> configure: error: Fluxbox requires the X Window System libraries and headers

Any ideas and suggestions??

---

### Post by po0f on 2006-09-29
k94382,

Along with build-essential, you will also need all the relevant header files for any library you are going to be using in a program that is compiled from source.  I believe [this](http://packages.ubuntu.com/dapper/x11/xorg-dev) is the package you need.

---

### Post by k94382 on 2006-09-29
So after doing some searching, I've found out that I need xdevel. Where do I get that from??

---

### Post by bodhi.zazen on 2006-09-29
Working late are we ?

Follow poof's link. I'm not sure which, or possible all of those packages you will need.

> If you're going through hell
Keep on moving, Face that fire
Walk right through it
You might get out
Before the devil even knows you're there

When you are done with this round, I think there is more you will need.

You will just have to take it one error message at a time.

The learning.....

---

### Post by blackened on 2006-09-29
I'm by no means bashing compiling from source, but if you deem it such a huge pain, then why not save yourself from this hell of your own devising, and install the packaged version? Feel free to tell me to stfu or whatever. Just voicing (typing) my thoughts when I should actually be working on a paper.

---

### Post by k94382 on 2006-09-29
I read that the packaged version is outdated unless you mean downloading fluxbox for debian. Also, it can't be that bad to install from source from the things I've read.

---

### Post by k94382 on 2006-09-29
Thanks guys, xorg-dev did the trick. Now I'm stuck with

> sudo make

and that replies with

> command not found

I have installed build-essential.

---

### Post by k94382 on 2006-09-29
bump

---

### Post by k94382 on 2006-09-29
Never mind. For some reason it seems to be working now.

---

### Post by bodhi.zazen on 2006-09-29
Nice.

./configure and make do not need to be run with sudo...

make install or checkinstall both do, however....

Screenshot?

---

### Post by k94382 on 2006-09-29
Mh... this sucks. I managed to install it but when I type startx, the computer seems to load something but returns to CLI. When I type startfluxbox, it returns

> Couldn't connect to XServer

---

### Post by bodhi.zazen on 2006-09-29
Use the full path....

```
/usr/bin/startx /usr/bin/fluxbox
```

All 1 line.....

---

### Post by k94382 on 2006-09-30
Nope, doesn't seem to do the trick...

---

### Post by bodhi.zazen on 2006-09-30
Can you check a few things:

[list=number][*]Do you have a file .xintrc in your home directory?
[*]Output of *which startx*
[*]Output of *which fluxbox*
[*]Output of *which startfluxbox*
[*]What happens when you enter *X* as a command?[/list]

The last command, X, is a capital X and should give you a gray screen with a black X which moves with the mouse. To exit Ctrl-Alt-Backspace.

---

### Post by k94382 on 2006-09-30
Here goes

1. I read about it but no clue what it's about. My own directory doesn't display anything when I type "ls"
2. usr/bin/startx
3. usr/local/bin/fluxbox
4. usr/local/bin/startfluxbox
5. Yes, it works!

---

### Post by po0f on 2006-09-30
k94382,

If there is no ~/.xinitrc, type the following at a teminal:
```
$ echo "exec startfluxbox &" > ~/.xinitrc
```
and see if `startx` will work for you.

---

### Post by bodhi.zazen on 2006-09-30
> **k94382 said:**
> Here goes

1. I read about it but no clue what it's about. My own directory doesn't display anything when I type "ls"
2. usr/bin/startx
3. usr/local/bin/fluxbox
4. usr/local/bin/startfluxbox
5. Yes, it works!

Try```
startx /usr/local/bin/fluxbox
```

files that start with a "." are "hidden".

To list them ```
ls -a
```

Try ls -a and see if you have a .xinitrc and a .fluxbox

---

### Post by k94382 on 2006-09-30
I never understood this but what does "~/" stand for in ~/.xinitrc?

---

### Post by bodhi.zazen on 2006-09-30
> **k94382 said:**
> I never understood this but what does "~/" stand for in ~/.xinitrc?

~ is short hand for /home/user_name

---

### Post by k94382 on 2006-09-30
Dude, I love you.

> startx /usr/local/bin/fluxbox

That seemed to do the trick. Next questions. How do I get a terminal and do I alwasy have to type that command to get it going?

---

### Post by bodhi.zazen on 2006-09-30
```
cat .xinitrc
``` to see the contents of ~/.xinitrc and make sure you do not have two enteries for "exec startfluxbox &"

And the command in .xinitrc should read ```
# exec fluxbox
```

[list=number][*] No &
[*]It may not work if /usr/local/bin/ is not on your path.[/list]

There are several ways to fix this, but let's fire up Fluxbox first.

---

### Post by bodhi.zazen on 2006-09-30
> **k94382 said:**
> Dude, I love you.

That seemed to do the trick. Next questions. How do I get a terminal and do I alwasy have to type that command to get it going?

First follow the link in my signature "Configure Fluxbox (Fluxbuntu) for a how to's on Fluxbox (the fluxbuntu site, not Lou's).

Second, type this code:
```
echo alias flux="'startx /usr/local/bin/fluxbox'" >> ~/.bashrc
```
Note: That is a double quote followed by a single quote!
ie 'startx /usr/local/bin/fluxbox' enclosed by " on either side.

Log out, log back in, and type:```
flux
``` In the terminal!

---

### Post by k94382 on 2006-09-30
Fluxbox is up and running, I just don't seem to find the terminal. If it's xterm, it doesn't start.

---

### Post by bodhi.zazen on 2006-09-30
> **k94382 said:**
> Fluxbox is up and running, I just don't seem to find the terminal. If it's xterm, it doesn't start.

We need to edit your fluxbox menu.

What terminal do you have installed?

---

### Post by bodhi.zazen on 2006-09-30
Do you Yahoo? I'll fire up gaim, my yahoo name is bodhi.zazen.

---

### Post by k94382 on 2006-09-30
I do MSN.

---

### Post by bodhi.zazen on 2006-09-30
> **k94382 said:**
> I do MSN.

In that case, how do you want to configure fluxbox?

If you add my alias you can start with the command flux.

I can show you how to enable startx.

Or we can edit your path to include /usr/local/bin/

We can add a terminal to your menu.....

---

### Post by k94382 on 2006-09-30
Alright, I'll get Yahoo, but for now I gotta get some sleep. Nite and thanks again.

---

### Post by bodhi.zazen on 2006-09-30
Congradulations ! \\:D/

---

### Post by k94382 on 2006-10-01
I have added you now. My ID is k34869

---

