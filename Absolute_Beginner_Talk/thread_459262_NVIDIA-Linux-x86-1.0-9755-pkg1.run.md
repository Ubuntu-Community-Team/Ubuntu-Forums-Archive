---
title: "NVIDIA-Linux-x86-1.0-9755-pkg1.run"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by pappapump on 2007-05-30
Anybody know how I am supposed to use a .run file to install this new Linux driver?
I tried the steps outlines on the instruction page but couldn't make sense of it all.
It's supposed to be the new driver for Ubuntu Nvidia.
I also have no idea how to run .sh files

---

### Post by starcraft.man on 2007-05-30
> **pappapump said:**
> Anybody know how I am supposed to use a .run file to install this new Linux driver?
I tried the steps outlines on the instruction page but couldn't make sense of it all.
It's supposed to be the new driver for Ubuntu Nvidia.
I also have no idea how to run .sh files

I assume your aiming for Nvidia drivers. Don't bother manually, its a pain... and since you only do it once no point.

[Envy]("http://albertomilone.com/nvidia_scripts1.html") is your friend. Download stable version 9.3 and then double click, install, go to applications > System Tools > envy, and click automatically install Nvidia. It is almost full proof that it works after that, just answer yes to everything and reboot.

That should be it, say thanks to al :D.

---

### Post by taurus on 2007-05-30
You need to shutdown X first before you can install it or you will get an error message about X is still running.  Therefore, at the GUI login screen, press <Ctrl><Alt>F2 to log into a console.  Then, run

```
sudo /etc/init.dgdm stop
cd ~/Desktop
chmod 755  NVIDIA-Linux-x86-1.0-9755-pkg1.run
sudo ./ NVIDIA-Linux-x86-1.0-9755-pkg1.run
sudo /etc/init.d/gdm start
```

---

### Post by EagleRock on 2007-05-30
.sh files are batch files for the command-line interface, as well as .run files.  If you want to try to install the driver, this link might help:

[http://www.linuxforums.org/multimedia/installing_nvidia_3d_drivers.html](http://www.linuxforums.org/multimedia/installing_nvidia_3d_drivers.html)

Other than that, I'm sure others around here might be able to help you better...

---

### Post by pappapump on 2007-05-30
Ok I'm printing all this as I type.
One question, what is envy?
OOH I SEEEE i see!
That was a link and the click said it all thanx a lot bro!

---

### Post by lazyart on 2007-05-30
Clicking the link that starcraft.man left for you explains it all.

---

### Post by pappapump on 2007-05-30
Now I can try cedega again with Guild Wars and maybe It won't come up with that unrecognized Video card warning.

---

### Post by pappapump on 2007-05-30
Ok now how was that supposed to be funny?
I installed that lame program now I can't run Ubuntu.
All I get is this trash screen with ascii text in color.
Looks like I'm back to where I started.
I have absolutely NO idea how to work this os from the command line and all I get from boot now is some lame dos type screen.
Time to wipe and reinstall again.
> **taurus said:**
> You need to shutdown X first before you can install it or you will get an error message about X is still running.  Therefore, at the GUI login screen, press <Ctrl><Alt>F2 to log into a console.  Then, run

```
sudo /etc/init.dgdm stop
cd ~/Desktop
chmod 755  NVIDIA-Linux-x86-1.0-9755-pkg1.run
sudo ./ NVIDIA-Linux-x86-1.0-9755-pkg1.run
sudo /etc/init.d/gdm start
```

And what is X?
Any Idea how I can unload Envy so I can go back to Ubuntu?
Or do I have to start all over again and trash 2 days worth of work?

---

### Post by pappapump on 2007-05-30
Hello?

---

### Post by pappapump on 2007-05-30
hey!
Where did you all go?

---

### Post by starcraft.man on 2007-05-30
> **pappapump said:**
> Ok now how was that supposed to be funny?
I installed that lame program now I can't run Ubuntu.
All I get is this trash screen with ascii text in color.
Looks like I'm back to where I started.
I have absolutely NO idea how to work this os from the command line and all I get from boot now is some lame dos type screen.
Time to wipe and reinstall again.


And what is X?
Any Idea how I can unload Envy so I can go back to Ubuntu?
Or do I have to start all over again and trash 2 days worth of work?

Uhhh, I dunno why envy failed to work... it works on every other Nvidia card I recommended it for.

To fix your problem, I assume your in the console since your DM (display manager failed), just log in (type your username then password and of course enter). Then run this command please:

```
sudo dpkg-reconfigure xserver-xorg
```

Then follow the prompts (say ok when you don't know or go with the default when in doubt) and when you get to pick your driver , choose "nv" rather than "nvidia".

Then continue to the end, it will save and I believe the command to reboot from console is:

```
sudo reboot
```

Your screen should be back, then we can figure what went wrong... I am not sure though, please specify your nvidia card and other hardware.

Oh and sorry, I was away a bit... I'm surprised no one else posted........ *stares around*

---

### Post by pappapump on 2007-05-30
Actually no, I'm on the live cd now.
I was about to re-install.
I'll print this out and try what you said.
Oh and btw as usual the program could'nt write to my USR directory and several errors occured and since i couldn't manually stop the install it just went ahead and blew me up.

---

### Post by starcraft.man on 2007-05-30
> **pappapump said:**
> 
Oh and btw as usual the program could'nt write to my USR directory and several errors occured and since i couldn't manually stop the install it just went ahead and blew me up.

By usual program do you mean envy? You'd have to be more specific with the errors (I don't really know why Envy would have had trouble with usr), I'm not really sure what could have gone wrong (seriously, your the first (I think) nvidia person I recommend envy to that had trouble with it). It didn't blow up don't worry, we can always try another way :).

Oh and whats your card please, and other assorted important hardware?

---

### Post by pappapump on 2007-05-30
Im running slow as molases now but at least I got back to ubuntu.
Choosing the nv driver didnt work and now im not able to use the restricted driver either.
The Envy program couldnt write to my usr folder, in fact I get that error a lot with a lot of installable programs.
Right now I'm working with a generic driver at a real low resolution.
At least I'll be able to save my torrent files and a few other things if all goes bad.
I opened the Envy program again and am uninstalling their driver from the gui.
I will attempt to go back to the restricted driver, though that caused me to go back to the black screen before.
Maybe with Envy removed I'll be back to where i was.

---

### Post by NewJack on 2007-05-30
I had a problem installing Envy myself.  What ended up working for me was to:

1- Do a clean install of Ubuntu (Do you have a separate / partition, cause that makes reinstalling a whole lot easier).

2- Before installing any other programs, install Envy and configure it as per the instructions.

3- Finally, install any other programs you need to install from the repos.

Hope that helps.

---

### Post by pappapump on 2007-05-30
I can see where that would be a good idea.
Do you think that having the Restricted driver in use at the time of install may have caused the crash?

---

### Post by NewJack on 2007-05-30
Here is the Envy page by Alberto Milone:  [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Follow the instructions on the page and you shouldn't have a problem.  But I do suggest you do a clean install of Ubuntu first.

---

### Post by pappapump on 2007-05-30
Thanx newjack.
Ima try another HD with that program when I'm done.
I have another 20 PC's to setup with Ubuntu since I dropped Microsoft products.
I'm trying to make an Ubuntu poster for the front window advertising that MS products are no longer supported.
Maybe I'll lose a few customers, but this isn't really the money making side of my business.
Matter of fact, the rising costs of MS products has pretty much wrecked any profit I could ever make from a new PC with competition from HP and Compaq.
So dropping support for MS products wont hurt me a bit.
I still fix problems with MS based machines but the customer has to bring all their software for their repair since I took most of my MS CD's and decided to use em for Target practice.

---

### Post by starcraft.man on 2007-05-30
> **pappapump said:**
> Thanx newjack.
Ima try another HD with that program when I'm done.
I have another 20 PC's to setup with Ubuntu since I dropped Microsoft products.
I'm trying to make an Ubuntu poster for the front window advertising that MS products are no longer supported.
Maybe I'll lose a few customers, but this isn't really the money making side of my business.
Matter of fact, the rising costs of MS products has pretty much wrecked any profit I could ever make from a new PC with competition from HP and Compaq.
So dropping support for MS products wont hurt me a bit.
I still fix problems with MS based machines but the customer has to bring all their software for their repair since I took most of my MS CD's and decided to use em for Target practice.

Just a thought but if you are setting up 20 computers with the exact same set up (i.e. same programs preinstalled/configured), the easy way is to image one desktop (after you set it up exactly how you want it) and then clone it to the others (using whatever imaging program you have). Ubuntu usually works off of any of the hardware by default (just don't install the drivers into the computer you image, unless their all the same card/driver as all the rest). Will save you the energy of setting up all of them by hand.

As for the Envy problem, I still don't know what went wrong... it works on all nvidia cards to my knowledge, its only ati thats gets the issues really.

---

### Post by pappapump on 2007-05-30
Well, whatever happened it affected all my nvidia stuff so that even the restricted drivers wont work.
Ima save everything and just do a wipe and re-install.
I'm just too frazzled now after 2 hours of trying to get this all fixed.
Update
After retracing my steps it seems that I installed an unstable release, ill see if the new ones worx now.

---

### Post by pappapump on 2007-05-30
OK starcraft man im about to try envy on a new install, wish me luck.

---

### Post by starcraft.man on 2007-05-30
> **pappapump said:**
> OK starcraft man im about to try envy on a new install, wish me luck.

En Taro Adun! 

:D

(I love that saying ^^)

It better work this time, else there must be something wrong with your card... if it goes wrong again use the command to get ya back into Ubuntu and we will further diagnose >.>.

---

### Post by pappapump on 2007-05-30
OMG that was a disaster.,
Crash and burn no less!
Envy 0.9.3 serious error.
Let me figure out how to do a screenshot and I'll show u the results.
I haven't even loaded the restricted drivers yet.

---

### Post by starcraft.man on 2007-05-30
> **pappapump said:**
> OMG that was a disaster.,
Crash and burn no less!
Envy 0.9.3 serious error.

What does serious error mean? Envy wouldn't install? You rebooted and it was in console mode (text log in)? You have to be more specific. Can you also tell me your hardware (including nvidia card)... 

I dunno why envy didn't work for ya twice in a row, guess chalk it up to Murphy and his silly law...

The restricted driver management can't interfere with the envy install, least as far as I know...

---

### Post by pappapump on 2007-05-30
Nah, package problem etc won't install.
Which image editor does screen shots?

---

### Post by starcraft.man on 2007-05-30
> **pappapump said:**
> Nah, package problem etc won't install.
Which image editor does screen shots?

Just push print screen(alternatively Applications > Accessories > Screenshot), should let you save a pic right there to desktop then attach...

---

### Post by pappapump on 2007-05-30
Ok here goes

---

### Post by pappapump on 2007-05-30
Wierd thing is that unstable release actually ran ok.

---

### Post by starcraft.man on 2007-05-30
> **pappapump said:**
> Wierd thing is that unstable release actually ran ok.

Weird........ >.>.

Try using the unstable envy then, it should run ok I think most of his new fixes are for broadening it out for more OS's I believe.

---

### Post by Hobo Joe on 2007-05-30
Just go ahead and do it manually, what you need to do is:

1. Save the driver to your desktop
2. Shutdown the X server by <Alt><Ctrl>F2.
3. Login.
4. type 'cd Desktop'
5. Type
```

sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run

```

Then follow the instructions and it SHOULD do everything for you.

---

### Post by pappapump on 2007-05-30
Next images complete with errors

---

### Post by Hobo Joe on 2007-05-30
I'm pretty sure it always says that. And it looks like it's downloading properly in the last pic.  Let it run for a minute.

---

### Post by pappapump on 2007-05-30
Just go ahead and do it manually, what you need to do is:

1. Save the driver to your desktop
2. Shutdown the X server by <Alt><Ctrl>F2.
3. Login.
4. type 'cd Desktop'
5. Type
Code:

sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run

Then follow the instructions and it SHOULD do everything for you.
__________________
Reply With Quote

ok i printed that just in case I go boom again.
If that happens I'll be gone for the better part of an hour.
Then finnigan begin again.

---

### Post by pappapump on 2007-05-30
Ok got that, time to reboot!
Lets hope I crash and return properly!
LMAO!
Thanx for the patience ppl, your'e all great.

---

### Post by Hobo Joe on 2007-05-30
> **pappapump said:**
> Ok got that, time to reboot!
Lets hope I crash and return properly!
LMAO!
Thanx for the patience ppl, your'e all great.

Glad to be of service!  ;)

Don't forget to help other people with their problems!

---

### Post by starcraft.man on 2007-05-30
> **pappapump said:**
> Ok got that, time to reboot!
Lets hope I crash and return properly!
LMAO!
Thanx for the patience ppl, your'e all great.

Uh, are you telling us you still haven't rebooted and got it working? or you did and your being sarcastic?

Hope ya got it working :).

---

### Post by pappapump on 2007-05-30
Didnt work.
Ok the ascii screen said that the drivers were wrong etc.
My Video card is an FX 5500 Nv of course.
Looks like Taurus may have the right answer for this problem.
I downloaded that driver already and the site says its a match for my card.

---

### Post by Hobo Joe on 2007-05-30
Sounds like it's time to try the manual method.

---

### Post by pappapump on 2007-05-30
Sorry, had to get the new file, lost the original driver.
So I save this file to desktop for your directions to work?
Still have no idea what an X-Server is.
Your freaked out Cat pic cracks me up bad.
I have 5 that look just like him.
Ok entering manual mode.
Buckaroo Banzai has nothin on me!

---

### Post by starcraft.man on 2007-05-30
Thats really weird... failing twice like that... can't say its happened to me before.

Good luck with the manual fix, I think I posted enough in this thread... you should be able to get it to work with his instructions.

Adios. :)

---

### Post by pappapump on 2007-05-30
I swear I typed it 3 times and says it couldn't find it and there it is STILL on the desktop typed exactly as the paper printout.
My Ascii screen says im in the desktop directory.

---

### Post by Hobo Joe on 2007-05-30
> **pappapump said:**
> Sorry, had to get the new file, lost the original driver.
So I save this file to desktop for your directions to work?
Still have no idea what an X-Server is.
Your freaked out Cat pic cracks me up bad.
I have 5 that look just like him.
Ok entering manual mode.
Buckaroo Banzai has nothin on me!

Make sure you adjust the commands for the filename.

To put it simply, the Xserver is the graphical interface.

If you want an explanation that is more than you would ever want to read, you can check [this]("http://en.wikipedia.org/wiki/X_server") out.

I think that picture is a short way of summing up my personality. :)

---

### Post by pappapump on 2007-05-30
mojo@mojo-desktop:~$ sudo /etc/init.dgdm stop
Password:
sudo: /etc/init.dgdm: command not found
mojo@mojo-desktop:~$ cd ~desktop
bash: cd: ~desktop: No such file or directory
mojo@mojo-desktop:~$ cd~desktop
bash: cd~desktop: command not found
mojo@mojo-desktop:~$ chmod 755 nvidia-linux-x86-1.0-9755-pkg1.run
chmod: cannot access `nvidia-linux-x86-1.0-9755-pkg1.run': No such file or directory
mojo@mojo-desktop:~$ cd desktop
bash: cd: desktop: No such file or directory
mojo@mojo-desktop:~$ cd- desktop
bash: cd-: command not found
mojo@mojo-desktop:~$ chmod 755 NVIDIA-Linux-x86-1.0-9755-pkg1.run
chmod: cannot access `NVIDIA-Linux-x86-1.0-9755-pkg1.run': No such file or directory
mojo@mojo-desktop:~$

---

### Post by pappapump on 2007-05-30
I think I'll try the manual driver install and see if I can select it that way.

---

### Post by Hobo Joe on 2007-05-30
> **pappapump said:**
> mojo@mojo-desktop:~$ sudo /etc/init.dgdm stop
Password:
sudo: /etc/init.dgdm: command not found
mojo@mojo-desktop:~$ cd ~desktop
bash: cd: ~desktop: No such file or directory
mojo@mojo-desktop:~$ cd~desktop
bash: cd~desktop: command not found
mojo@mojo-desktop:~$ chmod 755 nvidia-linux-x86-1.0-9755-pkg1.run
chmod: cannot access `nvidia-linux-x86-1.0-9755-pkg1.run': No such file or directory
mojo@mojo-desktop:~$ cd desktop
bash: cd: desktop: No such file or directory
mojo@mojo-desktop:~$ cd- desktop
bash: cd-: command not found
mojo@mojo-desktop:~$ chmod 755 NVIDIA-Linux-x86-1.0-9755-pkg1.run
chmod: cannot access `NVIDIA-Linux-x86-1.0-9755-pkg1.run': No such file or directory
mojo@mojo-desktop:~$

I see a couple mistakes, but they are part my fault.

I forgot to mention the part about 
```

sudo /etc/init.d/gdm stop

```
But you remembered it, BUT you forgot a slash between init.d and gdm.

Also, there is no ~ before the desktop command. It's just:
```

cd Deskop

```
Make sure to capitalize Desktop.
When you do the .run file, do 'sudo sh' rather than 'chmod'.
And like I said, if you downloaded a different package, make sure to adjust the command accordingly.

---

### Post by pappapump on 2007-05-31
KABOOM!
Back to live CD.
I'm completely worn out now.
I'll just give up on this till i have some more skill and live in restricted driver mode.
I'm spending more time repairing and altering this than I am enjoying it.
I'll be back after re-install and read some more.

---

### Post by erusfatum on 2007-05-31
hey guys! 
i have exactly the same problem as pappapump.
i installed envy, choose to install the nvidia driver etc, then it asked me if i want to restart and i did so.
then when ubuntu boots, it goes to text mode and a screen full of $@# and stuff like that pops up and says smt about x server couldnt start etc...
ill try now the sudo dpkg-feconfigure xserver-xorg or the manual install of nvidia-linux-x86 drivers
will inform you with the results...

ps i have a nvidia geforve 7600gt card

Update:  ive done only the sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run command and every thing worked fine and is as before!

---

