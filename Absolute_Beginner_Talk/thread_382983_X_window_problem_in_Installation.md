---
title: "X window problem in Installation"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by SuperAndy on 2007-03-12
Ok, absolute beginner... I have a very slight amount of unix/linux experience, literally sums to being able to navigate a file system in the shell... :p

However, I do want to learn, so I want to install ubuntu. When I try to do the live boot thing, with both i386 and x64 versions (i do have a 64bit processor) i get the ubuntu thing up, it goes through all the stages, i presume it gets to the point where it would show me the log in screen, or whatever, but i get an error message, telling me X window has failed, and I can have a look at the log.

If i do this, i can then see that it finds my graphics card ok, it gets it right, but then it says "no screen found", or something along these lines. It says this twice, i presume because i have two graphics ports on my card (its an ATI X800 GTO)

Full System Spec:
ATI X800 GTO PCI-E
LG L1710M 17" Monitor
1GB RAM
ASUS A8N-VM motherboard

Think thats all the vital stuff...

i can then get the shell, and from there, i can find the desktop folder, which does have stuff in it. so it must be messing up right at the last minute.

And I know i can use the text based installer, I have got into this ok, but there isn't much point, as the chances of an installed version of ubuntu working when the live one doesn't is pretty remote.

So, I offer myself to you, linux gods. please help!

---

### Post by SuperAndy on 2007-03-12
Ok, i have done some google searching, and found the following:

chances are its a problem with the driver. If i install in the text based installer, and then get to the shell installed, I should be able to see what driver I am running. If its ati, i can try VESA. if this works temporarily, then yay.

apparently this works, so, this will be my project.

Just posted it here so its in this place, hopefully it will be useful to someone else :)

---

### Post by Scunizi on 2007-03-12
This can happen.  I "feel" your growing pains with linux.  I started about 9 months ago from "www" (wonderful world of windows).  You might need to reset your xorg.conf file.  That a file that handles the x server (your graphical desktop.  Since you can get to the command prompt (non-graphical) from there type " sudo dpkg-reconfigure -phigh xserver-xorg ".  It will ask you some questions you should be able to answer, primarilly about screen resolution.  Do not check off any resolutions you are not sure of.  When it's done, restart the machine... there's another way to do this but I find I'm suffering from a memory leaka at the moment.  After rebooting you should hopefully be in the normal graphical environment.  From there you'll have to search for the way to install the ATI drivers.  If there are drivers in Synaptic for ATI use those first before trying to install the bleeding edge drivers directly from ATI or other places.  After installing the appropriate drivers from Synaptic, you will probably have to run the first command again after changing a line in your xorg.conf file.  I'm running Nvidia so I can't help you there.  If you want to just look at the file without being able to change anything, from the terminal type gedit /etc/X11/xorg.conf and you'll get the contents.  By the way after the graphical environment is up and running, after changing anything to xorg.conf you can restart the x server by CTRL/ALT/Backspace.  Not quite a windows tree finger salute but close.  It only restarts the x server.

---

### Post by SuperAndy on 2007-03-12
aye, i remember the ctrl+alt+bkspc, thats a nice one for when the gui just messes up.

cheers for the reply, i think what you said and what I found are coming from the same kind of direction...

I wont be doing anything about this for about 3 weeks, various uni commitments and then I wont be in the same country as my PC for 2 weeks... but after that period, I will be sure to report back as to whether it works or not

Thanks!

---

### Post by SuperAndy on 2007-03-15
hey, right.

i installed ubuntu in text mode, everything was great. it even detected vista, which was better than suse managed...

i then tried the method given above, but upon restarting i wasn't in the gui.

so i tried

dpkg-reconfigure xserver-xorg

and went through the entire thing. i selected VESA, because i know this should work in all situations, but, alas there was nothing, not even a jumbled screen. my monitor just says no signal input. so i presume from that some of my settings were wrong. i cant think why, but if anyone is familiar with this process, can they just give me some tips on what to do? Things like memory i left blank, just ok'd all the keyboard stuff, the only thing i can thing of is the address bit. hmm. well, we will see.

---

### Post by SuperAndy on 2007-03-15
i am a moderator on another forum. i kill people for doing this...

bump

---

### Post by Scunizi on 2007-03-15
Did you preface the dpkg line with sudo?  Is it a dual head video card?  Do you have two monitors hooked up to it?  What kind of card?  Please don't kill us/me!  We/ I get busy too.

---

### Post by SuperAndy on 2007-03-15
erm, yes to sudo

i have a VGA and DVI out, is that what you mean? if so, yes

nope

its an ati X800 GTO, in my sig

i realise ati is like, death, but there we go, i made a choice, i am stuck with it

and i have tried any manner of combinations of resolutions, glx enabled/disables, plugging my VGA monitor into VGA and DVI using the cunning converter, etc etc.

i have also manually entered the horiz and vert refresh rates

and when i run lspci -x i get an address of 03:00.0 for my graphics card, with 03:00.1 for the secondary (DVI)

---

### Post by Scunizi on 2007-03-15
If you installed it in text mode then you may not have install the graphical environment at all.  Unless you mean by text mode, the Alternate CD..  To install the graphic environment, sudo apt-get install desktop-ubuntu or is it ubuntu-desktop.  I tried to find a referance as to which way in another tab but couldn't quickly find it.  One of them will install the gui, the other will do nothing.

---

### Post by SuperAndy on 2007-03-15
well, i am pretty sure i did. a lot of gnome stuff was installed, along with gimp, open office, etc etc...

and there is a desktop folder in my user

---

### Post by Scunizi on 2007-03-15
This may be an Edgy thing with your video card.  I found a referance to it here.. [http://www.ubuntuforums.org/showthread.php?t=383063&highlight=x800](http://www.ubuntuforums.org/showthread.php?t=383063&highlight=x800).  Basically, what they say in the post is to edit the video configuration file.  The text mode or terminal is the right place to be to do this.
First boot and log-in.
next type "sudo nano /etc/X11/xorg.conf" (without the quotes). Pay attention to the case of the letters. Caps have a different meaning in Linux.  A file named XORG.CONF or Xorg.conf is not the same as xorg.conf.

You should be presented with a text file and lots of stuff.  You can only move around in this file with the arrow keys (well... there are probably shortcuts but I'm not aware of them).  Look for "Section "Device" ".  The first line of this section is "Identifier" and will list your video card (usually).  The next line is "Driver" and may say "ati" or "Ati". Put the cursor on the beginning of Ati and hit delete until you are left with only the quote marks and then type "Radeon".

Now Control O (that's oh no zero) to write the changes to the file. Then Control x to exit.  This will take you back to the normal text prompt.

Now type "sudo /etc/init.d/gdm restart" and see what happens.  The machine may appear to be rebooting and if we're successful you'll have your Gui.

By the way nano or vi or vim are all text line editors.  When you're actually in the GUI and need a text editor from the terminal a lot of people will use gedit.  It's much more like notepad and friendly when moving from one system to another.  

If this doesn't work you may want to post the entire contents of your xorg.conf file just to see if there are other issues going on as well.  Keep us posted.

---

### Post by SuperAndy on 2007-03-16
right, i did exactly what you said. i am confident with my nano skills, just finished a uni course in c programming...

i changed the driver and all that, rebooted the gdm.

then i got a text error, same to the xserver-xorg style, saying:

"Fatal Server Error
No Screens Found"

when i looked at the logs, it showed everything was ok, untill it came to load 'Radeon'. It couldn't do this, but carried on for a bit.

And then the (EE) No Screens Found error came up...

i would export this to a file or something. The easiest way would be a floppy i should imagine, but i have no idea how to mount that drive in ubuntu. Tell me that, and i will post my xorg.conf, and try and post those error logs.

by the way, i am very grateful for you helping me, and taking the time to try and work out whats going on :)

---

### Post by Scunizi on 2007-03-16
I guess I'm what you call a windows power user.  Been doing it since inception but I have zero programming skills.  I know how painfull it was for me to jump into this "new" operating system and wrap my head around some of the concepts.  I'm still a nOOb but the learning curve has flattened a bit.  

As for the floppy I assume (dangerous word) you've tried to put the floppy in and nothing happened that you could tell?  The naming convention for linux is much different for drives and other media.  Format a floppy with vfat 16 or 32 on your windows box and then put it in the linux drive.  Now type "cd /media".  This should be a familiar command and will change the directory you're in to media.  Now type "ls" and enter.  That's a lower case L.  It will give you a directory listing.  You'll probably see hda1, maybe sda1, floppy etc.  These are directory text listings of the drives that are mounted.  If you see floppy then you can cd /floppy and issue another ls to see what's on the disk.  When you format the floppy you might want to copy a small text file to it just so you'll see something in the directory when you pull it up.  If you can see it, it works!  Now to copy the file to the floppy you'll need to type "sudo cp /etc/X11/xorg.conf  /media/floppy"  that is if floppy is the correct label for it.  While you're at it look in your /etc/X11 directory and see if you have any other files that start with xorg.conf."something" and include those as well.  You're system may have automatically backed up your original and I'd like to compare it to the new one.

---

