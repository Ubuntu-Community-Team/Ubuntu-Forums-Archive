---
title: "How do I install a package? An ATI Driver package?"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by Mike_SMD on 2006-02-08
Hi folks,
I'd been experiencing real problems trying to get Ubuntu to provide 3D support on my Radeon 9500 Pro video card, I followed the guides people pointed out and played like mad but in the end got nothing. So here I am now, I just finished reinstalling Ubuntu and I'm going to try the one thing that wasn't listed as an option... I've downloaded the drivers from ATI's website and am planning to follow *their* instructions as per how to get them set up. I need a little bit of help though.

(and this is the embarrassing part)

How do I get the package to start doing it's thing?
You know, like... running?

This is the output from my shell, I was in the directory where I had deposited the installer.

mike@ubuntu:~$ ls
ATI  Desktop
mike@ubuntu:~$ cd ATI
mike@ubuntu:~/ATI$ ls
ati-driver-installer-8.21.7-i386.run
mike@ubuntu:~/ATI$ sudo ./ati-driver-installer-8.21.7-i386.run
sudo: ./ati-driver-installer-8.21.7-i386.run: command not found

(the sudo bit is as I read that I had to be logged in with super user priveleges for the installation... which I think is what 'sudo' sort of does)

Now...
I'm the first to admit that I'm helpless as a babe here, the few commands so far that I've picked up have been gleaned from peeking at the output of other people's shells (and naturally not much periphery knowledge ever seems to be included) but I'm sure that I can overcome this wee little sticking point. I can see why people migrating over from windows get frustrated with linux early and end up quitting though, despite the warm fuzzy of being part of an alternate movement --it does at times seem to be little more than the nerf version of hell. At least the people are nice.

So yeah. 
In clarified form how do I get THAT package to run in particular and then in the future will these directions work on others? I'm making an information exchange agreement out of this, one way or another I'll let you know what happens and if this helps to enable 3D support on my system I'll document it into some kind of guide that can be posted and fed like bread to the masses.

Have a nice day,

Mike_SMD

---

### Post by towsonu2003 on 2006-02-08
check out this one: [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

---

### Post by David Corrales on 2006-02-08
You need to set the execution permission on before running a file. You can do that by typing **chmod +x *filename***.
Then again, if you're new, you'll be best off following a guide to ensure that you don't break anything that leaves you with a showstopper :)

---

### Post by Mike_SMD on 2006-02-08
towsonu2003, thanks for the link but I've already gone that route. None of the tweaks and tips did anything except crash my x server... that's why I'm trying this alternate approach instead.

Ok.
So... I finally found a guide on running executables and it turns out that linux has this thing called 'permissions' and blah blah blah. I needed to set the permissions on ati-driver-installer-8.21.7-i386.run so that I could execute it. If the permissions aren't set on a file to allow a user to execute that file then it turns out that user just can't do it. Seems simple enough actually, and probably important so I'll file it away for some later in depth study.

So I executed it.
And it seemed to do it's thing, came up with a graphical installer, asked some easy questions, no error messages that I could see and then it told me everything worked. Finished with a list of things to do;

1) Backup the xorg.conf file     #this I did
2) Run aticonfig from the command line     #this I'm stuck on
3) Reboot for the changes to take effect     #naturally haven't done this part yet either

How do I run aticonfig? When I try I get this in response...

mike@ubuntu:~$ aticonfig
bash: aticonfig: command not found

Worse I tried the 'Search for Files' applet in Gnome under the Places heading (top left of the screen between Applications and System) and this name (aticonfig) isn't even showing up. What am I doing wrong here?

Would running aticonfig be the same as reconfiguring x using...

sudo dpkg-reconfigure xserver-xorg

... and then just manually entering in 'fglrx' instead of 'ati' in the driver heading? (that taken from the other thread posted by towsonu2003)

I don't want to do anything that will clutter things up and make them more difficult to sort out than I have to, as such any advice would be greatly appreciated.

Thanks once more for all the help,


Mike_SMD

---

### Post by David Corrales on 2006-02-08
Ok, it's time to search for the file. Type the next in console:

**sudo updatedb**
**locate *ati***

The first command will scan the filesystem creating an index with all the files so you can use **locate** to well, locate files :p
You then use **locate** with a string to search for a file that matches. You can change the *ati* string to anything you like, like *aticonfig* or *aticonf*. I suggested *ati* because that will show you all matching files that might be useful to you. Remember linux is case sensitive so *aticonfig* is not the same as *Aticonfig* or *AtiConfig*.

For the 3rd step, type:

**sudo nano /etc/X11/xorg.conf**

There, look for the line that reads *Driver     "ati"* and change it to *Driver     "fglrx"*

---

### Post by Mike_SMD on 2006-02-08
Hi David, thanks for the help...

I did what you said and tried to find the 'aticonfig' file but it isn't showing up. I got plenty of hits with 'ati' as the string but nothing when I specified 'aticonfig'... and none of the other hits looked even close.

While you were responding I decided to try running the following command...

sudo dpkg-reconfigure xserver-xorg

... and then using nano to edit my xorg.config file changing the driver from 'ati' to 'fglrx'. This just crashed my x server but I fixed it by changing the xorg.conf file back and then rebooting.

I just tried running fglrxinfo from the command line and got the following;

mike@ubuntu:~$ fglrxinfo
bash: fglrxinfo: command not found

Does this mean that it isn't actually installed yet? Or do I have to find the proper place to run it from? Maybe change some permissions? Naturally, it isn't showing up using the locate command either...

Ha!
Well, as usual... any help will help!


Mike_SMD

---

### Post by David Corrales on 2006-02-08
It looks like something didn't get properly installed since the files are nowhere to be found.
Did you use **sudo** to run the ATI driver installer? You should have in order to be able to write to places only a super user can.

---

### Post by Mike_SMD on 2006-02-08
Hey David... in the end I think you were basically correct.
However, it's also humble-pie time.

As of right now I have the following shell output and everything works!

mike@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9500 Pro Generic
OpenGL version string: 2.0.5582 (8.21.7)

mike@ubuntu:~$ glxgears -printfps
18399 frames in 5.0 seconds = 3679.738 FPS
17446 frames in 5.0 seconds = 3489.093 FPS
18590 frames in 5.0 seconds = 3717.965 FPS
18594 frames in 5.0 seconds = 3718.606 FPS
18277 frames in 5.0 seconds = 3655.340 FPS

Ah, HA! HA! HA! HA!

And this is how it happened (and where the humble pie comes in), you see all I did in the end was follow the instructions from an earlier thread that had been sent over by good old towsonu2003;

(New folks go HERE if you can't get 3D support with your ATI video card) 
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

... which before when I had peeked at thought was actually a *different* thread that I had previously explored (in my meek defense they both sort of start out the same, and I was kind of frustrated overall at that point). So yes, towsonu2003 supplied the answer... I followed the listed instructions to the letter and it all worked. Up and running like magic. No complaints so far.

So, sorry towsonu2003 for not paying better attention, and thanks to everyone who has helped out so far. I appreciate it, I'm learning as I go and frankly this is exactly the type of mentorship that is needed if the linux crowd is to keep on growing.

I hope you all have a nice day,


Mike_SMD

---

### Post by David Corrales on 2006-02-08
Haha nice to hear it's working! :)

---

### Post by towsonu2003 on 2006-02-08
now I'm *jealous*!

/throw chair to own ati card and continue to be jealo#$@^%WERF%$@NOCARRIER

;)

---

