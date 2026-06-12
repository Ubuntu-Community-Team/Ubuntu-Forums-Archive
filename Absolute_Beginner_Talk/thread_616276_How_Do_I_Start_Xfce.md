---
title: "How Do I Start Xfce?"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by HandyAndyShortStack on 2007-11-18
After a _harrowing_ installation battle between xubuntu feisty and my powerbook g3, I managed to get what appears to be an intact install of xubuntu 7.04 on my hard disk.  Yaboot works fine, but when ubuntu boots, all I can get is a command prompt.  I tried to run startx, but Mister Bash insists over and over again that that such a command cannot be found.  I can navigate through the filesystem and run some programs, but I'm a noob and I need pretty windows and buttons to get anything done.  Is there a way I can get this thing to work without reinstalling?  Any help or encouragement would be appreciated!

---

### Post by PmDematagoda on 2007-11-18
Do these in a terminal:-
```

sudo aptitude install xserver-xorg-core

```
and then

```
sudo aptitude install xubuntu-desktop
```
post any messages or errors you get, if you don't, then do:-

```
sudo startx
```

And see if your problem is solved.

---

### Post by HandyAndyShortStack on 2007-11-18
Well, Aptitude seems to work fine, but probably due to my powerbook's lack of internet connection, the packages you mentioned won't install.  I forsee three possible solutions for this problem: 

1.  I could try to establish an internet connection.  I use a zydas usb dongle hat doesn't get along well w/ xubuntu feisty's default network manager, though I have used wicd w/ it sucessfully.  I would need to install a network manager that I could run in the terminal.  

2.  If they are on my install cd, I could configure aptitude to use the cd as a repository.  I would need help getting it to do that.  

3.  Maybe I could get the packages in .deb form and transfer them to the powerbook w/ a usb dongle?

Would any of these work? :confused: I sure hope so

I'ma work on #1 for the time being

---

### Post by anewguy on 2007-11-18
What happens if you type:

sudo /etc/X11/X     (the password it wants will be your logon password)

---

### Post by mali2297 on 2007-11-18
> **HandyAndyShortStack said:**
> 
2.  If they are on my install cd, I could configure aptitude to use the cd as a repository.  I would need help getting it to do that.  


I think you need the alternate CD for that. If you have that, then check the file  **/etc/apt/sources.list**.  Open it in the editor nano (the option -B means that it will make a backup):
```

sudo nano -B /etc/apt/sources.list 

```
There should be a line like this:
```

# deb cdrom:[Xubuntu 7.04 _Feisty Fawn_ - Release powerpc (20070415)]/ feisty main restricted

```
Remove # in front of the line, if there is one. Save (ctrl-o) and quit (ctrl-x).
Next, make sure that you have the CD inserted and run from the command line:
```

mount -rv /media/cdrom
sudo apt-get update
sudo apt-get install xubuntu-desktop
sudo dpkg-reconfigure xserver-xorg

```
If everything works out alright, then you should be able to start Xfce with
```

startxfce4

```

> 
3. Maybe I could get the packages in .deb form and transfer them to the powerbook w/ a usb dongle?

This I think would be complicated as there are a lot of dependencies. It is easier to download and burn [the alternate CD]("http://cdimage.ubuntu.com/xubuntu/ports/releases/7.04/release/").

---

### Post by HandyAndyShortStack on 2007-11-18
anweguy -command not found

---

### Post by HandyAndyShortStack on 2007-11-18
Thanks mali, I already am using the alternate cd -i don't have enough ram to run the regular cd.  I don't appear to have nano and vim is either very hard to use in a terminal or I need to learn more about it -keys don't serve intuitive functions.  I'll fiddle around with it for a half hour or so and post how I do.

If this is my only option for text editing and it is broken, perhaps this install is using me more than I am using it.  In other words, back to the battle!  I am probably going to have to replace or clean my cd drive, as it requires a lot of coaxing to read every piece of the install cd without failing during the kernel or yaboot install.  Oy.

---

### Post by Dr Small on 2007-11-18
To start xfce as a session, run:
```
xfce4-session
```

---

### Post by mali2297 on 2007-11-18
> **HandyAndyShortStack said:**
> Thanks mali, I already am using the alternate cd -i don't have enough ram to run the regular cd.  I don't appear to have nano and vim is either very hard to use in a terminal or I need to learn more about it -keys don't serve intuitive functions.  I'll fiddle around with it for a half hour or so and post how I do.

If this is my only option for text editing and it is broken, perhaps this install is using me more than I am using it.  In other words, back to the battle!  I am probably going to have to replace or clean my cd drive, as it requires a lot of coaxing to read every piece of the install cd without failing during the kernel or yaboot install.  Oy.

Yeah, if nano is missing then you haven't got even a minimal (x)ubuntu. Who knows what else might be missing!? A new clean install is advisable.

---

### Post by HandyAndyShortStack on 2007-11-18
well, I managed to get a working internet connection up from the terminal!  I am so proud of myself.  I can ping google and ubuntu.com sucessfully and install packages if i select them from inside aptitude, but there is neither a package called xorg-core or xubuntu desktop in there.  Is there a way i can repair my system over the network?  Reinstalls are extremely risky w/ this machine!

---

### Post by maybeway36 on 2007-11-18
Make sure the main repository in sources.list is not commented out.
Then do a sudo apt-get update.

---

### Post by mali2297 on 2007-11-19
> **HandyAndyShortStack said:**
> Is there a way i can repair my system over the network?

There is probably some way...:-k

But I think it would be easier for you to learn some basic vi editing.  Find a tutorial, for example:
[http://www.washington.edu/computing/unix/vi.html](http://www.washington.edu/computing/unix/vi.html)

Useful commands in vi:
[COLOR="Orange"]
h  = move left
j   = move down
k  = move up
l   = move right

i       =  enter insert mode
ESC   = leave insert mode

ZZ     = save and quit
:q!    = quit without saving
[/color]

Then have a look at your sources.list:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup 
sudo vi /etc/apt/sources.list

```

---

