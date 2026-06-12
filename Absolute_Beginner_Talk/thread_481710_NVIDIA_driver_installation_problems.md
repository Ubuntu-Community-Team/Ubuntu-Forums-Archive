---
title: "NVIDIA driver installation problems"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Adverse Entropy on 2007-06-22
Hello there.

I'm a new Linux user who is just learning the ropes.

I've been trying to install NVIDIA's display driver, and have had no luck.

Here's what I've been doing, and what I think should be working:

* Download driver from site ([http://www.nvidia.com/object/linux_display_ia32_100.14.09.html](http://www.nvidia.com/object/linux_display_ia32_100.14.09.html))
* sudo init 3
* ch /home/*username*/Desktop **<---(the driver was saved to desktop, *username* replaced by my username)**
* sudo sh NVIDIA-Linux-x86-100.14.09-pkg1.run

It runs, but I am met with this error:

**ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).**

Is there something inherently wrong with what I'm doing? If anyone can shed some light on the matter, I'd greatly appreciate it.

(if there's already a topic on this, feel free to direct me to the existing one and delete)

Thanks! :)

---

### Post by Crafty Kisses on 2007-06-22
> **Adverse Entropy said:**
> Hello there.

I'm a new Linux user who is just learning the ropes.

I've been trying to install NVIDIA's display driver, and have had no luck.

Here's what I've been doing, and what I think should be working:

* Download driver from site ([http://www.nvidia.com/object/linux_display_ia32_100.14.09.html](http://www.nvidia.com/object/linux_display_ia32_100.14.09.html))
* sudo init 3
* ch /home/*username*/Desktop **<---(the driver was saved to desktop, *username* replaced by my username)**
* sudo sh NVIDIA-Linux-x86-100.14.09-pkg1.run

It runs, but I am met with this error:

**ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).**

Is there something inherently wrong with what I'm doing? If anyone can shed some light on the matter, I'd greatly appreciate it.

(if there's already a topic on this, feel free to direct me to the existing one and delete)

Thanks! :)
Looks like you have a window open with a X server going, close that, and retry the installation.

---

### Post by chamberlain2006 on 2007-06-22
A good idea for you would be to use a program called "envy" ([http://www.google.ca/url?sa=t&ct=res&cd=3&url=http%3A%2F%2Fwww.albertomilone.com%2Fnvidia_scripts1.html&ei=bWp8Rre_Gp3shwKz-sy6Aw&usg=AFQjCNHTTLRY1InWUcLEQ5I1KqVJ8hnCxg&sig2=6mOfpUqCVWrEFX1bh7eT2g](http://www.google.ca/url?sa=t&ct=res&cd=3&url=http%3A%2F%2Fwww.albertomilone.com%2Fnvidia_scripts1.html&ei=bWp8Rre_Gp3shwKz-sy6Aw&usg=AFQjCNHTTLRY1InWUcLEQ5I1KqVJ8hnCxg&sig2=6mOfpUqCVWrEFX1bh7eT2g))
You can use the graphical tool to install the proper driver.  Let me know if you need more help!

---

### Post by CheShA on 2007-06-22
You could try downloading and installing **[envy]("http://www.albertomilone.com/nvidia_scripts1.html")**, which will automatically detect and install drivers for you.  get it **[here]("http://www.albertomilone.com/nvidia_scripts1.html") **

---

### Post by Crafty Kisses on 2007-06-22
> **chamberlain2006 said:**
> A good idea for you would be to use a program called "envy" ([http://www.google.ca/url?sa=t&ct=res&cd=3&url=http%3A%2F%2Fwww.albertomilone.com%2Fnvidia_scripts1.html&ei=bWp8Rre_Gp3shwKz-sy6Aw&usg=AFQjCNHTTLRY1InWUcLEQ5I1KqVJ8hnCxg&sig2=6mOfpUqCVWrEFX1bh7eT2g](http://www.google.ca/url?sa=t&ct=res&cd=3&url=http%3A%2F%2Fwww.albertomilone.com%2Fnvidia_scripts1.html&ei=bWp8Rre_Gp3shwKz-sy6Aw&usg=AFQjCNHTTLRY1InWUcLEQ5I1KqVJ8hnCxg&sig2=6mOfpUqCVWrEFX1bh7eT2g))
You can use the graphical tool to install the proper driver.  Let me know if you need more help!

Yeah, that might do the trick.

---

### Post by Adverse Entropy on 2007-06-22
ENVY seemed to do it! Thanks so much.

But, being anal, I can't help but wonder why it didn't work for me by the normal method. Unless there are things using X Server in the background that I'm unaware of, I can't imagine it's that. The only thing I can think of is that changing the init (however you'd say that) didn't do the job.

Then again, I'm a noob. Oh well, thanks anyways!

---

### Post by Crafty Kisses on 2007-06-22
> **Adverse Entropy said:**
> ENVY seemed to do it! Thanks so much.

But, being anal, I can't help but wonder why it didn't work for me by the normal method. Unless there are things using X Server in the background that I'm unaware of, I can't imagine it's that. The only thing I can think of is that changing the init (however you'd say that) didn't do the job.

Then again, I'm a noob. Oh well, thanks anyways!

It sounds like you had a X server window running.

---

### Post by PandaGoat on 2007-06-22
Installing the nvidia driver is simple without envy.  The problem is that an Xorg session is running.  Put the driver in your home folder, and to switch to a screen without xorg using the shortcut alt + control + F2.  Log in and kill gdm and Xorg:
```
sudo killall gdm; sudo killall Xorg
```

Your current directory is home, which is where the nvidia driver binary is, so run:
```
sudo sh NVIDIA-Linux-x86-100.14.09-pkg1.run
```
Once you type NV you can press tab and it will complete the rest of the file name for you.

It will complain about not have the correctly configured kernel module and will attempt to download one and fail, then attempt to build it.  You will need kernel headers and build-essential.
```
sudo apt-get install build-essential linux-headers-2.6-486
```
You can do this before you kill xorg to use synaptic just in case you need a different linux headers version or if you can't remember the package names.

After it builds it will install and ask to reconfigure xorg.conf [accept].  Then reboot.

---

### Post by chamberlain2006 on 2007-06-22
The X server is just what makes things "graphical" on your screen, so installing a graphics driver might not be possible while it's running.  I find that Envy is very reliable, so I would usually use it instead of a manual method.

---

### Post by Crafty Kisses on 2007-06-22
> **chamberlain2006 said:**
> The X server is just what makes things "graphical" on your screen, so installing a graphics driver might not be possible while it's running.  I find that Envy is very reliable, so I would usually use it instead of a manual method.

Yeah same here, but the manual method is good too.

---

### Post by zanazzi on 2007-07-05
Hello all 

Guess what this thread aint dead yet!!

Im a noob too, very much a noob as u'll see ...

im having problems with these nvidia drivers to.

I have just installed  gutsy gibbon and want to get compiz/beryl working but my 7900GTo obv wont work yet

i have attempted to follow the commands suggested by Pandagoat in post #8

2 problems occured for me;

1st: the "sudo killall Xorg" command failled, i had an error msg saying that it couldn't kill Xorg!!!!!!!!!

2nd: the final bit, getting headers failed too

Plz help i really need to understand whats going on

thanx for ur time on this matter (again)

---

