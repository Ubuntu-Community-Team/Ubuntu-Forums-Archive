---
title: "Installing X (GUI)"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by svk on 2006-08-20
Hello!

Today, I finally managed to install Ubuntu Linux. Installation did not go pristine, however. The GUI failed to load, and I was stuck at a terminal screen. I googled about the problem, and found [this]("http://www.linuxforums.org/forum/debian-linux-help/41622-new-linux-ubuntu-install-gui-problem.html"). Specifically, I decided to follow the advice in [this post]("http://www.linuxforums.org/forum/237760-post18.html"), about installing X.

I went through the prompts in the terminal (by which I mean the environment that is not quite a pure ASCII console, but not quite a GUI system that I'm used to in Windows World), one after another. There was one where I had to enter the preferred video color depth. I made a selection and pressed 'Enter'.

However, out from the bottom of the screen popped up the console that warned me that I was deviating from the default option. Unfortunately, regardless of whether I wanted to confirm or deny, I could do neither! My first reaction was panic: uh-oh, how do I change focus away from the console and back to the terminal. I don't remember the sequence of keys that I pressed. I must have tried 'Y', and 'y', and 'ok', and 'accept', and 'confirm'. Next, I tried pressing any of the arrow keys and TAB in an attempt to drive the focus back to the terminal.

Basically, the more commands I entered (valid or not), the larger the console window became, and the further up the terminal went, until it finally disappeared out of view. I searched for basic maneuvering around the console, but I was not able to get myself out. I did find out how to scroll, but apparently, there was not enough buffer space to get myself all the way up (but even then, I wouldn't know how to change focus).

So I presume the installation is still running in the background. I have the gloomy command prompt in front of me, at which I am current staring, stupefied.

How do I get back to the installation? What is the "standard procedure" for these sorts of confirmations or warnings, should they ever occur again? How do I change focus?

Please help!

---

### Post by The Noble on 2006-08-21
You said you Installed Ubuntu from the CD, right? That means EVERYTHING you need to get a gui has been installed. X would have been installed already. Gnome/KDE/Xfce would have been installed. Everything would be configured. I am going to take a wild guess and say you got a crazy "X windows can not start"(on boot), with a bunch of question marks around the edge of the box. Is that it? If it is, it is quite easy to fix unless you have a really wacked system.

---

### Post by David Corrales on 2006-08-21
I'd reboot and do a text mode install. It's the best way if you're having problems with X initially.

---

### Post by svk on 2006-08-21
EDIT: To the previous poster (who replied while I was typing my post): I did do a text-mode install. I was recommended against the normal method since my RAM is small [64 MB]. But shouldn't the text-mode installation install the GUI operating system?

Well, I don't remember whether or not I had a warning message about X.

In fact, it just struck me that after booting into Ubuntu for the first time, there was no further installation. If I remember correctly, there had to be at least another half-hour's worth of package extracting, but I got nothing of the sort. It took me straight to the console, and I had a text-based operating system since.

What could be the cause?

Now, my system is indeed quite archaic. It is a Pentium-II 333 MHz machine with 64 MB of RAM a 5 GB hard drive. It previously had Windows 98 installed, and I'm dual booting now.

The installation, like I said, did not go perfectly: the first time around, I had a corrupted disk. The installation got around to 60% and then just bailed out. For a while, I was presented with the freakiest message ever when I booted: "Missing operating system". I nearly peed my pants. Of course, booting from CD still worked.

The second time around, I did NOT get any warnings about overwriting any of the previous files left over from the last installation attempt. However, since my hard drive was partitioned (automatically), the second time around, I had to play around with the previous partitions so as not to create even more of them. I decided to customize the partitions a bit by creating a /home partition. Also, since my RAM is abonimably horrid, I gave the swap partition some extra memory.

But the main peculiarity about my installation is that booting into Ubuntu for the very first time was fast -- too fast. I was immediately presented with the command prompt. Sorry, I didn't take note of any error messages (and I didn't yet know how to scroll up and down the console window -- speaking of which, is there a better way than using Shift+Page Up/down?). There was no further installation, and the GUI did not start.

So, in summary, I'm suspecting that it's either because of the age of my system (poor specs), or the anomalies in the installation (including aborting the first time around, and the immediate appearance of the command prompt instead of further installation after booting for the first time).

Ideas?

---

### Post by The Noble on 2006-08-21
Gah! Your system is quite old. Hopefully you are doing a Xubuntu install, as gnome would be EXTREMELY slow with 64 meg of ram. What you are saying is a little confusing, but what I am getting is that you used the Alternate disc for the install. You installed, but it hung at 60%. You rebooted and it said "No operating System Installed". Not that freaky really, it is just that some things were not installed. Impossible to tell what. Sounds like maybe a faulty disc or something. Anyways, you tried to reinstall and there were partitioning errors, but it worked. You rebooted and there was only the CLI. Weird, X should have given an error.

My recommendation is to use the disc check option when you boot from the CD. If all is smooth, Reinstall Ubuntu after formatting the drive. If Ubuntu is not seeing that there is stuff on the drive, use Windows and clear it.

I tried Installing Xubuntu on my old PI 166 Mghz (128 meg ram, 2 meg graphics card), and it did not work very well(read: at all). I would say you should install a Puppy Linux flavor, or damn small linux. By all means, still use these forums (as well as theirs), but just note that Xubuntu will be pretty slow.

---

### Post by svk on 2006-08-21
Sorry for the late response, I had to go to sleep!

Thanks for the suggestion, perhaps a less memory-intensive distribution would work better. I would at least like to get Ubuntu up and running before I switch, though. I was recommended Ubuntu because it is very beginner-friendly. And this *is* my first Linux distribution.

Anyways, after even more searching, I found yet more potential solutions. One of them involved reconfiguring xserver, and another reconfiguring gdm (from searching, looks like Gnome Display Manager). I followed the directions

After doing all of this, it looks like XServer makes an attempt to start, which is almost reassuring. However, my monitor blinks on and off during reboot, and I get an error message that it failed to start the X Server. It allows me to view the X Server output to try to diagnose the problem, but I'm not sure how I can copy and paste it here.

If I use startx from the command prompt, I get a bunch of error messages about fonts, and that it can't find the default font 'fixed'.

If I try to use dpkg-reconfigure gdm, the same thing happens as during reboot: the screen again blinks on and off several times, and then X Server complains that it is not set up correctly.

When I used dpkg-reconfigure xserver-xorg, I tried using all of these as my video driver: ATI (which is what my card actually is), vesa (which I found out from searching is very compatible with everything), and vga (which I found out from searching is the failsafe, absolute bare-minimum, ultra-compatible option). In the case of VGA, I also had to select 8-bit color. The other options don't work.

In the end, I get all the same problems. The screen blinks several times, X complains about fonts, and it doesn't start.

Sorry if I'm being a bit vague again. I blindly followed online directions without really knowing what I was doing, and I'm simply logging what I did here.

---

### Post by nalmeth on 2006-08-21
My advice:
Download the xubuntu alternate CD from this page,
[http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/](http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/)

Check the CD for errors, the checksums are available on the page, just scroll down.

Format the existing UBUNTU installation, and install XUBUNTU in that space. Xubuntu IS ubuntu, just with the lighter XFCE desktop environment. Gnome will be frustratingly slow (UBUNTU's desktop environment) on 64 megs of RAM.

You seem patiently persistent, which is great for this type of situation. However, from all that you seem to have done, I think it would be quite difficult to track down just what is exactly causing the issue at hand, with your current ubuntu installation..

If you don't want Xubuntu, then you should reinstall Ubuntu, and take a fresh start. Post the procedures you're following in a thread, and use the Community, as you have been already. We're here to help :)

Oh yeah, you may want to pick up some more RAM someday :-k

---

### Post by svk on 2006-09-03
Hello again!

It's been a while, but I have some good news: it works! I'm actually typing this from Ubuntu right now, GUI, eye candy, and all!

And the solution? I got more RAM! I did *nothing* else. I tweaked no further settings. Just more RAM (160 MB now), and that's all it took to get Gnome and X Server up and running. I hesitated at first since I'm the type of person who's scared to open up the case of my computer. But it wasn't too bad. I just had to find the manual for my specific computer model online, and they have step-by-step instructions for installing RAM. And furthermore, RAM is dirt-cheap! I got 128 MB for $30 from a specialized retailer (a retailer that sells RAM that is guaranteed to be compatible with my system).

Well, that was *almost* all it took. Just after getting more RAM, nothing happened, so I started from scratch. I reinstalled Ubuntu from the CD Rom again. I followed the same exact steps as last time, except I formatted the old partitions instead of creating new ones again.

So the above could be added to the community's wealth of knowledge for similar cases in the future. Just getting more RAM could get Gnome up and running in some cases.

EDIT: Also, in the meantime, I tried out Puppy Linux. But something freaky happened: the installation did not ask me to select a single option! It just installed and ran! The reason that this worries me is that I don't know *where* it installed to. To the best of my knowledge, it simply went ahead and overwrote my Windows partition, because, well, Windows doesn't boot anymore. Did I do something wrong? Was I supposed to set up a partition before the installation? Or is that not the reason that Windows no longer boots? Did Puppy set up a partition automatically?

I didn't lose anything important, but I would like to prevent this in the future if I want to try a different distribution. What went wrong, and how can I prevent it?

---

### Post by confused57 on 2006-09-04
Since you can boot into Ubuntu, open a terminal, enter:
```
sudo fdisk -l
```
The -l is a small "L"

I installed Puppy a couple of weeks ago, before installing I made a 2 Gb ext2 partition using the gparted live cd...I chose to install grub to the root partition that Puppy was installed on(hda7)...then I added the following entry to grub on the mbr:

title          Puppy
rootnoverify   (hd0,6)
chainloader +1

Many Linux distro's installers are quite capable of partitioning & resizing, but it's probably better to set up your partitions beforehand using the gparted live cd:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

After setting up partitions using gparted, make note of what the partitions are(hda1, hda2, hda3, etc)...so you'll install on the correct partitions.
Here's some screenshots using gparted live cd, navigate throughout the website to see other examples:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

