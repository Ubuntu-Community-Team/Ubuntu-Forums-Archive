---
title: "problem with monitor resolution"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by davexnet on 2007-11-02
Hello,
I'm new to linux.  I created the 7.10 x386 CD and booted the product.
After looking around in there a while I decided to install it using the graphical
interface.

Problem is, the monitor resolution is stuck at 800*600, and I can't see the bottom of the
dialog boxes to access the OK button.  The native res of my LCD is 1680*1050.
Is the problem a missing Nvidia graphics driver or possibly the monitor INF file equivalent?

I read a little in the sticky about updating the product.
Should the product be installed b4 this step, or can the updates be applied to the
temporary (ram disk) version I'm looking at now - and then install ?

Thanks for any enlightenment.

Dave

---

### Post by Hospadar on 2007-11-02
What happens when you go to System->Preferences->Screen Resolution? do you get any more options?

You could try installing the nvidia drivers (while in the livecd) with the restricted driver manager (in System->Administration) and you'd probably need to restart your X with ctrl-alt-backspace.  you might then need to go change your resolution the normal way, or try changing it with nvidia-settings, from a terminal (Applications->Accesories->Terminal) type nvidia-settings and poke about for the resolution setting and pick what you want.

If that doesn't work, try going to a terminal (ctrl-alt-F1) and typing "sudo dpkg-reconfigure xserver-xorg" you'll get a big ugly dialog with a ton of pages of options that you can just pick the defaults through, and you'll eventually get to one with a ton of monitor options, and you can scroll down and select the resolution you want with spacebar (and deselect other resolutions) and then continue with pressing enter until you get out of the dialog.

Then restart X with "sudo /etc/init.d/gdm restart" and then do a ctrl-alt-F7 to get back to your gui.

If none of this stuff does it for you, you could use the alternate install cd, which is a command line install (but still installs a gui)  It will be easier to get stuff working once you have and install probably.

---

### Post by davexnet on 2007-11-02
Hello, thanks for your detailed answer.
Regarding preferences/screen resolution, the other item present is
640*480, which obviously even worse.

I'll take a look a your suggestions and see what I can uncover.

Cheers,
Dave

---

### Post by poudin on 2007-11-02
i had good luck resolving problems with Nvidia driver by installgin Envy.

sudo apt-get install envy

After installing Envy it will appear in your Applications --> System Tools Menu..run it and it should auto detect and install the correct Nvidia driver for your system.

---

### Post by davexnet on 2007-11-03
Hello, I tried
sudo apt-get install envy
but I got package not found, so  didn't go any further than that.

So I tried Hospadar's suggestion and instaled the Nvidia driver from
restricted driver manager, and then did ctrl-alt-backspace.

X was restarting and a dialog warning box came up that said
"Ubuntu is running in low graphics mode", with options of
"configure", "shutdown" and "continue"

I chose "configure" and selected and set my monitor to it's correct res and refresh rate.
OK'd out, but it hung...
Last message on the screen was,
"running local boot scripts (/etc/rc.local)"

I feel like I'm getting closer, but not sure what to try next.
Thanks for any further info...
Dave

---

### Post by alienexplorers on 2007-11-03
Load the restricted drivers under:
> system>administration>restricted drivers manager
If you are running a nvidia card you can then run:
> gksudo nvidia-settings

I also have a link to ENVY in my sig line.

---

### Post by mdpalow on 2007-11-03
you never mentioned anything about enabling the restricted drivers after installation? Did you do that? If not, click SYSTEM -> ADMINISTRATION -> Restricted Drivers Manager.

Look if there is an nVidia driver just sitting there waiting for you to ENABLE it.

Good luck...

---

### Post by davexnet on 2007-11-03
Hello,
re: gksudo nvidia-settings,
is this run before X is restarted?  Presumably it must be, because I am unsbale to restart
X successfully.


Secondly, I saw your link to envy, and found this link.
[http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu10_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu10_all.deb)

How do I use it to install envy.  Will just linking to it from Firefox install it?

(I'm typing this from Windows xp; I'm running the Ubuntu directly from the CD.
I would like to install it, but want to get this display problem fixed first.
As you can see, I know almost nothing about Linux - but i'm ready to learn.)

Dave

---

### Post by alienexplorers on 2007-11-03
gksudo nvidia-settings is run after you enter X.  You may need to run from a command prompt:
> sudo dpkg-reconfigure xserver-xorg

---

### Post by davexnet on 2007-11-03
I think I must be missing something here .

I haven't actually installed the product to the hard drive.
I'm just running it live from the CD, so every time I restart, it goes back to the
beginning, just as it exists on the CD.

I would like to install it, but as I mentioned in my first post, I can't see the buttons in the dialog
boxes due to the poor monitor resolution.

I would like to be able to fix the resolution problem in the LIVE CD SESSION so that I
can install the product  !!!

Dave

---

### Post by Duck2006 on 2007-11-03
Have you tryed doing it from recover mode When it loads it loads in to the command promp.

---

### Post by mc4man on 2007-11-04
maybe try the alternate install cd

---

### Post by davexnet on 2007-11-04
Thanks very much for everybody's help.
I eventually got ENVY to install.
To get it to work, I had to enable "universe" and "multiverse"
(Whatever that does)

But after the Nvidia driver was properly installed, the setup wanted to reboot the machine.
That's unacceptable, since I was still in LIVE CD mode.

I canceled the reboot, and used ctrl-alt-backspace to restart X.
It worked, except the mouse pointer was completely missing.. As you can see, getting nowhere fast.

I eventually found the solution, and it was staring at me but I didn't see it.

When you boot the CD, I chose the top option, start or install Ubuntu.
The second option, start Ubuntu in safe graphics mode, is the thing that will enable me to
actually install the product.  The first choice gives me 800*600 (to small), whle the 2nd gives
1280*800 (or something like that) anyway it's good enough.  Now I can install it.

I've got vista on this machine, and I'm going to use the vista MBR/boot menu to boot linux usng this
method:
[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)

Cheers,
Dave

---

