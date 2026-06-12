---
title: "ATI drivers"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by Quan_Chi on 2007-02-26
OK im completely new to linux, Im talking new as in ive only been using linux for about an hour now.

I was trying to do this

[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)

I got to step 3.
I copied the code from the given link into my xorg.conf and tried to save it.
But xorg.conf is read only....

How do I save the changes I have made if its read only?

I have a ATI radeon 9550, and I noticed that it is talking about the 9600, will this make a differance?

---

### Post by Maestro23 on 2007-02-26
Make things easy on yourself.  Get the Envy script.  Command line and permissions kill people new to linux.

1. Get the correct drivers for your card.

2. Download/Use the Envy script: [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

*Works for both ATI and Nvidia

Good luck.

---

### Post by kittyhawk63 on 2007-02-26
Here is an alternative method to Maestro23. His method is easier if you know how to do it. 

**[CENTER]Installing ATI Radeon 9200SE driver[/CENTER]**

**For Advanced Linux Users**

1) Upgrade to Ubuntu 6.06. or higher
2) Install the fglrx driver.
3) Run sudo dpkg-reconfigure xserver-xorg, disabling kernel framebuffer (graphics card directly under the control of the X server).
4) Reboot.

**For New Users of Linux**

**Note**: I have written these instructions for those who are brand spanking new to the Linux Operating System (OS). If you know how to use Terminal and Text Editor you can proceed further down this page to the line: *1. Copy and paste the following line into Terminal*. As a "noobie" myself, I understand how difficult it is to follow instructions from those who forget that you and I don't know what we are doing. That's why I have written these simple instructions for you to follow. You will succeed in doing in a few minutes what it took me several hours to accomplish. 

**Note**: I found the instructions given here on the following web page: If you click on this link it will automatically take you to the section of the web page I am using. I strongly recommend that you go to this web page from Windows or another OS and read the full page. While you're at it, if you have them, I would highly recommend using Windows or another OS to read and print out this page of instructions. 

**[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_1:_Install_the_8.28.8_Driver_the_Ubuntu_Way](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_1:_Install_the_8.28.8_Driver_the_Ubuntu_Way)**

**Note**: I am using the **Ubuntu Way** of installing the ATI Radeon 9200SE driver. There is a **manual way** also. I know the **Ubuntu Way** will work for 32bit systems. It may also work for 64bit systems. The Manual method will work for both 32bit and 64bit. The Manual method is shown on this same web page.

**Note**: Seeing that you may be experiencing trouble with screen freezes, If you have no other OS, I would suggest that you print out the instructions in Text Editor just as soon as you can. It will save you time (if your screen freezes often) and you can work from the printed page along with Terminal. Go to **Text Editor** a few lines down. **Terminal** is just a few lines below Text Editor.

**Note**: I really do not prefer this, but if you need these instructions and you do not have Windows or another Operating System (OS) and your Linux computer keeps freezing before you can read and go through these instructions (*and print*), you can e-mail me. My e-mail address is:

**kittyhawk_63@myfastmail.com**



[CENTER]**TEXT EDITOR**[/CENTER]

Text Editor is located on the Menu bar (top of desktop):

Applications -> Accessories -> Text Editor

***Copy the following and paste into Text Editor.*** (*Or, copy and paste this entire document into Text Editor.*) Now choose **PRINT**. You won't be sorry for having this hard copy in the future.



**Let's get started**.

**A**. **Let's begin to install the driver for ATI Radeon 9200SE Video Card.**



**[CENTER]TERMINAL[/CENTER]**

Open up "Terminal" to insert the necessary command lines.
To open Terminal, go to the Menu bar at the top of the desktop and select in this order:

Applications -> Accessories -> Terminal

What you see immediatley below is a "Quote" tag.
> 
**Note**: You will be copying each of the following command lines into Terminal: ***Follow the instructions below this Quote tag***.

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx

When you start Terminal you will see a line like:

**username@username:~$**

**username** is the name you entered when you installed Ubuntu.

**Note**: After you copy the line, RIGHT CLICK anywhere in Terminal and LEFT CLICK "paste". The copied line will automatically be inserted after the **~$**.



[CENTER]**INSTALLATION**
**Method 1: Install the 8.28.8 Driver the Ubuntu Way**[/CENTER]

*1. Copy and paste the following command line into Terminal*. 

**sudo apt-get update** 

Now press your keyboard's <enter> key.

-wait until it is finished-


*2. Copy and paste the following command line into Terminal*.

**sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed**

Now press your keyboard's <enter> key.

-wait until it is finished-


*3. Copy and paste the following command line into Terminal*.

**sudo apt-get install xorg-driver-fglrx**

Now press your keyboard's <enter> key.

-wait until it is finished-


**B**. **Configure the Driver**

Copy and paste the following command line into Terminal

**sudo aticonfig --initial**

Now press your keyboard's <enter> key.

-wait until it is finished-


*Now you need to save any open documents before we reboot your system*:


**C**. **Finish the Installation**

Copy and paste the following command line into Terminal

**sudo shutdown -r now**

Now press your keyboard's <enter> key.

-wait until it is finished- Your computer will now reboot.

Have a great day! ):P 


**Note**: I could not get the following command lines to work for me. However, I installed the driver through Envy. Since you followed the instructions here, you may get the following command lines to verify. Even if you don't, your screen should no longer freeze. I checked out the instructions on this page and everthing worked as it should until I got to the following verifying command lines.


**D**. **Verifying**

Run the following command to check its output to ensure the fglrx driver is installed properly:

*Copy and paste the following command lines **as a unit**  into Terminal*

[B]$fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700
OpenGL version string: 2.0.6334 (8.34.8[/B])

Now press your keyboard's <enter> key.

-wait until it is finished-


**E**. **Revert to Xorg driver**

If (for any reason) the fglrx install fails, you can revert to the Xorg driver by executing

Copy and paste the following command line into Terminal

**sudo dpkg-reconfigure xserver-xorg**

Now press your keyboard's <enter> key.

-wait until it is finished-

---

### Post by Quan_Chi on 2007-02-27
Hmmm, I did what you said Maestro23 and it appears that it worked, 
But how I can I be sure that it worked?

---

### Post by kittyhawk63 on 2007-02-27
> **Quan_Chi said:**
> Hmmm, I did what you said Maestro23 and it appears that it worked, 
But how I can I be sure that it worked?

If you followed Maestro23's instructions, you just have to stay on line. If you experience no screen freezes, it will more than likely be working correctly.
KH

---

