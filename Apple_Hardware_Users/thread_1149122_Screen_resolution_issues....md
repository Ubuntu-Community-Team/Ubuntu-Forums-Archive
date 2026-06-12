---
title: "Screen resolution issues..."
date: 2009-05-04
forum: Apple Hardware Users
---

### Post by jtbrookreson on 2009-05-04
I just installed Xubuntu 9.04 on an G3 iBook 500 256 RAM, and everything seems to be working well, except my screen resolution is stuck on 800x600. How can I adjust that?

I am a linux idiot, so if you can walk me through it, I will be very grateful.

-JTB

---

### Post by RedSingularity on 2009-05-04
Have you installed the graphics driver?

---

### Post by jtbrookreson on 2009-05-04
Uhm...no?
And how would I do that?

---

### Post by RedSingularity on 2009-05-04
System>admin>hardware drivers

Should be in there to activate.

---

### Post by jtbrookreson on 2009-05-04
No drivers to install...

---

### Post by RedSingularity on 2009-05-04
What graphics card do you have?  Type "lspci" in terminal  and post the output.

---

### Post by jtbrookreson on 2009-05-05
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea PCI
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Pangea Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Pangea USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Pangea USB
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea Internal PCI
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth/Pangea FireWire
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth/Pangea GMAC (Sun GEM)

---

### Post by RedSingularity on 2009-05-05
Oh its a MAC?  Which OS version you running?  10.4, 10.3???

---

### Post by jtbrookreson on 2009-05-05
I am living a microsoft/apple free life.

I only have Xubuntu 9.04. Erased everything else.

---

### Post by RedSingularity on 2009-05-05
Lol good to hear.......64 bit or 32 bit?

---

### Post by RedSingularity on 2009-05-05
Oh nevermind.....it seems that many people have had this problem.  Looks like ubuntu versions and that graphics card dont get along well.  I dont see a fix either.  If you want linux on that have you considered a different distro?

---

### Post by jtbrookreson on 2009-05-05
uhm..... yes?

its a 500 mhz 256 RAM G3 iBook... 40 gig HD.

For about a year I have been using Ubuntu 6.06...monkeyed with Kubuntu, and Xubuntu... I decieded to upgrade to Xubuntu 9.04. during the online update to 8.04 (need to do that before I move up to 9.04), she totally crashed. I had to burn an install CD at work, installed it today...and here I am...

---

### Post by RedSingularity on 2009-05-05
Which install CD did you burn?  9.04?

---

### Post by cyberdork33 on 2009-05-05
this is an issue with the powerpc version of ubuntu. there have been a few similar threads here in the Apple users forum recently.

This one might help:
[http://ubuntuforums.org/showthread.php?t=1114297](http://ubuntuforums.org/showthread.php?t=1114297)

Good Luck

---

### Post by jtbrookreson on 2009-05-14
ok...after a week of drama with 9.04, 6.06, and finally back to 9.04....

So here I am, with a print out of the thread posted above (thank you). I loged onto terminal, followed the commands and after getting into the nano editor, I really have no idea what to do. I had a blank screen. Do I type in all that code? is there a way to open the code and just edit what needs to be edited? And then after that, how do I save it?

I understand the theory, its the execution that is killing me. I am a total noob that is learning that a litttle bit of knowledge is a very dangerous thing.

Thanks in advance....

-JTB

---

### Post by roym4 on 2009-05-14
While you could just type in all the info into an xorg.conf file it may be easier to generate an xorg.conf file to edit before you go in and make changes. 
You can do this by executing sudo dpkg-reconfigure -phigh xserver-xorg from the command line and then sudo nano /etc/X11/xorg.conf to modify it

---

### Post by stream303 on 2009-05-14
> **jtbrookreson said:**
> I understand the theory, its the execution that is killing me. I am a total noob that is learning that a litttle bit of knowledge is a very dangerous thing.


#1 problem with Ubuntu is the splash screen.  Usually you get that right off the bat with just an immediate black screen with a blinking cursor in the upper left, or just totally bizarre colors.

How to fix:

At the second-stage yaboot boot: prompt, hit TAB to stop the automatic countdown.  Now we are going to tell the kernel to ignore the ubuntu splash screen with an additional parameter, "nosplash"

```
Linux nosplash
```
(That's a capital L)

In addition to the splash screen, some have a problem with the framebuffer, and need to add another kernel parameter, "ofonly".

Again, at the 2nd-stage yaboot boot: prompt, enter:

```
Linux nosplash video=ofonly
```

Ok, now this should at least get you to X and a graphical login.  However, even this is problematic at times because the Apple hardware doesn't play nice with any ppc distro's installer, and one must manually edit /etc/X11/xorg.conf.

(note - newer g4's and G5's sometimes don't have any problems at this stage - it all depends on the model)

If you can get a somewhat usable graphical desktop, the most universal way of editing xorg.conf is to fire up a terminal with root priveleges and start the nano text editor:

(It has to have root priveleges since /etc/X11/xorg.conf is a system file.  Note the Capital-X in X11)

```
sudo nano /etc/X11/xorg.conf
```

Make your edits.  Save the new file with CTRL-O.  Exit the nano editor with CTRL-X.  Now either logout and log back in, or reboot the machine.

IF the gui is not even workable at all, you can try the above editing with nano from a virtual terminal, by entering CTRL-ALT-F2.  This will bring up a virtual terminal from which you login, and then edit the file.

If things are really bad, you may have to do this by rebooting with the installation cd, going into *Linux single* or use the "rescue" option which will look like it is going to reinstall, but you will eventually be prompted where your root partition is located.  Drop into that, and then you can use the vi editor to make your changes.  Since you are already root, there is no need for "sudo" to precede your commands.

The secret is to scour the threads, wikis, and even the ppc thread archives to find a reference xorg.conf file.  Since things change over the years, these files may not work if they are just dropped in as-is, but crucial elements such as your horizontal and vertical frequencies should work since the hardware hasn't really changed over the years.

It can seem like a lot of work, but I wanted to be a bit more comprehensive about what you are jumping into.  But don't blame the Linux installers - most of the pain comes from the Apple hardware not being designed to talk to anything but OSX, nor are the Apple folk just sending hardware data our way to make the developer's lives any easier. :)

---

### Post by jtbrookreson on 2009-05-14
OK...

Thanks alot. This is valuable information. Right now I am at work reading this, but soon I will be on my way home to try it our. Sadly, this old iBook is the only machine I own, so when she is down, I am down. Regardless, I am determined to feed my inner geek and learn more about Linux and dabble as much as I can.

Thank you all very much. I will post my results.

-JTB

---

