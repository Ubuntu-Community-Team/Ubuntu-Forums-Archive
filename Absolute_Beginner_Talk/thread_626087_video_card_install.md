---
title: "video card install"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by tbrownarcher on 2007-11-28
I have a sucsessful install of ubuntu and windows dual boot.

I accomplished this by taking out the NVIDIA video card and relying on the intel card in the mother board (integrated). 

My problem is now that I want to use the NVIDIA and I don't know how to install it since the screen goes blank when i put it in the computer slot.  

my system again is 

dell dimension 3000 2800 mhz processor
and I'm running ubuntu 7.10
I have an integrated graphic card which i'm using and want to disable
I also have an NVIDIA Gforce FX 5500 graphics card which is not actually in but i want to install.

can Anyone help me with this 

thanks,
tbrownarcher (nate)

---

### Post by gsiliceo on 2007-11-28
There was a known issue with another FX NVIDIA graphic card that was fixed this way:
> sudo gedit /etc/modprobe.d/blacklist
Then at the end of that file add this
blacklist intel_agp
Save the file and shutdown your machine
Install in the motherboard your graphic card
Turn on your pc, open the bios(usually F11 or F2) and change the default graphic card to the agp(or agi) port, you'll have to look around for this varies from bios to bios.

THen you'll need to install the nvidia restricted drivers. 
If you get a black screen at the end of boot time.
Start in recovery mode and
> dpkg-reconfigure xserver-xorg
WHen prompted use the "nv" driver or try the "nvidia".

Good luck

---

### Post by tbrownarcher on 2007-11-28
I don't know where to enter the first quote .. sudo gedit /etc/modporbe.d/blacklist  
and what is that ?  Is that a file ?  My last distro of linux had something called file manager? Is there something equivelant in ubuntu 7.1?

thanks,
tbrownarcher (nate)

---

### Post by gsiliceo on 2007-11-28
Im sorry, you need to hit alt+F2 or open a terminal from the acessories menu
By the way the equivalent is called nautilus

---

### Post by tbrownarcher on 2007-11-28
hmmmmmmmmm .  My bios has only one instance of video 

that is in the integrated hardware section

in that section there is a place to set it to on board or to auto

onboard restricts it to the onboard video card

so setting it to auto is the only option and when i do that and install the card in the slot i get a blank screen in Ubuntu .  I'm in windows right now with the card in and i get great screen .  

so how do i get the driver installed ?




the boot with the nvidia card in the slot stops at the graphics manager i forget it's name ... 


Thanks,
tbrownarcher (nate)

---

### Post by PmDematagoda on 2007-11-28
Try this:-

1) Install the Kernel source code:-

```
sudo apt-get install linux-source-2.6.22
```

2) Download and install the [Nvidia drivers]("http://www.nvidia.com/object/unix.html") as given in their web site.

3) After installing do:-
```

sudo dpkg-reconfigure xserver-xorg
``` and select the driver as Nvidia and any other options you may want.

4) After configuration, do:-

```
sudo startx
```
To see if the GUI now works properly.

---

### Post by tbrownarcher on 2007-11-28
i assume I am going to do this in a terminal again ??? 

and you must be saying that there is a file with nvidia drivers on their site that would work with linux are they designated on linux as linux drivers??

thanks,
tbrownarcher (nate)

---

### Post by Therion on 2007-11-28
1. Install the nVidia video card, and disable the onboard video in the system BIOS.

2. Boot your PC.

3. When the GRUB menu comes up, hit Escape and select "Recovery Mode".  You'll end up at a command prompt.

4. From the command prompt type in:
```
nano /boot/grub/menu.lst
```

5. Scroll down using the arrow keys until you find the first line that begins with Kernel.  It's a looong line of code that will go off the end of your display.  At the end of that line you'll see the word "splash".  Remove "splash" from that line so it looks like this:
```
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=43a49820-eae9-4b96-9f94-a81a2aadcb2c ro quiet
```

6. Use Ctrl+X to Save the changes, okay the file over-write when prompted.

7. Reboot.  This should get you to the Ubuntu desktop.  

8. From there install the restricted driver (you'll be prompted about this automatically) and you should be good to go.

---

### Post by PmDematagoda on 2007-11-28
> **tbrownarcher said:**
> i assume I am going to do this in a terminal again ??? 

and you must be saying that there is a file with nvidia drivers on their site that would work with linux are they designated on linux as linux drivers??

thanks,
tbrownarcher (nate)

Yes, you will have to use the terminal.

And the drivers are there, for Linux 32 bit and 64 bit, select the one you want and download it, the instructions for installation are given there as well.

---

### Post by tbrownarcher on 2007-11-29
therion:

[HTML]4. From the command prompt type in:
Code:

nano /boot/grub/menu.lst[/HTML]

the result?  **[COLOR="Blue"] E27:  unrecognized command[/COLOR]** 

so i can't do that until i know more i guess 

----------------------------------------------------------------------------------------------
PmDematagoda:

sudo apt-get install linux-source-2.6.22

The result:  could not resolve 'us.archive.ubuntu.com'




thanks,
tbrownarcher (nate)

---

### Post by gsiliceo on 2007-11-29
Have you tried dpkg-reconfigure xserver-xorg? and choosing "nv" as your driver?

---

### Post by tbrownarcher on 2007-11-29
Gsiliceo:

**[SIZE="3"]"Have you tried dpkg-reconfigure xserver-xorg? and choosing "nv" as your driver?"[/SIZE]**

If i use the auto option the intel 8286 card is detected .

If i use the manual option and choose NV it gives me "Generic"

the intel is integrated and there is no option to shut it off only the 2 options 'onboard and auto'

Is there a way to turn that chip off with some other software after I boot? The bios only having the option to make the machine choose is not working.  

**_Though it may be working as a choice but not working because of lack of driver_**

the NVIDIA is in a slot and in windows it works fine ..... 

Also it is being used at the beginning of boot to run the little bar back and forth. (I know this because of the aparent screen resolution which shows bigger when i take the NVIDIA card Out of the computer).  However when boot is finished It must be going to the NVIDIA card and unable to use it because of no driver.  (I think i know this because the screen stops at the 4th text line which means the video manager is trying to boot the card. If the Intel card were being used it would boot because it does when the nvidia card is removed from the computer.


getting frustrated, But thank you very much,

tbrownarcher (nate)

---

### Post by gsiliceo on 2007-11-29
> 
Is there a way to turn that chip off with some other software after I boot? The bios only having the option to make the machine choose is not working.

Yes, you can blacklist in the kernel devices in this file
> /etc/modprobe.d/blacklist
I added this line to the end of that file for a similar problem, maybe it will work for you.
> blacklist intel_agp

---

### Post by tbrownarcher on 2007-11-29
gsiliceo:

[SIZE="5"][B]
"Quote:
Is there a way to turn that chip off with some other software after I boot? The bios only having the option to make the machine choose is not working."[/B][/SIZE]

"Yes, you can blacklist in the kernel devices in this file
Quote:
/etc/modprobe.d/blacklist"

I tried this and it said permission denied or something similar.

I tried it from a directory that started with root and my user name .  I am **[SIZE="4"]now[/SIZE]**
not asked for a login when i boot into the fix it boot .  I did this hours ago and can't remember exact wording i wll try to write it down the next time 

I'm sure i need to be asked for a login to do this and it's not asking me for that on boot.




thanks,
Tbrownarcher (nate)

---

### Post by gsiliceo on 2007-11-29
YOu need to open that file with root access this way
> sudo gedit /etc/modprobe.d/blacklist
And no in recovery mode you are not asked for a password is the normal behavior.

---

### Post by tbrownarcher on 2007-11-29
Maybe I'm just too hard headed.  SIGH!

[B][SIZE="3"]"YOu need to open that file with root access this way
Quote:
sudo gedit /etc/modprobe.d/blacklist"[/SIZE][/B]


I did that and got .......

Cannot open display
run gedit --help to see a full list of available command line options.  

I looked in the help and was so confused i just came back here ... I acually tried 
**[B][B]sudo gedit display /etc/modprobe.d/blacklist**[/B][/B] but it couldn't do it or display it


Thanks,
 tbrownarcher(nate)

---

### Post by tbrownarcher on 2007-11-29
OK I Guess:

I tried to boot the computer with the install cd and used the graphics terminal there.  

I got the file /etc/modprobe.d/blacklist to display and i edited it by 
putting blacklist intel_agp in the last line of the file and saved it

I then tried booting and after putting in my login it told me that it could nto find the nvidia stuff.

[COLOR="black"][SIZE="5"]I'm sorrry !  I need to go put the driver in.  I forgot that .. so sorry will be back in a half hour or less.  9:11 pm Thursday nov 29, 2007
[/SIZE][/COLOR]


thanks,
tbrownarcher (nate)

---

### Post by tbrownarcher on 2007-11-29
i hope i'm not driving everyone crazy .  It's driving me so ! 

I am using the cdrom to boot the system and using the graphic interface that way because the terminal could not resolve the site.

the terminal in the gui in accessories will do all it is supposed to do if it's actually writing to drive i do not know.  

i did sudo apt-get install linux-source-2.6.22 and a file came down but i dont' know what to do with it. nor really where it is ... 



I used my browser to download the drivers for nvidia by opening the site in my browser and downoading the drivers there.  The drivers came down in a text file in the browser.  Is that what i wanted to do or is there a way to redirect it and if so how and to where ???? 


also.  how do you guys do the quote: boxes ??? i dont' see that option here.


thanks,
tbrownarcher (nate)

---

