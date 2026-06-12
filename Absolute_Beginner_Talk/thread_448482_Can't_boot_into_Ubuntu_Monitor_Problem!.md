---
title: "Can't boot into Ubuntu Monitor Problem!"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by destructo on 2007-05-19
Hi there, hopefully someone can help.

Here is the problem. I have a LG L1953T monitor.

When I turn the computer on it starts loading everything, there are two "beeps" then when it goes to the log in screen the monitor switches itself off and says "digital power saving mode" and the light goes from blue to orange and just sits there. I can not get access to anything.

Is there something wrong with the monitor or a way I can get back into my computer without a reinstall. 

Here's what I've tried to fix this problem.


I have tried using the analog cord but I get the same problem.
I have taken the graphics card and put it back in.
I have tried changing the boot sequence.
I have also managed to get my stuff off of the computer and back it up, well most of it.


Thanks.

---

### Post by tchoklat on 2007-05-19
is this with Ubuntu installed or with the LIveCD?

---

### Post by netwerx on 2007-05-19
Does this only happen when trying to boot your os, or do you not get any image at all from the minute you hit your power button on your computer?

EDIT: Opps, missed part of the post, yur getting to the logon correctly right?

---

### Post by destructo on 2007-05-19
thanks for the quick response.

This is with ubuntu installed.

I do not get to the logon screen at all, the monitor switches itself off before i get to that stage.

---

### Post by jerrylamos on 2007-05-19
#1.  What Ubuntu are you trying to run?  Dapper 6.06? Edgy 6.10? Feisty 7.04?  They're all different.
#2. How did CD Live run?  You should be able to run most applications CD Live before  doing an install.  If CD Live doesn't run what you want to do,  install likely won't either.
#3. On boot options with CD Live, did you try "safe graphics mode"?  What happened?
#4. On CD Live, push F6, and delete the word "quiet" on the line.  Then when you continue boot you should get a flood of messages.  What do the last few lines say?
#5. On CD Live, push F6, add "break=top" to the line, example:
.....quiet splash break=top
That might give you a command line where some screen setup could be tried.
#6. If break=top gives you a usable command line, try this:
sudo dpkg-reconfigure -phigh xserver-xorg

If that gives you something to work with you can try different graphics drivers and screen settings,  After you finish, there are a couple things you could type I'm not sure which might work:
exit
Ctrl-Alt-Del
startx

Post back here anything that you see on the screen before it goes blank.

Cheers, Jerry

---

### Post by destructo on 2007-05-19
1. ubuntu 7.04 feisty fawn 64 x86.
2. I already have Ubuntu installed and i have been using it for about 3 weeks.
3. I don't undestand as there is no option when i boot it with the cd

---

### Post by destructo on 2007-05-19
Notice i already have ubuntu installed and its workijng i just can't get into it.

here are the options on the cd when i boot with cd.

Install in text mode
Text mode Install for manufacturers
Install a command-line system
Check Cd for defects
Rescue a broken system
Memory test
Boot from first hard disk


then down the bottom it has these options


F1 Help F2 Language F3 Keymap F4 VGA F5 Accessibility F6 Other Options

---

### Post by destructo on 2007-05-19
bump. :)

---

### Post by destructo on 2007-05-19
anyone else got any ideas?

---

### Post by destructo on 2007-05-19
okay i got a command line and typed in 

sudo dpkg-reconfigure -phigh xserver -xorg and a list of things came up, what option should i pick and/or is this right

here's the lines

deconf: Ignoring invalid priority "ghigh"
deconf: Valid priorities are: low medium high critical
Unknown option: x
Unknown option: o
Unknown option: r
Unknown option: g
Usage: dpkg-reconfigure [options] packages
-a, --all   reconfigure all packages
-u, --unseen only
-- default-priority
-f, --force
-p, --priority
--terse

---

### Post by destructo on 2007-05-19
bump

---

### Post by destructo on 2007-05-19
bump

---

### Post by destructo on 2007-05-19
this seems to be the problem

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/31992](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/31992)

---

### Post by destructo on 2007-05-19
when i try either of these lines in "recovery mode"

/var/log/xorg.o.log

/etc/x11/xorg.conf

I get  "no such file or directory"

any ideas, I really need to get back into my computer as i need to do my assignment, please help.

---

### Post by destructo on 2007-05-19
another link if it helps

[https://answers.launchpad.net/ubuntu/+question/5816](https://answers.launchpad.net/ubuntu/+question/5816)

---

### Post by destructo on 2007-05-19
okay in recovery mode i did this 

"sudo dpkg-reconfigure -phigh xserver-xorg" and changed the resolution back. what do i do now?

---

### Post by jerrylamos on 2007-05-19
The CD options you list look like the Alternate CD to me, not the regular Ubuntu Feisty Fawn 7.04 with Gnome.  There's nothing about "text mode" on the regular Ubuntu Feisty CD.  The Alternate CD has a lot less packages on it and is for installing web servers and such that don't need Xwindows and don't use Gnome, or for installing to a problematic machine in text mode, expecting someone would add Gnome to it later (big big package with lots of dependencies).

If you have/can install the Alternate CD, then you'd have to ask someone or search the forums on how to add Gnome to it.  I don't have such an installation to look at the menu selections.  I think it would be less trouble to install the regular Ubuntu with Gnome already on it, provided of course it is compatible with your hardware.

The command 
sudo dpkg-reconfigure -phigh xserver-xorg 
has no spaces before the - except for the -phigh.  
dpkg-reconfigure is one word.
xserver-xorg is one word.

What this command does is set up X windows for your system.  A few things you need to know are what the Linux driver is for your graphics controller, and what resolutions and color depth you would like to use.  The driver for my various Intel graphics controllers is i810.  I don't know the driver for your graphics chip, maybe someone looking at this forum would know, or the manufacturers internet site for your controller.  The resolution has a lot to do with what your display will support like 1024x768 or 1280x1024 or whatever.  There is a color depth number which has to do with how much video memory you have; 16 is probably safe to start with.

The expected case is that Xwindows will be able to detect what driver you need and what screen resolutions are possible.  It does work a lot of times, however in a few like one of my systems I had to set resolution with the command.

If you don't know what graphics driver to use, look for VESA.  it works but is slow.

Post what happens next....Jerry

---

### Post by destructo on 2007-05-19
yes thanks jerry i was putting the command in incorrectly. I have the resolution of 1280x1024 and yes you are very clever in picking up on the fact that i am using alternate edition. I'm sure now i should have mentioned that.

When i changed the resolution to 1280x1024 i put in "/etc/X11/xorg.conf" and it comes up with

"bash: /etc/X11/xorg.conf: Permission denied"

what now?

---

### Post by destructo on 2007-05-19
Woho, i got back in, thanks for your help Jerry. I am currently downloading a dvd of ubuntu 7.04. I had trouble installing other versions of ubuntu so i went for the alternate version and it worked. I hope this new version that i am getting will be able to install.

Thanks.

---

### Post by jerrylamos on 2007-05-20
> **destructo said:**
> yes thanks jerry i was putting the command in incorrectly. I have the resolution of 1280x1024 and yes you are very clever in picking up on the fact that i am using alternate edition. I'm sure now i should have mentioned that.

When i changed the resolution to 1280x1024 i put in "/etc/X11/xorg.conf" and it comes up with

"bash: /etc/X11/xorg.conf: Permission denied"

what now?

You can do an edit of xorg.conf if you like; I prefer to run the sudo dpkg-..... command.  You need to have supervisor privileges example
sudo gedit /etc/X11/xorg.conf
but gedit is what I use, gedit is a Gnome full screen editor.  Note if there's an error in xorg.conf then Xwindows can't come up and you have to do a sudo dpkg-... all over again.

It can be quite informative to look at xorg.conf from a terminal command line:
less /etc/X11/xorg.conf
less is a full screen browser that can't change the file so it is safe, but you can readily see what the dpkg did.  To exit less, press q for quit.

People do use the Alternate when one of the regular Ubuntu's won't come up, however there may be workarounds that allow the regular Ubuntu to boot to a usable state.

Cheers, Jerry

---

