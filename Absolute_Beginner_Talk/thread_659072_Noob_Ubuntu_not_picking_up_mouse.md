---
title: "Noob: Ubuntu not picking up mouse"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by glaurens on 2008-01-05
Hi,

Completely new to ubuntu and my problem is that it installed without a problem, except that it doesn't pickup my USB mouse. This obviously makes it very difficult to navigate since I don't know the correct control keys, etc.

Could anybody please tell me how to fix the problem with the mouse, and then also the control keys to actually navigate to be able to fix the problem with my mouse.

Tx

G

---

### Post by master_kernel on 2008-01-05
1) Check the connectiion -- are you sure it works with any other computer?
2) If the above is not the problem, what brand is the mouse

---

### Post by glaurens on 2008-01-05
MS compact optical mouse model 1016? Please don't tell me MS is the problem?

---

### Post by spydon on 2008-01-05
> **glaurens said:**
> MS compact optical mouse model 1016? Please don't tell me MS is the problem?

Can you press alt+F2 and write gnome-terminal and then write lsusb in the terminal and see if it shows up there...

---

### Post by glaurens on 2008-01-05
It shows 3 lines:

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

I don't even know what this means?

---

### Post by gmjs on 2008-01-05
Hi,

This is quite strange.  I've never seen a mouse not work at all under Ubuntu.  You have installed Ubuntu natively haven't you?  I know that the mouse does not work 'out of the box' if running Ubuntu and other Linux distros under Microsoft Virtual PC.

Excellent advise from spydon: is the mouse listed when you type **lsusb** at a command line prompt?  I'm quite interested why it isn't working myself!

Another small clue to help solve the problem - does it 'light up' when you connect it to the PC?  If not, I'm stuck.  If it does and the mouse cursor just does not move, I may have a suggestion.

Thanks,

Graham

---

### Post by gmjs on 2008-01-05
> **glaurens said:**
> It shows 3 lines:

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000



This just means that the system has found 3 USB ports.  The ID 0000:0000 means there is nothing connected to any of them.  Do you not have a USB keyboard then?!

Here's mine for a comparison:
[B]
Bus 005 Device 003: ID 054c:0174 Sony Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 045e:0053 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
[/B]

---

### Post by glaurens on 2008-01-05
The mouse doesn't light up, even though I've tried it in a number of different ports, and rebooting in-between. Ubuntu is installed natively and I'm using a PS2 keyboard, i.e. the reason it is not listed.

Will also try the USB to PS2 connector now, if I can find it somewhere.

---

### Post by glaurens on 2008-01-05
Well, the USB to PS2 connector worked, but purely the fact that ubuntu only picked 3 USD ports up, concerns me since there should be 7?

In any case, thanks for the help.

---

### Post by gmjs on 2008-01-05
Different!  There is one last thing you could try.  If you type the following at a command line:

**lsmod | grep hid**

and find that it displays a **0** next to **hid** then it may be worth trying the following with the USB interface mouse plugged in:

**sudo modprobe hid**

**sudo modprobe usbhid**

Otherwise I'm stuck!  Hopefully there's someone a lot better at this than me who knows!

Good luck,

Graham

---

### Post by glaurens on 2008-01-05
I assume that by command line you mean gnome-terminal?

I did the lsmod | grep hid and the result was absolutely nothing, and I only got new prompt line.

I executed the two sudo lines, entered my password during the first one, but nothing happened.

Very interesting thing though, when I plug the mouse into a USB port now, after using the PS2 adaptor, it lights up, but doesn't move!!

---

### Post by gmjs on 2008-01-05
Some progress then - does **lsmod | grep hid** display something now?

If you're feeling brave ;) you can try reconfiguring XServer (the graphics side of things) to see if that  gets the mouse to work.  The mouse is very much incorporated into the graphics server under Linux.

Just a word of warning - it can stop the graphical interface from working if something does go wrong, but it's completely reversible as long as you back up the current settings first (see below).

[SIZE="3"]**Backing Up the Current Graphics Settings**[/SIZE]

Open a terminal window (yes - gnome-terminal will do just fine [Applications > Accessories > Terminal) and enter the following to create a copy of the current graphics server settings:

```
**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup**
```

[SIZE="3"]**Reconfigure XServer**[/SIZE]

Reconfigure XServer by entering the following at the prompt:

```
**sudo dpkg-reconfigure xserver-xorg**
```

You will be asked to enter your password before the system will let you run the command.

During the setup, you should be able to go with all the default values by pressing the Enter and TAB keys.

At the **Mouse Port** screen, mine defaults to **/dev/input/mice** and is working fine so select that option if it is not the default and if it is available.

Make sure you select the screen resolutions that your monitor can cope with when the option appears towards the end of the setup (I've selected 1280x1024, 1024x768, 800x600 and 640x480).

When asked to choose a **method for selecting monitor characteristics**, I'd select **Medium** and choose your desired resolution and refresh rate (60Hz for an LCD or TFT screen).

Now press **Ctrl+Alt+Backspace** to restart XServer.  Hopefully (he says) you should be returned to your Ubuntu Login Screen and the mouse should work too.

[SIZE="3"]**No - It Broke**[/SIZE]

If not and Ubuntu tries to display GNOME three times and fails, you may see a blue screen with a white message box and seemingly corrupt text characters.  DO NOT PANIC!  All can be restored.  Choose **No** at all the prompts and press Ctrl+Alt+F2 to open a new tty.  Enter your username and password as you would when logging into the graphical interface.

Enter the following commands (the first one deletes the incorrect settings file and the second one replaces it with the old one):

```
[B]sudo rm /etc/X11/xorg.conf
sudo mv /etc/X11/xorg.backup /etc/X11/xorg.conf[/B]
```

To test, enter the following to restart XServer and (hopefully) GNOME:

```
**startx**
```

It should work beautifully though if you do ever try it.  To be honest, the PS2 converter sounds easier!

I'm very disappointed that the mouse doesn't just work for you.  It should.  I can supply screenshots of the 'Reconfigure XServer' part if you want to do it but would prefer more help.  Otherwise I won't!  I've spent way too long on here today!

Graham

---

### Post by gmjs on 2008-01-05
P.S.

> **glaurens said:**
> I did the lsmod | grep hid and the result was absolutely nothing, and I only got new prompt line.

If Human Interface Devices (namely USB mice and keyboards etc) are functioning correctly, the output from this command should be similar to this:

```
[B]
usbhid                 26592  0 
hid                    27392  1 usbhid
usbcore               134280  6 usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
[/B]
```

---

### Post by glaurens on 2008-01-05
I think it is now official, my pc was definitely struck by lightning (about 4 weeks ago) since it behaves extremely erratically. Sometimes it won't switch on, then it will switches on but doesn't make it past the first beep, or won't go past the IDE detection screen, or boot into ubuntu and for no reason just hang with a blank screen and not being able to be turned off. 

There are other symptoms as well, but I think you get the idea, and obviously the mouse is part of the same problem.

Thanks for the help

---

### Post by williamirvine67 on 2008-04-27
i kinda have the same problem when i use a live cd. i have a ps/2 mouse and keyboard, but ubuntu dosent pick up either of those (light does shine in keyboard though). its really annoying. i want to use ubuntu but i cant even get the mouse to click install, (on desktop screen not ubuntu boot screen). if anyone has an idea on how to help me it would be awesome

---

