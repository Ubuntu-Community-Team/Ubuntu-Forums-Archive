---
title: "Trying to install to no avail"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by lauerm on 2006-03-31
I unfortunately have no idea what I am doing!  I burned a CD and booted my laptop with it - went through the install... and then it asks me for my username and password and i do that...
The screen looks like a dos screen with "login@compuerName:~$" and a flashing cursor.
What am I supposed to do here so that I get a GUI????
Thank you

---

### Post by Unicast on 2006-03-31
Try "startx" without the quotes.

---

### Post by lauerm on 2006-03-31
i typed "startx" at the prompt and it replied with:
xauth: creating new authority file /home/lauerm/.serverauth.6060
xauth: creating new authority file /home/lauerm/.Xauthrority
X: user not authroized to run the X server, aborting.
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.
lauerm@cybelle-laptop:~$

Now What ??

---

### Post by linear on 2006-03-31
If you are not booting directly into a gui, something is wrong with your install. Any error messages just before that command prompt?
 
(I believe the command to start Gnome would be **sudo /etc/init.d/gdm start**, anyway.)

---

### Post by johnnymac on 2006-03-31
Try....

sudo startx

If that doesn't work....do this:

dmesg

take the output of dmesg (last few lines) and copy it here

---

### Post by lauerm on 2006-03-31
when i boot, i get the pretty logo as it loads..
then it asks for my login and password...
it tells me my last login, that programs inculded are free and there is no warranty...
then i get username@computerName:~$

I tried startx and got nothing
I tried sudo startx and it asks for my password, and writes "
   xauth: creating new authority file /home/lauerm/.serverauth.6065
   X: warning; process set to priority -1 instead of requested priority 0
   giving up.
   xinit: Connection refused (errno 111): unable to connect to X server
   xinit: No such process (errno 3): Server error.
username@computerName:~$

so i tried dmesg and it scrolled alot of numbers and comments really fast and ended with the command prompt again.

now what?

---

### Post by lauerm on 2006-03-31
and i tried:
sudo /etc/init.d/gdm start
and got nothing

---

### Post by Princey on 2006-03-31
[QUOTE=lauerm]and i tried:
sudo /etc/init.d/gdm start
and got nothing[/QUOTE]

From what I've read it seems that you did a server install. Just being sure, when you put the CD in to install what did you do?

A. Press ENTER
B. Typed INSTALL then pressed ENTER

Which of the above method was it? Maybe that will help clarify as from what I gather neither desktop environment (gnome or kde) was installed. If your answer was A. above, I think the next step would be to type this:> sudo apt-get install gnome desktop

Let us know what happens.

---

### Post by lauerm on 2006-03-31
from my working desktop, i burned the iso file onto a cd
put it in my laptop, changed the bios to boot from cd and followed the instructions...

i just typed "sudo apt-get install gnome desktop"
it asks me for my password and writes:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem

so i typed that and it writes:
dpkg: requested operation requires superuser privilege

---

### Post by pbaehr on 2006-03-31
As a general rule any time something requires superuser privileges put "sudo" in front of it. (superuser do)

I don't know why dpkg isn't set up. I thought the install took care of that. It seems like something went horribly wrong with your install. Maybe it didn't complete?

---

### Post by lauerm on 2006-03-31
my friend on IM suggested:
sudo dpkg --configure -a
and it is setting up stuff now!!!
looks like we are rolling
thanks to everyone who posted :)

---

### Post by Princey on 2006-03-31
[QUOTE=lauerm]my friend on IM suggested:
sudo dpkg --configure -a
and it is setting up stuff now!!!
looks like we are rolling
thanks to everyone who posted :)[/QUOTE]

Great :D to hear it's rolling. Was about to tell you to type sudo infront of dpkg -- configure -a when I noticed someone beat me to it through IM to you. Welcome to the Ubuntu fold.

---

### Post by lauerm on 2006-03-31
I have been instructed by my IM friend to let you know that my laptop decided to take a nap during the set up process and that is why things weren't quite right...  (i neglected that detail in the beginning)...
thanks again everyone!

---

### Post by johnnymac on 2006-03-31
DOH!!

Yeah....probably should have turned that off through the bios while you were installing.  If your not able to get things running...my suggestion would be to disabled your hibernation stuff in the bios and do a re-install with the CD.

GL and welcome to ubuntu....

---

### Post by lauerm on 2006-03-31
okay friends...new development...
it went through the package set up and i got the command prompt, so i typed:
sudo apt-get install gnome desktop
and it writes: couldn't find package gnome

i think i am going to start over from the beginning (and turn off hibernation if i can)

---

### Post by johnnymac on 2006-03-31
if you can't...just baby sit it until you get to gdm login screen.  The entire base-install will only take like 30 mins.

---

### Post by lauerm on 2006-03-31
I have a GUI!!!  i don't know what to do with it yet, but it is there!!!!
thanks everyone!!

---

