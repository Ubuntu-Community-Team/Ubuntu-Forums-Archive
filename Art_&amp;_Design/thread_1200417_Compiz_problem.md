---
title: "Compiz problem"
date: 2009-06-30
forum: Art &amp; Design
---

### Post by LinuxGreg on 2009-06-30
Ok well i have done a TON of searching and no one has been able to solve my problem...
I ad compiz running perfectly on my PC but i had just booted it up this morning and i got an error message that my AWN would not start.  Then i found my Effects to not be working.  I had thought this was odd so i went to appearance and what do you know? My visual effects were off.  i said "oh, well i will just turn them on" only to realize it would not enable.

Any help would be apreciated! I'm running 9.04 Jaunty And have n Nvidia graphics card but imnot positive exactly what version.

i get this message when i got to my x server thing

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by Technique13 on 2009-06-30
yeah i had the same problem, it comes with an update of ubuntu with the update manager that will toy with your nvidia drivers. The trick is to re-install your Nvidia drivers using the package downloadable from the website. then make sure you turn off your X-server and use console (alt-f2) to install. 

sudo /etc/init.d/gdm stop

the above line turns your x-server off and replacing 'stop' with 'restart' will restart it after the installation.

Now, in my experience this will not work, instead it will prompt you and say that your x-server is not working when you try and restart the computer. From here I selected the option to "restore last known configuration" and then subsequently re-installed the Nvidia drivers a second time. This solved the problem and my Compiz works again.

Thats how i solved the problem, im not sure if this will work for you, but your symptoms sounded familiar, hopefully someone else can provide less ad-hoc fix.

Cheers, and good luck

---

### Post by renkinjutsu on 2009-06-30
> **LinuxGreg said:**
> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

do exactly that... run ```
sudo nvidia-xconfig
```and restart

---

### Post by LinuxGreg on 2009-06-30
ok i did the sudo nvidia -xconfig thing first. it allowed me to enable my custom visual effects (for compiz) and now compiz is working GREAT!   On the down side my AWN dock that starts up on log in is just a whit bar going across the bottem of the screen and when i click preferences it is just a blank white window. My emerald themes are not working either...in fact i dont even have one.  My widows dont have a title bar so the only way to close them is file>quit.

Thanks again for the compiz, but any help with these would be apreciated

and lucky me the terminal is also blank

also i can not seem to find a downloadable package on the Nvidia site.  

I finally got back to square 1 and when typing in the "sudo nvidia-xconfig" command this happened....

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'




Here is my graphics card info....

Graphics Processor: GeForce2 MX/MX 400
VBIOS Version:        03.11.01.30.97
Memory:                 64 MB

Bus Type:                AGP 4X
Bus ID:                   1:0:0 
IRQ:                       16
X Screens:              Screen 0
Display Devices:      Princeton Graphics Systems PrincetonEO705 (CRT-0)

---

### Post by renkinjutsu on 2009-06-30
hmm.. if compiz compositing is working, that should mean that your video drivers are working.. go to ccsm (compiz config settings manager) and enable Window Decorations..

if that's already checked, you can try pressing ALT+F2 and type ```
compiz --replace
``` instead of enabling compiz from the desktop effects menu.

---

### Post by LinuxGreg on 2009-06-30
neither of those worked, i even tried reinstalling both awn and compiz multiple times

I also ran a compiz check and everything was OK
|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

---

