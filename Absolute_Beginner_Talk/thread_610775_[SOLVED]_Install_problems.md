---
title: "[SOLVED] Install problems"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Ebrutus on 2007-11-12
I'm sure that someone has posted with this exact same problem, but 

here is my story.

I have a spare computer that was donated to me, older Athlon 700 

maybe, with really bad virus problems.  So I figure I will be 

crazy and install Ubuntu on it, just to learn it.

I reformatted it, using old dos 6.22, just to get the hard drive 

clean.

Downloaded 7.1 iso, and burned the image to CD.  It would hang up 

at the same point on the splash screen. (The progress bar would 

stop moving).  So I moved on to the 7.1 alternative text installer 

(I chose the 1024x768 resolution during setup).  It installed ok 

and then I would reboot with the newly installed system, and my 

monitor would lose its signal, LEDs started blinking.  The best 

way that I can describe it is when you pick an improper video 

resolution, and your monitor displays nothing, or shuts down.

What are my next steps:

A. Keep reinstalling trying all the possible resolutions? (a bit 

much)

B. Try installing 6.06 (I have the same video problem with that 

one too, monitor goes black)


I have been able to boot up from the CD with 6.06 but I get 

640x480 resolution, and I cannot see the whole screen.  I would 

install from that desktop, but since I cannot see the whole 

screen, I cannot click on all the buttons.

Thanks in advance for your help.  I hope one day to be an Ubuntu fanatic!  It's not going so well right now though...

---

### Post by taurus on 2007-11-12
What's the spec of that old machine?  Instead of using Gnome, maybe you should consider using Xubuntu instead since XFce4 window manager is for an older machine with less RAM.

[http://www.xubuntu.org](http://www.xubuntu.org)

---

### Post by Ebrutus on 2007-11-12
Taurus,

Thanks, that's great advice.  I'll get right on it!!!!

I don' t know my machine specs right off the bat, but I'll check.  Xubuntu sounds like a great match for it though.:guitar:

---

### Post by taurus on 2007-11-12
Fluxbuntu is another option if you want to use fluxbox window manager instead of XFce4.

[http://www.fluxbuntu.org](http://www.fluxbuntu.org)

---

### Post by anemptygun on 2007-11-12
Even though xubuntu is lighter than gnome it is still not very light. I would recommend some other desktop environments over xfce, such as fluxbox (fluxbuntu).

Also maybe try this..

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

:)

---

### Post by anemptygun on 2007-11-12
asdasdasdfgdftgre

---

### Post by anemptygun on 2007-11-12
^ I was too slow for taurus ...  :P

---

### Post by Ebrutus on 2007-11-13
Ok, I'm back...

Tried Xubuntu, same results.

Desktop version, hangs on install splash screen

Alternate version, lets me install, screen blacks out in first boot up.

My machine is an AMD K62-500 with about 196MB memory.  I'll have to open up the box to get my 

video info, unless I can just boot up with the CD and get it through the Ubuntu desktop.

I can try the Fluxbuntu... does that use a different graphical setup?

It seems that the general Ubuntu architecture is conflicting with my monitor, or video card.  Also 

it seems strange that I can boot from the CD, and get into the introductory Ubuntu desktop, with 

no video problems.
:confused:
Any thoughts?

I will try Fluxbuntu tonight though, and hopefully report back tomorrow.

Thanks again!

---

### Post by taurus on 2007-11-13
Just reconfigure X again.  Press <Ctrl><Alt>F2 to get to a console.  Log in and run

```
sudo dpkg-reconfigure xserver-xorg
```
Then, press <Atl>F7 to get back to the original GUI login screen.  Now, restart X with <Ctrl><Alt>Backspace.

---

### Post by mummra1 on 2007-11-13
There was a problem in 7.1 with the usplash.conf file.  Take a look at /etc/usplash.conf

Check the resolution.  It should say...

```
xres=1024
yres=768
```

```
Then do an update-initramfs -u -k 'uname -r'
```

Then reboot and you should be set!

---

### Post by Ebrutus on 2007-11-13
Taurus,

Sorry, I'm too much of a noob to understand that.  At what point do I input that code?

---

### Post by taurus on 2007-11-13
Wait for it to finish booting.  Otherwise, you can boot into recovery mode from GRUB menu and reconfigure your X there if you choose.

```
dpkg-reconfigure xserver-xorg
```
If you're not sure about a question, just take the default.  However, you should ise **vesa** driver for your graphic card for now until you get X up and running.  Then, install the right driver for your graphic card, whatever that might be.

Once you are done configured it, reboot.

```
shutdown -r now
```

---

### Post by Ebrutus on 2007-11-13
Ok, I'll try that... thanks...

Once I get some of this set up, will I be able to try the regular Ubuntu again....

I assume that when I rewrite the partition, all will be lost and have to reconfigure?

I should have changed my handle to noob, but it's probably already taken:)

---

### Post by Ebrutus on 2007-11-13
mummra1,

How exactly do you view that file that you were telling me to look at?  Just through the GUI introductory screen?  I have about 5 minutes if experience with that user interface.

---

### Post by mummra1 on 2007-11-13
Which version of Ubuntu are you running now?  If you are on Ubuntu, you would want to use gedit

```
sudo gedit /etc/usplash.conf
```

...this will open up a text-editing program so you can see the file.  Otherwise you can use vi editor if you know the commands...

I'm not sure what text editor xubunutu uses...

---

### Post by taurus on 2007-11-13
> **mummra1 said:**
> Which version of Ubuntu are you running now?  If you are on Ubuntu, you would want to use gedit

```
sudo gedit /etc/usplash.conf
```

...this will open up a text-editing program so you can see the file.  Otherwise you can use vi editor if you know the commands...

I'm not sure what text editor xubunutu uses...

mousepad for XFce4 and please use gksudo if you need to use gedit.

---

### Post by Ebrutus on 2007-11-13
so I can type :

gksudo gedit /etc/usplash.conf

and I will be able to edit... 

does that mean that you can use mousepad, or gedit with xubuntu?

---

### Post by Ebrutus on 2007-11-13
do you know of a free absolute knuckleheads guide to xubuntu, or ubuntu?

I'm so stupid that I had to read "chicken soup for dummies":>

---

### Post by CatKiller on 2007-11-13
> **Ebrutus said:**
> Downloaded 7.1 iso, and burned the image to CD.  It would hang up
at the same point on the splash screen. (The progress bar would stop moving).

The desktop cd needs 256 MB of RAM to get into the live cd environment, in case you were wondering why this bit happened.

Graphics problems can be the most disheartening for new users. Hang in there! You do actually have a fully functional computer at your fingertips. Just to reiterate, you can get to a text-based interface by pressing **Ctrl-Alt-F2**. You should be able to log in here using the user-name and password you chose during the install process. You can then enter the command ```
sudo dpkg-reconfigure xserver-xorg
``` to enter a text-based configuration tool for the graphics. The **vesa** driver is low on performance but high on compatibility - most graphics cards will have a VESA mode that you can use. Once that's going, you can use a more user-friendly tool to configure the graphics for what you actually have in that computer.

For reference, all configuration settings for your user are kept in your Home folder. If, when you install Ubuntu, you create a separate partition for the Home folders of your users, you can re-install or change the operating system and leave all the settings intact just by preserving that partition.

Good luck!

---

### Post by Ebrutus on 2007-11-14
Catkiller,

Thanks for the advice.  I was able to set up the "vesa" driver last night.  When I do that I get the 640x480, but I can boot up from the hard drive (xubuntu).

Now that I'm this far, do I need to pull my computer apart, and look at the video card to determine it's specs?

The auto diagnostics in (sudo dpkg-reconfigure xserver-xorg) detected that I needed the "S3" driver, but it was wrong.  That driver doesn't work properly.

I did figure out that when my monitor is blinking because of improper video driver, I can "Ctrl-Alt-F2" and it will throw me into code entry mode.

So, I'm getting closer, just need to get to 1024x768 and I'll be happy for the moment.  I'll be back for more questions, rest assured.

btw ... what does (sudo dpkg-reconfigure xserver-xorg) mean

I can understand reconfigure xserver, that makes sense... what about the rest of it.  I just want to know, so that I can possibly understand the broader concept of ubuntu.

Thanks,
Brett

---

### Post by dstew on 2007-11-14
Ebrutus:

In regard to your previous request for basic Ubuntu information, it might be best to get the basic *Linux* information first. Then you will understand Ubuntu better. Go to [http://www.linux.org/](http://www.linux.org/) and click on the Courses button. There is a beginner's tutorial that is very good. It really helped me get oriented to the Linux/Ubuntu world. There are also good descriptions of distributions, of which Ubuntu is only one. There are several hundred Linux distributions available. But they all run Linux at the core, so if you understand Linux, you can better understand any given distribution.

**sudo dpkg-reconfigure xserver-xorg** is a command that will runs the program **dpkg-reconfigure** ("Debian package reconfigure") using the program **sudo** ("superuser do")  that gives you temporary administrative privleges. The target of the command is **xserver-xorg** which is the name of a Debian program package to reconfigure. This particular command will give you a bunch of questions to answer to set up your xserver display. Debian program packages are program bundles that are installed automatically using the **dpkg** series of commands. The Ubuntu distribution of Linux is based on Debian packages. The packages can be automatically downloaded and installed using the **apt-get** command, or using the graphical **synaptic** tool (which is a front end for apt-get).

You can find out information about linux commands by entering **man** ("manual", as in user's manual) on the command line, followed by the command name. For example, **man sudo** or **man dpkg-reconfigure**. You can also see these "man pages" on-line using Google.

---

### Post by CatKiller on 2007-11-14
> **Ebrutus said:**
> Now that I'm this far, do I need to pull my computer apart, and look at the video card to determine it's specs?

```
lspci | grep VGA
``` will tell you what the graphics card thinks it is.

> The auto diagnostics in (sudo dpkg-reconfigure xserver-xorg) detected that I needed the "S3" driver, but it was wrong.  That driver doesn't work properly.

There is at least one type of S3 integrated video that people seem to have a bit of trouble with. I don't have any experience of them though, I'm afraid.

> btw ... what does (sudo dpkg-reconfigure xserver-xorg) mean

What dstew said :)

---

### Post by Ebrutus on 2007-11-14
Ok, I have xubuntu installed

I tried to type:

gksudo gedit /etc/usplash.conf

and it will not let me edit it.  it says cannot edit display.  I cannot edit it in the GUI desktop because it says it is read only.

What do I do?

I cannot change the resolution for my life!!

---

### Post by ntu on 2007-11-15
I did 
gksudo gedit /etc/usplash.conf
in the terminal and it opened the gedit window in usplash conf. I can edit it and there is a button above to let me save changes (I did not save my changes).

---

### Post by Ebrutus on 2007-11-15
Ok, I got the resolution set by using the nano editor (1024x768).  Then I am supposed to update the splash something or other, what is that command line supposed to be?

1) Change the resolution in /etc/usplash.conf to 1024x768
2) Add vga=791 to the kernel line in /boot/grub/menu.lst
3) sudo update-initramfs -u -k `uname -r`

or should I do this splash fix?

Quote:
Originally Posted by orange2k  
I found a solution that worked for me on kubuntuforums:

(before I did what follows, I used StartupManager to set the boot-splash resolution to 1024x768 16-bit)

edit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

edit /etc/modprobe.d/blacklist-framebuffer
comment out the following (prefix with #)

blacklist vesafb
blacklist vga16fb

last but not least, run the following in a terminal

sudo update-initramfs -u

---

