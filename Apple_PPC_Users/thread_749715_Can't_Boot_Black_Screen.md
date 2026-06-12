---
title: "Can't Boot Black Screen"
date: 2008-04-08
forum: Apple PPC Users
---

### Post by crapple on 2008-04-08
Here is my problem first see this forum post
[Click Here]("http://ubuntuforums.org/showthread.php?t=738179")
I still have the black screen so I decided to install 8.4 beta.  On 8.4 it started up no problem until the login screen and then it was black but I could here sound.  This is the same thing that happened to me on 7.10 Any ideas?

I have a powerpc G4 emac.

---

### Post by linuxh8tertoo on 2008-04-08
Are you sure you're eyes were open?

---

### Post by stream303 on 2008-04-09
> **crapple said:**
> On 8.4 it started up no problem until the login screen and then it was black but I could here sound.  This is the same thing that happened to me on 7.10 Any ideas?

I have a powerpc G4 emac.

OswaldKelso has a great xorg.conf file for his g4 emac:
[http://ubuntuforums.org/showthread.php?t=695325&highlight=emac](http://ubuntuforums.org/showthread.php?t=695325&highlight=emac)

Looks like the trick here is to use:

```
Option "UseFBDev" "true"
```

in the **Device** section of /etc/X11/xorg.conf.  Take a look at those responses and see if anything there helps.  In Hardy, the xorg.conf looks a bit bare, but I'd try editing in that line and see after a logout-login or reboot.

If it is totally blank right after the yaboot boot loader, have you tried this at the second stage:
```
Linux nosplash
or
Linux nosplash fb=false
```

---

### Post by crapple on 2008-04-09
I don't really get what you mean I am really new to all this Linux stuff.
Where do I put the codes and how do I redo the xconfig thing.

---

### Post by stream303 on 2008-04-10
Ok, let's do this in two parts - one for passing kernel parameters at boot, and the other for modifying your xorg.conf.

*It looks like a lot, but after you do it once or twice, it is no big deal.*

You can pass kernel parameters at boot time to compensate for hardware quirks or personal preferences to override the default compiled into the install kernel.

Let's take "nosplash" for example.  The splash screen for PPC is usually pretty ugly with a multi-colored Ubuntu logo and a gas-gauge.  If you use nosplash at boot time, you can see the boot messages roll down the screen instead, and in some cases, this parameter has been known to fix the lack of virtual terminals, depending on your hardware.

I'll simplify this example by showing what you'd do from an already-working install and get to the live-cd options futher on.

When you boot, in the upper left you come up to the yaboot boot-loader menu in two stages.  In stage 1, you can usually select either "L" for linux, or "C" for booting from cd.  In this case, we'll boot from Linux, and press "L".  If you don't do anything, it will time-out and the choice will be made for you and assume you wanted Linux.

Now stage-2 appears and halts temporarily at the **boot**: prompt.  This is where you type in your options.  If you don't do anything, it will time out and the default option compiled into the kernel will take effect.

We want to add the **nosplash** parameter, so at the *second-stage* **boot**: prompt, just hit -tab-.  This will buy you some time, and will show you some options available to you.

Normally you will be presented with two options: Linux and Old.  We want Linux, but want to add nosplash.  (if you typed Old, it would boot an older kernel if one was available - in case the new one you just installed just bricked your system.)

This is as simple as typing

```
Linux nosplash
```

Now when it boots, you will see the boot messages roll by instead of the multi-colored and sometimes distorted Ubuntu logo gas-gauge.

From the threads here, you see that there are a lot of possible kernel parameters you can pass, even multiple ones on the same line like:
```
 Linux nosplash video=ofonly
```

This is a drag to have to manually type nosplash every time you boot.  What we do now to automatically add it at boot time is add it to the** "append=" line in /etc/yaboot.conf**.  Yaboot is the ppc bootloader, like Grub is the bootloader for x86.

Now with an editor, change the line in /etc/yaboot.conf to:

```
append="nosplash"
```

You can do this gui:
```
gksudo gedit /etc/yaboot.conf
```

or text-mode:
```
sudo nano -w /etc/yaboot.conf
```

Thing is, when you edit the yaboot.conf file, the system doesn't know about it.  You have to tell it you have made the change and want it to incorporate it.  Anytime you make a change to the yaboot.conf file, you need to perform the ybin command, so from a terminal type:

```
sudo ybin -v -C /etc/yaboot.conf
```

Note the capital C.

I like getting into the habit of using this longer version of the command, rather than the shorter ybin -v yaboot.conf that appears.  Helps to keep things straight, and a good habit for the future especially if  you have multiple installs on a disk, firewire drive etc.

Now when you reboot, the system will add the nosplash parameter at boot time without any intervention on your part.

**Live-CD's, and Alternate cd's:**

When you boot from one of these, and hit -tab- at the second-stage boot, you will be presented with many more options you can type in.  One of the most important is Linux-rescue or something similar.

This will allow you to boot into a single-user / rescue mode, that looks like it is starting a normal install, but will lead you to a shell prompt from which you can fix problems further down the line like in /etc/X11/xorg.conf for example!  Of course if you can get the system to boot into a normal gui or shell-prompt without the need for a "rescue" attempt, in order to make modifications, so much the better.

---

### Post by stream303 on 2008-04-10
Editing your **/etc/X11/xorg.conf** file

Even though Ubuntu tries hard to get your graphics setup just right, sometimes it needs manual intervention to compensate for lack of a proper response from automated probing during install.  If you search the forums, you can find suggested solutions to add or remove from the xorg.conf file.

If the system is booting ok, but is at least somewhat usable, you can find the things you need to add or remove and edit them.

Most importantly, make a backup of the original xorg.conf file!  This is what I do after a fresh install so I can restore it if I go crazy:

```
sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.original
```

For a gui editing experience with Ubuntu gnome:
```
gksudo gedit /etc/X11/xorg.conf
```

or text based:
```
sudo nano -w /etc/X11/xorg.conf
```

You make your edits, and then either reboot, or what I do is just logout (System > Quit > Logout) and login again without rebooting to see how the changes worked.

If you can get to a "virtual terminal", you can also perform the edits there.  Just hit ALT-F1, start nano, and when done you can reboot, or do a quickie by going back to the gui with ALT-F7, and do the logout-login thing again.

If you can't even get to a barely usable system, you can boot from an installer disk, but at the second-stage boot, hit -tab- and then type something similar to "Linux rescue" or just "rescue", "rescue-ppc64" or similar.  Sometimes "Linux single" will do the same thing.

This will lead you to a shell prompt.  Now you can try editing the file with the nano editor.  If things look really ugly with the editor, you can try to set the terminal variable first:
```

set TERM=vt100
or
set TERM=Linux
```

Try either one and see if your editor works better in this rescue shell.

We'll, that's a super-brief rundown of two of the most typical things ppc'ers have to do sometimes to get their system up and running.  There are other ways of doing this too.  Hope this sheds a little light on things.

---

### Post by crapple on 2008-04-10
Thank you I will try this.

---

### Post by crapple on 2008-04-10
It didn't work nosplash still won't do it.  I get past the ubuntu logo and loading bar fine but the  I can only here noise no picture.

---

### Post by stream303 on 2008-04-11
Ok, after you hear the noise, can you bring up a virtual terminal with CTRL-ALT-F1 and see the login prompt, or is that all black too?

---

### Post by poh on 2008-04-11
I used my ibook (1.33GHZ; 1.5GB ram) to install Hardy last night, and I have the similar black screen problem. It booted well and went into linux (I used dual boot Ubuntu and Mac OS), but seems to be stuck before starting gnome. Even i tried to used Ctrl+Alt+F1, I still could not prompt it.

The ibook ran Feisty well before the installation, even failed in Gutsy but still can start in prompt mode. Could anyone tell me the possible solution?

---

### Post by stream303 on 2008-04-11
I took a look at your video cards at:

[http://www.everymac.com](http://www.everymac.com)

and it seems that you both have ATI Radeon Mobility cards.

At the second stage boot prompt where you interrupt the countdown by hitting -tab- does typing any of the following at the boot prompt get us somewhere, or at least a little further along:
```

Linux video=radeonfb
or
Linux video=fbdev
or
Linux video=radeon:1024x768
or
Linux video=radeon:1024x768@60
or
Linux video=radeon**fb**:1024x768
or
Linux video=radeon**fb**:1024x768@60

(Substitute the resolution values to your own native display settings)
```

So Linux video=ofonly didn't work either?

Lets see if we can track this down...we might also have to disable DRI in /etc/X11/xorg.conf but I guess for now let's see if you can get virtual terminals.

You can also try the above and specify nosplash at the end as well ....

---

### Post by BladeMelbourne on 2008-04-11
Thought I might mention it here since stream303 is talking about radeonfb.

A while ago my Hardy install would freeze everytime I quit X or tried to switch to a virtual terminal:
[https://bugs.freedesktop.org/show_bug.cgi?id=14446](https://bugs.freedesktop.org/show_bug.cgi?id=14446)

The solution for an ATI Radeon 9200 (G4 Mac Mini) was to add the following to /etc/yaboot.conf
```
append="nosplash video=radeonfb:1280x1024-24@60"
```
where the components are PixelWidth x PixelHeight - ColourDepth @ RefreshRate.

Previously video=ofonly was all that I needed.

Now I have no crashes, and I even have access to the virtual terminals (which I have never had once X has started). I still have DRI and glxgears performs at about 1250 fps - which is about as good as it can be with such a crap display adapter.

HTH.

---

### Post by crapple on 2008-04-12
I can't get into the virtual terminal with any of those codes I tried no splash to.  Is there a way to just boot the computer in terminal mode.  
All I get is a black screen.

---

### Post by BladeMelbourne on 2008-04-12
You are after single user mode:
```
single
```

You may be able to type 'Linux single' at the boot menu. You could also create an additional boot option in /etc/yaboot.conf and add 'single' to the append line.

Note that networking is not available under level 1 - although you can modify yaboot and perform basic maintenance. Saved me a few times ;-)

---

### Post by crapple on 2008-04-13
I tried single it didn't work I got a blue screen with a bunch of random lines and it wouldn't do anything.  All I need is to access some sort of terminal so that I can reconfigure the X server like previously said.  Any other ideas?

Also will 8.4 have these things fixed not the beta the full version?



Thanks

---

### Post by crapple on 2008-04-13
I tried single it didn't work I got a blue screen with a bunch of random lines and it wouldn't do anything.  All I need is to access some sort of terminal so that I can reconfigure the X server like previously said.  Any other ideas?

Also will 8.4 have these things fixed not the beta the full version?



Thanks for all the help

---

### Post by crapple on 2008-04-13
Sorry for the double post I didn't think it worked the first time my browser crashed.

---

### Post by stream303 on 2008-04-14
I feel your pain and hate to see that Emac go without Linux.  Maybe take a break from Ubuntu and give Debian Etch a shot at least to prove that it can be done.

Etch isn't the very latest, but it is the latest stable version.  If you like, you could download the very first CD-1 image near the top of the page, and use that to boot and install Debian Etch.  (You don't need all the others).
[http://cdimage.debian.org/debian-cd/4.0_r3/powerpc/iso-cd/](http://cdimage.debian.org/debian-cd/4.0_r3/powerpc/iso-cd/)

Alternatively, you could download the "netinst" image, seen towards the bottom of the page, which is much smaller, and will grab what you need from the net.

I'm not trying to push you away from Ubuntu, but perhaps Debian Etch might get that Emac up and running faster.

I'd be interested to see if Debian might be a better choice for your particular setup...

---

### Post by crapple on 2008-04-14
Thank you for your help but I still can not get it to boot. I can't get into a terminal type thing typing Linux Single in Yboot. It brings me to this blue screen and when i type it just makes a black line every time I hit a letter on the keyboard. Any Ideas on how to get the thing to boot or to get into a terminal type thing?
Thank you 
Crapple

---

### Post by crapple on 2008-04-14
I did a fresh install of 8.4 and I got to the terminal can you tell me what to do now!  The reconfigure x server thing is for if you have a relatively stable system already?


ThankS

---

### Post by stream303 on 2008-04-14
Way to go Crapple!

Hang in there pal, I know it's been a rough ride...

Do you have a gui desktop, or are you sitting at the text-based terminal?

Depending on what date of the daily you downloaded, updates are once again coming in...

If you are at just a text based terminal, I'd do:

```
sudo apt-get update
then
sudo apt-get upgrade
```

If you are at a gui desktop, I'd go to System > Administration > Update Manager > Check

and see if you can pull in the latest ...

Thanks for hanging in there!

---

### Post by crapple on 2008-04-14
I am in the terminal text based.  I already have the latest stuff it still won't get into the actual desktop environment, don't I need to do something with the x config file?

Thanks again for all your help

Correction:
I didn't have the internet plugged in. Now it did upgrade.

---

### Post by stream303 on 2008-04-14
The only thing I can think of at this point might be the date-bug preventing gdm from starting.  When you type
```

date
```

do you get something realistic?  If not, check this out:
[https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug)

and either restart gdm, or reboot.

Let's see if we can't get to some sort of graphics, even if they are wrong and we can go from there...

---

### Post by crapple on 2008-04-14
Okay 
It still will not get past a black screen and let me load it. 
I now do not hear the sound that means type your user  name like before. 
Any ideas on how to get it to boot with graphics 
You know like a normal Ubuntu should
Crapple

---

### Post by crapple on 2008-04-14
Okay I am trying this.

---

### Post by crapple on 2008-04-14
The date seems fine to me. It fits all of my clocks and other computers and calenders. Any more suggestions? Is there some sort of a way to find out what is wrong?
Crapple

---

### Post by stream303 on 2008-04-14
Normally I'd say to run
```

sudo dpkg-reconfigure xserver-xorg
```

but **WAIT**!  It appears to configure the xorg.conf the old way with a bad option instead of using the new vmmouse.

Right now, I'd say to just run those two update and upgrade commands from the terminal every day, unless someone sees something I'm missing.

---

### Post by crapple on 2008-04-14
I will try this.  Should I file a bug for 8.4?  Will it be fixed in the full version of 8.4?

---

### Post by crapple on 2008-04-14
Also do you happen to know if 8.04 will officaly support power pc when it is released? Or will it be kind if like 7.04 and 7.10? Thanks
Crapple

---

### Post by stream303 on 2008-04-14
It's hard to say what 8.04 will be like, other than most likely "unofficially supported", that is it all depends on *volunteer* developers and users.  6.06x has an officially-supported lifetime until 2009, so I don't expect to see Hardy becoming official, since all releases since what, Feisty are unofficial.

As long as we have builds available, download repos, great forums, and volunteer developers, we should be in good shape.

We can always run off to something else, but I'm not going to give up just yet.  The community alone is just as valuable as the actual code.

---

### Post by NoWayBill on 2008-04-14
OK lets give this a shot.
This has worked in all the RedHat based distros I've used, Debian noob.

However you will have to have your user account set up.
I assume you reached the terminal by appending a **3** to the end of the kernel line.
Log in, enter...
> cd /etc/X11/
Then...> sudo vi xorg.conf
Now **vi** is very old school but it works.
Maneuver through the file using your arrow keys.
Find the Section that looks similar too....
> Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection
Cursor over the driver, in my case "fglrx" and **delete** everything inside the quotes.
I recommend replacing it with "vesa", the basic generic driver.
That should be able to get you into the GUI where you can make proper fix more easily.
To insert text first hit **i**, insert the desired text then hit **esc** to stop the insert command.
Then hit **ZZ**, note caps, to save and exit.
Lower case just exits
Then command **startx** and the GUI should start.

I should note that I'm an x_86 user, but I believe the Linux tools will be the same.
There may not be a "vesa" driver for the PPC.

---

### Post by BladeMelbourne on 2008-04-14
It should be noted that the "fglrx" driver is not available on PPC, however "vesa" is.

Also, do not use vi. Use nano. It is easier to use and perfect for editing xorg.conf
vi will only make it harder for those who are already struggling.

---

### Post by crapple on 2008-04-16
Didn't Work on Ubuntu


But thanks anyways

---

### Post by Shadegrown on 2008-04-20
I had the same problem with my ibook g4 with radeon 9200. I installed the 8.04 using mini.iso and when I booted the system for the first time the screen went black after "Loading, Please wait..."

I tried many different 'video=' and 'nosplash' combinations and now I finally got it working:

**Linux nosplash video=ofonly**

did the trick for me :)

---

### Post by stream303 on 2008-04-20
Great!  Now to make that permanent so you don't have to deal with that at boot time, edit your /etc/yaboot.conf file:

```
sudo nano -w /etc/yaboot.conf
```

and add or change the append line:

```
image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="nosplash video=ofonly"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="nosplash video=ofonly"
```

Save the file, and now make the system aware of your changes:

```
sudo ybin -v -C /etc/yaboot.conf
```

I don't own a radeon, but I believe there is a better option than video=ofonly for you in the threads here.  At least it's up and running!

---

### Post by Shadegrown on 2008-04-21
You were right, I found a better boot option.. BUT I couldn't boot the system manually with the option in the second stage boot strap. It worked only after I had added it to yaboot.conf and used the ybin command. Is there a known reason for this behavior?

```

append="nosplash video=radeonfb:1024x768-32"

```

Now I only need to find out why my sound card isn't working and why the "apple+<key>" commands do not work, eg. I can't type @. I'm using FI layout with mac variant.

---

### Post by stream303 on 2008-04-21
Are any of the channels just muted?  I found this out when I ran
alsamixer
and the master volume was muted along with a pcm channel set too low.  I just unmuted them in Alsamixer by toggling the "M" key and using the up/down arrows to adjust levels.

Or is it more serious than this?

---

### Post by Shadegrown on 2008-04-22
> **stream303 said:**
> 
Or is it more serious than this?

It seems that the soundcard wasn't detected when I installed the system. Strange, since when I tried 8.04 live there was no problem with soundcard and everything worked.

I get this when I run the alsamixer:

alsamixer: function snd_ctl_open failed for default: No such file or directory

---

### Post by michaelpagz on 2008-04-25
Hello, I am having this very same problem with an emac. I'm newish to linux so I don't have alot experience with the terminal. I am trying to do this```
sudo nano -w /etc/yaboot.conf
```to get to ```
image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="nosplash video=ofonly"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="nosplash video=ofonly"
```

in hopes that I might get passed the black screen as well, but when i go to get to yaboot.conf it is a new document and which I suppose I just created? I'm using the g3,g4,g5 version of the 8.04 cd. I really hope to get this going on here.

---

### Post by stream303 on 2008-05-06
Are you trying to do this from the live-cd?  If you somehow got the system installed onto the hard drive, but boot with the live-cd in order to edit, you might find it in

```
sudo nano -w /media/disk/etc/yaboot.conf
```

---

