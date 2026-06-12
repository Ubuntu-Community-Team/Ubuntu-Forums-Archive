---
title: "No display after install and boot"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by baldmancan on 2007-05-09
I installed Xbuntu alt then when I restarted I got the little "mouse" boot progress bar. Then display goes black and nothing else happens. Any suggestions are apreciated.
Thanks

---

### Post by Ozeuss on 2007-05-09
did you try to load it in safe mode or in a nonquiet splash so you can see the output?

---

### Post by baldmancan on 2007-05-09
Thanks for responding,
No I did not know how to do that.
I am reading all I can but am new to this operating system.. 
I refuse to give Microsoft another dime to upgrade to vista or anymore of  their noncompatible, guaranteed to crash and make my life hell, software. 
13 years of their crap is enough.

I know there is a significant amount of things I have to learn.
With the forums members help and patience I am willing to trudge on through.
(having said all that...)
I dont know how to boot into safe mode or in a nonquiet splash.
Is it something I can do during the boot process? 
Please walk me through this or direct me to an explanation of keystrokes to accomplish the task.

Thanks,
Steve

---

### Post by baldmancan on 2007-05-09
I also forgot to mention I tried to run a live cd of regular Ubuntu and it also failed to display after boot.

---

### Post by Terl on 2007-05-09
Could you post your system specs please?  This would be helpful in figuring out what may be wrong.  I am concerned because the live cd did not run for you either.  Did you burn these yourself and at a slower speed?

---

### Post by celsdogg on 2007-05-10
i am also having the same problem with feisty.

i installed it on my desktop machine. i had a hard time getting the display to show using the live cd too. i had to add vga=771 to get it to at least show.

it seems that by default ubuntu is trying output a video resolution or refresh rate that my monitors cant handle. one monitor tells me that the input is out of range, the other shows lines across it.

i have a dual monitor setup, using a samsung syncmaster 941bw (1440x900) and a aopen F95gs (1280x1024). the samsung is using dvi, and the aopen is using regular 15 pin d-sub. these are connected to a geforce 6600 x16 pcie with 256mb gddr3. the system is an athlon 64 3200+ (venice) with 1gb of ram on an MSI K8N mobo.

any suggestions? i can get to a command line and i tried changing xorg.conf a little bit, but i didnt know very well what to do.

---

### Post by celsdogg on 2007-05-11
anybody?

---

### Post by alexh on 2007-05-11
I just installed it yeaterday and am having the exact same problem. When i try to boot into it for the first time the screen goes just goes blank, i assume it is because it is trying to display in a resolution that my monitor can't cope ieth but i have no idea how to change it. 

Help please.

---

### Post by baldmancan on 2007-05-11
The system I installed this on is an old hp desktop it has a 500 mhz celeron processor, 512mb ram, and a 60 & 20 gb HD. The monitor is an older 20" display. 
It was running xp, but very slowly.
What other information would be helpful?

---

### Post by celsdogg on 2007-05-11
i have been using this thread to help me solve this problem:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

it deals with killing X then reconfiguring it using the applet. no matter what i try, it wont work.

---

### Post by celsdogg on 2007-05-11
[http://ubuntuforums.org/showthread.php?t=233481](http://ubuntuforums.org/showthread.php?t=233481)

there is another thread that may help some. didnt for me :(

still looking for the solution. . .

---

### Post by celsdogg on 2007-05-11
i just found out that the output is at 80.9Khz / 180.3hz which none of my monitors can support. not even my only crt that i hooked up just for testing. no matter how i configure x, it doesnt change. right now the max resolution is at 1024x768.

someone has to have had experience with this.

---

### Post by baldmancan on 2007-05-14
does anybody have a solution yet?

---

### Post by baldmancan on 2007-05-14
My Monitor specs are:
Display 
Diagonal Size: 21" 
Viewable Size: 19.8" 
Dot Pitch / Pixel Pitch: 0.28 mm 
Max Resolution: 1600 x 1200 / 60 Hz 
Max Sync Rate (V x H): 120 Hz x 82 kHz 

Could this be a problem?

---

### Post by baldmancan on 2007-05-14
Other Specs:
Resolutions supported 1120 x 768 • 1152 x 870 • 1280 x 1024 • 1600 x 1200 • 640 x 480 • 800 x 600 • 832 x 624 
Synchronization Range - Vertical  55 - 160 Hz 
Synchronization Range - Horizontal  31 - 96 kHz 
Native (Recommended) Resolution 1280 x 1024

---

### Post by celsdogg on 2007-05-14
i think the problem is the horizsync range and the vert refresh range.

i installed the ubuntu server 64 bit edition, then once that was installed and used apt to get the ubuntu desktop:

sudo apt-get install ubuntu-desktop

after i did this ubuntu came up fine, altho it was using the vesa driver, and the resolution on both my lcd's was 1024x768. i checked xorg.conf in /etc/X11/xorg.conf and the previously mention ranges are at:

HorizSync 28-72
VertRefresh 43-60

previously when i installed feisty32 bit desktop edition the ranges were always higher such as:

HorizSync 30-100
VertRefresh 50-160

so i would try editing the xorg.conf file and lowering those ranges. if that doesnt work, installing the server edition worked (i didnt install any dns, etc.) and then installing ubuntu-desktop.

now i just got to work on getting the nv driver utilized, and setting up dual monitors.

---

### Post by celsdogg on 2007-05-14
ok, i found the real solution. this worked for me anyway.

once the screen comes up, you have probably heard the sound that indicates that the login screen is there, cept you cant see it. you may simply have the incorrect drivers in use, or ones that dont work quite well.

*press ctrl + alt + F1*

this gets a terminal. login to the terminal and kill gdm or kde (or whatever) by typing

*sudo /etc/init.d/gdm stop*

or kde instead of gdm, etc. whatever your desktop manager is.

once that is done install the proper video drivers through apt. i have an nvidia card, so to do that i used:
[I]
sudo apt-get install nvidia-glx nvidia-kernel-common[/I]

then 

*sudo nvidia-xconfig*

this will set the video driver to *nvidia* instead of *nv* or whatever was in there. if not using an nvidia card, go to *ubuntuguide.org* and find the instructions for your video card.

once that is done press

*sudo /etc/init.d/gdm start*

the login screen should appear and you should be good to go.

---

### Post by baldmancan on 2007-05-15
Well, after  days of frustration, 
I borrowed a friends copy of knoppix 5.1.
This Linux version booted from cd and was up and  running in  about 3 minutes. 
No problems, display working fine. 
No funky video commands or driver searching
Don't really know why ubuntu did not work for me... maybe future releases will work better.
Anybody who can't get ubuntu to work might try Knoppix.

---

### Post by ianmdev on 2007-05-17
I regret to say I've had similar problems with Feisty Fawn.  Worse still is that it is all intermittent.

This is something that might hurt Ubuntu a little - which is a pity since it's such a great distro. [This is starting to remind of the package management problems with SUSE 10.1, etc.]

I've experienced problems like this with other distros, but it was relatively easy to sort out.  There are a number of different ways to do it, but it's a good idea to know how to edit "xorg.conf" directly.

It doesn't appear to be that easy to sort out on Ubuntu, although I'm relatively new to this distro.

In any case, it appears that the problem has to do with the grub boot configuration.  This helped me quite a bit:

[LIST=1]
[*]Open /boot/grub/menu.lst with a text editor
[*]Locate the "kernel" entry under the "title" entry for "Ubuntu, kernel 2.6.20-15-generic"
[*]Where it says "quite splash" or "splash quiet", just add "vga=771"
[*]Save the file and reboot
[/LIST]

For me, nothing was happening at all after the initial bootup!  I couldn't even SSH into the box from another machine.  Once I made the above change to the grub configuration, everything ran (and continues to run) smoothly.

Hopefully, this will help someone else out there.

Obviously, this doesn't help you if you're running the Live CD (btw, I think the Live CD is awesome).  Let's hope these minor problems get resolved soon [people just want to boot off the Live CD, play with the distro, and have fun - with no pain involved].

All the best.

---

### Post by celsdogg on 2007-05-18
^^^ i have used vga=771 for the live cd. hit escape at the boot menu to get a CLI. then type in *live vga=771*

---

### Post by osaurus on 2007-10-27
I had a similar problem installing 7.1 with an older Samsung monitor.  After the hard drive stopped churning, I used <Ctrl> <Alt> <+> to change the screen resolution.  While holding <Ctrl> <Alt>, press <+> once, wait a couple of seconds to see if the new resolution works, then repeat until (hopefully) your display is usable. (I found the right resolution on the 5th stop of the rotation).  Once you get to the desktop,  you can set the resolution for your monitor manually.  Good luck!

---

