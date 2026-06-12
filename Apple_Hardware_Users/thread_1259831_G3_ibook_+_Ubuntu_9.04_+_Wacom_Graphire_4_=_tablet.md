---
title: "G3 ibook + Ubuntu 9.04 + Wacom Graphire 4 = tablet (almost)"
date: 2009-09-06
forum: Apple Hardware Users
---

### Post by cptfx on 2009-09-06
I've been having incredible luck getting my ibook to run Ubuntu thanks to the forums here.  But there is one last thing that has me stumped and I don't even know how where to look for a solution.  So here's the setup

ibook G3 700MHz Dual USB
Wacom Graphire 4 tablet
Ubuntu 9.04 PPC version

The tablet is simply not recognized.  I did a 'sudo cat' to each of the files in /dev/input and nothing reported anything from the tablet.  It is showing up on a 'lsusb' as a Wacom Device.  Plus, I know that the tablet works flawlessly on my desktop and laptop which are both running 9.04 as well.  And when I had 6.1ppc installed on this ibook, it worked.  Not well, but at least it was recognized and could kinda move the mouse around.

My xorg.conf  has been modified all over the place.   I have a copy from my xorg.conf when I was running 6.10 and I tried replacing the wacom sections but to no avail. I think the root issue is that the tablet isn't showing up at /dev/input/wacom (or any of the events) even though it's showing up on the usb bus. So really this could be a question on 'How to get a usb device to respond once it's recognized' or something like that.  But I really don't know what's going on at this point.

What I would like is to know where to look and what type of stuff that I have to change.  

Also, maybe this should be in the hardware laptop section but since it works with my other setups I think it has something to do with the 9.04ppc setup versus the regular 9.04

Any help is greatly appreciated.  I'll continue fiddling with this setup in the mean time.

---

### Post by Favux on 2009-09-06
Hi cptfx,

With Jaunty (9.04) you are "suppose" to use the 10-wacom.fdi rather than xorg.conf to configure the tablet.  So first comment out any wacom entries in xorg.conf and "ServerLayout" if you have it.  In other words try to get it to the default state if you can.

Next make sure both default 0.8.2-2 linuxwacom packages are installed.  Check Synaptic Package Manager that xserver-xorg-input-wacom & wacom-tools are installed.  If not install them and reboot.

If we're lucky it's just the wacom.ko (the usb kernel driver/module) isn't "kicking" in.  So in a terminal enter:
```
dmesg | grep [Ww]acom
```
and let's look at the output.

---

### Post by cptfx on 2009-09-06
Thanks for the reply.  Both 0.8-2-2 packages are installed.  I commented out the lines in xorg.conf.   Rebooted ran dmesg on wacom and nothing happen.  I got no output.  

So, I need to add some wacom driver to the kernel or something like that.  I have no experience editing/doing stuff to the kernel.  So this is going to have to be remedial.  But I certainly welcome the opportunity to learn more about it.  It's a necessary skill that I never *had* to do.  What would be good search terms for approaching this particular problem?  Alternatively, what am I suppose to be doing at this point?

---

### Post by Favux on 2009-09-06
Hi cptfx,

Hopefully nothing that complicated.  With some setups although wacom.ko is present it doesn't "kick" in.  Let's see if yours is one of them.  The wacom.ko should be automatically installed with the "linux-image" for you kernel.  I don't see why it would be different for PPC version.

So let's try adding 'wacom' (without the quotes) to the end of the 'modules' file in "/etc/".  In a terminal:
```
gksudo gedit /etc/modules
```
Save & close.  Reboot.  Then try the dmesg command again.

---

### Post by cptfx on 2009-09-06
nope.  I still get nothing

---

### Post by Favux on 2009-09-06
Hi cptfx,

Ouch.  Hopefully it's not getting complicated.  Try rebooting a few more times.  If that doesn't work see if the wacom.ko is installed.  It should be at:
```
/lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
Where 'uname -r' is your kernel.  Enter it in a terminal without the quotes if you don't know.

And/or you could try:
```
modprobe -l | grep wacom
```

---

### Post by cptfx on 2009-09-06
wacom.ko is not, in fact, present.  And modprobe returned nothing.  And this is, so far, not complicated at all.  Thanks for the help

---

### Post by Favux on 2009-09-06
Hi cptfx,

Sure, not a problem.

I don't understand why you are not seeing it.  Since the directory is there but the wacom.ko isn't maybe in fact it isn't installed with Ubuntu 9.04 PPC "linux-image"?  That doesn't make much sense.  Why don't you search kernel etc. in Synaptic Package Manager.  Consider reinstalling the "linux-image" for your kernel, which has the pre-packaged kernel modules and rebooting and see if it's there now.

You'd have to do some searching/googling to try and find out if wacom.ko is included for your version.  That may take quite a lot of research.  Or you could do a search in your directories to see if it is somewhere.

The other option is to compile a wacom.ko and install it, which isn't too difficult.

---

### Post by cptfx on 2009-09-07
I reinstalled the linux-image package and still no result.  The tablet directory exists because it contains a few other .ko drivers but no wacom.ko.  So, how do I go about installing wacom.ko?  This seems like the best option right now.  And, is wacom.ko the driver for wacom?  Or is there some other better terminology?

---

### Post by Favux on 2009-09-07
Hi cptfx,

Well I guess the packagers for Ubuntu 9.04 PPC "linux-image" left wacom.ko out.  Let's hope there wasn't a reason for it.

What you'll want to do is this HOW TO:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  Except, very important, do not install the newly compiled linuxwacom!!!  In other words in step 5) do not do this line:
```
sudo make install
```
Just do the Jaunty copy line that comes after to get the 0.8.4-1 wacom.ko in place and reboot.  It works for the Intuos4 so why not the Graphire4?  So we are just installing the newly compiled wacom.ko which is the linuxwacom usb kernel driver/module.

---

### Post by Favux on 2009-09-07
Oops!  Forgot to mention you'll need to reinstall the two linuxwacom packages before you reboot.

---

### Post by cptfx on 2009-09-07
Those were very simple instructions. Which, I ultimately managed to mess up.  I did the  'make install'.  So I tried to undo it with a 'make unistall'.  This may have worked but I don't know where to look for feedback.  So I redid the procedure and screwed it up again by doing 'make' in the src folder.  Did another 'make uninstall' and redid everything.  This was the output of the 'make' step:

```
ld: arch/powerpc/lib/crtsavres.o: No such file: No such file or directory
make[4]: *** [/home/cptfx/Desktop/linuxwacom-0.8.4-1/src/2.6.28/wacom.ko] Error$
make[3]: *** [modules] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.28-6-powerpc'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/cptfx/Desktop/linuxwacom-0.8.4-1/src/2.6.28'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/cptfx/Desktop/linuxwacom-0.8.4-1/src'
make: *** [all-recursive] Error 1
```Also, I got several "warning: this is the location of a previous destination" but I don't think those were errors.

So basically wacom.ko is not being generated.  At this point I'm unsure of the damage that I've caused.  I'm not above doing a fresh reinstall and trying again from scratch.  Unless you think that would be pointless.  I'm slowly making my way through the rest of that Forum post on LinuxWacom driver installation to see if anything else relates to my situation.


Finally why do you use ./ all the time?  Couldn't you leave that part out and achieve the same result?  Or does it serve some purpose.

---

### Post by Favux on 2009-09-07
Hi cptfx,

Just making sure your in the right directory.

Check Synaptic and if you have the two linuxwacom packages installed uninstall them.  See Appendix 4 on how to uninstall.  These two commands:
```
sudo apt-get install wacom-tools xserver-xorg-input-wacom
sudo apt-get purge wacom-tools xserver-xorg-input-wacom
```
were what would have removed your current default linuxwacom.  More particularly the second one.

I just wanted to make sure things were cleaned up and then have you reinstall the two default 0.8.2-2 Jaunty packages.  Otherwise for the wacom.ko gali98's HOW TO on post #104 here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)  would be good.  Except you would need to change 0.8.4 to 0.8.4-1.  Also 0.8.3-6 is still in the linuxwacom repository I think.  When you need to reinstall the module that's how you'd want to do it so you don't need to keep reinstalling 0.8.2-2 through Synaptic and the new wacom.fdi I'm hoping we'll get to.

Let's see if you can compile wacom.ko on ppc with the linuxwacom make file.

---

### Post by cptfx on 2009-09-07
I'm still not getting a wacom.ko after running make.  I tried it with 0.8.3-6 and 0.8.4-1 and I had both the wacom packages completely uninstalled when I did it.  Then I tried it with them installed b/c gali98 has them installed at the beginning of that tutorial.  None of those attempts seemed to produce any different outputs.

The errors always start after this:
ld: arch/powerpc/lib/crtsavres.o: No such file: No such file or directory

I don't know what directory arch is supposed to be located in or where this call is being made.  I don't see that line in the MakeFile.

Also, during the step:  'sudo apt-get install linux-header-generic'.  I've been using linux-headers-2.6.28-6-powerpc.  That's my current kernel so that intall doesn't do anything.  Should I be installing headers for a different kernel, or is that just to make sure that the headers are up to date.

---

### Post by Favux on 2009-09-07
Hi cptfx,

Right it's just to make sure that the headers are up to date for the build.

Maybe we found why they didn't include the wacom.ko, they couldn't get it to build.

In the unpacked linuxwacom-0.8.4-1 there's a linuxwacom-0.8.4-1/prebuilt that contains /32 and /64.  It's tempting to wonder if that's where it's asking for arch/powerpc/lib/crtsavres.o.  But I don't know, we're beyond my limited expertise.

When I compile the wacom.ko ends up in linuxwacom-0.8.4-1/src/2.6.27/wacom.ko out of a list of other kernels up to 2.6.31.  It sounds like the makefile isn't set up for ppc.

I don't know if manually adding the directory arch/powerpc/lib/ somewhere would satisfy it and where that would be.

So it seems like with the linuxwacom packages available to you, you could get a serial Wacom tablet working but not a usb tablet.

The LWP site says "Supported OS' Linux & FreeBSD" and doesn't talk about cpu arch that I see.  You could post on general discussion:  [http://linuxwacom.sourceforge.net/index.php/main](http://linuxwacom.sourceforge.net/index.php/main)  and see if someone will help.

Any other thoughts?

---

### Post by cptfx on 2009-09-07
I'll try posting something over at the sourceforge page.

The only other thing that I can think of is that the tablet was registering on a 6.10 build.  Do you think I would be able to pull the wacom.ko from there.  It's a live cd.  Right now I need to get to bed, but if I were to boot that live cd and mount my hda partition.  Would I be able to copy the wacom.ko from the live cd onto my harddrive?  I'm sure that I would have plenty of compatibility problems, but it might be a start.  I'll try playing around with it tomorrow evening.  Any advice  or tips wrt that approach?

---

### Post by Favux on 2009-09-07
Hi cptfx,

I haven't done that but I don't see why you couldn't copy it as long as you can find it.

The usb support, wacom.ko, came in at about version 0.7.9.  So if the linuxwacom version on the CD is about that or more recent you have a shot.  6.10 seems awfully old though.  I don't think 0.7.9 was available until Hardy so it probably came out during Gutsy.  We know the more recent wacom.ko's work for 0.8.2-2 anyway.

---

### Post by Favux on 2009-09-08
Hi cptfx,

You could try one of these:  [http://packages.debian.org/search?searchon=contents&keywords=wacom.ko&mode=exactfilename&suite=unstable&arch=powerpc](http://packages.debian.org/search?searchon=contents&keywords=wacom.ko&mode=exactfilename&suite=unstable&arch=powerpc)  from  [http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)  There were also some from 2.6.26 (stable).  I searched packages with wacom.ko and powerpc.  Don't know if they'll work.

On the HOWTO at the LWP site I found:  [http://linuxwacom.sourceforge.net/index.php/howto/ppcwcmdrv](http://linuxwacom.sourceforge.net/index.php/howto/ppcwcmdrv)  I think it's too old to be of immediate use, but it could point you in the right direction.

---

### Post by cptfx on 2009-09-09
Alright here's an update of what I've been up to.  This is more or less so that I can keep track of what I did, but hopefully it might help someone else out.  The process is really just one of a monkey sitting at a keyboard.  I really don't know what I'm doing but I'm probably learning something atleast.  Basically, I'm recompiling a new kernel, but it's a long process and I've got enough text for a post.  So here it goes.

I tried to install the Debian wacom stuff without any success. Then I tried to pull wacom.ko from the 6.10 live cd. I got it and, as I was in the process of copying it to the modules folder, I saw that I already had wacom.ko in there. It's dated Mon @ 1:49am. I'm guessing that this is when I did the 'make install'. Anyway it's there but I'm getting no response with the tablet. dmesg shows nothing for wacom. And if I do a lsmod I don't get anything either. And I've restarted a bunch of times since that showed up. I found something awhile back on modprobe so I thought I would mess around with it. I tried to do

depmod
sudo modprobe wacom

and I got:
FATAL: Error inserting wacom (/lib/modules/2.6.28-6-powerpc/kernel/drivers/input/tablet/wacom.ko): Invalid module format

I googled it and this may be b/c I compiled the kernel and the module with a different compiler. I don't actually know what that means. But I figured that I should recompile the kernel and hopefully they would match up then

So I followed the steps [here]("http://www.howtoforge.com/kernel_compilation_ubuntu_p2")[]("http://www.howtoforge.com/kernel_compilation_ubuntu_p2")

When I did makeconfig, wacom showed up there but the actual recompiling of the kernel failed.  I got something to the effect of: no rule to make target kernel/bounds.c

So, this [post]("http://ubuntuforums.org/showthread.php?t=1047374") says that I need the full source for the kernel in order to compile.  So, I downloaded kernel 2.6.28.10 from kernel.org.  I don't remember why I picked that one.  I think it was on the front page.  So I was able to select the wacom driver during the makeconfig and it's compiling right now.  It's a long process.  Hopefully I get some results

---

### Post by Favux on 2009-09-09
Hi cptfx,

I hope it works.

The existence of the debian package means someone knows how to compile the wacom.ko.  If you click on the link to the linux-image package that has your cpu arch you'll see a list of maintainers.  Maybe you could contact one of the maintainers of the package and ask for help?

---

### Post by cptfx on 2009-09-09
Alright, the new kernel works good.   Wacom stuff is starting to appear on my system, but it still doesn't register any motion.  The R/L mouse buttons work and so does the scroll wheel, but that's it.  I now get the following results:

dmesg | grep W/wacom

[   17.504996] input: Wacom Graphire4 4x5 as /devices/pci0001:10/0001:10:19.0/usb2/2-1/2-1:1.0/input/input5
[   17.545938] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver
[   17.544584] usbcore: registered new interface driver wacom


xinput -list

"Wacom Graphire4 4x5 pad"    id=6    [XExtensionKeyboard]
+ a bunch of other stuff and entries show up for the stylus etc


xsetwacom list

gives nothing


xxd or cat on /dev/input/events and mice

gives nothing (for the tablet)


And I had no 10-wacom.fdi file.  That seemed alittle weird so I installed the sample one that you posted in some other post.  I still get no response for xsetwacom list.  


I realize there is alot of info out there but I'm having trouble figuring out what exactly  I should be looking for at this point.

---

### Post by cptfx on 2009-09-09
And there's another problem too.  After restarting, before the login screen, the screen would turn off and on and eventually I got an error saying that it happened to many times.  After booting a live cd it said that the Gnome settings daemon threw an error.  Something to the effect that it wasn't getting a response that it was waiting for.  I renamed the extension for 10-wacom.fdi and now it boots fine.  I repeated the experiment and it's definitely the .fdi file.  .... I've got no clue.

---

### Post by Favux on 2009-09-09
Hi cptfx,

Congratulations!!!  Wow, outstanding job.

I'll have to think about that.  What do you mean?:
> I renamed the extension for 10-wacom.fdi and now it boots fine.

What you've run into with xsetwacom list is that the default wacom.fdi doesn't parse the names HAL/dBus is returning correctly.  Try this .fdi in post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)  I doubt it will help with your hang problem though.

---

### Post by cptfx on 2009-09-11
when I said that I renamed the extension.  I basically meant that I just renamed it so that it wasn't recognized.  I changed it from 10-wacom.fdi to 10-wacom.fdi.broke

And the 10-wacom.fdi that I used was the same one from that post.

---

### Post by Favux on 2009-09-11
Hi cptfx,

That's rare that a .fdi breaks X.  You may be only the second person I've heard of.

My guess is it it this line:
```
<append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
```
In which case the default wacom.fdi would do the same thing.  So that's one test.

As I understand it you now have the default Jaunty 0.8.2-2 linuxwacom packages for your powerpc arch and you've compiled the wacom.ko (ver. ?).  You've got usb to the tablet now.  It doesn't seem likely it's the wacom.ko breaking things.

If the "info.callouts.add" is breaking things then something is probably wrong with "hal-setup-wacom.c" (it installs to "/usr/lib/hal/hal-setup-wacom").

The 0.8.2-2 in Jaunty isn't vanilla.  It's been patched to support Xserver 1.6 and HAL.  Did they not compile it with "libhal1-dev"?  And that's the problem?

Although you'll lose hotplugging you could try xorg.conf.  But 0.8.2-2 seems to have some problems with xorg.conf so I don't know how that would go.  Or go whole hog and compile a newer linuxwacom, say 0.8.4-1 (without "libhal1-dev") and use xorg.conf?

---

### Post by cptfx on 2009-09-11
Alrighty.  It works now.  I went ahead and severely screwed up my system by trying to reinstall HAL and it basically said "I'm afraid I can't do that Dave"  So I did a fresh install.

Here's what I did
-Installed Ubuntu 9.04 ppc alternate
-Installed wacom-tools
-Compiled kernel 2.6.28.10 using the instructions [here]("http://www.howtoforge.com/kernel_compilation_ubuntu") and making sure that I selected the wacom drivers as built-in (not modular as I did previously)
-created a 20thirdparty directory and created a 10-wacom.fdi using the file[ here]("https://help.ubuntu.com/community/Wacom.fdi")
-logged out and logged back in and it worked perfectly.

Now, I don't get any message when I run xsetwacom list.  But I do get output for xinput -list.  So that seems to go against what all the instructions say should happen but it works.  I don't think I left out any steps but I didn't thoroughly document it or anything.  Hopefully that can save someone some headache.

Edit:  I also had the xubuntu-desktop installed previously and now I'm using ubuntu-desktop.  Not sure how that would break anything though.  Possibly the most important thing that I left out was that I have to unplug and replug the usb connection for it to recognize.  I seriously think that this may have been the problem all along.

---

