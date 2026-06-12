---
title: "Laptop Graphics Driver Issue"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by XAnarchy on 2008-02-27
I installed Ubuntu on my laptop a few days ago and using wine i figured i'd try and play some games, but after some research it turns out that i've gotta update my graphic drivers.... who knew.\

So i downloaded the intel graphics driver for me (i think) and went about installing it and untared etc and ran the install.sh file in terminal, all good pressed yes and enter a few times then i got the error 

"ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules. Installation will be aborted. "

So basically, i want to know, what are kernel modules and how do i get them.

I've also got a general question about terminal. what does the * mean after/before thing?


Thanks in advane to any help that can be given!
XAnarchy

---

### Post by glennric on 2008-02-27
If you have an intel graphics card you shouldn't have to update your driver.  The default driver in linux works rather well.  

A kernel module is what drivers are called in linux.  

A * in the terminal is a wildcard.  It will match anything.  For example 
```
ls *.txt
```
will list all files in the current directory that end in .txt

---

### Post by XAnarchy on 2008-02-27
How do i go about getting the latest kernel modules?

---

### Post by Origin415 on 2008-02-27
Do you have a compiler on your system? Ubuntu does not have one preinstalled.

```
sudo aptitude install build-essential
```

The kernel modules arent the problem, you dont need the actual modules, only the headers which should be installed by default.

---

### Post by glennric on 2008-02-27
> **Origin415 said:**
> 
The kernel modules arent the problem, you dont need the actual modules, only the headers which should be installed by default.

The kernel module is his problem.  That is what he is trying to compile.  The driver for the graphics card is the kernel module.

---

### Post by glennric on 2008-02-27
If you really want to compile the kernel module, you had better make sure that the headers for your kernel are installed.  If you are running the default Ubuntu kernel this is "linux-headers-2.6.22-14-generic".  However, be warned that compiling a kernel module is not something that a newbie should be attempting to do.

---

### Post by XAnarchy on 2008-02-27
Im currently redownloading the ubuntu cd cause i couldn't find it. Im trying to install what he says and it told me to put in the cd. 

So after that should i try doing what i did before? Or do you recomend something else glennric?

---

### Post by XAnarchy on 2008-02-27
Well do you think you'd be able to run me through it? Cause if this isn't working with wine then im sure nothing else will. What are the risks of doing this? Then again what are the benefits?

---

### Post by glennric on 2008-02-27
What games are you trying to play, and what research led you to believe that you need to update your graphics card driver?

---

### Post by XAnarchy on 2008-02-27
Tibia a really basic MMORPG is the game. I was researching other peoples problems with the game and playing it through ubuntu. Basically the game loads but the start screen is upside down and really messed up. I saw a screenshot of someone elses with the exact same problem and people there recommended he updated his drivers. Which fixed it for him. However mines not so simple as its not a graphics card as such, its a dodgy onboard intel graphics. Which led me to where i am now trying to update it.

---

### Post by igknighted on 2008-02-27
> **XAnarchy said:**
> Tibia a really basic MMORPG is the game. I was researching other peoples problems with the game and playing it through ubuntu. Basically the game loads but the start screen is upside down and really messed up. I saw a screenshot of someone elses with the exact same problem and people there recommended he updated his drivers. Which fixed it for him. However mines not so simple as its not a graphics card as such, its a dodgy onboard intel graphics. Which led me to where i am now trying to update it.

as a general rule, only very rarely on a once in a blue moon basis should you ever go search for applications or drivers on the internet.  Pretty much everything you could need is either installed by default, or available through the repositories (synaptic).

As for asking for the CD... open synaptic and go to settings -> repositories.  Then un-check the CD as an install source, you do no need it.

---

### Post by XAnarchy on 2008-02-27
I finished installing that program the dude before you told me to do. Not sure if you think its necessary but its done none the less. Incase it comes in handy

---

### Post by XAnarchy on 2008-02-27
> **igknighted said:**
> as a general rule, only very rarely on a once in a blue moon basis should you ever go search for applications or drivers on the internet.  Pretty much everything you could need is either installed by default, or available through the repositories (synaptic).

As for asking for the CD... open synaptic and go to settings -> repositories.  Then un-check the CD as an install source, you do no need it.

Lol, already done. But thanks, might come in handy in future!

---

### Post by igknighted on 2008-02-27
run the command 'lspci | grep VGA' and post the results, we can point you to the proper set-up for your graphics card.

---

### Post by XAnarchy on 2008-02-27
00:01.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) 

is what i got from that

---

### Post by igknighted on 2008-02-27
thanks, and for good measure, can you run this on as well?
```
glxinfo | grep direct
```

---

### Post by XAnarchy on 2008-02-27
direct rendering: Yes

---

### Post by glennric on 2008-02-28
I have a similar adapter in another computer.  Which driver are you using for that?  To find out look in the file /etc/X11/xorg.conf for the line 'Section "Device"'  The driver should be listed below that.

---

### Post by XAnarchy on 2008-02-28
next to drive in device is just says "intel" .... thats not right is it

---

### Post by igknighted on 2008-02-28
Ok, the first command (as it seems) simply identified what the chipset was.  The second command was checking the 3d rendering capabilities, which are working.  The question then is what you are trying to gain by compiling a new driver.  My other question is which driver you are using, as there are two.  First is called 'i810', and the other is 'intel'.  I believe (although I do not use intel graphics) that 'intel' is superior.  To check which you are using, run the command
```
 cat /etc/X11/xorg.conf | grep Driver  
```
It will give you a list of drivers, one should be i810 or intel

---

### Post by XAnarchy on 2008-02-28
I wasn't trying to compile a new driver i was just using what i thought to be normal and go hunting for the drivers if something isn't working right. Which appears to be the wrong thing to do. The driver is Intel and not i810. I just want this damn thing ot work. Everything time i go through wine and start "tibia" it says "Tibia starting" with a little box in the task bar and the mouse thinking thing goes but then it just exits. So perhaps its an error with the game? or perhaps an error with Wine?

---

### Post by glennric on 2008-02-28
Try changing that line to 
driver "i810" 
instead.  That is the one I use.  I couldn't get the intel one to work right even though that is the one that Ubuntu put into the xorg.conf file by default.

---

### Post by igknighted on 2008-02-28
> **XAnarchy said:**
> I wasn't trying to compile a new driver i was just using what i thought to be normal and go hunting for the drivers if something isn't working right. Which appears to be the wrong thing to do. The driver is Intel and not i810. I just want this damn thing ot work. Everything time i go through wine and start "tibia" it says "Tibia starting" with a little box in the task bar and the mouse thinking thing goes but then it just exits. So perhaps its an error with the game? or perhaps an error with Wine?

Very likely.  Have you checked the wine application database to see if the program works for others?  [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by igknighted on 2008-02-28
> **glennric said:**
> Try changing that line to 
driver "i810" 
instead.  That is the one I use.  I couldn't get the intel one to work right even though that is the one that Ubuntu put into the xorg.conf file by default.

His 3d rendering is working... why fiddle with it?  IMO, wine is a much more likely culprit.

then again... some of the intel drivers have weird bugs... it could help

---

### Post by XAnarchy on 2008-02-28
> **glennric said:**
> Try changing that line to 
driver "i810" 
instead.  That is the one I use.  I couldn't get the intel one to work right even though that is the one that Ubuntu put into the xorg.conf file by default.

I can't change it cause i dont have permission? And i can't edit it by right clicking and going into properties there all 'greyed' out.

---

### Post by XAnarchy on 2008-02-28
> **igknighted said:**
> His 3d rendering is working... why fiddle with it?  IMO, wine is a much more likely culprit.

then again... some of the intel drivers have weird bugs... it could help

I think wine might be the problem too. Ill uninstall it and install an older version to see if that fixes it.

---

### Post by igknighted on 2008-02-28
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5403&iTestingId=5474](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5403&iTestingId=5474)

doesn't seem like that works in wine... these are old reviews though, don't know what version you are using

---

### Post by XAnarchy on 2008-02-28
Tibia 8.0
by Ricky Johansson on Wednesday October 17th 2007, 4:03
Tibia 8.0 also works with Wine 0.9.15
Only tested the DirectX 5 engine as my laptops videocard can't handle the other engines.
The native Linux client uses nothing but the OpenGL engine, which was the reason for me to try the Windows client.


Wine 0.9.15 makes it work. Maybe it will be worth my while hunting that one out. Ill give it a go.

---

### Post by XAnarchy on 2008-02-28
Right, came across another error trying to install wine 0.9.15. 

"No suitable lex found. Please instlal the 'flex' package."

How do i get flex? 

apt-get flex? im so noob -.-

---

### Post by igknighted on 2008-02-28
either 'sudo apt-get install flex' or open synaptic and search/install it from the graphical environment

---

### Post by XAnarchy on 2008-02-28
Thanks. Will post results as soon as i get them. <crosses fingers>

---

### Post by igknighted on 2008-02-28
> **XAnarchy said:**
> Thanks. Will post results as soon as i get them. <crosses fingers>

OH...

delete your old wine install first (including the .wine folder in your home folder).  I think multiple versions can conflict.

---

### Post by XAnarchy on 2008-02-28
I did delete Wine. However i didn't delete the .wine folder in my home folder :S. Guess ill see

---

### Post by XAnarchy on 2008-02-28
I downloaded the Linux version of Tibia but it never worked so thats why i decided to go with Wine and windows. But while im here i'll ask. I untarred it and i run it through terminal but i get this error.

"X Error of failed request:   GLXUnsupportedPrivateRequest
    Major opcode of failed request:   143  (GLX)
    Minor opcode of failed request:   16 (X_GLXVendorPrivate)
    Serial number of failed request:   58
    Current serial number in output steam:  59"

Any idea? Something i need that im missing, if you got no clue then ill stick with wine. But if its easier to fix that then wine im willing to try it.

---

### Post by XAnarchy on 2008-02-28
Hmm, i got the latest version of wine cause i couldn't work out how to install 0.9.15 (will try later) and i tried doing "Wine Tibia.exe engine 0" in the tibia folder. But i got the error 

"xanarchy@xanarchy-laptop:~/Tibia$ fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0 count 0!

---

### Post by XAnarchy on 2008-02-28
Help please anyone?

---

