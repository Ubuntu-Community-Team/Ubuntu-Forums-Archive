---
title: "Cherry Cymotion Master Linux in Edgy"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Goodson1974 on 2007-03-19
Hi all

I've just received a Cherry Cymotion Master Keyboard and cannot install the Keym@n software that ships with it.

When i try and install the [I]keyman_1.0.0-13_i386.deb from the CD with GDebi package installer, the following error occurs: -

Error: Dependency is not satisfiable: kdelibs4

I checked in Symantic and there was no kdelibs4 listed.

I've searched in the forums, but there does not seem to be anything Edgy specific regarding this keybaord.

Has anyone had any luck getting the extra keys to work?

Any help would be greatly appreciated.
[/I]

---

### Post by icckleblackcat on 2007-04-01
Hi,

I'm builing a system with one of these at the mo and have ordered a couple more for the other systems in the house :)

it might take a little while but I'll keep you posted on how I got on & hopefully try & post a howto :)

you'll just have to be a little patient with me....

---

### Post by Goodson1974 on 2007-04-02
Good luck with it!
 
Any help would be great :)

---

### Post by icckleblackcat on 2007-04-12
Ha... just arrived today :)

means I can get started.....

---

### Post by darkrose on 2007-04-12
closest i have got so far to getting this working is

download the keyman package from cherry for suse 10.1
convert to .deb with alien
install libxerces27
install the new keyman deb
edit /etc/init.d/keyman and change the first line to #!/bin/bash
now to get it all working issue the following commands:
/etc/init.d/keyman restart
keymanserver

You will get a pile of errors when starting keymanserver but it does work, no ability to remap the keys yet though.
Still working on getting it to work without the errors.

---

### Post by darrengoddard on 2007-07-24
i'm very interested in a resolution to this challenge too.  i got this keyboard as a free gift when i subscribed to linux format magazine.

i'm going to report this issue to them and if i do get a positive response from them, i'll post it here.

dg:)

---

### Post by darrengoddard on 2007-07-24
Well, I've spoken to the reviews editor at Linux Format and this is his advice.  

QUOTE
You basically need to change the keyboard definition used by the xorg.conf file to configure the screen and keyboard when your system starts the X windows.
 
From a command line, type:
 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
sudo nano /etc/X11/xorg.conf
 
This first makes a backup of the file, then opens it using the 'nano' command line text editor. Cursor down in the file to the 'InputDevice' section, and change the XkbModel value to 'cherryblue'. Here's how it looks in my xorg.conf:
 
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "cherryblue"
        Option          "XkbLayout"     "gb"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection
 
Press 'Control + x', then 'y' and carriage return to save the file. You then need to log out and back in again or restart your machine. You should now be able to use the extra keys, although you'll need to define them yourself in the applications you use.
END QUOTE

Hope this helps.  It worked for me.

dg:)

---

### Post by TheKernel on 2007-11-08
Not sure if its too late to be any use, but I also have the Cherry CyMotion Master Linux keyboard received as a subscription gift from Linux Format. 

On Feisty Fawn, I installed the keytouch and keytouch-editor packages. Keytouch has keymappings for a number of keyboards including the CyMotion.

To install:

sudo apt-get install keytouch keytouch-editor

Once installed, there should be entries under your system menu for both keytouch and keytouch-editor.

Selecting keytouch will immediately ask you for your keyboard type. Select the Cymotion Master Linux.
The additional key mappings are immediately available. I haven't needed to use the editor.

I'm sure I also used these packages when I had  Edgy but I may be wrong.

Hope this helps :)

Nigel

---

