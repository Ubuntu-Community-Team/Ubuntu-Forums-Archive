---
title: "So frustrated with enabling 3-D that I don't know what to do anymore..."
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by ZeusABJ on 2006-06-15
Ever since the first day I installed Ubuntu I have been trying like crazy to resolve some odd performance issues I have been having (video is choppy, etc). Imagine how happy I was when I came across this:

[http://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](http://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html)

And ran the following suggested command:

```
glxinfo | grep rendering
```

Which returned:

```
direct rendering: No
```

So I follow their tutorial to enable my GeForce 6800 GT video card and it should solve my problems right? Well I got the nvidia-glx driver installed but when I ran the next command:

```
sudo nvidia-glx-config enable
```

All I got was a bunch of errors! So I tried running the nvidia-settings application. I get a window with some nvidia graphics (that are clearly offcial) and my only options are 5 checkboxes, all of which are totally useless to me. So someone refers me to EasyUbuntu:

[http://easyubuntu.freecontrib.org/index.html](http://easyubuntu.freecontrib.org/index.html)

I run it and while it does a super job of setting up my Firefox plugins I noticed things were still sluggish. Running this command:

```
glxinfo | grep rendering
```

Reveals this (once again):

```
direct rendering: No
```

So I dig arouns and find yet ANOTHER tutorial (which is pretty simlar to the first). So I run it:

1. sudo apt-get install nvidia-glx
2. sudo nvidia-glx-config enable
3. sudo reboot

The only difference (this time) is I get a different error message. This one tells me to run another command to change "nv" to "nvidia" in some sort of config file. So I run the command and reboot. Upon restarting I get what looks like the Linux equivalent of a Windows BSOD. I am so confused and frustrated by now I just don’t know what to do. I’m trying my best to read and follow the online documentation for setting up my system (so I won’t bug anyone with newbie questions) but none of the information I’m getting seems to work. Am I just screwing up or is the documentation just wrong? Can someone please help? I’m really trying hard here, but I just can’t seem to do this on my own.

---

### Post by dermotti on 2006-06-15
Try running

**sudo dpkg-reconfigure xserver-xorg**

and reboot

This is assumi gyou still have the nvidia-glx package installed.

---

### Post by nalmeth on 2006-06-15
Can you post which howto's you are following? I usually pass this one on:
[http://wiki.serios.net/wiki/Ubuntu_NVIDIA_proprietary_display_driver_installation](http://wiki.serios.net/wiki/Ubuntu_NVIDIA_proprietary_display_driver_installation)

It includes the part about installing the restricted modules for your kernel so that the restricted Nvidia driver will work.

Don't worry you don't need to mess around with the kernel more than copying and pasting the command in the howto.

---

### Post by ZeusABJ on 2006-06-15
[QUOTE=dermotti]Try running

**sudo dpkg-reconfigure xserver-xorg**

and reboot

This is assuming you still have the nvidia-glx package installed.[/QUOTE]

Well the problem is it looks like its hosed. I'm willing to bet there's a "command line" method to fix it, but I think I'll just re-install and start from scratch. So (with my fresh install) do you think if I go this route:

1. sudo apt-get install nvidia-glx
2. sudo dpkg-reconfigure xserver-xorg
3. sudo reboot

Maybe your suggestion will work?

---

### Post by nalmeth on 2006-06-15
no you can't forget the restricted modules. Don't give up and reinstall yet, if all you've messed around with is apt, I think its unlikely your installation is hosed. Read the howto I posted:
> sudo apt-get install nvidia-glx linux-restricted-modules-$(uname -r)
sudo nvidia-glx-config enable

---

### Post by dermotti on 2006-06-15
That all i do to get my 6600gt working when i reinstall.

---

### Post by ZeusABJ on 2006-06-15
[QUOTE=nalmeth]no you can't forget the restricted modules. Don't give up and reinstall yet, if all you've messed around with is apt, I think its unlikely your installation is hosed. Read the howto I posted:[/QUOTE]

Sorry Nalmeth, here they are:

**How To #1 (Scroll down to "For NVIDIA Video Drivers"):**
[http://www.ubuntuforums.org/showthread.php?t=3713](http://www.ubuntuforums.org/showthread.php?t=3713)

**How To #2 (Scroll down to "3D Graphic Cards"):**
[http://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](http://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html)

Are those just out of date or something?

---

### Post by nalmeth on 2006-06-15
Not the best documentation, I have nothing on ubuntu-geek, he's done a lot more good than me, but the part where he instructs " install linux-686, or whatever matches your kernel " is confusing.
Did you install anything resembling that? If so, uninstall it and reboot before you install the restricted modules for the wrong kernel (**unless you know you need the 686 kernel).
If you skipped all the kernel business, just run the two commands I posted.

The 2 best sources for documentation (AFAIC):
[URL="http://wiki.ubuntu.com/UserDocumentation"]http://wiki.ubuntu.com/UserDocumentation[U]
[_Ubuntu Document Storage Facility_]("http://doc.gwos.org/index.php/Main_Page")[/U][/URL]

---

### Post by btarlinian on 2006-06-15
I would recommend the following (if you've already reinstalled)

open synaptic

Mark nvidia-glx
Mark nvidia-kernel-common (if not already marked)
Make sure that the package linux-386 is installed. if not install it.

Click apply.

Then enter these commands in the terminal (don't enter the lines beginning with a # sign)

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
# this basically makes a backup of your current X configuration file

sudo gedit /etc/X11/xorg.conf
#opens the X configuration file for editing

Scroll down until you see something like this. (where **** is the name of your graphics card)
```

Section "Device"
	Identifier	"NVIDIA Corporation ****"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

```

Replace "nv" with "nvidia"
This basically tells X to use the proprietary nvidia driver, which is actually from Nvidia, instead of the open source nv driver, which comes with X.


Then reboot your computer, and everything should work.


If you haven't reinstalled try this from the recovery console the second entry in grub, except replace gedit with nano, and don't use sudo (because you're already root) and use aptitude instead of synaptic.

Good luck!

---

### Post by ZeusABJ on 2006-06-15
Hey btarlinian, I think it backed up that file when I ran that command that was supposed to change the "nv" to "nvidia" for me, I managed to get bast the BSOD to the command line. So maybe it isn't hosed. Anyone know how to restore that file?

---

### Post by btarlinian on 2006-06-15
[QUOTE=ZeusABJ]Hey btarlinian, I think it backed up that file when I ran that command that was supposed to change the "nv" to "nvidia" for me, I managed to get bast the BSOD to the command line. So maybe it isn't hosed. Anyone know how to restore that file?[/QUOTE]

Enter these commands:
ls /etc/X11 | grep xorg.conf

and post the ouput.

If you can see xorg.conf.bak or something like that, do this.

cp /etc/X11/xorg.conf.bak (or equivalent) /etc/X11/xorg.conf

---

### Post by ZeusABJ on 2006-06-16
Yeah.... no backup apparently.... reinstall time!!! Woo hoo! Can you guys beleive I have a Masters in Computer Science?! Of course no one ever taught me Linux...

---

### Post by frente69 on 2006-06-16
(sorry to hijack)
Thanks btarlinian,
Your little guide helped me to get back up and running.
I did have working nvidia drivers until the pc wanted updating today.
I swear i did had linux-386 installed.
Anyhow I have copied your post and saved it to a text file for the next time the autoupdate thingo wants to install stuff  and break my nice warm and fuzzy GUI :-)

---

### Post by ZeusABJ on 2006-06-16
[QUOTE=frente69](sorry to hijack)
Thanks btarlinian,
Your little guide helped me to get back up and running.
I did have working nvidia drivers until the pc wanted updating today.
I swear i did had linux-386 installed.
Anyhow I have copied your post and saved it to a text file for the next time the autoupdate thingo wants to install stuff  and break my nice warm and fuzzy GUI :-)[/QUOTE]

ROFL, well glad SOMEONE is making progress!!! Thats just hilarious, I've been working on this monster since Dapper launched and this guy is already back up after reading my post! Man I apparently stink at this Linux stuff! Reinstall is complete! Lessee how fast I can hose this one....

---

### Post by frente69 on 2006-06-16
Heh,.. When i installed for the first time ever 2 days ago i think i broke the gui about 10 times before i got it right :-)

---

### Post by ZeusABJ on 2006-06-16
Nice to know I'm failing with the best of them!

---

### Post by therunnyman on 2006-06-16
Here's an oddity: I'm using a GeForce4 MX 4000, and when I grep threedeeinfo, I get the "Direct Rendering: No" as well.  Thing is, I'm watching Direct 3D Rendering happen right now...wot's that all about?

runny

---

### Post by ZeusABJ on 2006-06-16
Oh yes! Thank you Lord! It is WORKING!!!! I combined aspects of btarlinian and dermotti's methods to come up with a working solution. My desktop runs smooth as silk now! Man someone make this tread a sticky because I just can't believe I'm the only person dealing with this issue.

---

### Post by tseliot on 2006-06-16
BTW you could have used my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

### Post by _simon_ on 2006-06-16
^ lol yep tseliot's guide works like a charm

---

### Post by ZeusABJ on 2006-06-17
[QUOTE=tseliot]BTW you could have used my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")[/QUOTE]

Honestly Tseliot? I took one look at your gude and got a little intimidated. There is just a LOT to look at on that page. Also I actually did try your guide at one point a week or so ago and somehow hosed my config file (probably because I messed up a step). All my fault I'm sure. Keep in mind I'm still new to all of this and still a bit freaked out when I see pages after pages of command line code. I'm still used to my warm and fuzzy GUI's but I'm getting where I need to be, slowly but surely.

Thank you *ALL* for your help and patience.

---

### Post by _simon_ on 2006-06-17
[QUOTE=ZeusABJ]Honestly Tseliot? I took one look at your gude and got a little intimidated. There is just a LOT to look at on that page. Also I actually did try your guide at one point a week or so ago and somehow hosed my config file (probably because I messed up a step). All my fault I'm sure. Keep in mind I'm still new to all of this and still a bit freaked out when I see pages after pages of command line code. I'm still used to my warm and fuzzy GUI's but I'm getting where I need to be, slowly but surely.

Thank you *ALL* for your help and patience.[/QUOTE]

First impressions - yes it could be intimidating but if you take a deeper look it's split into different methods and they're not that long.

The new kernel meant I had to reinstall the nvidia drivers on 2 machines here and I follwed step one which worked great.

To show you how simple it really is, this is all I did:
NOTE: DO NOT FOLLOW MY STEPS - READ THE GUIDE - YOUR KERNAL MAY BE DIFFERENT!

```
sudo apt-get install linux-k7
```

```
sudo apt-get install nvidia-glx
```

```
sudo nvidia-xconfig
```

```
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
```

Put this in the above:

```
[Desktop Entry] 
Name=NVIDIA Settings 
Comment=NVIDIA X Server Settings 
Exec=nvidia-settings 
Icon= 
StartupNotify=true 
Terminal=false 
Type=Application 
Categories=Application;System;

```

Save the edited file.

Log out and press CTRL+ALT+BACKSPACE

That's 4 lines of terminal code and some for the desktop settings - all of which you can just copy paste!

See, it's not that complicated :)

---

### Post by ZeusABJ on 2006-06-17
Oh yeah I know that now. In fact I'm trying very hard to contain my excitement. Getting my video up and running has finally been that last great hurdle I needed to jump. Since then everything else seems to have come much easier. I've already been able to use my Ubuntu machine to perform many of the functions I use my XP box for. I just can't begin to tell you how liberating it feels to know I can REALLY quit using Microsoft software! I know it sounds corny, but I've just felt so trapped by them for years always wondering how they would screw me over with the next release of Windows!!! Now for the first time since Windows 95 I'm actually EXCITED about Operating Systems!!!! 

From what I now know I truly believe Open Source is the only viable future for software. I firmly believe that Linux is just going to get better and better. With it as my OS of choice I no longer have to live under the thumb of a greedy corporation like Microsoft!!!! Thank you all so much for doing what you do by sacrificing your time to help people like me. I know it sounds so cheesy, but it just feels like a huge weight has been lifted from my shoulders. I really had no idea until now how much it burdened me to know that Microsoft (a company with the ethical disposition of the worst crook you can imagine) had so much control over my computer.

Don't laugh... but I got so excited at one point... I even called their customer service hot line to gloat...
Before you judge me, try to understand something. I live in Louisiana, one of the most technologically backwater states in the USA. I have very few friends that are up on Linux and my wife doesn't get it when I rant, so I HAD to tell someone!!! Hey they do record calls for “quality assurance” Maybe my message will get back to Steve Balmer himself. Oh that would so rock!!! Those of you who don't think I'm crazy, feel free to do the same:

[http://support.microsoft.com/contactus/?ws=serviceproviders](http://support.microsoft.com/contactus/?ws=serviceproviders)

It's VERY liberating, especially when I got to list all the stupid crap I no longer have to put up with like Activation, Genuine Advantage, legal threats every time I upgrade my motherboard, etc. GOOD LORD I'm just so happy!!!

---

### Post by -deadcats on 2006-06-17
[QUOTE=ZeusABJ]It's VERY liberating, especially when I got to list all the stupid crap I no longer have to put up with like Activation, Genuine Advantage, legal threats every time I upgrade my motherboard, etc. GOOD LORD I'm just so happy!!![/QUOTE]

Well, bless your little heart! Good on ya, mate! But just wait; the worst is yet to come. 

Wait until your favorite Linii bites the big one--like when they release a new distro and you find out its a real bomb--then you're hunting around for a new one. This process can take weeks as you wind your way through the various pros and cons of each distro's current release. 

At that point you'll probably be VERY efficient at installing not only the current Nvidia drivers, but MP3, WMV, MPEG, dvd-rippers--all that stuff!

Then, of course, you'll have to find out which distro has the very latest kernel, GNOME or KDE gui, and how to blow-up your current distro for the want of being on the bloody-friggen-edge. And you'll relish it.

Why-the-heck wait 4-5 years for the next Windows release, when you can have a new Linux distro every six months, you'll ask yourself. Why wait even that long, when you can download somebody's newest distro nearly every damn week!

I'm sorry, Buddy, but when you reach that stage your fragile little heart's been pwnd by Linux. Welcome to the addiction. 

Regards,
-dc

---

### Post by tseliot on 2006-06-17
[QUOTE=_simon_]First impressions - yes it could be intimidating but if you take a deeper look it's split into different methods and they're not that long.

The new kernel meant I had to reinstall the nvidia drivers on 2 machines here and I follwed step one which worked great.

To show you how simple it really is, this is all I did:
NOTE: DO NOT FOLLOW MY STEPS - READ THE GUIDE - YOUR KERNAL MAY BE DIFFERENT!

```
sudo apt-get install linux-k7
```

```
sudo apt-get install nvidia-glx
```

```
sudo apt-get install nvidia-glx-legacy nvidia-xconfig nvidia-settings
```

```
sudo nvidia-xconfig
```

```
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
```

Put this in the above:

```
[Desktop Entry] 
Name=NVIDIA Settings 
Comment=NVIDIA X Server Settings 
Exec=nvidia-settings 
Icon= 
StartupNotify=true 
Terminal=false 
Type=Application 
Categories=Application;System;

```

Save the edited file.

Log out and press CTRL+ALT+BACKSPACE

That's 5 lines of terminal code and some for the desktop settings - all of which you can just copy paste!

See, it's not that complicated :)[/QUOTE]
Why installing "nvidia-glx" and "nvidia-glx-legacy"?

Using them both would be impossible (and useless). Perhaps you made a mistake when you wrote.

---

### Post by _simon_ on 2006-06-17
[QUOTE=tseliot]Why installing "nvidia-glx" and "nvidia-glx-legacy"?

Using them both would be impossible (and useless). Perhaps you made a mistake when you wrote.[/QUOTE]

oops you're right, i just made a mistake when I wrote that post! I've corrected it now. Many thanks for that guide by the way :)

---

### Post by tseliot on 2006-06-17
[QUOTE=ZeusABJ]Honestly Tseliot? I took one look at your gude and got a little intimidated. There is just a LOT to look at on that page. Also I actually did try your guide at one point a week or so ago and somehow hosed my config file (probably because I messed up a step). All my fault I'm sure. Keep in mind I'm still new to all of this and still a bit freaked out when I see pages after pages of command line code. I'm still used to my warm and fuzzy GUI's but I'm getting where I need to be, slowly but surely.

Thank you *ALL* for your help and patience.[/QUOTE]
It's a long guide because I like explaining things. And newbies need redundant explanations.

A good alternative to the guide can be my script (Envy). The Problems Section of my guide is useful also if you use the script (as the script only installs the driver and uninstall a few things).

---

### Post by u.b.u.n.t.u on 2006-06-17
I just did a fresh install of ubuntu. I entered this code in the terminal.

```
sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`
```

I rebooted and had 3D.

---

### Post by ZeusABJ on 2006-06-17
[QUOTE=tseliot]It's a long guide because I like explaining things. And newbies need redundant explanations.

A good alternative to the guide can be my script (Envy). The Problems Section of my guide is useful also if you use the script (as the script only installs the driver and uninstall a few things).[/QUOTE]

Good points! 

Please understand I'm not dissing your guide in any way. By the time I came across it I was just really frustrated with how long it was taking to get my video running. I'd already tried several tutorials (unsuccessfully) and was desperately seeking a quick fix. So instead of being calm and reading through your guide (like I probably should have done) I just broke down and asked for help. Please understand that I really admire people like you who take the time to do what they do and make a serious effort to document and share their knowledge with he rest of us. Without good documenters  seriously doubt Linux would have ever made it as far as it has!

---

### Post by tseliot on 2006-06-17
[QUOTE=ZeusABJ]Good points! 

Please understand I'm not dissing your guide in any way. By the time I came across it I was just really frustrated with how long it was taking to get my video running. I'd already tried several tutorials (unsuccessfully) and was desperately seeking a quick fix. So instead of being calm and reading through your guide (like I probably should have done) I just broke down and asked for help. Please understand that I really admire people like you who take the time to do what they do and make a serious effort to document and share their knowledge with he rest of us. Without good documenters  seriously doubt Linux would have ever made it as far as it has![/QUOTE]
Thanks.

BTW I wrote my script to automate the installation of the driver so as to make newbies' life a bit easier.

---

### Post by ZeusABJ on 2006-06-18
[QUOTE=tseliot]Thanks.

BTW I wrote my script to automate the installation of the driver so as to make newbies' life a bit easier.[/QUOTE]

Well I've discovered a few glaring errors in planning that will require a reinstall of Ubuntu on my part anyway, so I'll be sure to give your guide a go this time when I set up my video drivers this next go-round.

---

### Post by ZeusABJ on 2006-06-18
[QUOTE=ZeusABJ]Well I've discovered a few glaring errors in planning that will require a reinstall of Ubuntu on my part anyway, so I'll be sure to give your guide a go this time when I set up my video drivers this next go-round.[/QUOTE]

Yeah Tseliot I just completed my reinstall and your Nvidia HowTo made things MUCH easier. I guess I was just frustrated and not in the mood to read any more guides when I posted this topic. Also I now have a little better grasp of how to use Linux commands and I'm feeling a little less intimidated by the Terminal. One question though. I followed method one, step 6 "Create a link to the &#8220;Nvidia-Settings&#8221; Panel in your application menu" but I can't find this "link" to the settings utility. I interpreted that step to mean that you are talking about creating an "icon" to launch the Nvidia settings utility, and it is supposed to be listed in the "Applications" menu once that step is completed. Am I just confused?

Thanks for all your help!

---

### Post by tseliot on 2006-06-19
[QUOTE=ZeusABJ]One question though. I followed method one, step 6 "Create a link to the &#8220;Nvidia-Settings&#8221; Panel in your application menu" but I can't find this "link" to the settings utility. I interpreted that step to mean that you are talking about creating an "icon" to launch the Nvidia settings utility, and it is supposed to be listed in the "Applications" menu once that step is completed. Am I just confused?

Thanks for all your help![/QUOTE]
You need to type the command I suggested. You will only find a blank file (as it doesn't exist) and then you will have to paste the lines from the guide and save the file

---

### Post by ZeusABJ on 2006-06-19
[QUOTE=tseliot]You need to type the command I suggested. You will only find a blank file (as it doesn't exist) and then you will have to paste the lines from the guide and save the file[/QUOTE]

Yeah I think I missed something when I copied your lines originally. I repasted and it appeared. SWEET!

---

### Post by FoundDeath on 2006-06-23
Hi,

I have this problem with my nvidia card.
I got the logo splash screen "Nvidia" when i start X(xgl) but no direct rendering here. :-? 
I got the kernel for my proc, reinstall my restricted modules(linux-restricted-modules-2.6.15-25-k7), reinstall my nvidia-glx.
The logo splash screen from Nvidia is here... but no direct rendering :neutral: 
Sorry for my english, i try to find any information about this on forum with my language.

---

### Post by tseliot on 2006-06-23
[QUOTE=FoundDeath]Hi,

I have this problem with my nvidia card.
I got the logo splash screen "Nvidia" when i start X(xgl) but no direct rendering here. :-? 
I got the kernel for my proc, reinstall my restricted modules(linux-restricted-modules-2.6.15-25-k7), reinstall my nvidia-glx.
The logo splash screen from Nvidia is here... but no direct rendering :neutral: 
Sorry for my english, i try to find any information about this on forum with my language.[/QUOTE]
Remove XGL

---

### Post by FoundDeath on 2006-06-25
Works fine.
I remove xgl, then reinstall nvidia-glx and restricted modules.
Thank U. :)

---

