---
title: "How To: Install driver for ATI Radeon 9200SE"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-02-25
[B][CENTER][LEFT]Note: Before you try the following, you may try this. Start Terminal and type [COLOR=Red]gksudo gedit /etc/X11/xorg.conf[/COLOR]  Go to the line that states you have [COLOR=Red]ati [/COLOR]as the device. Change [COLOR=Red]ati[/COLOR] to read [COLOR=Red]vesa[/COLOR]. It works for me.
[/LEFT]
 
Installing ATI Radeon 9200SE driver[/CENTER]
[/B]

Do you want to print the following instructions?

[CENTER]**Using TEXT EDITOR**[/CENTER]

Text Editor is located on the Menu bar (top of desktop):

Applications -> Accessories -> Text Editor

***Copy and paste this document into Text Editor.*** (*Or, select, copy, and paste any part of this document into Text Editor.*) Now choose **PRINT**. You won't be sorry for having this hard copy in the future.





**For New Users of Linux**

**Note**: I have written these instructions for those who are brand spanking new to the Linux Operating System (OS). If you know how to use Terminal and Text Editor you can proceed further down this page to the line: *1. Copy and paste the following line into Terminal*. As a "noobie" myself, I understand how difficult it is to follow instructions from those who forget that you and I don't know what we are doing. That's why I have written these simple instructions for you to follow. You will succeed in doing in a few minutes what it took me several hours to accomplish. 

**Note**: I found the instructions given here on the following web page: If you click on this link it will automatically take you to the section of the web page I am using. I strongly recommend that you go to this web page from Windows or another OS and read the full page. While you're at it, if you have them, I would highly recommend using Windows or another OS to read and print out this page of instructions. 

**[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_1:_Install_the_8.28.8_Driver_the_Ubuntu_Way](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_1:_Install_the_8.28.8_Driver_the_Ubuntu_Way)**

**Note**: I am using the **Ubuntu Way** of installing the ATI Radeon 9200SE driver. There is a **manual way** also. I know the **Ubuntu Way** will work for 32bit systems. It may also work for 64bit systems. The Manual method will work for both 32bit and 64bit. The Manual method is shown on this same web page.

**Note**: Seeing that you may be experiencing trouble with screen freezes, If you have no other OS, I would suggest that you print out the instructions in Text Editor just as soon as you can. It will save you time (if your screen freezes often) and you can work from the printed page along with Terminal. Go to **Text Editor** a few lines down. **Terminal** is just a few lines below Text Editor.

[COLOR=Blue]**First Things First**[/COLOR]
1. Go to Applications->Accessories->Terminal and type the following in Terminal: 
[COLOR=Red] gksudo gedit /etc/apt/sources.list [/COLOR]    (*You can copy/paste this line into Terminal*)
Now remove (uncomment) each "[COLOR=Red]#[/COLOR]" that is before each "[COLOR=Red]deb[/COLOR]" line.
Close Terminal

2. Go to System->Administration->Synaptic Package Manager
Type in your password if needed. Hit <enter> or <return>
Select "Search" and type: [COLOR=Red]xorg-driver-fglrx[/COLOR] and click "search"
With your mouse pointer select the line that says: xorg-driver-fglrx
Select "Mark for Installation" in the pop up.
Go up on the page and select "Apply".
Select "Apply" again in the pop up.
Wait until the installation of this package is finished.
Close Synaptic Package Manager

**Let's get started**.

**A**. **Let's begin to install the driver for ATI Radeon 9200SE Video Card.**



[B][CENTER]TERMINAL[/CENTER]
[/B]

Open up "Terminal" to insert the necessary command lines.
To open Terminal, go to the Menu bar at the top of the desktop and select in this order:

Applications -> Accessories -> Terminal

What you see immediatley below is a "Quote" tag.
> 
**Note**: You will be copying each of the following command lines into Terminal: ***Follow the instructions below this Quote tag***.

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx 
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv[COLOR=Red] <-- (I have problems with this line. I leave it out.)[/COLOR]
sudo shutdown -r now

When you start Terminal you will see a line like:

**username@username:~$**

**username** is the name you entered when you installed Ubuntu.

**Note**: After you copy the line, RIGHT CLICK anywhere in Terminal and LEFT CLICK "paste". The copied line will automatically be inserted after the **~$**.Another method of copying and pasting. If you have a mouse with a wheel, highlight the line you want copied, go to terminal and press the wheel. The line will be copied and pasted.

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


*3. Copy and paste the following command line into Terminal*. This is necessary if you did not install xorg.conf using Terminal. Just make sure that you have uncommented the "debs" as instructed under First Things First.

**sudo apt-get install xorg-driver-fglrx**

Now press your keyboard's <enter> key.

-wait until it is finished-


**B**. **Configure the Driver**

Copy and paste the following command line into Terminal

[B]sudo aticonfig --initial
[/B] 
Now press your keyboard's <enter> key.

-wait until it is finished-

Copy and paste the following command line into Terminal

**sudo aticonfig --overlay-type=Xv **[COLOR=Red]<-- (I have problems with this line. I leave it out.)[/COLOR]

Now press your keyboard's <enter> key.

-wait until it is finished-

*Now you need to save any open documents before we reboot your system*:


**C**. **Finish the Installation**

Copy and paste the following command line into Terminal

**sudo shutdown -r now**

Now press your keyboard's <enter> key.

-wait until it is finished- Your computer will now reboot.

**E**. **Revert to Xorg driver**

If (for any reason) the fglrx install fails, you can revert to the Xorg driver by executing

Copy and paste the following command line into Terminal

**sudo dpkg-reconfigure xserver-xorg**

Now press your keyboard's <enter> key.

-wait until it is finished-

**F. [COLOR=Red]WARNING[/COLOR]**

Each time that the "kernel" is updated you may need to rerun these sudo commands. I would recommend it. 

If you get stopped at boot with a "resolution" error, hit CTRL-ALT-DELETE and on reboot hit "ESC" and boot up in Safe Mode. Run these commands at the prompt. Now you see why you should print out these instructions. If you now know how to enter the commands in terminal, just print out the short list in the "quote" box above. It will save paper and ink.

Have a great day! ):P

---

### Post by futron on 2007-02-26
Hi, will this work for Mobility Radeon 9200? Thanks.

---

### Post by kittyhawk63 on 2007-02-26
> **futron said:**
> Hi, will this work for Mobility Radeon 9200? Thanks.

Futron,
I am not certain, but to make sure, go to the link below and see if it does.

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_1:_Install_the_8.28.8_Driver_the_Ubuntu_Way](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_1:_Install_the_8.28.8_Driver_the_Ubuntu_Way)

As you will see it is for the 9500. But it worked just fine on my 9200SE.

Edit: I didn't notice the word "Mobility". My card is an ATI. You may want to seek further advise befoe you proceed.

---

### Post by diskotek on 2007-03-27
hi, i applied the ubuntu way..after reboot, screen lost. what shoud i do to get back my old configuraiton?

---

### Post by kittyhawk63 on 2007-03-27
> **diskotek said:**
> hi, i applied the ubuntu way..after reboot, screen lost. what shoud i do to get back my old configuraiton?

Look at the last of the instructions for reverting back.

---

### Post by theonlyrealperson on 2007-03-27
Hi! I followed these directions and I thought I was installing 8.28 which I think is compatible with my ATI mobility Radeon 9000, but it didn't work. (I guess there are a lot of assumptions in there.)

Can you point me to the correct way to install a driver for that?

Thanks!

P.S. I've done searches in this forum and others, and I think I'm too much of a Linux n00b to figure out which one I'm supposed to be installing. Sorry...

---

### Post by kittyhawk63 on 2007-03-27
> **theonlyrealperson said:**
> Hi! I followed these directions and I thought I was installing 8.28 which I think is compatible with my ATI mobility Radeon 9000, but it didn't work. (I guess there are a lot of assumptions in there.)
Can you point me to the correct way to install a driver for that?
Thanks!
P.S. I've done searches in this forum and others, and I think I'm too much of a Linux n00b to figure out which one I'm supposed to be installing. Sorry...

You're right.It is suppossed to load 8.28.8.

Edit: I forgot one line in the instructions. I'm really sorry. That may have been your trouble. Re-run the instructions. I forgot the line: **sudo aticonfig --overlay-type=Xv**

---

