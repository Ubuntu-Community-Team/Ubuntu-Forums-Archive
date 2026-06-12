---
title: "Unknown issue running (K)Ubuntu on AMD 64 5000+ system"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by MachineHead on 2007-04-08
Hello everyone,

Since i'm quite new to the world of Kubuntu I have no idea how to solve this.
I downloaded several versions/ distro's of the AMD 64 Kubuntu versions:
[I]- Kubuntu 6.06.1 Alternate AMD 64
- Kubuntu 6.06.1 Desktop AMD 64
- Kubuntu 6.10 DVD AMD 64[/I]
Untill this time I cannot get one of them to proper boot.

**Actions taken:**
- Reboot pc and insert Live-cd/DVD
- Arrive at Kubuntu splash screen.
- [Enter] at the Run or install Kubuntu option.
- Program starts loading (Cd and HDD activity)
- Program loads 100%

And there it is, here everything stops.
No Cd or HDD activity.
I used a Kubuntu Live-cd before on my old system, on wich it worked fine.
Now i can't even get into Kubuntu to install.
At this moment I'll try the alternate cd to boot.
So I will edit this post in a few minutes to report on that.

**System:**
AMD 64 5000+
2048 Corsair single channel 800 Mhz RAM
MSI K9 SLi Platinum mainboard (MCP55)
2x XFX Geforce 7800 GT 256 DDR2
X-Fi Creative Fatality24 bit sound card
80 GB Sata II HDD 8 mb cache                                     [Windows file system]
160 GB Sata II HDD 8 mb cache                                   [Reserved for Kubuntu file system]
250 GB Sata II HDD 16 mb cache                                 [Data storage, games, movies, files etc]

__________________________________________________________________________
For two hours I have been working on the alternate install of Kubuntu.
It installed fine and all to the 160 GB HDD.
After rebooting and trying to boot to Kubuntu trough GRUB it showed the splash and loading of components.
After that it just sits there with a not-blinking cursor in the upper left corner of the screen doing nothing.
I removed the partition trough windows, note that the 160 GB HDD had no pratitioning at all.
Now I will burn *Ubuntu 6.10 desktop AMD 64* and see or this one will work.

Please anyone help me out, I so want to get rid of windows asap!

Sincerely,

MachineHead

---

### Post by rai4shu2 on 2007-04-08
Try turning off USB 2 if you can in the BIOS. That's how I used to get Dapper and Edgy to work on my MSI K9N.

The later kernels (2.6.18 and newer) seem to have fixed that issue for me.

---

### Post by MachineHead on 2007-04-08
Thanks for your reply.

Could u help me clear up one thing regarding to this problem.
- I did install Kubuntu
- GRUB loads up the Linux kernel etc.
- I get the splash and loading of components.
- After that black screen with zursor in left upper corner of the screen.

Is this the same issue you encountered ?
And if so, after turning off USB 2.0 and entering (K)Ubuntu you download the newer kernel from the repositories wich do support USB 2.0 ?

Please specify for me.
And thanks loads for your comment, you're the first out of three forums.

Regards,
MachineHead

---

### Post by rai4shu2 on 2007-04-08
In my case, the hardware would freeze up at the splash screen or some random time after that (or possibly not freeze at all), but it could be related.

You could download a new kernel, but it may be easier to use some other distro. Fedora Core 6, for example has 2.6.19 right now. Sabayon has 2.6.20 (and they're getting ready to crank out a release with 2.6.21rc).

---

### Post by MachineHead on 2007-04-08
Thanks again,

Well I really just want Kubuntu or Ubuntu.
I have a Live-Cd running on a 32 bit system at the moment.
I'll test it on this pc in a moment (got 3 systems)

My main pc is reinstalling Windows atm, that is the system on wich I'm encountering this problem.

Can it just be 64 bit support?
Cause I can't find any info elsewhere about Linuc cracking up on other systems.

Regards,

MachineHead

---

### Post by rai4shu2 on 2007-04-08
If it's the same problem with the USB controller, then it's not a 32/64-bit issue. It's just that older kernels didn't support that particular controller properly in USB 2 mode.

---

### Post by calraith on 2007-04-08
I'm on a Gigabyte socket AM2 SLI board.  I cannot boot with APIC enabled due to a buggy BIOS, according to the kernel panic messages.  I have to append "noapic" to the kernel string in grub before my machine will boot.  Maybe the same thing is happening to you, except since Grub is configured by default for "splash quiet" you don't get to see the kernel panic.

I also cannot load X with the default driver "nv" for some reason.  Like you, I have two GeForce cards.  (Still having a bear of a time getting SLI enabled, but I'll save that whine for another time.)

So, here's what you do.  For now, we'll pretend the problem is a kernel panic.  Insert any of the Ubuntu CD's you've burned.  When the Ubuntu boot menu first appears, before you hit anything else, hit F6.  Backspace "quiet splash" out of the kernel boot line so you can watch the kernel panic.

If it fails trying to init APIC like mine does, power the machine off and back on, and hit F6 when you get back to the Ubuntu boot menu.  Somewhere in the line, simply add noapic and hit Enter to boot.  Successful?

If your machine is like mine, then it will have successfully progressed up until X tries to load, then your display will be unresponsive.  (Interestingly enough, I can hit Ctrl-Alt-F1, ignore that my display remains black, and Ctrl-Alt-Del to restart the system at this point.)  If this is the case, then you must use the "Alternate Install" CD and install via text interface.  Just like before, hit F6 at the Ubuntu boot menu and remove "quiet splash" (so you can see failures), and append "noapic" (if appropriate).

Install as normal, following all prompts until you get to the "Hit Enter to restart" or "Continue."  DON'T yet.  Hit Alt+F2 to get to a busybox session (or simply open a terminal window if you didn't have to use the Alternate Install CD).  Hit Enter to activate the console.  Type the following as root:

```
chroot /target /bin/bash
nano -w /boot/grub/menu.lst
```

There are a few sections to which you should pay some attention:

[LIST]
[*]Firstly, hit Ctrl-W and search for "defoptions."  Around line 89 you should see "# defoptions=quiet splash."  Add "noapic" if appropriate, and "vga=791" (or whatever vga= value you prefer).  Leave this line commented out!  Debian's "update-grub" script, which is run every time a new kernel or modules update is installed, uses this line to append default parameters to the kernel boot string.  We don't actually want grub itself to parse it, though.
[*]Next, just a few lines down, around line 106, you should see "# altoptions=(recovery mode) single."  Add "noapic" there if appropriate as well.  I'd recommend leaving off the vga= string there, since single user mode is supposed to be a failsafe boot option, as vanilla as possible.  As before, leave this line commented out.
[*]Thirdly, scroll down till you get to the meat of menu.lst, the actual boot options Grub uses.  You'll see "kernel  /boot/vmlinuz-2.6.etc..." for both regular boot and single user mode.  Append "noapic vga=791" to the regular mode, and just "noapic" to the single user.
[/LIST]

Ctrl-X Y to save menu.lst, then

```
grub-install /dev/sda
```

to apply the changes.  Next, assuming your machine is like mine and refuses to load X with driver "nv,"

```
nano -w /etc/X11/xorg.conf
```

Change the driver from nv to nvidia.  It doesn't matter that driver nvidia probably isn't installed yet.  At least this way, gdm or kdm will fail gracefully instead of freezing your console when you reboot.  Exit the chroot by typing "exit," and reboot.

When gdm / kdm tries to load X 3 times, it'll fail and disable itself, then put you at a console.  If you're on Dapper or Edgy, hop onto NVidia's website using links or lynx from the console:

```
# Dapper or Edgy:
sudo apt-get install links
links www.nvidia.com
```

and download and install NVidia's binary driver.  If you're on Feisty, 1.0-9755 is available from apt, and won't have to be reinstalled with every kernel update.  Simply do the following:

```
# Feisty only!
sudo apt-get update
sudo apt-get dist-upgrade -y
sudo apt-get install -y nvidia-glx nvidia-kernel-common
```

The dist-upgrade ensures you have the newest kernel compilation.  It's optional I reckon.  *shrug*

Let me know whether any of this was helpful.  Best of luck!

---

### Post by MachineHead on 2007-04-08
Hi there Calraith,

Thanks for that enormous entry mate.

I'll print that in a minute and try to work everything out.
See i'm a total console newbie, so it will take me some time.
A friend of mine who has been using Ubuntu/Kubuntu for ages reckons it's a hardware related issue aswell.

So I guess your in the right direction, I will try what u posted.

For the USB 2.0 solution, no result at all.
Still thankfull for you trying.

I will reply here the results on what Calraith said.

Greetings,

MachineHead

---

### Post by steevk on 2007-04-08
Give the 32 bit version a try...I know that on my AMD64 dual core 3800+ system, 64 bit Kubuntu didn't work well at all, but 32 bit works great...

Granted this was almost a year ago now that I think of it, so it's quite possible that that's changed.

---

### Post by calraith on 2007-04-08
> **MachineHead said:**
> I'll print that in a minute and try to work everything out.
See i'm a total console newbie, so it will take me some time.
A friend of mine who has been using Ubuntu/Kubuntu for ages reckons it's a hardware related issue aswell.

So I guess your in the right direction, I will try what u posted.

Yeah, no matter what the problem is, you can tell a great deal more simply by hitting F6 at the Ubuntu boot screen when booting from CD, and erasing "quiet splash."

---

### Post by MachineHead on 2007-04-10
Hi again,

Well your entry was sure helpfull Calraith.
I have Kubuntu 74 installed ok, and it's up and running.
The commands you said that I needed to execute didn't  go flawless though.

It was quite funny.
I entered the first command you mentionend and hit [Enter]
The result was disappointing, Linux went on about me not being Root and commands it didn't recognized.:lolflag: 

So I skipped all the other comments and started on [links]  and the nvidia driver download.
Well I installed [links]  in no-time, easy-peasy.
But finding and downloading the driver was a difficult task.
I managed to download the Nvidia graphics and GPU driver.

After that I tried installing them, went into euphoria on entering the text based installer of the drivers, and started crying again when it asked for [binutils] and later for [gcc], and I think I sustained brain-damage at the term *"Precompiled kernel <something>"*
Still have no exact idea what it means.
So I threw caution to the winds and reboot my pc, it still wouldn't boot any graphics.

But now after hitting ALT+F2 I saw that i was root@<pcname>, AWESOME!
Dunno how, dunno why but it worked.
I got binutils on my system, even managed to do something with gcc.
Edited the xorg.conf file with some effort and I reboot.

Then it suddenly worked, I got an Nvidia splash screen and after that Kubuntu login screen.
The time it took was up to  3,5 hours so I had enough of Konsole for a few days >.<

If there is any way that I can find out what I did to make it work, please tell me how.
So I can post those command scripts or print-outs I see in more topics here aswell.
Might be usefull for other AMD64 users.

Calraith thanks ! You brightened my day last sunday :popcorn: 

Regards,

MachineHead

---

### Post by calraith on 2007-04-10
Oh, yeah.  I left out that detail.  Before you can install the NVidia binaries you have to install build-essential, which includes gcc, etc.  Sorry about that.  :oops:

For future reference, "sudo" gives you root access for that one command -- such as "sudo apt-get update."  After apt-get update does its thing, completes, and drops you to the next shell prompt, you're regular user again.

In the diatribe I wrote above, wherever root access is required but I didn't include sudo in the command, that's because I was assuming that at that point you'd be using the Live CD, and using "chroot" to change root to your hard drive.  If you want more details about what chroot does, I'll explain a little further.  For now, I won't risk making you assimilate too much information in a short amount of time.

Glad you're up and running now!

---

### Post by MachineHead on 2007-04-11
Hi Calraith,

Hehe no prob. I got there eventually, but I have no idea wich commands I used.
If it isn't much work, would you be able to tell me how I can set my Kubuntu that I do not have to fill in my password everytime?
I know it's possible, cause my mate showed me once.
But he lives across the country, won't see him untill a few months.

I'm also interested in how to install the gcc and binutils properly.
Cause I remember getting things like "no such command" "unknown command or file name" etc.
I can't seem to be able and get the hang of browsing to a file in konsole screen.

is it : sudo cd /etc/<filename> for example?

Mmmm, I propably should be asking this in another thread?
Ah well, a od will pm me if so ^^

Regards,

MachineHead

---

### Post by calraith on 2007-04-11
> **MachineHead said:**
> If it isn't much work, would you be able to tell me how I can set my Kubuntu that I do not have to fill in my password everytime?

I'm also interested in how to install the gcc and binutils properly.

I can't seem to be able and get the hang of browsing to a file in konsole screen.
is it : sudo cd /etc/<filename> for example?

See the [Kubuntu Desktop Tricks]("https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/desktop-tips.html") page for instructions for setting up auto login.

To install the build utilities properly, go to [Add / Remove Programs]("https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/kde-app-install.html") and search for and install "build-essential."  Or in Konsole, type:
```
sudo apt-get install build-essential
```As a Windows user, I'm sure you have a basic familiarity with DOS commands.  You can draw some parallels to help you on the Linux console.
```
Windows          Linux          What it does
-------          -----          ------------
pwd              pwd            prints working directory
dir              ls             directory listing
cd               cd             change directory
md               md             make directory
rd               rd             remove directory
del              rm             remove a file
rd /s            rm -rf         recursively removes files and directories
dir | more       ls | more      directory listing, pausing when the console fills
```So you can see, navigating the Linux filesystem is not too different from navigating the Windows filesystem.  One major difference is that in Linux, "ls" provides color information.  For the most part, blue means directory, green means executable, and plain black or white means standard text file.  Strictly speaking, this has more to do with a filesystem object's permissions than its file type.  But most files and directories in the Linux filesystem adhere to these conventions.

You do not need sudo to navigate the filesystem.  Sudo is only useful for executing a single command as root (as the machine administrator account).

If you get a chance, have a look at the [Kubuntu Desktop Guide]("https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/index.html").  It has lots of fundamental information that I guarantee will save you some headache down the road.

Cheers,
Steve

---

### Post by MachineHead on 2007-04-11
Thanks for the support Calraith.

I allready saved the Kubuntu.pdf to my Windows system.
And ehm I'm a spoiled kid I guess ^^ never had to use the DOS system too much.
So i have no idea.
Wich makes the little table you drawn there very usefull.

Hehe, I have a stack of printed Calraith quotes + the guide backing me up atm.
I will  overcome Windows! (and be able to control a proper OS)

Just craving for the day that games can be played in Linux (Yes I know cedega, maybe try again later in my Kubuntu quest)

Thanks loads again!

MachineHead

---

### Post by MachineHead on 2008-04-16
Well I'm back, with a new system and almost the same problem.
Now I'm trying to run Gutsy Gibbon 7.10 on my system:

AMD Athlon Xp 64 bit 6000+
4 GB RAM 800 Mhz
MSI K9 SLi Platinum mainboard
500 GB HDD SATA II
500 GB HDD SATA II
250 GB HDD SATA II

I tried the all the steps you told me last time Calraith, because I couldn't find a proper 7.10 guide.
No results until now.
Problem is, the files you told me to edit before, seem to be blank now.
I guess in the newer distro that the files are located somewhere else, or have another name and I do not know what it is.

This problem is also being discussed in this thread:
[http://ubuntuforums.org/showthread.php?t=756708](http://ubuntuforums.org/showthread.php?t=756708)

-MachineHead

---

