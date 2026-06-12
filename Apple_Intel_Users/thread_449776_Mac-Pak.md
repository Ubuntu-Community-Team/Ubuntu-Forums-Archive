---
title: "Mac-Pak"
date: 2007-05-20
forum: Apple Intel Users
---

### Post by martinbures on 2007-05-20
What if we incorporate all of the changes in the macbook, macbook pro, imac, etc wikis into install scripts/meta-packages.  Make something either like automatix, or make something like apt-get install macpak-macbook.

All of the mac machines within each type are identical - we could make all of the customizations stupidly easy to apply.  

I don't know how to do this but with some guidance I could give it a try.

I have a Core Duo Macbook.

martin.

---

### Post by david_edmundson on 2007-05-20
That's a really good idea, the danger comes with the fact even though the hardware is the same, the software currently installed and what's already been changed in the system could be different.

I think a good place to start would be writing a load of independant shell scripts for each task. From that writing a front end to launch them would be a doddle.

The best language to write the scripts in is shell script. Shell scripts are basically just lists of commands that you would type in a terminal (like batch scripts in Windows/DOS). It should be nice and easy for a user to quickly check what is going to be running as root on his machine.

Start making a list in the forum of scripts that need to be made. To start the ball rolling:
915resolution installation
WebCam
Trackpad setup
Keyboard setup
Keyboard shortcuts 
Backlight
Suspend

---

### Post by ronocdh on 2007-05-21
> **david_edmundson said:**
> That's a really good idea, the danger comes with the fact even though the hardware is the same, the software currently installed and what's already been changed in the system could be different.

I think a good place to start would be writing a load of independant shell scripts for each task.
I agree about the scripts; if you guys've ever used Kilz's and Kuja's over in the the 64-bit forum, they run like a dream. So convenient!

But I think the problem is more that Apple isn't the best about disclosing changes to the hardware; we'd have to pay extremely close attention (via **lspci**, I suppose) to who's using what hardware, because even within the C2D MBP, we've seen the Atheros chipset change. Stuff like that.

I'm just adding a precaution, I still think it's an awesome idea and I would totally support it. Given the progress from Edgy to Feisty with OOB compatibility for the Mactels, I'm really looking forward to Gutsy! But let's see what we can pull together.

---

### Post by oskarloko on 2007-05-21
> if you guys've ever used Kilz's and Kuja's over in the the 64-bit forum

what's ???

Ok, yes, it will be great...

... we'll use python-gtk... ¿ not better just shell scripting ?

---

### Post by martinbures on 2007-05-21
I don't know anything about shell scripting but I have been teaching myself python for a while so I could definitely write in that.

I was just looking at the edgy and fiesty wikis and was thinking that it would be pretty simple for the first cut.
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

For example:

macbook

# get os version
version = os.sys.version

def exec_cmd( file ):
    for line in file.readlines():
        os.popen( line )

if version == 'EDGY':
    # open file with edgy commands
    cmd_file = open( 'EDGY_cmd_file.txt', 'r' )
    exec_cmd( cmd_file )

elif version == 'FEISTY':
    # open file with feisty commands
    cmd_file = open('FEISTY_cmd_file.txt', 'r' )
    exec_cmd( cmd_file )

else:
    print 'Sorry - can't work with this version...'


You know - get some sort of simple framework in place so that someone with an imac can do that one, someone with a powerbook can do that one, etc.

so:
EDGY_cmd_file.txt
sudo software-properties -e universe
sudo apt-get update
sudo apt-get -y install network-manager-gnome
#

wget [http://ubuntu.desrt.ca/macbook-backlight_0.0-1_i386.deb](http://ubuntu.desrt.ca/macbook-backlight_0.0-1_i386.deb)
gdebi-gtk macbook-backlight_0.0-1_i386.deb
sudo chmod u+s /usr/bin/macbook-backlight
gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_1 "0x65"
gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_2 "0xd4"
gconftool-2 --type string --set /apps/metacity/keybinding_commands/command_1 "/usr/bin/macbook-backlight -10"
gconftool-2 --type string --set /apps/metacity/keybinding_commands/command_2 "/usr/bin/macbook-backlight +10"
sudo ln -bs /bin/true /usr/sbin/laptop-detect
sudo sed -i~ 's/KP_Enter/Pointer_Button3, Pointer_Button2/' /etc/X11/xkb/symbols/pc
gconftool-2 --type bool --set /desktop/gnome/accessibility/keyboard/enable true
gconftool-2 --type bool --set /desktop/gnome/accessibility/keyboard/mousekeys_enable true

...
etc

Something like this would probably be good for the first 90% of the stuff.  make a simple way to have most of the stuff configured.

what do you guys think.  I'll add more later but have to run.
martin.

---

### Post by martinbures on 2007-05-21
Ok, so here is a real first-cut.  

The first problem is that when I issue popen2( command ), it does not have a password.  The command has sudo in it, so it fails.  How can I query and pre pass sudo?

remember - real rough...

martin.

---

### Post by david_edmundson on 2007-05-22
Good effort, 

Some quick points/ideas

You've proven you can do shell scripting...
Rename FEISTY_PLATFORM.TXT to FEISTY_PLATFORM.SH and add the top add 
'#!/bin/sh'. Then make it executable. This is now a shell script that can be run independently of the python. (which would be ideal for testing). This also means you can run system.popen('kdesu ./feisty_platform.sh') instead of reading the file in and running it line by line. (kdesu in the KDE run as root dialogue..Gnome has one similar but I don't know that it's called)

Which should resolve the whole issues with root access.

On an additional note:
Comment your script (however you choose to run it) with lots of "echo Installing Wireless drivers" or some such, so the user has some idea what's going on.

I'd split the scripts up into one for each action. That way you avoid having to duplicate, and makes it easy to update scripts in future.

On the whole, Very good work! I'm impressed.

---

### Post by ronocdh on 2007-05-22
> **david_edmundson said:**
> kdesu in the KDE run as root dialogue..Gnome has one similar but I don't know that it's called.
For KDE it's **kdesu** and for GNOME it's **sudo**.

Regarding Martin's work, first, great job! I think this is a wonderful starting point. We're going to need a lot more input from the forum members here, because for instance, I see this is already skewed toward the MacBooks rather than the MacBook Pros or the iMacs, given that you've included 915resolution package and nothing else. ;)

However you plan to do hardware determination, once we get verbose output (like grepping **lspci** or something), we can tailor the package for all models.

Killer initiative, this looks like it'll be a great contribution to the community!

---

### Post by martinbures on 2007-05-22
I was trying to make it so that it was really simple.  That way, anyone with a different mac just changes a few things in the text file.  This could be use for other laptops also, or other machines/configurations.  

Maybe by making it real simple, all of the detection could be reduced.  Maybe to get the xorg configurations, I could make a patch and then it would be a matter of the script installing a patch.  And if the alternate kernels were placed in a repository, getting suspend could be real simple for everyone.

I really appreciate the input.  I'll try to get an update out within the next day or so.  Hopefully I can get some of this stuff working.  If anyone has some ideas, throw out some thoughts.  Maybe we can make this process painless.

---

### Post by ronocdh on 2007-05-22
> **martinbures said:**
> Maybe by making it real simple, all of the detection could be reduced.  Maybe to get the xorg configurations, I could make a patch and then it would be a matter of the script installing a patch.  And if the alternate kernels were placed in a repository, getting suspend could be real simple for everyone.
I agree, of course. I think that the best option would be to get hardware detection to the level that your package could include bash commands for all packages which *could* be necessary, and of course call only those which actually are, based on the hardware.

If it's not feasible to get hardware detection to this level, then you'll have to craft different scripts for all the different models, e.g. [LIST]
[*]MacBook (Core Duo)
[*]MacBook (Core2 Duo)
[*]MacBook Pro (Core Duo)
[*]MacBook Pro (Core2 Duo)
[*]iMac (ATI)
[*]iMac (Nvidia)
[*]Mac Pro
[*]Mini
[*]etc.
[/LIST]
This is where the lot of us comes in! So keep lists at the ready, guys, of which packages you have found indispensable in configuring your systems. Again, great work, Martin!

---

### Post by oskarloko on 2007-05-23
Just pointing

For GNOME - gksudo 
For KDE - kdesu
For terminal: sudo

---

### Post by ivesjd on 2007-05-23
Something to help with key remapping would be great too. It is pretty simple, but can be hard to figure out what keys are what.

---

### Post by martinbures on 2007-05-24
Thanks, Oskarloko.  I'll use that instead.  That should fix the problem.

martin.

---

### Post by martinbures on 2007-05-24
Ok.  Here is a quick update.

- right now, only for macbook core duo -

1.  Removed sudos.  Run as root to get around this:

sudo python mac-pak.py

2.  Made a patch of xorg.conf and added that to the install script, so you get out-of-the-box qsynaptics.

What is included:
915resolution
qsynaptics
webcam

Once I figure out why I can't get the kernel to compile, I will try to find a way to post debs for the updated kernel/madwifi so that suspend will work properly.

So on top of that, list any additional tweaks that you do that I might include to make it more usable - like a good qsynaptics config file or something.

I am going to test it tomorrow or this weekend.  If anyone wants to try it and has any feedback, let me know, or make a fix and post it back.

later.
martin.

---

### Post by martinbures on 2007-05-25
Oops.  It will error out when you run it - there is stuff for later at the bottom that will look for a file that doesn't exist yet.

I'll fix it soon.

martin.

(you can just comment out the stuff that deals with the file that does not exist and it should run)

---

