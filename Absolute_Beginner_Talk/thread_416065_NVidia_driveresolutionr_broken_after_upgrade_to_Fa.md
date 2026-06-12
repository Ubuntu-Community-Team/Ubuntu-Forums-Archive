---
title: "NVidia drive/resolutionr broken after upgrade to Fawn"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Charco on 2007-04-20
I just upgraded and I hate it. My whole system is messed up. First, I logged on normally, but the whole screen was black. I switched from my X-Server session that had Beryl on it to the Failsafe Gnome. I tried to run Warcraft, but it didn't work. Since both of those didn't work, I decided to install the new Automatix2 and remove the video driver. I restarted and then the resolution became max 800x600. I reinstalled the NVidia driver through Automatix, but this time I got an error when it loaded. So then ran automatix-nvidia-restore. Now I am back at a louse 800x600, with no Warcraft capabilities or Beryl. Arg, this install has just been so horrible, I never should have clicked upgrade. Please help! :(

I found this, but I have no idea what it means!
> 
Q: My X server fails to start, and my Xorg log file contains the error: "(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!"

A: Nothing will work if the NVIDIA kernel module doesn't function properly. If you see anything in the X log file like "(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!" then there is most likely a problem with the NVIDIA kernel module. First, you should verify that if you installed from rpm that the rpm was built specifically for the kernel you are using. You should also check that the module is loaded ('/sbin/lsmod'); if it is not loaded try loading it explicitly with 'insmod' or 'modprobe' (be sure to exit the X server before installing a new kernel module). If you receive errors about unresolved symbols, then the kernel module has most likely been built using header files for a different kernel revision than what you are running. You can explicitly control what kernel header files are used when building the NVIDIA kernel module with the --kernel-include-dir option (see sh NVIDIA-Linux-x86-1.0-4349.run --advanced-options for details).

Please note that the convention for the location of kernel header files changed approximately at the time of the 2.4.0 kernel release, as did the location of kernel modules. If the kernel module fails to load properly, modprobe/insmod may be trying to load an older kernel module (assuming you've upgraded). cd'ing into the directory with the new kernel module and doing 'insmod ./nvidia.o' may help.

Another cause may be that the /dev/nvidia* device files may be missing. To recreate this files simply run this script (as root). It assumes your users who have GUI access are in group "video"):

for i in 0 1 2 3 4 5 6 7; do
  node="/dev/nvidia$i"
  rm -f $node
  mknod $node c 195 $i  || echo "mknod \"$node\""
  chmod 0660 $node      || echo "chmod \"$node\""
  chown :video $node    || echo "chown \"$node\""
done
         
node="/dev/nvidiactl"
rm -f $node
mknod $node c 195 255   || echo "mknod \"$node\""
chmod 0666 $node        || echo "chmod \"$node\""
chown :video $node      || echo "chown \"$node\""

Finally, the NVIDIA kernel module may print error messages indicating a problem -- to view these messages please check /var/log/messages, or wherever syslog is directed to place kernel messages. These messages are prepended with "NVRM".


---

### Post by Charco on 2007-04-21
Bump. Sorry, but nothing will load, and I'm desperate.

---

### Post by Charco on 2007-04-22
Ok, I changed the xorg.conf to load the nv driver, and now it loads at least.
But then I install the nvidia driver from the .sh file on thier site. Then I apt-get the nvidia-glx.
Then I:
modprobe nvidia

I get:
FATAL: Error running install command for nvidia

And X wont start :(

Why!!!!

---

### Post by dan_linder on 2007-05-03
If it makes you feel better, I'm in the same boat.  A new 8600 card in an X86_64 install.  

Are you using the latest 100.14.03 driver?

At one time a work-around was to boot up and switch to a text console, kill kdm (sudo /etc/init.d/kdm stop), then re-run the installer, then restart kdm (sudo /etc/init.d/kdm start).

That then allowed me to run X ... until today... :(

Does that work for you?

Dan

---

### Post by dan_linder on 2007-05-03
Just found that this has apparently been reported as a bug (at least my case):

The last link was a bit more helpful, but hasn't provided the total fix.

Launchpad bug site thread: [https://bugs.launchpad.net/ubuntu/+bug/107646](https://bugs.launchpad.net/ubuntu/+bug/107646)

Last link in thread: [https://bugs.launchpad.net/ubuntu/+bug/107646/comments/21](https://bugs.launchpad.net/ubuntu/+bug/107646/comments/21)

I'm still working on it on my system... 

Dan

---

### Post by dan_linder on 2007-05-03
Ah, think I got it... :)

I ended up following some of the pre-cleanup steps that are mentioned in this URL under the "Method 2" section:

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED)

Basically, here is what I did:
[LIST=1]
[*]sudo apt-get install linux-headers-`uname -r` build-essential gcc xserver-xorg-dev
[*]sudo apt-get --purge remove linux-restricted-modules-`uname -r` linux-restricted-modules-common nvidia-glx nvidia-settings nvidia-kernel-common
[*]sudo rm /etc/init.d/nvidia-*
[*]sudo /etc/init.d/gdm stop (OR "kdm stop" if you use KDE)
[*]cd “directory_where_you_have_the_nvidia_installer”
[*]sudo sh ./NVIDIA-Linux-x86_64-100.14.03-pkg2.run
[*]Use the defaults for the installer.
[/LIST]

At this point I could run "X" and got the usual X11 "hash" background.  Running /etc/init.d/kde start I was able to login.  Running "glxgears" in a terminal brought up the three gears, and it was reporting nearly 9000 fps - much better than the 25-50 I was getting with the software MesaGL drivers.

I think the key things for me were:
:arrow:Using the --purge to remove _ALL_ the files that were being brought over with the prepackaged nvidia .deb packages.
:arrow:Running the NVIDIA installer _without_ using the --update.  I believe that was possibly pulling in the other driver version that was confusing my system.
:arrow:I did NOT install the gcc-3.4 compiler

So, just to recap, here is my system that is (apparently) working now with X11:
AMD Athlon X2 64 6000 running 64bit Kubuntu installation
eVGA NVidia 8600 video card

My other problem that I had where the NVidia driver would "disappear" after each reboot seems to have been fixed with this, too.

Good luck with your installations!

Dan

---

