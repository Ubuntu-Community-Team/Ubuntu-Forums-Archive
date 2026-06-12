---
title: "Total newbie needs help with NVIDIA drivers"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by leman on 2008-02-06
I just got a new hard drive recently, and once I'd shifted a lot of my Data around I found that I completely emptied a couple of my drives. So I decided to use one of them to give Linux a go, and chose to install the latest version of Ubuntu. Unfortunately, I'm having great difficulty getting my dual screen setup to work the way it does in Windows XP. I've been trying without success to install the latest Linux-64 drivers from NVIDIA's website. I've found a few guides for installing NVIDIA drivers, but they're all for earlier versions of Ubuntu or for completely different Linux distributions.

So, please could someone point me to how to install the latest NVIDIA-Linux-x86_64-169.09.pkg1.run on Ubuntu 7.10 (64-bit)? Thanks for any help you can give. :)

---

### Post by dca on 2008-02-06
You can give this a read:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
 
I think in the 'Add/Remove' option in Applications menu, if you enable all available apps in the 'show' drop-down menu they're a few nvidia driver install options...

---

### Post by sirzepp on 2008-02-06
I've not been using the "restricted drivers" in the Ubuntu install.  Once I install Ubuntu, I run over to Nvidia's site, download the appropriate file(the one you have).  Then I make sure I've got all the kernel header files and other requirements listed on Nvidia's site(I think the instructions are actually on the page you click to download the ".run" file.  After all of that, I switch to a console (ctrl-alt f2) and type "sudo /etc/init.d/gdm stop".  I enter my password, and GNOME stops.  Then I run the Nvidia install...if you downloaded it to your home directory...make sure your command line is pointing there "~/" and type "sudo sh NVIDIA*.run".  The install should run.  If you installed all the headers AND you haven't install the ubuntu restricted drivers, then the install should run without any errors.  It will ask you a few questions and make a few statements, but you shouldn't get any errors.  After that...you are dropped back to the command line and you can type "sudo reboot" to restart your computer.

For me, this works best.  I understand it.  The only problem I've found is if I install the restricted drivers from the restricted drivers applet in Ubuntu.  If I do that, then I can't get my system to run in high-res AND I can't install the NVIDIA drivers without doing a fresh install.  I'm a total newb...so I'm sure there is a better way...but this has worked for me.

Oh, and everytime you install/update to a new kernel...your system will revert to the "low-res" error.  Just boot into Ubuntu in low res(hit continue on the dialog that will come up).  Run the "sudo dpkg-reconfigure xserver-xorg" to get back to running the "nv" 2-d driver with a working xorg.conf.  Reboot.  Then you can repeat the process I outlined above to recompile the NVIDIA drivers for your new kernel.

Like I said, this is working for me.  It may be clunky, but it works(for me).  Hope that helps.

---

