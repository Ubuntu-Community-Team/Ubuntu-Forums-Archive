---
title: "Strange lines, keyboard not working..."
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by uflieven on 2007-10-19
Hello, anyone who has Xubuntu 7.10 working?

I downloaded it twice, yesterday with bittorrent, today without, and on one pc (rather old) the installation fails after the Xubuntu logo with progressbar have disappeared. Instead I get some funny lines across the screen. When using safe graphics mode, I managed to get it installed (though very slow) but the problem persisted after installation. CD-Rom integrity was tested also and (yesterday) it reported no problems.

On another pc (rather new) I can't even get the USB keyboard working, that is when the first screen with install options comes up, a few seconds after booting.

Anyone with the same problems, who is also using Xubuntu?

If needed, I'm going to have a look if i can still access yesterday's installation (can be a problem) to add some files when asked for.

Thanks in advance for your help.

---

### Post by liamwithers on 2007-10-19
Those funny lines may be the screen resolution as it was with me. Go to System --> Preferences --> Screen Resolution, and try all the different ones.

Hope this helps, Liam

---

### Post by uflieven on 2007-10-19
Thanks for your reply, Liam.

I was just rebooting to check that out, when I realized that yesterday, it wasn't even possible to change the screen resolution. The only thing I got was a gray screen with black dots instead of the usual blue desktop background. It was on 1024x768, but because a have a small CRT screen and text was a bit too small, I wanted to change to 800x600. But that wasn't possible.

---

### Post by molly_001 on 2007-10-19
uflieven,

Have you managed to get a display readable?  Please let us know, there is more help available!

Thanks.

---

### Post by uflieven on 2007-10-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/154592](https://bugs.launchpad.net/ubuntu/+bug/154592) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Yes, it eventually gets readable. Right now I'm posting from Firefox inside gutsy.
But when I start four in a row, i have also problems.
When it's the computer's turn, it quits the application or hangs.

---

### Post by uflieven on 2007-10-20
I guess the MD5SUM may not be correct, instead of one sum, I get about 30, almost one for each directory on the CD. But then again, most of you have it running since the day it came out. I downloaded once on the 18th, and once 30 hours later. And still, the same problem. How I am gonna know if I download again, it's gonna work?

---

### Post by Linux_Man on 2007-10-20
Seems much like RAM corruption, Memtest the RAM, leave it on for a few hours and see if theres any errors that would explain the slowness, corruption of the screen etc.

---

### Post by uflieven on 2007-10-20
Thanks for your answer, linux_man

I'm now running memtest for about ten minutes, will leave it on for a few hours, but I doubt there will be a problem since I can use Windows XP without problems.

You were right, linux_man: now that it's running a bit longer I already have 30 errors.

What can I do to fix it?

---

### Post by uflieven on 2007-10-20
Now already 80 errors. They seem to occur each pass in test #5.

---

### Post by molly_001 on 2007-10-20
Great call by linux man.

uflieven,
If you are getting MemTest errors, then you need to determine whether the corruption is in:
(a)  an individual RAM stick
(b)  more than one RAM stick
(c)  your motherboard's memory controller

The easiest way to do this these days (with new RAM being super super cheap) is just to replace all RAM sticks.  Or, upgrade your amount of RAM, with new sticks.
Take out the old sticks completely.

Then run MemTest again.

---

### Post by uflieven on 2007-10-20
The ram sticks can be tested, but if it's my motherboard memory controller...
Well, tomorrow I will first test the RAM, and see which modules cause the problem, by swapping them in and out and testing with memtest.

Otherwise, I think it's gonna be a new pc, the one im using now is fairly old and RAM for it won't come as cheap as ram that's used in todays computers.

But I still don't know how this could happen. All worked fine until I put in the Xubuntu CD. Hope that's not the problem...

---

### Post by uflieven on 2007-10-20
The ram sticks can be tested, but if it's my motherboard memory controller...
Well, tomorrow I will first test the RAM, and see which modules cause the problem, by swapping them in and out and testing with memtest.

Otherwise, I think it's gonna be a new pc, the one im using now is fairly old and RAM for it won't come as cheap as ram that's used in todays computers.

But I still don't know how this could happen. All worked fine until I put in the Xubuntu CD. Hope that's not the problem...:(

---

### Post by molly_001 on 2007-10-21
Let us know how the RAM testing goes.
Having inserted various linux LiveCDs into about 100 computers, I can't imagine how it could be responsible for corrupted RAM.  One thing I would do for sure tomorrow is to make sure you are using a MemTest bootable CD (in other words, don't use the MemTest on any other LiveCD such as Xubuntu LiveCD.)
 
And burn the MemTest bootable CD on a different computer.

---

### Post by uflieven on 2007-10-21
Before the RAM-test, I wanted to know if the problem persists with Debian (had burned a debian CD about 1 month ago)

And guess what...

No problem whatsoever!!!

No strange lines, it just boots and works. So maybe it's my mainboard that's not supported. It's an old one, so I won't be surprised.

The only thing that bothers me is, why do I have problems now?

With Edgy and Feisty it worked fine.

---

### Post by uflieven on 2007-10-21
The strange thing is...

Running memtest under Debian... and more errors than yesterday with Xubuntu.
Still, my system is running fine...

---

### Post by molly_001 on 2007-10-21
Until you are willing to burn MemTest (just the program MemTest) onto a new blank CD and on a different machine and a different burner, you won't be able to isolate any problem regarding RAM.  Please understand that to get *any errors at all* on MemTest is very rare and almost always points to a problem which will continue to plague you in any operating system.

You can get the standalone .iso of MemTest [here]("http://www.memtest.org/#downiso"). 

So that's: (1) MemTest burn only; (2) burned not on your current computer; (3) burned not on your current optical drive.

If other Debian Linux distributions have worked for you in the past, especially Edgy or Feisty, then the current problem is (in addition to the possible bad RAM issue) one of configuration of the X server.  This can be fixed with sudo dpkg-reconfigure xserver-xorg after waiting a couple of minutes after your are sure the OS has loaded.

I've had the same situation with any version of *buntu on many machines, wherein slight changes they make (in the different versions) to the default Xserver configuration, will make a "later" release appear to not work whereas an earlier release did work.

---

### Post by uflieven on 2007-10-21
Ok, I replaced the RAM, burned memtest only on a CD-RW, on another computer (which has of course, another optical drive).

I'm running memtest now for about 45 minutes without errors, which is longer then when the first errors appeared before swapping the memory. I'll continue to run it until tomorrow morning. If there are still no errors, you would think everything will be fine, but I doubt it.

Why?

Because I tested the Xubuntu CD right after swapping memory, and same problem.
So, if tomorrow, memtest still reports no errors, I'm going to download the alternate install CD.
If that doesn't work either, I'm saying goodbye to Ubuntu for 6 months :(, and will use Debian instead.

---

### Post by molly_001 on 2007-10-21
> **uflieven said:**
> uflieven wrote . . . 

I replaced the RAM, burned memtest only on a CD-RW, on another computer (which has of course, another optical drive) ... I'm running memtest now for about 45 minutes without errors, which is longer then when the first errors appeared before swapping the memory.



Well, by swapping out the old memory with new memory modules, which is what I think you are saying that you did, you will have excluded the opportunity to check those older RAM modules for errors.   But it's all good if the current RAM test runs with no errors.  Later, you could do the same process to test those older RAM modules, too.

> **uflieven said:**
> uflieven wrote . . . 

... I tested the Xubuntu CD right after swapping memory, and same problem.



This is because, in all likelihood, the problems you see running the LiveCD are with the X server, and not with your hardware, or even with comptability issues. 

Keep in mind that you need to do a clean, blank CD burn on that *other* machine of [either]  Xubuntu Alternate Install [or] the LiveCD, with a new burn on that other machine.  I am not convinced that your CD drive in the troubled machine is burning correctly.  
 
> **uflieven said:**
> uflieven wrote . . . 

So, if tomorrow, memtest still reports no errors, I'm going to download the alternate install CD.
If that doesn't work either, I'm saying goodbye to Ubuntu for 6 months :(, and will use Debian instead.



I suspect your MemTest will run during the night without errors.  At that point, you need to download and burn (again) the LiveCD, or, the Alternate Install CD, on that *other* machine.  This will eliminate a "bad burn" potential issue on the troubled machine's optical drive.  [It may be wise to start the downloading tonight on that other machine, if you can.]

Even after an install with the Alternate Install CD, you are likely to still have the graphic problems immediately at the start of the X server.  I've installed various releases of *buntu on machines as old as 11 years and as new as those from this year.  It may seem illogical, but the X server is where the problem is 99% of the time.  The trick is to find the correct X server settings for your adapter so that you get rid of video corruption (or get a screen, at all).  I would say xorg needs to be manually configured on at least two-thirds of the machines I have worked with older than 4 or 5 years of age.

---

### Post by uflieven on 2007-10-22
I have run memtest for about 12 hours, and still no problems.
Then I've burned the alternate install CD on that *other* computer.
Now I'm gonna try if I have some luck with it.

---

### Post by uflieven on 2007-10-22
Busy installing...
The installer sometimes progresses very slow (like hanging for 10 minutes, then continues)

---

### Post by molly_001 on 2007-10-22
The appearance of hanging using the Alternate Install is observed by me also, especially on older machines.  I think they should update the code on the "bar graph" progress so that it doesn't give this appearance.

Mine generally hangs at 6% and again at 40%.

---

### Post by uflieven on 2007-10-22
Finished installing.
Now booting...

---

### Post by uflieven on 2007-10-22
Seems it's a little better then first, no more lines and circles on the screen. :)
Still, the startup is not very smooth (First I get 2 lines (which I also get with other disto's), then I get the startup screen with the progress bar, and before it's fully filled, I get another 20 lines of text.
Then I again get the startup screen with progress bar, but placed to high on the screen (I guess the Xubuntu logo falls off), and a bit later it's showing the login screen. Ok, I can live with that, but it's still not very good.

Worse :(, Four-in-a-row still hangs when it's the computer's move. And, in the above mentioned 20 lines of text, I still get the error: FATAL, error inserting battery (/lib/modules/..../battery.ko) (see bug report).

I'll play around a bit with gutsy and see if I get any more errors.

---

### Post by molly_001 on 2007-10-22
> **uflieven said:**
> uflieven wrote . . .

 the startup is not very smooth ... screen with the progress bar, and before it's fully filled, I get another 20 lines of text. ... 



The above is standard for the boot and loading process until it loads the X server to fit the screen to correct resolutions.  Also, to receive an error line during boot is not abnormal at all.  Ubuntu does its best to load various modules and if it cannot, you will receive an error.   I don't know why some are called "fatal" errors if in fact the OS loads...

You can change the boot loading screen to suit your needs.  This is via 

```
gksu gedit /boot/grub/menu.lst

```

I generally remove the " -quiet " tag
for the Ubuntu loading line, so that I receive an all-text load.  Every step is reported that way.  Not that I am fast enough to be able to read each line as it appears ...

---

### Post by uflieven on 2007-10-22
I'll make a backup of my menu.lst and will then try to remove the -quiet option.

Changing screen resolution is still not possible (it's fine now, but in case I need it changed, it won't do it)

Thanks for your help so far, molly_001 :)

---

### Post by molly_001 on 2007-10-22
You're welcome to the help.
Just so you know, the inability to change resolution is due to the X server configuration.  I'll explain how to fix this, but first I need to know whether you know that your monitor can indeed support at least 1024x768 resolution, or, perhaps even 1280x1024.

Let me know.

Personally, I really enjoy Ubuntu at 1280x1024.

---

### Post by uflieven on 2007-10-22
It supports 1024x768, but not 1280x1024, I'm afraid.

Is there a way I can configure the sound?

---

### Post by martinrandau on 2007-10-22
.

---

### Post by molly_001 on 2007-10-22
I am assuming you are at 800x600 res right now for the below.

So, you can configure your adapter to use 1024x768, and then when you make the changes to res in gnome (your graphical environment) it will actually work.

Right now, your X server is configured to make 1024x768.  Your adapter is not, however.

To fix: First back up xorg file as it is currently.
Start the terminal, then type:

[SIZE=-1]**sudo cp** /**etc/X11**/name-of-file-to-use /**etc/X11**/xorg.conf.backup

So, an example:
Let's call that backup file "xorg.uflieven.backup"

You would type in terminal (note the capital 'X' is important in Linux):

[/SIZE]```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.uflieven.backup


```When you have done this, please let me know.  
Regarding sound, you will need to know the name of your sound card adapter to have any success.  

Thanks.

---

### Post by uflieven on 2007-10-22
Sorry, but I think the 'code' in your post should be reversed.
I tried like you said, but Xubuntu reported: no such file or directory.
So I did:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

and that went better.

Regarding sound: can't I find the name of my sound card adapter somewhere in Xubuntu, using a command, for example?

---

### Post by molly_001 on 2007-10-22
Thanks for the code correction in the above post.  I edited my original mistake now.

To learn your sound device, try the following, and please type back all that you see after typing in the following command:

Warning:  It may not work at all, but give it a shot anyway.

```

cat /proc/asound/card0/codec#* | grep Codec
```

---

### Post by uflieven on 2007-10-22
Sorry, but I have no asound directory under the directory proc...

---

### Post by molly_001 on 2007-10-22
OK, I figured as much.  Do the following:

```
sudo apt-get install alsa-oss
```

Then, use the cp command we wrote about earlier, to make a backup of the ALSA sound configuration file:

```


sudo cp /etc/asound.conf /etc/X11/asound.uflieven.backup
```

Now follow the guide below, which is coped from [here]("http://tinyurl.com/2jjstg") (very very near the bottom of that page).  It is best to use that page instead of what I have pasted below.


 [PHP]How to configure sound to work properly in GNOME

    * Read #General Notes
    * Read #How to add extra repositories 

sudo killall esd
sudo cp /etc/esound/esd.conf /etc/esound/esd.conf_backup
gksudo gedit /etc/esound/esd.conf

    * Find this section 

...
auto_spawn=0
spawn_options=-terminate -nobeeps -as 5
...

    * Replace with the following lines 

auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default

    * Save the edited file 

sudo apt-get install libesd-alsa0
gksudo gedit /etc/asound.conf

    * Insert the following lines into the new file 

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

    * Save the edited file 

sudo ln -fs /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

System -> Preferences -> Sound
Sound preferences

General Tab -> Sounds for events (Un-Checked)

    * Save and close all opened applications, Reboot computer [/PHP]

---

