---
title: "The &quot;It sux to be me&quot; syndrome"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Wee Nyaff on 2007-04-23
First, a bit about me.

I am a 64yr old newbie as far as Linux goes although I have been dabbling in computers since Commodore 64 days.  Only using them, I am not a programmer.Between work and home I have 5 computers and would like to leave the costly Windows upgrade treadmill.
I have been using Ubuntu Feisty Fawn for about 10 days if you count from the first install, or about 5 hours if you count from the latest install.

The machine (commonly known as "You bast***") is as follows
ASROCK m/board dual series bought to run some new hardware along side some older hardware.
Intel P4 3.0G CPU
1G DDR2 RAM
Nvidia Geforce 7600 GS to get the best out of Vista Home Premium.
Monitor a Viewsonic VA1912w normal resolution 1440x900

The reason it sux to be me.

When I first installed Ubuntu I encountered the usual Nvidia screen resolution problem IE 1024x768 or less only. 
"Thinks- go to Ubuntu forums and see if answer is there" 
Yes the answer is there albeit in 70 or more slightly different versions.
Spend hours /days learning how to gedit,backup,replace and curse at xorg,conf.
No good cannot get screen resolution up to 1440x900.  Cannot install latest Nvidia driver. (Yes I learned all the steps and carried them out properly)  It crashes every time no matter what.
Because I want the big screen for watching movies I change to a smaller screen to learn Ubuntu on.  Finally through experimenting with everything that has been written I get that resolution to 1280x1024.

Gedit xorg.conf to read (in part)  Device 	Identifier	 "generic video card"
					Driver		 "nv"	changed from vesa
					Hsync		30-80
					Vsync		50-80	these settings are changed also  

An acceptable screen resolution on that screen but still cannot install Nvidia GLX or the stand alone driver from Nvidia.com.

Now my son enters the fray and installs Feisty as a dual boot up with his Windows machine.  He finds ENVY and announces it is the answer to all my prayers.  Comes round downloads it, installs it and confidently reboots to solve my problems.
"IT EFFING WELL CRASHES"
In the last 24 hours he has installed feisty , found and installed Envy, installed Beryl and got them all working perfectly on his machine.
You are now up to date.  Thanks to all of you who did try to help me with my problems.  This machine will be remaining on Ubuntu as I love the idea of open source and the help that you guys/gals give.  Hopefully someone will eventually find a solution to this problem that I and others have.
It sux to be me. Rant over.
Alan](*,)

---

### Post by Nythain on 2007-04-23
> **Spr0k3t said:**
> Open a console and do the following:```
sudo apt-get install nvidia-glx-new
```Also, make sure you have turned on the nvidia drivers in the restricted drivers manager set. From there, open the nvidia settings as such:```
gksudo nvidia-manager
```Let me know how things work out once you've got that far. Also, Automatix2 isn't needed since Feisty... I would call it redundant now.
no need for envy or automatix really with feisty... you might need to make sure the nvidia drivers are enabled and reconfigure your xserver afterwards, i forget how to do that, but a simple search should land the result

---

### Post by Wee Nyaff on 2007-04-23
Thanks for the attempt Nythain, naturally it did not work.  Nothing works unfortunately.
I guess I am not a good advert for linux when I cannot solve what appears to be a simple problem for others.
Alan

---

### Post by gldvxx on 2007-04-23
the nvidia thing isn't really a "simple" problem, the reason why there are so many ways to get it working only reflects how difficult of a problem it can be!!  in your xorg.conf, you want to make sure you are using "nvidia" not "nv" (if you want to use the proprietary drivers).  if you see nv in the xorg.conf, don't change it yet.  in Feisty, you can go to System->Administration and select "Restricted Drivers".  There should be an option to enable the nvidia drivers. if you get a message about needing to install a restricted package, then you'll need to use Synaptic to get what you need.  Go to System->Administration->Synaptic.  make sure you have the extra repositories enabled (go to Settings->Repositories and check all but "Source Code").  hit Reload in Synaptic and search for nvidia, you should see a list of "linux-restricted" modules.  select the 2.6 386 version (not generic or low latency).  once that is installed, try opening the Restricted Drivers dealio again.  you'll have to restart for the nvidia stuff to be activated -- you'll know its using the right driver if you go under Applications->System Tools->Nvidia Settings and launch the Nvidia settings program.  You should have a whole list of options in that program, if you don't then you are using the nv driver not the nvidia one, and you should edit your xorg.conf file so it says nvidia instead of nv.

anyways that's kind of long but it's stuff i've been wrestling with too and finally got working.  give it a go and if you run into any problems post here, people, including myself, are more than happy to help out!

---

### Post by Wee Nyaff on 2007-04-24
> **gldvxx said:**
> the nvidia thing isn't really a "simple" problem, the reason why there are so many ways to get it working only reflects how difficult of a problem it can be!!  in your xorg.conf, you want to make sure you are using "nvidia" not "nv" (if you want to use the proprietary drivers).  if you see nv in the xorg.conf, don't change it yet.  in Feisty, you can go to System->Administration and select "Restricted Drivers".  There should be an option to enable the nvidia drivers. if you get a message about needing to install a restricted package, then you'll need to use Synaptic to get what you need.  Go to System->Administration->Synaptic.  make sure you have the extra repositories enabled (go to Settings->Repositories and check all but "Source Code").  hit Reload in Synaptic and search for nvidia, you should see a list of "linux-restricted" modules.  select the 2.6 386 version (not generic or low latency).  once that is installed, try opening the Restricted Drivers dealio again.  you'll have to restart for the nvidia stuff to be activated -- you'll know its using the right driver if you go under Applications->System Tools->Nvidia Settings and launch the Nvidia settings program.  You should have a whole list of options in that program, if you don't then you are using the nv driver not the nvidia one, and you should edit your xorg.conf file so it says nvidia instead of nv.

anyways that's kind of long but it's stuff i've been wrestling with too and finally got working.  give it a go and if you run into any problems post here, people, including myself, are more than happy to help out!

Thanks Gldvxx for your help.  I followed your instructions to the letter.  I did have to use the synaptic package option.  I noticed that somehow the 64 bit version was installed instead of the 32 bit version.  I removed that and installed the 32 bit version.  All started up okay.  I went back to the restricted drivers again but the only option it gave me was to remove a Lucent /agere winmodem.  I declined as I did not see the relevance. The nvidia settings did not give me the options you expected so I edited my config file to read" nvidia" instead of "nv" and restarted.  It crashed and I had to reinstall my back config to get back.  It still sux to be me.
Alan](*,)

---

### Post by steve.horsley on 2007-04-24
If you still want to try, this is what worked for me (nvidia 6600 GT):
1) Install 32-bit Ubuntu Feisty
2) Use synaptic to install nvidia-glx-new
3) edit /etc/X11/xorg.conf and change "nv" to "nvidia"
4) reboot
5) Start a terminal and run the command **gksudo nvidia-settings**

I can't vouch for resolutions over 1280x1024 because that's all my monitor does, but the option is there in the setup screen. If this approach still crashes, it seems you have some kind of hardware compatibility issue, and I'm afraid it may be that only different hardware will get the nvidia drivers working. But you should still be able to get the resolution you want with the nv driver - but it may take a lot of perseverance with the xorg.conf file.

---

### Post by Wee Nyaff on 2007-04-24
> **steve.horsley said:**
> If you still want to try, this is what worked for me (nvidia 6600 GT):
1) Install 32-bit Ubuntu Feisty
2) Use synaptic to install nvidia-glx-new
3) edit /etc/X11/xorg.conf and change "nv" to "nvidia"
4) reboot
5) Start a terminal and run the command **gksudo nvidia-settings**

I can't vouch for resolutions over 1280x1024 because that's all my monitor does, but the option is there in the setup screen. If this approach still crashes, it seems you have some kind of hardware compatibility issue, and I'm afraid it may be that only different hardware will get the nvidia drivers working. But you should still be able to get the resolution you want with the nv driver - but it may take a lot of perseverance with the xorg.conf file.

Steve, thanks, been there done that.  As soon as I reboot from editing from "nv" to "nvidia" it crashes and I get the error messages that I can view prior to fixing up my config file.
Alan

---

### Post by Talon2 on 2007-04-24
> **Wee Nyaff said:**
> 
It sux to be me.
(*,)

Same here.  Video card = GeForce 7600GS

I do appreciate those who are offering advice but I'm quite sure at this point that the solution is not at hand.  I've tried everything I can find.  As far as I'm conserved nvidia support is badly broken in Fiesty (at least for my 7600gs card).

---

### Post by TheMono on 2007-04-24
Strange. I am sitting here with my 7600GS running two monitors, one at 1280x1024 and one at 1024x768...

It never gave me so much as a speck of trouble.

Which method did you try FIRST? Did you reinstall at any point. The problem being if you are installing from a source other than the official repository and also from the repository at another point, things can go horribly wrong.

Can I suggest a reinstall, and then install the packages linux-restricted-modules-generic, nvidia-glx. That is all you should need. I strongly suggest that you don't tr installing the nvidia distributed ones or envy.

From there, run "sudo nvidia-glx-config enable". Then let us know what error you are getting after that point.

EDIT: I forgot to mention, Beryl works perfectly (well, as perfectly as Beryl ever does) even across both the monitors.

---

### Post by Sethalos on 2007-04-24
I have the same card and couldn't change the resolution either. Until I reconfigured my xorg.conf file.

I simply just added "1440x900" under the 24 bit option and then logged off, pressed CTRL-ALT-BACKSPACE, waited for the reboot.

Once it rebooted I went into my System > Preferences > Screen Resolution and bingo it was there, selected it...and it worked.

There was a walkthrough to do this in the forums here.

Seth.

---

### Post by Wee Nyaff on 2007-04-24
> **Talon2 said:**
> Same here.  Video card = GeForce 7600GS

I do appreciate those who are offering advice but I'm quite sure at this point that the solution is not at hand.  I've tried everything I can find.  As far as I'm conserved nvidia support is badly broken in Fiesty (at least for my 7600gs card).

Talon2,
Don't give up hope.  There is always a solution.  I have just 2 minutes ago resolved my problem.  I finally read the error message entirely and found that one problem appeared to be that the configuration was looking for a power connection to my video card.  It stated that this was not connected and because of this it could not start.  Despite the fact that it did start when I had "nv" as my driver instead of "nvidia"
It gave me the option (if there was no power connection - and there is not) to enter the option of "NoPowerConnectorCheck" in my screen section of my xorg.conf file.
So in the screen section under the identifier line I inserted the line as follows:

Option            "NoPowerConnectorCheck"

Under device I made my driver "nvidia" also and the rest as they say is history. On reboot it immediately became clear that the problem had gone.  I was able to enable nvidia settings and enable desktop effects.  I have not installed "Beryl" yet but I do not see why that would not work now.

In my case the short story is operator error.  Which is why "It sux to be me"
Alan

---

### Post by TheMono on 2007-04-24
If desktop effects work, Beryl will almost certainly work too. They're very much the same thing. You may find one is faster for you though - on my card I find Beryl significantly faster than the "desktop effects" package, compiz.

---

### Post by rumli on 2007-04-25
> **Talon2 said:**
> Same here.  Video card = GeForce 7600GS

I do appreciate those who are offering advice but I'm quite sure at this point that the solution is not at hand.  I've tried everything I can find.  As far as I'm conserved nvidia support is badly broken in Fiesty (at least for my 7600gs card).

I have a 7300GS and I finally got it working using the steps listed [here]("http://www.cs.cornell.edu/~djm/ubuntu/#nvidia-driver").

After following the steps, I change my screen resolutions using:
```
sudo nvidia-settings
```
because the System > Preferences > Screen Resolution menu lists incorrect frequencies.

---

