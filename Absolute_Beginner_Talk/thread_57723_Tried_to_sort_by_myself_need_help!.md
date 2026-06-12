---
title: "Tried to sort by myself need help!"
date: 2005-08-17
forum: Absolute Beginner Talk
---

### Post by mit on 2005-08-17
Hi,

New to Linux and am prepared for the learning curve as I have only ever used Windows  [-X 
Installed Ubuntu no probs  :smile: 
On re-booting it stayed on configuring network devices and then said fatal error and loaded up to the desktop no probs. The problem is definately to do with the Centrino wireless set-up.
It is in Device manager but i don't know if it is causing a problem or I don't know how to ask it to search for availible networks.
I have installed the Ndiswrapper but stuck on part 3) call sudo....
from the link viewed [here](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)
Any advice on how to get the Centrino working would be very appreciated and worth a  virtual beer !  :)

---

### Post by az on 2005-08-17
If the driver is found on a cd, copy it's files somewhere, like in a folder on your desktop.

The the .inf file will be in
/home/mit/Desktop/foldername/file.inf

You can just cd into that directory 

cd Desktop
cd folder
ls
(that will list everyting)

and then do
sudo ndiswrapper -i filname.inf
(tab completion is when you type the first letter or two of the filename and press tab - the filenem will complete for you.  Fun!)

and do

---

### Post by Juergen on 2005-08-17
> I have installed the Ndiswrapper but stuck on part 3) call sudo....
Yo, we are not on Starship Enterprise... :-)
What they mean is: open a Terminal-Window and type this command.
Sudo changes to the administrator- (root-)account for just this one command and will ask for your **user**-password.

And the stuff azz tells you is also entered in a terminal.

---

### Post by mit on 2005-08-17
Thanks guy's will have a go now!

---

### Post by mit on 2005-08-17
Got the driver file for Linux from Intel and used the terminal but after typing in the command it asked for a password but it won't let me type anything in  :mad:

---

### Post by Juergen on 2005-08-17
It's just not displayed. Security...

---

### Post by mit on 2005-08-21
Thanks for the help guys. Am i right in saying that if the piece of hardware is listed in device manager it is a) being recognised by the kernel and b)the driver is loaded for it?

---

