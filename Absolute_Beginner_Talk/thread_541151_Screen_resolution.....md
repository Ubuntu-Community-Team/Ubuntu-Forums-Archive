---
title: "Screen resolution...."
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by computercontrolled on 2007-09-02
Hello to all, i just installed ubuntustudio, really looks amazing and works fine (well just take stoo much time to boot) anyway...i only have 3 creen resolutions available 1024 x 768 being the wider, but i would like to have more creen resolution the screen is too big for me. my videocard is ASUS N6200TC, i have no idea what to do....help please im a total linux noob

---

### Post by moma on 2007-09-02
Hello,

Start the command line application (gnome-terminal or konsole) from Applications -> Accessories -> Terminal menu.

0) First, take a backup of your existing /etc/X11/xorg.conf.  
Run these commands on the command line (CLI), but do not type the $. It just denotes the command prompt.
$  [COLOR="SeaGreen"]sudo cp --backup=t /etc/X11/{xorg.conf,xorg.conf.backup} [/COLOR]

1) Now study some details about your graphic card.
$ [COLOR="SeaGreen"]lspci | grep -i vga[/COLOR]

I think it will say ATI. Is ASUS N6200TC an ATI card?

2)  Now re-configure the (most important -p high ) display settings. Run the command 
$ [COLOR="SeaGreen"]sudo dpkg-reconfigure -phigh xserver-xorg[/COLOR]

In the first dialog select the driver:  
[COLOR="Navy"]**fglrx**[/COLOR] is the ATI's commercial driver.
[COLOR="Navy"]**nvidia**[/COLOR] is the NVIDIA's commercial driver.

{ I suppose you've also installed a proper driver package for your card. Look for the names in the Synaptic Package Manager and install the driver.  Or activate the driver via System-> Administration -> Restricted Driver Manager.  }

In the second dialog mark (by pressing spacebar, arrow and TAB-keys) the desired screen resolutions. Save the setings and

3) Restart the X (the X-server) by pressing CNTR + ALT + BACKSPACE keys and re-login.

4) Select screen resolution from the GNOME's  System -> Preferences -> Screen Resolution dialog.
----------------------------------------------

A short guide: 
Åpen [this guide...]("http://www.futuredesktop.org/") and browse to the step 6). Do as instructed.

---

### Post by papermoon on 2007-09-02
i have a similar problem but this isnt working for me :S

---

