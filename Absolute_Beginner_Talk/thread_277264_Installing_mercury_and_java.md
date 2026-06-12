---
title: "Installing mercury and java"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by izacboy_123 on 2006-10-14
Hi:( 

I've recently installed Ubuntu Linux.

And i must say it's a silly game trying to do things](*,) 

For 1. How do i install Mercury? And i need java so how do i install Java?

And another question. How do i change resolution higher than 800x600?

And another question. Where do programs get installed?

And another question. How do programs ACTUALLY install?

Sorry for so many questions!:-|  <- Oh and there are two Neutral smilys in that Smilies box to the right(Just thought it was a fualt or something) --->

I am so confused the way Linux works that it's driving me MAD!](*,) 

Sorry:( 

Any help and i would kiss you!:-D 

Isaac

---

### Post by izacboy_123 on 2006-10-14
Please help. I REALLY need this to work!](*,) 

Isaac

---

### Post by PriceChild on 2006-10-14
Try this on how to install packages: [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

As a staff member i reccomend you don't install non-official-repository applications such as mercury messenger.

As a forum member: download from [http://prdownloads.sourceforge.net/projeto-messias/mercury-messenger_1.8_all.deb](http://prdownloads.sourceforge.net/projeto-messias/mercury-messenger_1.8_all.deb) then ```
sudo dpkg -i mercury-messenger_1.8_all.deb
```

Find java here: [http://wiki.ubuntu.com/Java](http://wiki.ubuntu.com/Java)

---

### Post by izacboy_123 on 2006-10-14
I don't understand all this terminal business. All i want to do is install a program!](*,) 

In windows, install and play! It's driving me crazy!! I have no knowlege of this terminal!

If i want to install something, it would be logical to double click on it and it installs it!

I JUST DON'T UNDERSTAND!!!!!!](*,) ](*,) ](*,) 

Where does the program go? where is the excutible program? why do i need commands? why do you have to put 'sudo' to open programs as the root? It's not very good sucurity. It gives no indercation where the program goes!

Why do i have to use the terminal!? Why can't i just double click on the install program?](*,) It's just........... IMPOSSIBLE!](*,)

---

### Post by PriceChild on 2006-10-14
Ok... most of this can be done in the gui...

For mercury:
[http://prdownloads.sourceforge.net/projeto-messias/mercury-messenger_1.8_all.deb](http://prdownloads.sourceforge.net/projeto-messias/mercury-messenger_1.8_all.deb)
Download this then double click it to open up GDebi.

You could just use gaim (applications>internet)

Follow this: [https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096) to add the Multiverse repository.

To install java, System>Administration>Synaptic Packagement

Click the search button and search for sun-java5-bin package, right click it when it comes up and install.
Do the same for sun-java5-plugin.

Then click "apply" and packages should be downloaded and installed.

i still reccomend you follow [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by izacboy_123 on 2006-10-14
> **PriceChild said:**
> To install java, System>Administration>Synaptic Packagement

Click the search button and search for sun-java5-bin package, right click it when it comes up and install.
Do the same for sun-java5-plugin.

Then click "apply" and packages should be downloaded and installed.

That doesn't work. Nothing shows up on the list.

I tried Giam. It doesn't work. And there's no 'Help' button. There is never any 'Help' buttons around!

And i still want to change the resolution higher than 800x600! And YES! My graphics card, moniter and what not does support 1024x768. I done it in Windows XP.

I still want to know why 'sudo' is such a good sucurity measure. Any old fool could type that in to get into anything that only the Root could access.

---

### Post by izacboy_123 on 2006-10-14
Oh. And i installed Mercury AND java by downloading and double clicking.(WITHOUT USING THE TERMINAL!)](*,)

But how do i run the bloody program!?](*,)

---

### Post by PriceChild on 2006-10-14
> **izacboy_123 said:**
> That doesn't work. Nothing shows up on the list.[https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)
> I tried Giam. It doesn't work. And there's no 'Help' button. There is never any 'Help' buttons around!What doesn't work? Please be more specific
> And i still want to change the resolution higher than 800x600! And YES! My graphics card, moniter and what not does support 1024x768. I done it in Windows XP.I was going to answer the easier problems with more documentation first. but here you go.... and you MUST do it in a terminal (applications>accessories>terminal)
```
sudo dpkg-reconfigure xserver-xorg
```Leave all the options as they are. Choose beginner when you get to the monitor section and choose your display modes with the spacebar, using enter to continue. Once saved, ctrl+alt+backspace to restart X and log in again.
> I still want to know why 'sudo' is such a good sucurity measure. Any old fool could type that in to get into anything that only the Root could access.Please read [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by Delkster on 2006-10-14
> **izacboy_123 said:**
> If i want to install something, it would be logical to double click on it and it installs it!

If you download a .deb package file, in Ubuntu you can just double-click on the file to install it. I don't know about Kubuntu, though.

> Where does the program go?

The executable file goes to /usr/bin. (Some base system binaries are in /bin instead)

The application probably doesn't install libraries (comparable to dll files in Windows) of its own but they go to /usr/lib or its subdirectories. Again, some very base libraries are in /lib, though.

System-wide configuration files go to /etc or its subdirectories. 

> why do you have to put 'sudo' to open programs as the root?
If you are running as a non-root user, how else would the system know that, at this particular time, you want to run this particular program with root privileges if it weren't for something specific that you have to do in order to indicate that?

As for those root-needing applications that are included in the menu, the menu items themselves do that for you. Generally you only need to manually say 'sudo' when running commands in a terminal.

> It's not very good sucurity. It gives no indercation where the program goes!

Most people have no idea where applications actually install files in Windows either. When I use Windows, I certainly don't. Having them in determined standard places (as described above -- more information can be found in the [Filesysten Hierarchy Standard](http://www.pathname.com/fhs/)) is actually more 'secure' (in case all that has much to do with security in the first place) than having every installer program throw stuff wherever they like.

Those people who know where installers put stuff in Windows are relatively proficient, and those with an equal level of proficiency in Unix/Linux know probably even better where such files go in Linux. You just can't translate knowledge of Windows into knowledge of everything else.

GDebi, the graphical .deb package installer which opens if you double-click on such a package, actually lists the files contained in the package and the locations where they're going to be installed. Once the package has been installed already, you can launch Synaptic Package Manager, find the package by using the search function, and find the list of files installed by that package in the package properties.

> Why do i have to use the terminal!? Why can't i just double click on the install program?

In some tasks you may still need it, although not in this particular one if you're using Ubuntu and have a ready-built .deb package for the program at hand.

---

### Post by izacboy_123 on 2006-10-14
When you say, sudo dpkg-reconfigure xserver-xorg, do i keep pressing enter?:confused:

---

### Post by Delkster on 2006-10-14
> **izacboy_123 said:**
> I still want to know why 'sudo' is such a good sucurity measure.

When you say that you don't know why it's a good security measure, what are you comparing to? Running as root (Administrator in the Windows world) all the time, or running as a normal user most of the time and logging in as Administrator only when needed, or what?

> Any old fool could type that in to get into anything that only the Root could access.

That's why it asks for a password.

---

### Post by PriceChild on 2006-10-14
> **izacboy_123 said:**
> When you say, sudo dpkg-reconfigure xserver-xorg, do i keep pressing enter?:confused:Yes, until you reach the part i mentioned

---

### Post by izacboy_123 on 2006-10-14
I reached the part you mentioned. 

640x480
800x600
1024x768

They were all included in the list! BUT THEY ARE NOT IN THE RESOLUTION MENU!!!!!!](*,) 

Why? WHY!?!?](*,) 

Is this another sucurity measure?](*,) 

I can't even do much with 800x600 because everything is too bloody big to fit in 800x600!](*,)

---

### Post by Delkster on 2006-10-14
Could you post the contents of the /etc/X11/X.org configuration file? (That's where the configuration for the X Window System, the base of the graphical environment, resides)

Actually, the contents of the log file in /var/log/Xorg.0.log might also be useful.

---

### Post by izacboy_123 on 2006-10-14
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"uk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. 3D Rage IIC AGP"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. 3D Rage IIC AGP"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

1024x768 IS listed. So i do not see the problem:-?

---

### Post by Delkster on 2006-10-14
Thanks. I don't see anything immediately wrong with the configuration, but could you still post your X.org log? The brand and model of the monitor might also help.

---

### Post by izacboy_123 on 2006-10-14
There's no 'X.org' file in 'X11' folder. And i can esure you that my moniter DEFINETLY supports 1024x768. I've been running this moniter on 1024x768 for years!

---

### Post by Delkster on 2006-10-14
The X.org log is /var/log/Xorg.0.log (configuration files are in /etc whereas log files are in /var/log).

I believe that your monitor is capable of the resolution you want, but knowing the exact monitor brand and model would help me search on the web and find out if there's, for example, a common problem recognising that particular monitor and its supported modes correctly in X.org.

---

### Post by izacboy_123 on 2006-10-14
I can't copy+paste becuase there's too many charecters. And i can't attach it becuase it's an invalid file!](*,) 

And i said i installed mercury and java. How do i run mercury?

---

### Post by PriceChild on 2006-10-14
> **izacboy_123 said:**
> I can't copy+paste becuase there's too many charecters. And i can't attach it becuase it's an invalid file!](*,) 

And i said i installed mercury and java. How do i run mercury?
Rename it with a ".txt" extension and attach it then.

---

### Post by Delkster on 2006-10-14
> **izacboy_123 said:**
> And i said i installed mercury and java. How do i run mercury?

I haven't installed it but judging by the contents of the package (I'm looking at it in GDebi), it should install a menu item in Applications > Internet, but if it doesn't, the executable is /usr/bin/mercury. You can run it by pressing Alt+F2 to open a "Run application" window and entering "mercury" there, or by commanding "mercury" in the terminal. If it didn't succesfully create a menu item (you could log out and back in just to check if that helps, although it should have appeared immediately), you can create your own icon in the panel or add an item to the menu now that you know the location of the executable.

---

### Post by Delkster on 2006-10-14
> **PriceChild said:**
> Rename it with a ".txt" extension and attach it then.

To be more exact, first copy it into your home folder, then rename it and post it (you can't rename the file in /var/log directly because only root has the privilege to make changes in that directory).

---

### Post by PriceChild on 2006-10-14
> **Delkster said:**
> To be more exact, first copy it into your home folder, then rename it and post it (you can't rename the file in /var/log directly because only root has the privilege to make changes in that directory).My mistake

---

### Post by Delkster on 2006-10-14
> **PriceChild said:**
> My mistake

No problem, and I didn't mean to point any fingers or nitpick, but I predicted that being more specific may help.

---

### Post by izacboy_123 on 2006-10-14
Hey. I've tried running mercury.

Which file do i need to run? Someone told me a should do this in the terminal:
```
Sudo /usr/lib/mercury/jni/linux/libtray.so
```

Is that correct?:-?

---

### Post by Delkster on 2006-10-14
> **izacboy_123 said:**
> Hey. I've tried running mercury.

Which file do i need to run? Someone told me a should do this in the terminal:
```
Sudo /usr/lib/mercury/jni/linux/libtray.so
```

Is that correct?:-?

I don't think that's exactly correct. First of all, you shouldn't need sudo for running an instant messenger, and files ending in .so are generally libraries (a bit like .dll files in Windows), so you don't run them directly.

Did you try /usr/bin/mercury ?

---

### Post by izacboy_123 on 2006-10-15
I've installed mercury AND java and i try this code in the terminal:
```
Mercury
```
And it came up with an error message like this:
```
/usr/bin/mercury: line 1329: strings: command not found
Unable to locate the application's 'main' class. The class 'com.dMSN.Main' must be public and have a 'public static void main(String[])' method. (LAX)
Unable to Launch Java Application: Unable to locate the application's 'main' class. The class 'com.dMSN.Main' must be public and have a 'public static void main(String[])' method. (LAX)
```

What the...?!](*,)

---

### Post by izacboy_123 on 2006-10-15
And to tell you all what i downloaded and installed. Here are the links:
For java:[http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)
I chose Linux(Self-extracting file)

And for mercury:[http://www.mercury.to/index.php?page=Downloads](http://www.mercury.to/index.php?page=Downloads)
I chose teh 'Debian' one!

Tell me what the hell i am doing wrong](*,)

---

### Post by izacboy_123 on 2006-10-15
Cmo'n somebody!!!](*,) 

I've been trying to install and run a program for 3 days now!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by izacboy_123 on 2006-10-15
Bump...

---

### Post by izacboy_123 on 2006-10-15
Cmo'n! I'M DESPERATE for a reply! I've installed mercury ocrrectly becuase it's in the Applications -> Internet -> Mercury Messenger

When i click on Murcery, it just loads for about 4 seconds then, it closes and nothing happens.

And when i run in the terminal using:
sudo Mercury
I get this error message:
```
/usr/bin/mercury: line 1329: strings: command not found
Unable to locate the application's 'main' class. The class 'com.dMSN.Main' must be public and have a 'public static void main(String[])' method. (LAX)
Unable to Launch Java Application: Unable to locate the application's 'main' class. The class 'com.dMSN.Main' must be public and have a 'public static void main(String[])' method. (LAX)
```

And even without sudo i get the error message:
```
/usr/bin/mercury: line 1329: strings: command not found
Unable to locate the application's 'main' class. The class 'com.dMSN.Main' must be public and have a 'public static void main(String[])' method. (LAX)
Unable to Launch Java Application: Unable to locate the application's 'main' class. The class 'com.dMSN.Main' must be public and have a 'public static void main(String[])' method. (LAX)

```

Please someone in the world must know what is going wrong!](*,)

---

### Post by PriceChild on 2006-10-15
You need to install Java correctly.

Don't use it off of java's site. Follow the instructions i have already posted for the gui, or [http://wiki.ubuntu.com/Java](http://wiki.ubuntu.com/Java)

---

### Post by izacboy_123 on 2006-10-15
god sake. Now somone tells me! I have a feeling i have been doing so much wrong things, that my whole system is full of poop!:mad:

I might consider re-formatting my pc again. And start from scratch:(

---

### Post by izacboy_123 on 2006-10-15
sun-java5-bin

I looked for that in the add/remove programs list. It's not there:(

---

### Post by PriceChild on 2006-10-15
Follow my instructions i have already given in this thread, or [http://wiki.ubuntu.com/Java](http://wiki.ubuntu.com/Java)

Both tell you how to enable the multiverse repository, which contains java.

---

### Post by izacboy_123 on 2006-10-15
I don't understand which packages to install. That's what get's me with linux. What the hell does it use?

With Windows XP it sais Windows XP. Not aload of numbers and wierd names. it should say:
Ubuntu Linux

But NOOOOOO:( 

I am a complete and utter begginner at all of this Linux stuff! I don't even know the own name of the OS i am using!! I think it is Ubuntu Linux.

Giving me all these links is nothing i can learn off. It's giving me even more confusing questions and problems that make more problems!](*,) ](*,) 

I JUST DON'T UNDERSTAND:(

---

### Post by izacboy_123 on 2006-10-15
What the heck is Multiverse repository?

And why can't i press CTRL + C to copy. But can press CTRL + V to paste??:confused:

---

### Post by PriceChild on 2006-10-15
Please read [http://wiki.ubuntu.com/Java](http://wiki.ubuntu.com/Java)

it gives EXTREMELY detailed instructions on how to install Java.

It gives a link to [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories) which explains about how repositories work.

Follow [https://wiki.ubuntu.com/AlwaysEnableUniverseMultiverse?highlight=%28multiverse%29](https://wiki.ubuntu.com/AlwaysEnableUniverseMultiverse?highlight=%28multiverse%29) for even more instructions on how to enable multiverse.

Please just attempt to follow one of these. When you get stuck at a point, ask a specific question, giving the error message or exactly what point you do not understand what to do next.

---

### Post by Delkster on 2006-10-15
> **izacboy_123 said:**
> sun-java5-bin

I looked for that in the add/remove programs list. It's not there:(

The page may be a little confusing. It says:

"Sun Java5: Install it from the Applications -> Add/Remove... menu making sure to check the unsupported and proprietary software checkboxes, **or** install the sun-java5-bin package." (emphasis mine)

So, the package name is sun-java5-bin, which is the name by which you'll find it if you look for it in Synaptic, for example, but Add/Remove Applications uses more humane names and doesn't reveal the technical package names directly. In Add/Remove Applications, just make sure that you have unsupported and commercial software enabled and use the search to look for "java". The Sun Java Runtime 5.0 will be near the end of the list.

After that you can then also select the newly installed Sun Java Runtime Environment as the default Java virtual machine as instructed on the [Wiki page](https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b). Yes, the page could probably be a little more specific when it comes to selecting the default Java VM.

---

### Post by PriceChild on 2006-10-15
> **izacboy_123 said:**
> And why can't i press CTRL + C to copy. But can press CTRL + V to paste??:confused:You can do both.

A handy feature of linux i highlighting text, then middle clicking to paste it somewhere. - lots of timesaving.

---

### Post by Delkster on 2006-10-15
> **izacboy_123 said:**
> And why can't i press CTRL + C to copy. But can press CTRL + V to paste??

If you mean copying from the terminal, the hotkeys for copying are Ctrl+Shift+C there (it's generally Ctrl+C elsewhere) because Ctrl+C has a different special meaning in the terminal. Has had for years, so that can't really be changed easily. Thus, the hotkeys for copying have to be something different.

---

### Post by izacboy_123 on 2006-10-15
Which one do i install for mercury?

---

### Post by Delkster on 2006-10-15
> **izacboy_123 said:**
> Which one do i install for mercury?

Which Java environment? We've probably just described different ways of installing the same one. Look for "**Sun Java 5.0 Runtime**" in **Add/Remove Applications**, like I said.

---

### Post by izacboy_123 on 2006-10-15
> **Delkster said:**
> Which Java environment? We've probably just described different ways of installing the same one. Look for "**Sun Java 5.0 Runtime**" in **Add/Remove Applications**, like I said.

Sun Java 5.0 Runtime?

I can't find it. And i looked in the Advanced area too.

---

### Post by matt_risi on 2006-10-15
I'm actually having the same problem with Mercury, and I have the above Java package installed already (from Add/Remove).

By the way, to whomever started this post, running Ubuntu can be a pain in the neck, but it's a choice you made. If you want something that runs, looks, and acts like Windows, reinstall your M$ partition. If not, try to be more courteous to these nice people who are helping you and I. They don't have to.

---

### Post by aktiwers on 2006-10-15
Why not just install it with Automatix? 
You sound like a person who would love Automatix to begin with, and then learn all the other stuff slow. Give it a go!
[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

I installed Java with automatix, and it sure works great. And its Easy!

---

### Post by izacboy_123 on 2006-10-16
> **Delkster said:**
> The page may be a little confusing. It says:

"Sun Java5: Install it from the Applications -> Add/Remove... menu making sure to check the unsupported and proprietary software checkboxes, **or** install the sun-java5-bin package." (emphasis mine)

So, the package name is sun-java5-bin, which is the name by which you'll find it if you look for it in Synaptic, for example, but Add/Remove Applications uses more humane names and doesn't reveal the technical package names directly. In Add/Remove Applications, just make sure that you have unsupported and commercial software enabled and use the search to look for "java". The Sun Java Runtime 5.0 will be near the end of the list.

After that you can then also select the newly installed Sun Java Runtime Environment as the default Java virtual machine as instructed on the [Wiki page](https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b). Yes, the page could probably be a little more specific when it comes to selecting the default Java VM.


I've told you Sun-java5-bin is not in Add/Remove programs, nor is it in Synaptic. And i've searched for java.

---

### Post by izacboy_123 on 2006-10-16
Oh, and i tried installing the sun java packages. I got them from:[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java5/](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java5/)

But they all give the same error message:
Error: Dependency is not satisfiable:(THEN THE NAME OF THE PACKAGE)

I have tried all the packages is says i need to install for Ubuntu. All of them give the same error message:(

---

### Post by PriceChild on 2006-10-16
> **izacboy_123 said:**
> I've told you Sun-java5-bin is not in Add/Remove programs, nor is it in Synaptic. And i've searched for java.Which is why i have asked you to enable the universe and multiverse repositories.

---

### Post by izacboy_123 on 2006-10-16
How do i do that?:confused:

---

### Post by aktiwers on 2006-10-16
Go to System => Administration => Synaptic Package Manager

Then type in your password..  and go to Settings and pick Repositories and check the universial boxes.


But did you try Automatix as I said above?

---

### Post by PriceChild on 2006-10-16
> **izacboy_123 said:**
> How do i do that?:confused:For the third time: [https://wiki.ubuntu.com/AlwaysEnableUniverseMultiverse?highlight=%28multiverse%29%7C%28enable%29](https://wiki.ubuntu.com/AlwaysEnableUniverseMultiverse?highlight=%28multiverse%29%7C%28enable%29)

---

### Post by izacboy_123 on 2006-10-16
Linux crashed. So i installed it again. I'm going to start from scratch.

---

### Post by izacboy_123 on 2006-10-16
My friend is saying the complete oposite of what you are saying. He says download java package from [www.java.com](www.java.com) - And download Mercury from [www.mercury.to](www.mercury.to)

He says download java package and run the package from the terminal. But your saying download sun-java packages:confused: 

Your telling me to use the syptic system but my friend hasn't said anything about using that:confused: 

What the heck am i do to if people are giving me totaly different solutions. I appreaciate all the help, but it's confusing me when other people tell me different:confused: 

hmmmmm:-k

---

### Post by izacboy_123 on 2006-10-16
> **aktiwers said:**
> Go to System => Administration => Synaptic Package Manager

Then type in your password..  and go to Settings and pick Repositories and check the universial boxes

Oh, thanks!;)  I've checked all of the boxes, but i still can't find Sun-java in the list:(

---

### Post by Delkster on 2006-10-16
> **izacboy_123 said:**
> My friend is saying the complete oposite of what you are saying.

--

Your telling me to use the syptic system but my friend hasn't said anything about using that

I don't know your friend's background but what he's suggesting would probably be the way to go with some other Linux distributions that don't offer their own packages of Sun Java. It was also the way things used to be in Ubuntu, but now that there's a package in Ubuntu's own repositories, that's the best place to get it from.


If you still can't find Sun's Java, could you post the contents of your **/etc/apt/sources.list** file? That's where Ubuntu keeps information about the repositories it knows (which is where it can automatically download and install software and updates from). We could check and see if there's something wrong about it.

If you just did a clean install, open **Applications > Add/Remove**, enable "**Show unsupported software**" and "**Show commercial software**", search for just "java", and I'm quite surprised if you don't find "Sun Java 5.0 Runtime" at the end of the list.

You have the latest release of Ubuntu (6.06, so-called "Dapper Drake"), right? Some older releases don't have Sun Java in the repositories.

---

### Post by izacboy_123 on 2006-10-17
Thanks. I tried but i still can find sun-java:( 

And i checked the boxes you told me to check before i search for 'java'. Does this search for packages on your hard drive? Or find them via the internet?

If it finds them on your hard drive. Can you link me to the correct one? That would be great thanks!;)

---

### Post by izacboy_123 on 2006-10-17
OH WAIT!:)  i've found  Sun Java 5.0 Runtime!!:D 

*Double clicks on it*
*Clicks on the checkbox to the left of the icon*
:( 

'sun-java5-bin' is not available in any software channel
The application might not support your system architecture.

Aww:(  What's wrong there?

---

### Post by Onomatopoetikon on 2006-10-17
Well well.. I have the same problem, (and java is just fine and dandy, so it's most likely something else), and I stumbled upon this thread.. 

Good heavens man! It's taken the nice guys here 3 days to make you enable repositories, trying to make you follow the detailed guides in the documentation, listening to you rambling about why your OS isn't another OS, and your frustration about a feature such as sudo, which is the exact thing that makes this OS more secure than the other.. geez..

You know what? This is a very welcoming, friendly and forthcoming community. Normally there is no sign of a "no Homers allowed" mentality here, but this time, maybe there should be? Maybe you simply haven't got the interest and curiosity it takes to learn?

Your consisteny in **not** being willing to take advice, follow leads, do a little research and just plain 'ole RTFM is close to making this post look like a trolling attempt! Why would you even want to use Linux, if you don't want to find out what it is? 

Linux is **not** "free Windows"! Linux is Linux, learn how to use it instead of complaining about how it is not Windows! :mad: If you haven't got the desire to learn about Linux, remove it from your computer right now! It'll only cause you frustrations.

Phew, sorry guys.. had to get that off my chest. It's great to be helpful, but there's a limit.. helping someone is a two-way street, you guys can't take upon you to do everyones homework for them.

---

### Post by izacboy_123 on 2006-10-17
Have i ben alot of trouble?:( 

I'm sorry.:(

---

### Post by PriceChild on 2006-10-17
> **izacboy_123 said:**
> 'sun-java5-bin' is not available in any software channel
The application might not support your system architecture.Enable the multiverse repository as mentioned here: [http://wiki.ubuntu.com/Java](http://wiki.ubuntu.com/Java)

A more detailed guide on doing this is found here:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by izacboy_123 on 2006-10-17
omg omg omg!!:) 

I followed instructions here:[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

And i decided to see if it would let me check the 'Sun Java 5.0 Runtime'. AND IT DID!!!:-D 

Shall i click 'Apply'? Or will it bug up Linux?

---

### Post by PriceChild on 2006-10-17
Yes press apply, then follow the rest of the instructions.

---

### Post by izacboy_123 on 2006-10-17
YAAAY!:-D  It worked!! Thankyou so much!8) 

Is it safe to Install and Run 'Mercury' now?

---

### Post by PriceChild on 2006-10-17
> **izacboy_123 said:**
> YAAAY!:-D  It worked!! Thankyou so much!8) 

Is it safe to Install and Run 'Mercury' now?Find it in Applications>Internet>Mercury Messenger

or run it from cl with "mercury"

---

### Post by izacboy_123 on 2006-10-17
Oh good thanks! I still need to install it yet.

When i download Mercury, shall i double click on the package?
Or run 'sudo (FILENAME)' to install it as root?

Thanks:cool:

---

### Post by PriceChild on 2006-10-17
Either double click the package to install it with Gdebi
```
sudo dpkg -i <<name of package>>.deb
```to install on cl.

---

### Post by izacboy_123 on 2006-10-17
I installed it by double clicking on it.
Then i restarted Linux by pressing CTRL + ALT + BACKSPACE.
And i went to Applications -> Internet -> Mercury messenger...
It was loading. Then it stopped... Then it quit:( 
What have i done wrong to make it not work? I did install the right java package didn't i?

---

### Post by PriceChild on 2006-10-17
Can you run mercury inside a terminal to see what errors you get?

---

### Post by izacboy_123 on 2006-10-17
Okie dokie. I went to the terminal and typed in:'mercury'. It came up with this error message:
```
/usr/bin/mercury: line 1329: strings: command not found
Unable to locate the application's 'main' class. The class 'com.dMSN.Main' must be public and have a 'public static void main(String[])' method. (LAX)
Unable to Launch Java Application: Unable to locate the application's 'main' class. The class 'com.dMSN.Main' must be public and have a 'public static void main(String[])' method. (LAX)
```

By looking at it, i suspect an error with Java?

Thanks

---

### Post by PriceChild on 2006-10-17
Please follow the rest of the java guide... in particular this section: [https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b](https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b)

---

### Post by PriceChild on 2006-10-17
Please follow the rest of the java guide... in particular this section: [https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b](https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b)
Or just run this:```
sudo update-java-alternatives -s java-1.5.0-sun
```

---

### Post by izacboy_123 on 2006-10-17
Hi. I tried this that code in the terminal. I think it doesn't work becuase they all say they don't exist:
```
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/HtmlConverter
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/java-rmi.cgi
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/serialver
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/ControlPanel' to provide `ControlPanel'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java_vm' to provide `java_vm'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/javaws' to provide `javaws'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/keytool' to provide `keytool'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/pack200' to provide `pack200'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/policytool' to provide `policytool'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/rmid' to provide `rmid'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/rmiregistry' to provide `rmiregistry'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/unpack200' to provide `unpack200'.
No alternatives for firefox-javaplugin.so.
No alternatives for mozilla-javaplugin.so.
No alternatives for mozilla-snapshot-javaplugin.so.

```

hmmmmm:-k

---

### Post by PriceChild on 2006-10-17
Well some of them worked... try starting mercury now.

---

### Post by Delkster on 2006-10-18
> **izacboy_123 said:**
> And i checked the boxes you told me to check before i search for 'java'. Does this search for packages on your hard drive? Or find them via the internet?

On your hard drive there's a list of packages that Add/Remove Applications knows about. That's just a list -- whatever is installed is fetched from the Internet (or a CD or something). The list itself is sometimes updated from the Internet, too.

So, the packages are on the Internet but the search is done on your hard drive.


> **izacboy_123 said:**
> Hi. I tried this that code in the terminal. I think it doesn't work becuase they all say they don't exist:

Some of the files it tries to find probably don't exist because they're part of the JDK (the Java developer tools) and aren't included in the Runtime version which you just installed. I'd say that those errors are harmless. You don't need those files for running Java applications anyway, only for developing them.


Judging by the error message, the problem with Mercury might be within the Mercury package itself, not with your system. I'll check out if I can find something strange in it when I have time, which unfortunately isn't right now.

Meanwhile, you mentioned that you want to use Mercury instead of Gaim (which is included with Ubuntu) because the latter didn't work or something. What exact problem did you have with it? You might have the solution to your original problem right there.


As for the trouble installing Java and enabling repositories, I honestly thought that Add/Remove Applications offers to enable the required repositories for you when you attempt to install an application that is only available in one of those repositories you haven't enabled yet, so I thought you wouldn't have to do it manually. I guess I was wrong.


> **izacboy_123 said:**
> Have i ben alot of trouble?
Not really, but it makes it easier to help you if you provide the information we're asking for. For example, we don't ask you to post the contents of certain configuration files just for fun. We ask for it if we think that by seeing the configuration we might be able to find out what's wrong and thus how to correct it.

---

### Post by PriceChild on 2006-10-18
> **Delkster said:**
> Judging by the error message, the problem with Mercury might be within the Mercury package itself, not with your system. I'll check out if I can find something strange in it when I have time, which unfortunately isn't right now.Already checked, he hasn't updated alternatives.

---

### Post by izacboy_123 on 2006-10-18
> **PriceChild said:**
> Already checked, he hasn't updated alternatives.


What do you mean?

---

### Post by Delkster on 2006-10-18
> **izacboy_123 said:**
> What do you mean?

He means this:

> **PriceChild said:**
> Please follow the rest of the java guide... in particular this section: [https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b](https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b)
Or just run this:```
sudo update-java-alternatives -s java-1.5.0-sun
```

Since you now have more than one Java Runtime Environment installed, you have to tell the system that you want to use Sun Java by default. The system for managing such situations where more than one package can provide the same services is the "alternatives" system, and you now need to configure it so that Sun Java is used instead of the other possibilities.

Ubuntu comes with a free open-source Java environment installed, so that's why you now have more than one of them (the original one and now the Sun Java Runtime you installed). The one that comes with Ubuntu just doesn't run all Java applications yet so that's why you need Sun Java.

Just follow PriceChild's instructions and see if it works after that. If not, I'll look further to see if there's a problem with the package itself.

---

### Post by PriceChild on 2006-10-18
I've searched for you error... and according to google.... only 4 other people have experienced it... because they didn't use the following code:
> **PriceChild said:**
> Please follow the rest of the java guide... in particular this section: [https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b](https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b)
Or just run this:```
sudo update-java-alternatives -s java-1.5.0-sun
```

---

### Post by izacboy_123 on 2006-10-19
> **PriceChild said:**
> Please follow the rest of the java guide... in particular this section: [https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b](https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b)
Or just run this:```
sudo update-java-alternatives -s java-1.5.0-sun
```

I tried the code. But as i said, it failed.

I have no idea what the guide is talking about. I can't follow it, it's too complicated. I just really don't understand.

> n Ubuntu 6.06 or 5.10, if you want to use Sun's Java instead of the open source GIJ (GNU Java bytecode interpreter) you need to set it as default. To list installed JVMs:

Riiiiight... :-?

---

### Post by Delkster on 2006-10-20
> **izacboy_123 said:**
> I tried the code. But as i said, it failed.

If it fails, what does it say? We can't really say what's wrong or how to fix it if we don't know the error it gives, if any.

So, could you post the exact command you're entering, accompanied with the result it gives?

---

### Post by PriceChild on 2006-11-10
If```
sudo update-java-alternatives -s java-1.5.0-sun
```fails then you haven't installed java properly as described above.

(The user hasn't been active in 3 weeks but may be subscribed so replying again just incase, sorry i haven't paid attention)

---

### Post by Outworlder on 2006-11-16
I have stumbled on this thread.

Guys, if some damn application doesn't work, the proper thing to do is trying  to contact the author/community.

First, try this link:

[http://www.mercury.to/index.php?page=Wiki&wikipage=Linux_Setup](http://www.mercury.to/index.php?page=Wiki&wikipage=Linux_Setup)

If that doesn't solve the problem, the Mercury forums is the proper place to ask.

```

Exception in thread "main" java.lang.ClassFormatError: com.dMSN.Main (erroneous class name)
at java.lang.VMClassLoader.defineClass (libgcj.so.7)
at java.lang.ClassLoader.defineClass (libgcj.so.7)
at java.security.SecureClassLoader.defineClass (libgcj.so.7)
at java.net.URLClassLoader.findClass (libgcj.so.7)
at java.lang.ClassLoader.loadClass (libgcj.so.7)
at java.lang.ClassLoader.loadClass (libgcj.so.7)
at java.lang.Class.forName (libgcj.so.7)
at gnu.java.lang.MainThread.run (libgcj.so.7)
Winne@evh007:~>

```

> you current java is gnu classpath I believe, it should be sun

So, there.

If it doesn't work, follow the instructions here:

[http://www.mercury.to/index.php?page=Wiki&wikipage=ChangeJVersion](http://www.mercury.to/index.php?page=Wiki&wikipage=ChangeJVersion)

This Mercury.lax is what solved the problem for me.


I think I will write a nicer post so that people can refer to it in the future.

---

### Post by PriceChild on 2006-11-16
I would like to point out that I have been trying to get the user to make Sun java his default for the past 7 pages or so.

---

### Post by Outworlder on 2006-11-16
> **PriceChild said:**
> I would like to point out that I have been trying to get the user to make Sun java his default for the past 7 pages or so.

Point taken. I saw your heroic efforts.

This wasn't enough to solve the problem for me, however. So, in case there are some users that are actually able to read and willing to try the solutions, the links are there.

I do believe that this is Mercury's fault, though. A better launcher script could at least point out the problem.

---

### Post by janbockaert on 2006-11-18
where do you find this mercury.lax file?

---

### Post by Outworlder on 2006-11-18
> **janbockaert said:**
> where do you find this mercury.lax file?

Mercury installed it at:

/usr/lib/mercury/Mercury.lax

---

### Post by janbockaert on 2006-11-18
thanks, unfortunately, still no mercury for me. I guess i'll stay with gaim.

---

### Post by Outworlder on 2006-11-19
What is your current problem? We can still try to troubleshoot it.

---

### Post by janbockaert on 2006-11-21
i get this error when entering 'mercury' in the terminal:

nawk: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

---

