---
title: "X Window problem"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by chaofan on 2007-01-29
Alright, so I get Ubuntu, burn it to a disc with the ISO burner, and launch Ubuntu from said disc. It gives me a few options, and I select "Start or Install". It goes through the launching sequence, and once it gets to a DOS like screen (Linux kernel, I assume) it says something along these lines:
Attempting swap
Mount: Function not implemented
[OK]
Something else here
[OK]

and tells me it has problems with the X Window setup. I hit OK to see the gigantic diagnostic thing.

I assume that this has something to do with the configuration of the X Window because it disables the thing entirely at the end and lets me control the kernel.
Can someone help me with this? I'm pretty good with windows, but I wanted to stop being biased against ALL other OS's (Apple still phails) and try out linux. However, this isn't helping me any as to seeing why windows isn't the best. Hopefully you guys are nicer than this OS is.

EDIT:

Oh, something that isn't as important, whenever I press delete or backspace, it gives me funny symbols like \L/ for backspace, \$> for other buttons, ect.

(also, links to things would be great help too, cause I searched here and found nothing)

---

### Post by scrooge_74 on 2007-01-29
Which version of ubuntu did you use?

What type of video card you have?

Try booting in recovery mode.

You end up in a terminal window because the Xserver can start so you dont get a graphical interface just texr mode instead

---

### Post by chaofan on 2007-01-29
I have 6.10 (regular ubuntu, i noticed a Kubuntu and a Xubuntu), I have an N-Vidia FX 5500 by PNY, 1GB 333mhz DDR ram, an external 300gb harddrive and an internal 80gb harddrive, an IDE MAXTOR disk drive.

However, are you sure it isn't a config problem?

---

### Post by scrooge_74 on 2007-01-29
Lets see if I can give you some light into your problem.  First right now there are 3 sets of ubuntu (and its derivatives) 6.06 the one I have the long term support call Dapper, you have 6.10 which is Edgy and should be ok for you and then is Faisty which is in testing and not for new people comming into Linux (I dont even dare use it yet).

Nvidia cards can be a problem (I have one and it took me some time to configure it properly following this [advice]("http://albertomilone.com/latestrepo.html") after the system was install.

You can also check this [site]("http://www.psychocats.net/ubuntu/installing") to give you an introduction.

Probably the system is not recognicing the video card and is picking up the wrong set of drivers.

you can try booting in recovery mode to see if it helps, also if you have a terminal console and can type commands you can try this command

sudo dpkg-reconfigure xserver-xorg and then give replys to the questions, when you get to the video driver pick nv as the driver or go for VESA.    The nv driver is an open source version of nvidia drivers , it wont give you 3D and some other stuff your card can do, but will let you do a lot.

After you finish with all the questions type startx and if things got corrected you will get into a graphical enviroment.  If not you have to read the error messages and check what it says so it can be fixed.  you could try posting the info on  /etc/X11/xorg.conf  but i dont know how familiar you are with Linux commands.

Read carefully the info in [psychocats]("http://www.psychocats.net/ubuntu/installing") site, it will be beneficial for you.

---

### Post by chaofan on 2007-01-29
Well, before you posted, I launched in "safe graphics mode", which is the only thing that seemed remotely close to "recovery mode". It turned out the same way. I'll try following some of your advice, and let you know if it turns out ok. Also, thanks for the help!

EDIT:

I just popped the disc in my laptop, and it ran like a charm. That alone proves that somethings wrong with my PC (Possibly the gphx card like you said, but both are Nvidias(5500 and 460GO))

---

### Post by blackened on 2007-01-29
> I just popped the disc in my laptop, and it ran like a charm. That alone proves that somethings wrong with my PC (Possibly the gphx card like you said, but both are Nvidias(5500 and 460GO))

There's not technically anything "wrong" with your pc, it just needs some configuring. Linux is totally usable from the command line interface, it's just not as pretty.

---

### Post by chaofan on 2007-01-29
Ok, so i decided to turn my laptop into a linux machine. I'm liking it so far, except I can't seem to get the linksys drivers to install correctly. I won the battle against figuring out sudo (didn't realise the password doesnt show up when typing it), but for some reason ./configure doesn't exist.

This is the help page for the drivers: [Linksys driver](http://linksys.custhelp.com/cgi-bin/linksys.cfg/php/enduser/std_adp.php?p_faqid=773&p_created=1084221483&p_sid=tr8cSTsi&p_accessibility=0&p_lva=2744&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NCZwX3Byb2RzPTAmcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3NjZl9sYW5nPTEmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1saW51eA**&p_li=&p_topview=1)

EDIT:

Christ... did they have to make the commands CASE SENSITIVE? oh well, something to note for the future i guess....

---

### Post by 3rdalbum on 2007-01-29
True.

./configure is not an application that is installed on a Linux system - it's a script that is distributed with each program that needs to be compiled. So your terminal needs to be in the directory that contains the "configure" script.

Easy way to do it: Open a terminal and type "cd " (with a space at the end), then drag the extracted Linksys folder to the terminal, switch back to the terminal window and press Return. Now, you'll be able to type "./configure" and it should all work. (note: In order to compile any software, you need to use Synaptic to install the "build-essential" package).

---

