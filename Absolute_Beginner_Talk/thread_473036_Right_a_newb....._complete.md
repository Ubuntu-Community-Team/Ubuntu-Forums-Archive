---
title: "Right a newb..... complete"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Duckmeister on 2007-06-13
Hey guys,

I installed Ubuntu tonight after being recommended it by several people. I know very very little about Linux and Ubuntu, and have come across my first problem.

Although the installation alongside my XP was easy, after logging in to the installed OS, when going to change the visual settings (System/preferences/desktopeffects), my screen just goes completely white and this does not change after a reboot.

The OS looks sweet but for me its not worth the upgrade if there is not the eye candy ;)

If you need the specs for my comp its an HP Pavillion dv5000 with a ATI X200m Gfx card (i know that there are issues with the ATI cards but when i looked in the thread for help it gave me code which i had no idea where to put).

Anyway would really appreciate some help :) Thanks in advance,

Dux

---

### Post by Duckmeister on 2007-06-13
*b.u.m.p*

---

### Post by wreti on 2007-06-13
Input code into the Terminal. Applications>Accessories>Terminal

---

### Post by w4ett on 2007-06-13
In your terminal type: sudo gedit /etc/X11/xorg.conf and copy/paste the output of that file here.

also the output of: glxinfo

and let's see what can be done.

---

### Post by Duckmeister on 2007-06-13
i copied and pasted it but when i did, it asked for a password.

Problem is I tried to enter the only password that i think it could be (my login password) but it wouldnt let me enter any text?

Thanks for help so far though guys :)

---

### Post by w4ett on 2007-06-13
the password is INVISIBLE....just type in your login P/W and press <enter>

---

### Post by wreti on 2007-06-13
As a security measure, the text doesn't show. Just type it in anyways and press enter.

---

### Post by Duckmeister on 2007-06-13
ah yes that stage seemed to work for the first part of the code, however the next part:

> # Update loaded modules.
Code:

sudo depmod -a



is a problem.

WHen i enter it it does nothing....

THis is what i get:

> alex@alex-laptop:~$ sudo depmod -a
alex@alex-laptop:~$ 
alex@alex-laptop:~$ sudo depmod -a
alex@alex-laptop:~$ 



ty

---

### Post by Mazza558 on 2007-06-13
> **Duckmeister said:**
> ah yes that stage seemed to work for the first part of the code, however the next part:



is a problem.

WHen i enter it it does nothing....

THis is what i get:



ty

Yup, that means the command has completed. No errors is good news, in this case.

---

### Post by Duckmeister on 2007-06-13
oh...... well thats nice but sadly, another problem... :'( (which is a shame becuase i have heard about how user friendly Linux is.... restore my faith!!)

THe problem is that now when i click on system>Preferences>Desktopeffects, i get the warning message, "The composite extention is not available".....

:'(

---

### Post by w4ett on 2007-06-13
did you complete the sequence:

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

and then reboot or restart x?

---

### Post by Duckmeister on 2007-06-14
yup ive done all of that, but it still says:

> The Composite extension is not available

:'(

---

### Post by Duckmeister on 2007-06-14
*b.u.m.p*

---

### Post by NeoLithium on 2007-06-14
Hello :)
There is an ATI driver walkthrough for you right here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28ATI.29)

and then there is some information on installing the composite manager for once you have the correct driver installed, right here:
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

Hopefully this will help you out. I don't have the same drivers, but they are pretty straightforward tutorials, and if you have any problems, of course, just pop back into your thread and let us know how things are going :)

Welcome to Ubuntu!

---

### Post by Duckmeister on 2007-06-14
haha thats brilliant :) thanks a lot will get down to it now :)

---

### Post by Duckmeister on 2007-06-14
Hmm i downloaded the ati driver from the manual install on that link you sent me, and when i went to open it i got this warning:

> gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

and i get a drop down menu..... what shall i do???

---

### Post by NeoLithium on 2007-06-14
Which way were you following? The Install the Ubuntu Way, or the Manual Installation, and just so we're on the same page, have you gone through step by step up to that point? 

Don't worry, we'll get this installed with ya! :)

---

### Post by Duckmeister on 2007-06-14
thanks a lot:) seems the linux community is all its cracked up to be :)

Well, i followed the first way (ubuntu way), but that just didnt do anything.....

I then did the manual way and dowloaded the ati driver, but it wont let me open the file..... it comes up with a little window that says,

 "gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."

and gives me a drop down menu under the name of "character coding"......

I then click 'retry' and the text in the box changes to,

"Please check that you are not trying to open a binary file.
Select a different character coding from the menu and try again."


Thanks a lot btw :)

---

### Post by NeoLithium on 2007-06-14
Well, we try to help out as best we can for everyone.  After you did the 'Install the Ubuntu way' did you move down on the screen into the configuration section, and continue on? The driver needs to be configured as well, which might be a reason that it seems to do nothing.

---

### Post by Duckmeister on 2007-06-14
yup followed all parts and it still hasnt worked :( starting to annoy me now :'(

---

### Post by Duckmeister on 2007-06-14
*B.U.M.P*


Sorry about all the bumps btw

---

### Post by Duckmeister on 2007-06-14
if it helps i have a x200m gfx card...

---

### Post by lahook on 2007-06-14
I tried the methods on the ubuntu install ati binary page, and couldn't get the drivers to work correctly. It kept showing up as the mesa fglrx drivers. 
A lot of people have had success using the instructions from ati's website. I didn't try their method.
I tried Envy.
The first try I did autoinstall, it gave me the same mesa drivers with fglrxinfo
next I ran envy and chose manual install, worked like a charm.

here's the link for Envy  [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

I hope this helps

---

### Post by Duckmeister on 2007-06-14
used the programme.... same old error....

"the composite extension is not available"

Save my Linux!!

---

### Post by Duckmeister on 2007-06-14
*b.u.m.p*

---

### Post by Duckmeister on 2007-06-14
Oh come on guys i want this to work so much. its my first experience with Linux and its not going too great tbh....

---

### Post by lahook on 2007-06-14
post /etc/X11/xorg.conf like w4ett requested earlier

gedit /etc/X11/xorg.conf

and fglrx info and glxinfo

fglrxinfo 

glxinfo

other people here can help you by seeing them

you might just have to enable composite in the xorg.conf file

---

