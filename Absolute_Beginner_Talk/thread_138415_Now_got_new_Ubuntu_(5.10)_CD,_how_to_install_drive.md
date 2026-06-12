---
title: "Now got new Ubuntu (5.10) CD, how to install driver Canon LBP660 on Breezy"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by agarwaldvk on 2006-03-01
Hi Everybody

I have already installed the 5.04. Yesterday, I received the CD's for Breezy and am looking forward to installing the same as a dual boot with Windows XP on one of my home computers (having heard so much about it on this forum about it being so much better and easier than Hoary).

I did try it with the Live CD and had no problems and hopefully I should be ok when I actually go ahead with the installation.

I have found a site where a Linux driver for my Canon LBP660 is available. The URL is shown below :-

[http://www.boichat.ch/nicolas/lbp660/](http://www.boichat.ch/nicolas/lbp660/)

However, it does ask to check for "GhostScript" or "Cups" to be installed. Apparently, there are different steps to be taken to extract and subsequently install the driver depending upon the application that I choose to use.

Part information from the above site is reproduced below :-

> 
Install notes
Check you have Ghostscript installed.

Extract the archive, then type:

# make

And log in as root and type:

# make install

Install in CUPS
Check you have CUPS installed.

Then type, replacing 660 by 460 if you are using a Canon LBP-460 :

# make cups-install-660-a4

or

# make cups-install-660-letter depending on your paper format.


If you decide to install manually the printer in CUPS, please set the device to file:/dev/null (NEVER set it to xxxx:/dev/lp0).



Can some please walk me through the steps that I need to take to :-

 - Check if I have the preferred application installed - "GhostScript" or "Cups".
 - If not, then how do I get and install the same
 - Extract the compressed file to wherever it is supposed to be extracted
 - Run it to install the driver


Best regards


Deepak Agarwal

---

### Post by linear on 2006-03-01
Yes, you do have Cups - it's the basis of Ubuntu's printing system.

What you may not have is "make" - you need to install the "build-essential" package to get it.

---

### Post by agarwaldvk on 2006-03-02
linear

Does "extract the file" mean that I need to extract it in my home directory using the gunzip command? If yes, could you please give me the command that I need to type to extract the same to my home directory from a floppy drive. I will download the file on to a floppy drive. I do know how to mount a floppy drive though.

Would you be able to also give me the command that I need to type to install the build essential package as well.

Or if I do the "Post Install" things as suggested in the "Hermanzone" website that is enabling extra repositories, will that have done the install for the "build essentials package?


Best regards


Deepak Agarwal

---

### Post by linear on 2006-03-02
First, you might want to read this:

[https://wiki.ubuntu.com/CompilingSoftware](https://wiki.ubuntu.com/CompilingSoftware)

It demonstrates most of the commands you need.

Next, you can install build-essential either using Synaptic, or with this command:

```
sudo apt-get install build-essential
```
(Don't need extra repositories for this.)

---

### Post by agarwaldvk on 2006-03-03
Guys

I did the :-

sudo apt-get install build-essential

It went through ok!

After that I did :-

sudo make cups-install-lbp660-a4 as suggested and it complained

"No rule to make target 'cups-install-660-a4'". Stop

Any further suggestions please!


Best regards


Deepak Agarwal

---

### Post by az on 2006-03-03
[QUOTE=agarwaldvk]Guys

I did the :-

sudo apt-get install build-essential

It went through ok!

After that I did :-

sudo make cups-install-lbp660-a4 as suggested and it complained

"No rule to make target 'cups-install-660-a4'". Stop

Any further suggestions please!


Best regards


Deepak Agarwal[/QUOTE]


Are you in the build directory?  Do you have libcupsys2-dev installed (you need that to compile stuff for cups.  Any library has the associated headers for compiling against.  See the -dev package for that lib.)

---

### Post by agarwaldvk on 2006-03-04
Dear Azz

Where do I find the build directory?

I looked in Home and lib - it wasn't in there.

Or am I on a totally wrong track. Please help - I need more help!


Best regards


Deepak Agarwal

---

### Post by agarwaldvk on 2006-03-05
Hi Everybody

Can someone help me with this?

I have a Canon LBP 660 laser printer. I am trying to install a driver under Breezy for the same that I found on one of the sites. But have so far not been able to for a variety of reasons - could you please have a look at some of my earlier postings where I have indicated the kinds of problems I am having and what can I do to fix them. I would like to be able to print on printer.

I even tried with on of the default selections of Ubuntu (it recommended LBP1000 but I could get it to print a test page). As an aside, I was able to get my other Canon i560 on S800 driver (on Ubuntu 5.04) as suggested by one of the Ubuntu users earlier.

Any help would be greatly appreciated.


Best regards


Deepak Agarwal

---

### Post by linear on 2006-03-07
Let's start from the beginning.
 
For the sake of illustration, let's say you have the driver software tar file in **/usr/local/src**, and that it's named **lbp660.tar.gz**.
 
Open a terminal window, and type:
```
cd /usr/local/src
tar -zvxf lbp660.tar.gz
```
This will create a new directory named **lbp660** within /usr/local/src. Change to this directory:
```
cd lbp660
```
This is what someone earlier called the "build" directory. Now type:
```
make
```
Were there any error messages? If so, stop and try to figure out what's wrong (could be missing a library). If all looks ok, type:
```
sudo make install
```
Any errors here? If not, now try:
```
sudo make cups-install-lbp660-a4
```
If you get the same error as earlier, then something is wrong with the installation scripts provided with the driver. I suspect you could finish the printer setup in Ubuntu without the script, but am not sure.

---

