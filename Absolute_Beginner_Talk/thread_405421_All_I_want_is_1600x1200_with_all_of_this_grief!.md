---
title: "All I want is 1600x1200 with all of this grief!"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by BobLand on 2007-04-09
I'm using fiesty on a fairly vanilla computer.  I have GeForce 4 with a ViewSonic P180.  I've been using this combo for over 5 years in W2K.

I've tried every suggestion that I've found scattered all over the place and none work.  Who do I have to bribe to get this to work?

Is this possible at all?  I'd love to get off windows but I feel like I'm going from bad to worse.  Prove me wrong.  PLEASE!

bobland

---

### Post by STREETURCHINE on 2007-04-09
i cant help you but ,if you post links to what you have tried it would save people from posting solutions you have already tried.
it is always good to give as much information as possible..:)

---

### Post by kyphi on 2007-04-09
I am not sure what your question is.

Do you mean that you want to change resolution to 1600x1200 in Ubuntu ?

If so, then do this:

In an Ubuntu terminal type

sudo dpkg-reconfigure -phigh xserver-xorg

on the ensuing screen use your up/down keys to scroll to the resolution you want and then select it by pressing the spacebar. Then enter and exit.

Then log out and back in. Done.

---

### Post by Peter1234123 on 2007-04-09
Okay, I have an ATI Raedion Mobility X700, however, I got my screen resulution to 1600x1400, what I did was, first of all upgrade Linux Kernal (forgot command) then type sudo apt-get install fglrx (or something lke that) then use Nano or Pico to open up your xorg config file, and change the driver to fglrx.

---

### Post by slimdog360 on 2007-04-09
Im guessing you would have alrady tried the suggestion from kyphi and it still didn't work? Im pretty sure the fglrx thing is just for ati, so (if Im correct) that won't work either. If you havent already tried this, do the same thing sudo dpkg reconfigure-xserver... you get the idea. But when you come to the bit where you have to sleect your monitor setting, go advanced. 

It will ask you for some numbers, for the HorizSync (it will the the first set of numbers) type in 30&#8211;80. For the VertRefresh (the second set of number which you have to enter) type in 56&#8211;75.

Then save the settings... and restart X with ctrl+alt+backspace. I pulled those numbers off of a similar monitor, it was a 20" LCD with the same resolution, so if yours is a different size this may not work. And if it doesnt work reply back, with the size of the monitor, and we can try to figure somehting else out.

edit: other numbers I've found

HorizSync 30-83
VertRefresh 56-76

HorizSync 30.0 - 95.0
VertRefresh 50.0 - 85.0

Horizsynch 27-96            #Try this one last, I have a feeling the refresh rate on this one may be a bit high.
Vertrefresh 50-160        #

---

### Post by BobLand on 2007-04-09
Here's more info:
Chip: GeForce4MX440 with AGP8X
DAC: Integrated RAMDAC
MEM: 64MB
BIOS: 4.18.20.07.00

Monitor
Viewsonic P815
Driver (in windows) Microsoft
Refresh Frequency: 60 Hz

Pentium 4
1 GB Memory

Boot Drive: Maxtor 185 GB dual booted W2K/Ubuntu fiesty

xorg.conf has 1600x1200 added to screen.  Nothing else.  Making small changes kills X.
Tried changing the driver to nv, nvidia, glx and a few others that escape me.  None worked.
Tried sudo dpkg-reconfigure -phigh xserver-xorg.  Selected 1600x1200.  Rebooted.  Nothing.

The other things I tried I found in various forums such as nvidia and fiesty.  I didn't keep track because I didn't think I'd end up at a dead end. 

After looking at a 1600x1200 screen for all of these years, a 1024x7xx feels claustrophobic.

Ubuntu recognizes my card exactly.  Why can't it just supply the correct driver and be done with it?  

PS - I'm writing this in W2K.

bobland

---

### Post by slimdog360 on 2007-04-09
okay, so that model number of the monitor is a little different. So its a crt after all. 

DId you try my way at all? Whether you have or haven't give it one more go, so thats,
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
do all the stuff at the start, using the 'nv' driver, then when selecting your monitor choose the Advanced option, choose your resolution, then for the numbers that I talked about last time, use these new numbers.

HorizSync       30.0 - 115.0
VertRefresh     50.0 - 160.0

save it and start the graphical stuff with the 'startx' command (minus the parenthesis)

if it doesn't work this time, Id be surprised but just in case, redo that but get the crappier resolution by using the simple option. Then once you get to a desktop open a terminal and type in ```
cat /etc/X11/xorg.conf
```
and post the output of that here.

---

### Post by BobLand on 2007-04-10
This is a test post.  After writing the results of my findings VBulletin would not let me post.  It logs me out.  I log in then it logs me out.  More frustration.  Closer to pulling the trigger.

I'll try again if this posts.

bobland

---

### Post by BobLand on 2007-04-10
Here's the problem: "The text that you have entered is too long (54137 characters). Please shorten it to 40000 characters long."

So, how do I bring the conf and log across?

---

### Post by Big Dave on 2007-04-10
After you've done:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and then selected all the resolutions up to 1600x1200, try doing:

```
sudo xrandr -s 1600x1200
```

I've not tried that on Ubuntu, but it works on Debian Etch, so your milage may vary.

---

### Post by BobLand on 2007-04-10
Dave,
I ran thru a few of the selections offered by dpkg.  When I ran xrandr I got the message on all that said 1600x1200 is not supported.  This is confirmed in the X11 log.  In xconf,
I've tried nv, nvidia, and VESA.

In the log file I get "Not using mode "1600x1200" (no mode of this name)" for all driver names as above.

So if the above drivers do not support this mode, is there one that does?

Thanks,
bobland

---

### Post by Norfolk 'n' Good on 2007-04-10
I hope this may help.

I also have a Viewsonic (VA1912w) and like you I also had difficulty setting the proper resolution.  Anyway, the solution was to do a google search for the model number and find the specs for the horizontal and vertical syncs (mine were 30-83 and 50-85 respectively).  Once you have these, open your terminal and type...

```

sudo gedit /etc/X11/xorg.conf

```

Somewhere in there you will see vertical and horizontal syncs already listed.  If they're not the same as those you have found for your model, change accordingly.  Next scroll down a little further an look fore the different screen resolutions... I'm not at my PC, but it should look something like...

> 
24
"1440x800" "800x600" "5x5"


Find the resolutions under the 24 heading, or a higher setting if yours has it, and change the first set of numbers in the quotes to the resolution "1600x1200"... your resolution.

Save this change and restart your computer.  Hopefully, you will be pleased with the result.

---

### Post by BobLand on 2007-04-10
Found the correct refresh rates.  Added them in.  Rebooted.  No difference.

I tried to run the latest nvidia drivers but ran into this problem which may be indicative of the problem.

When I ran the driver I got an error saying I have to stop X.  If I run /etc/init.d/gdm stop I'm thrown into the command line with a blinking cursor that does nothing - no prompt.

The last line before the blinker is "running local boot scripts (etc/rc.local)."  I've waited for a while but it never changes.  I have to reboot to recover.

On another note, once I fix xorg.conf in command mode, how do I return to the graphical interface?  If I run /etc/init.d/gdm start, the screen says it is started but I'm still in command mode.  How do I return or do I have to reboot?

Thanks,
bobland

---

### Post by jhenager on 2007-04-10
> **BobLand said:**
> Here's the problem: "The text that you have entered is too long (54137 characters). Please shorten it to 40000 characters long."

So, how do I bring the conf and log across?

Save them both as files and attach them to your next post.

---

### Post by locke.dragon on 2007-04-10
it may not help, but i fixed my resolution woes by installing 915resolution through symantec package manager.  have you tried this?

---

### Post by BobLand on 2007-04-10
locke,
can you be more specific?

---

### Post by locke.dragon on 2007-04-10
just go to System>>Administration>>Symantec Package Manager (that's what you do in edgy eft).  and punch in "915resolution" in the search bar.  install it and restart x using control+alt+backspace and you should be all set.  if not, then just un-install 915resolution.

---

### Post by BobLand on 2007-04-10
I'm trying to install the latest driver.  The process asks me to stop the x server.  When I use sudo /etc/init.d/gdm stop I'm dumped into the command processor with a blinking cursor and no prompt.  Since I can't get past this point I can't install the driver.  Since I can't install the driver then Ubunto is NoBuntu and it's good bye.

Perhaps, when zany zebra comes out I'll try again.

---

### Post by locke.dragon on 2007-04-10
please don't quit ubuntu on my account.  :(  it took me nearly a week to fix my resolution problem.  if you don't have the right hardware, then 915resolution won't work.  that's all.  just wait, someone will post something you can use.

---

### Post by BobLand on 2007-04-10
I'm still wondering if the problem I'm having stopping the x server is indicative of something evil.

I recall in the many threads I've browsed that someone said to use a different method of stopping the x server.  Unfortunately, the search function does not search strings, just the first word it finds.

So, until I can at least install the latest driver I'm dead in the water.

---

### Post by josephus on 2007-04-11
Hi Bobland,

I just finished your other post about leaving Ubuntu.  I'm not trying to convince you to stay, but if you ever wanted to try to get 1600x1200 you might want to try to install nvidia drivers. I know that you tried to install the latest nvidia drivers, but if you read through the documentation, you'll find that the latest version does not support your card.  You'll have to use one of the older version

[http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html)

also you might want to post your full xorg.conf, it might help people figure out what's wrong.

---

### Post by igknighted on 2007-04-11
> **BobLand said:**
> Found the correct refresh rates.  Added them in.  Rebooted.  No difference.

I tried to run the latest nvidia drivers but ran into this problem which may be indicative of the problem.

When I ran the driver I got an error saying I have to stop X.  If I run /etc/init.d/gdm stop I'm thrown into the command line with a blinking cursor that does nothing - no prompt.

The last line before the blinker is "running local boot scripts (etc/rc.local)."  I've waited for a while but it never changes.  I have to reboot to recover.

On another note, once I fix xorg.conf in command mode, how do I return to the graphical interface?  If I run /etc/init.d/gdm start, the screen says it is started but I'm still in command mode.  How do I return or do I have to reboot?

Thanks,
bobland

If you hit enter at that point the prompt should come right up.  Forget the driver from the nvidia site though and either install nvidia-glx through synaptic or just get the program "Envy".  It automates the install of nvidia and ATI graphics drivers.

The drivers from nvidia and ATI are not designed to fit into the linux philosophy, and the open source alternatives are not well supported because these companies don't release good specs for their cards.  Please let nvidia know of your frustration, because the ball is in their court to fix this.

---

### Post by scottdizzle on 2007-04-16
Hey! I found the solution to this. I was having the same problem.

I finally got 1600x1200 res by reading this:

[http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/](http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/)

Then after I installed.. it tried to update my xorg.conf file for me but messed it up instead. Hopefully that doesn't happen to you. All I had to do to fix it was go in xorg.conf and add "1600x1200" to my color depth selection in the list. When I got back into XWindow/Gnome/Ubuntu.. I went to Screen Resolution and I had a new option to allow me to select 1600x1200 and it not only works!... it works and scrolls smoothly and everything!

Took forever to find out how to do that.

---

