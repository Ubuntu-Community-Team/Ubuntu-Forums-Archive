---
title: "My Adventures with Ubuntu 5.10 - Need Help"
date: 2005-09-18
forum: Absolute Beginner Talk
---

### Post by sonyack on 2005-09-18
So I download the 5.10 iso and burned it and no key would work on the keyboard.  I finally figured out that I had to use a ps/2 port.  So I rummage around and find a usb to ps2 adapter.  Found another for the mouse, just in case.  Keyboard worked, but the installation dragged on and on and failed.  Someplace here someone said burn the iso at very slow speed.  Did that, and taDa, this burn went ahead and installed.  I did notice that once I got to the Ubuntu Configuration stuff, the item "Console Fonts" listed as "Failed."  Shrug.

I have installed Ubuntu 5.10 on a secondary drive, and was a little nervous about letting it alter the master boot volume, lest it somehow mess up my Windows XP installation, but I went ahead, because if things went ok, then I would not have to enter bios and change the boot order everytime I wanted to switch, and things went fine.

So I get to the login and do that and get to the desktop and everything seems to be working.  I found out I could stumble around a bit, usefully.  Changed the desktop theme.  Fired up Firefox, which I use on Windows anyway, and even got my favorite Firefox skin and installed it just fine.  Configured the email client.  Got some wallpaper.  

Well.  Now the hard part.  Plugins for Firefox.  Not a clue how to.  Watch a video clip off the cd-rom.  Nope, no codec, even with the bundled video player.  Oh well, I'll get DivX Player and that'll solve that.  Nope, don't know how to install that.  Audio 
cd's autoplay and the cdplayer works.  But, no Flash, no Realplayer, no WMP, no Quicktime for the browser, none of these for the OS.

So I look at the directions for "installing" these downloaded plugins for Linux again and again and try it again and again.  Again and again, typing the commands in terminal brings up the message "no such file or directory."  So I am doing something wrong.

I need these pulgins, who doesn't.  I need a video player that will do at least microsoft and realplayer stuff, besides the standard mpg/mpeg and avi.  I don't think there is a Quicktime for Linux.

So I need a tutorial on how to install things.  It has to be simple and step-by-step and not assume I know where things are or how to get to them.  Does anybody know where to find such a tutorial?

---

### Post by Havoc on 2005-09-18
Well, If you're a "newbie", whatever that means, then you're better off with Hoary (5.04), since Breezy (5.10) is still quite beta at the moment.With Hoary, you can download "Easy Ubuntu", or the Unofficial Add-on CD (Look in the forums), and they'll do the hard stuff for you.Or you could just wait till Breezy comes out for good, and people the community starts putting out stuff to lessen the pain.

Ubuntuguide is good for a quick reference though.That, and the wiki are great for reference.If you want an in-depth solution, just go here:

[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

Generally the best way to go for in-depth.Oh, and I want to note that the Ubuntuguide does not "support" Breezy yet.

---

### Post by kspr on 2005-09-18
edit: remove this post.

---

### Post by Havoc on 2005-09-18
Oh and the reason why Ubuntu does not include such things (Multimedia except for ogg and some others, flash, realplay, and others) is because Ubuntu is both free as in "Free Beer!" and as in "Freedom of Speech".Those applications are obviously not one or another (Or even sometimes, both), so Ubuntu cannot include that.

Before you start BASHING UBUNTU! [-X

---

### Post by sonyack on 2005-09-18
Aha.  Didn't realize that 5.10 was so beta.  I guess I should get the earlier version and do things over.  Thanks for the clues re: help.  "Documentation" didn't seem to me to be about elementary pointers and help.

Yep, total newbie to this.  Yesterday was the first day I looked at anything Linux.  Pleased at what I am seeing, but will be more pleased once I learn how to.

Thanks again.

Edit:
OY!  I thought I was bashing myself!  It's not Ubuntu's fault I don't have a clue.  Like, if I get on a bicycle and fall off and crash into things, that's because I don't know how to ride it, and need pointers and practice.  If I tell people what happened to me when I got on the bicycle, that's not bashing the bicycle....

So, sorry if my post is readable as a bashing, certainly was not intended that way.

---

### Post by aysiu on 2005-09-18
For the first time in the five months I've been using Linux, the Ubuntu Guide website appears to be down, but ordinarily, this should help:

[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

---

### Post by Havoc on 2005-09-18
I'm just pulling your leg...You're not a flying skull, are you? Morte?
Anyways, It's not that Breezy is *THAT* beta, It's just that the communtity has made some quick (And automatic) solutions in order to lessen the pain of initial configuration....The same can be done in Breezy, but you have to know which packages you're gonna download etc.

Oh and, here's some advice.The nice thing about Linux is that you almost never (A little bit of an overstatement, yes) have to search through the net to find the applictaion you need.Just open up synaptic (The package manager), and search for the description of the thing you want.Click on the little box to install.Once you know you've got what you want, click on apply! It's that easy! No endless web searching, no hassle!

You just have to enable the repositories.Do a quick search on that.
Or mabye, open up a terminal (First thing, do NOT fear the terminal.It holds a LOT of power) and type "sudo gedit /etc/sources.list", without the quotes, of course.Enter your user password in the prompt, and a text editor will open up.
Then you gotta uncomment (remove the #) the lines where it tells Ubuntu, "Oh, look in here too!", meaning, the lines that look something like this:

*deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted*

The text file actually tells you which lines are those.After you're done, save the file, exit the text editor, open up synaptic, click "refresh" or something and there! You've got 16000 packages working for you!

There *is* a graphical way of doing that in synaptic, but I don't really remember.If you're afraid of the command line, don't be.If you're still afraid you can search for the graphical solution.  :^o

---

### Post by TristanMike on 2005-09-18
Well, if Ubuntu is your first dive into the Linux waters, then let me be the first to say, "Come on in, the water is fine!"

You for sure want the 5.04 version untill sometime in October when the Offical 5.10 comes out. Don't worry about Havoc's post. I think that was a little to hasty to assume you were Ubuntu bashing, as you were clearly not. But it can be a fine line between honest questioning and "bashing" but don't be afraid to ask questions.

 :)

EDIT: Havoc beat me to it ha, ha, good job old man.

---

### Post by sonyack on 2005-09-18
Thanks, everyone, for your kind replies.  For a couple years I've been the one helping people with their computers - how they get themselves into these messes, I'll never know - and now I'M the fish out of water, lol, so it's a little disorienting.

I think I'll stick with this 5.10, as it is already installed.  I've got the email, and Firefox does well enough without the plugins so I can cope until I figure out how to get things plugged into FF.  I wanted DivX Player for the system because it plays all the file types, including the Windows stuff.  I guess RealPlayer does, too, but I'm not thrilled with the skin.  On Windows, I use everything but the MS stuff, if it works, so I never have to see MS apps, other than the os gui.

So I'll just have to slow down here and do some research and try to step-by-step it.  Thanks again.

---

