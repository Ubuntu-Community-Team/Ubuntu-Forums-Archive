---
title: "How to make a script like windows .bat file"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by gbfoxbat on 2007-07-17
Hi,

I would like to make a script or like windows batch file that I can run whenever needed. I need this because my USB ports freeze after laptop comes around after hibernation and basically this is what I run through terminal sudo 

rmmod usbhid xpad ehci_hcd ohci_hdc usbcore
sudo modprobe usbcore usbhid xpad ehci_hcd ohci_hcd 

The idea behind is that I want to create a batch file that I can run from desktop instead of going through the process of starting terminal etc...etc.

Thanks for the help

---

### Post by Malibu Illusion on 2007-07-17
Put this into a file:

```
#!/bin/sh
if [ $(whoami) != "root" ]; then
	echo "You need to execute this script as root."
	exit 1
fi

rmmod usbhid xpad ehci_hcd ohci_hdc usbcore
modprobe usbcore usbhid xpad ehci_hcd ohci_hcd
```

Name it: whatever.sh and you're done.  Execute it with: 

```
sudo sh whatever.sh
```

---

### Post by gbfoxbat on 2007-07-17
> **Malibu Illusion said:**
> Put this into a file:

```
#!/bin/sh
if [ $(whoami) != "root" ]; then
	echo "You need to execute this script as root."
	exit 1
fi

rmmod usbhid xpad ehci_hcd ohci_hdc usbcore
modprobe usbcore usbhid xpad ehci_hcd ohci_hcd
```

Name it: whatever.sh and you're done.  Execute it with: 

```
sudo sh whatever.sh
```

Thanks for the help...However I cannot still run this of the desktop and have to enter terminal. Is there anyways I can run this off the desktop by just clicking it just like a windows batch file.?

---

### Post by jordanmthomas on 2007-07-17
You can use gksudo...you'd need to use your password still, but you could just click on it.
```
gksudo sh whatever
```

---

### Post by splintercellguy on 2007-07-17
I think you'll have to chmod it so the execute bit is set.

---

### Post by jordanmthomas on 2007-07-17
splintercellguy: not as long as you keep the sh before the filename.  You're looking at something like this:
```
#!/bin/bash
script
script
script
```
to run as **scriptname** instead of **sh scriptname** you would need to chmod +x it.  However, you could not chmod it and do **sh scriptname**.  Does that make sense?

---

### Post by gbfoxbat on 2007-07-17
> **jordanmthomas said:**
> You can use gksudo...you'd need to use your password still, but you could just click on it.
```
gksudo sh whatever
```

But I still need to type gksudo in terminal right? or in run command? thats exactly what i want to avoid that is opening or going into a terminal

---

### Post by jordanmthomas on 2007-07-17
No, you can create a launcher on your desktop and put
```
gksudo sh whatever
``` as the command line and then it will be launched when you click the launcher

Here's what I'm talking about:  (screenshots)

---

### Post by splintercellguy on 2007-07-17
> **jordanmthomas said:**
> splintercellguy: not as long as you keep the sh before the filename.  You're looking at something like this:
```
#!/bin/bash
script
script
script
```
to run as **scriptname** instead of **sh scriptname** you would need to chmod +x it.  However, you could not chmod it and do **sh scriptname**.  Does that make sense?



Yep, thanks for the enlightenment :).

---

### Post by gbfoxbat on 2007-07-17
> **jordanmthomas said:**
> No, you can create a launcher on your desktop and put
```
gksudo sh whatever
``` as the command line and then it will be launched when you click the launcher

Here's what I'm talking about:  (screenshots)

Thanks for the tip.. but have a another issue in order to create a launcher I presume one clicks on the desktop right click and chooses option create launcher I assume. But I dont have this option please see attached screen shot

---

### Post by splintercellguy on 2007-07-17
Ah, you appear to be using Xfce. I think there's something like Create shortcut or something equivalent in that window manager.

---

### Post by gbfoxbat on 2007-07-17
> **splintercellguy said:**
> Ah, you appear to be using Xfce. I think there's something like Create shortcut or something equivalent in that window manager.

Hmm im very new to ubuntu and looked everywhere and didnt see any options such as you mention

---

### Post by splintercellguy on 2007-07-17
If you right click on the desktop, there should be something like Create shortcut, nothing like that? Screenshot of your context menu?

---

### Post by jordanmthomas on 2007-07-17
Nope, that's KDE, not xfce.  You won't have gksudo installed either unless you added KDE after Gnome.  :)
I am not entirely sure how to make a shortcut in KDE, so we'll do this the old fashioned way, cool?

Open up a Konsolem
```
mkdir ~/bin
cd bin
kwrite unFreeze

```
Put these lines in it:
```
#!/bin/sh
if [ $(whoami) != "root" ]; then
	echo "You need to execute this script as root."
	exit 1
fi

rmmod usbhid xpad ehci_hcd ohci_hdc usbcore
modprobe usbcore usbhid xpad ehci_hcd ohci_hcd
```
Save and close;
then, make it executable (back in console)
```
chmod +x unFreeze
```
Now, cd to your Desktop
```
cd ~/Desktop
kwrite unFreeze

```
put this:```

#!/bin/bash
kdesu $HOME/bin/unFreeze
```
save and close,
chmod +x it:
```
chmod +x ~/Desktop/unFreeze
```

Now, you should have a link on your desktop you can use to unfreeze your USB stuff.

**for the record, you should be able to add a custom launcher onto your panel (kicker) somehow.  I haven't used KDE in a while so I can't remember the exact steps or I'd give them to you.

---

### Post by gbfoxbat on 2007-07-17
> **jordanmthomas said:**
> Nope, that's KDE, not xfce.  You won't have gksudo installed either unless you added KDE after Gnome.  :)
I am not entirely sure how to make a shortcut in KDE, so we'll do this the old fashioned way, cool?

Open up a Konsolem
```
mkdir ~/bin
cd bin
kwrite unFreeze

```
Put these lines in it:
```
#!/bin/sh
if [ $(whoami) != "root" ]; then
	echo "You need to execute this script as root."
	exit 1
fi

rmmod usbhid xpad ehci_hcd ohci_hdc usbcore
modprobe usbcore usbhid xpad ehci_hcd ohci_hcd
```
Save and close;
then, make it executable (back in console)
```
chmod +x unFreeze
```
Now, cd to your Desktop
```
cd ~/Desktop
kwrite unFreeze

```
put this:```

#!/bin/bash
kdesu $HOME/bin/unFreeze
```
save and close,
chmod +x it:
```
chmod +x ~/Desktop/unFreeze
```

Now, you should have a link on your desktop you can use to unfreeze your USB stuff.

**for the record, you should be able to add a custom launcher onto your panel (kicker) somehow.  I haven't used KDE in a while so I can't remember the exact steps or I'd give them to you.

Yep its KDE your right. I will try what you mention and let you know, Thanks for the help.

---

### Post by cawill on 2007-07-17
kdesu is used in kde instead of gksudo if you didnt already know this.

---

### Post by jordanmthomas on 2007-07-17
Yes, once I learned he was using KDE I used kdesu instead of gksudo in my instructions.

---

### Post by loudmouthman on 2007-07-17
ironically Windows batch files are the cousins of the long utlised and very powerful shell scripting languages which unix operators have become familiar with. The most common shell file you will see is BASH and if you want to learn more I cannot recommned enough the [Advanced Bash Scripting Tutorials]("http://tldp.org/LDP/abs/html/")

---

### Post by gvoima on 2007-07-17
Does those modules get automaticly unloaded/reloaded on hibernation? I know USB  controllers will.

If not, then you should be better of to add them on the modules list in acpi-support, rather than running a script everytime. Atleast you should try that, if you already haven't.

---

### Post by matey3 on 2008-02-14
Thanks for the info.
Can some one please tell me how I could rename some of the functions in unix?
OK I am lazy and have fat fingers so I dont want to type --help |more every  time so since I am used to old dos I'd like to do a command then /? to get the help for that command. Now I know I cant use / since it is a directory pointer so can I create a "batch file" named ? and in that file I can type in" --help |more " so I can use it every time?

Thanks a bunch in advance!

example I want istead of doing this:
chmod --help |more  
do this:
chmod -? 
or
 chmod ? 
or whatever works with least amount of typing.

I already changed "clear" to "cls" but I dont know how to pass parameters to the commands.

Regards;

---

### Post by samwyse on 2008-02-14
> **gbfoxbat said:**
> Thanks for the tip.. but have a another issue in order to create a launcher I presume one clicks on the desktop right click and chooses option create launcher I assume. But I dont have this option please see attached screen shot

"Link to Application" is what you need.

---

### Post by jordanmthomas on 2008-02-14
> **matey3 said:**
> Thanks for the info.
Can some one please tell me how I could rename some of the functions in unix?
OK I am lazy and have fat fingers so I dont want to type --help |more every  time so since I am used to old dos I'd like to do a command then /? to get the help for that command. Now I know I cant use / since it is a directory pointer so can I create a "batch file" named ? and in that file I can type in" --help |more " so I can use it every time?

Thanks a bunch in advance!

example I want istead of doing this:
chmod --help |more  
do this:
chmod -? 
or
 chmod ? 
or whatever works with least amount of typing.

I already changed "clear" to "cls" but I dont know how to pass parameters to the commands.

Regards;

Unfortunately, the ? is reserved and you won't be able to use it easily.
You can try this though.
```
gksudo gedit /usr/local/bin/h
```
Put this in there
```
#!/bin/bash
$0 --help

```
The $0 means "the first argument given to this program" $1 would be the second, etc.
Then, make it executable
```
sudo chmod +x /usr/local/bin/h
```
Then, you'll be able to run something like this:
```
h chmod
``` to get help on chmod


Hope this helps some.  If anyone knows a way to use ? without it being a real pain, feel free to chime in.

---

### Post by matey3 on 2008-02-15
Thank You very much indeed.
you are right about special chars they are reserved. 


> **jordanmthomas said:**
> Unfortunately, the ? is reserved and you won't be able to use it easily.
You can try this though.
```
gksudo gedit /usr/local/bin/h
```
Put this in there
```
#!/bin/bash
$0 --help

```
The $0 means "the first argument given to this program" $1 would be the second, etc.
Then, make it executable
```
sudo chmod +x /usr/local/bin/h
```
Then, you'll be able to run something like this:
```
h chmod
``` to get help on chmod


Hope this helps some.  If anyone knows a way to use ? without it being a real pain, feel free to chime in.

---

