---
title: "KERNEL Install fails in iMac G3"
date: 2008-03-21
forum: Apple PPC Users
---

### Post by systemarpi on 2008-03-21
[SIZE="3"]Hi, I am helping a School that have received (from donation) some[COLOR="Blue"] iMac´s G3[/COLOR] ([COLOR="Blue"]new world[/COLOR] as far as I know)

But some of them don't boot some other have OS problems, so I decide to Install Kubuntu in all of them, to haver a standard environment in all computers

As far as I know, trying to install [COLOR="Blue"]Kubuntu[/COLOR] from the Desktop CD would be useless since I have only [COLOR="Blue"]64mb of RAM[/COLOR] per machine.

So I decide to download the [COLOR="Blue"]Alternate CD[/COLOR], the problem is that the setup stops at the Kernel install, showing the message:

Unable to install the selected Kernel
An Error was returned while trying to install the kernel into the target system
Kernel package: &#8220;linux-powerpc&#8221;.

So I switch to console virtual 4 to see what happened this is what I got:

First, [COLOR="Blue"]a lot of[/COLOR] (like 20 or more) [COLOR="Blue"]Buffer I/O error on device hdc[/COLOR]

[COLOR="Blue"]Then:[/COLOR]
[COLOR="Red"]apt install: fail to fetch cdrom: [Kubuntu 7.10 -Release powerpc] /pool/main/l/linux-ubuntu-modules-2.6.22/ linux-ubuntu-modules-2.6.22-14-powerpc_2.6.22-14.37_powerpc.deb Hash sum mismatch[/COLOR]

[COLOR="Red"]apt install: fail to fetch cdrom: [Kubuntu 7.10 -Release powerpc] /pool/main/l/linux-meta/linux-image-powerpc_2.6.22.14.21_powerpc.deb Hash sum mismatch[/COLOR]

[COLOR="Red"]apt intall: E: Unable to fetch some archives, maybe run apt-get update or apt-get &#8211;fix-missing?[/COLOR]

[COLOR="Blue"]Then:[/COLOR]
[COLOR="Red"]base-installer: error: exiting on error base-installer/kernel/fail-install[/COLOR]

I really don't know what to do now... please help

I tried to do something with[COLOR="Blue"] BusyBox[/COLOR] (Virtual console #2) but thats pretty limited or I don't know how to use it.

[COLOR="Red"]FAQ[/COLOR]
[COLOR="Red"]Did you check md5 after and before burning? [/COLOR][COLOR="Blue"]Yes I did
[/COLOR][COLOR="Red"]What speed did you burn the iso?[/COLOR] [COLOR="Blue"]4x as low as possible to prevent error with the old iMac (burned with K3b)[/COLOR][/SIZE]

---

### Post by InvIsiBlekID on 2008-03-21
Did you check the cd for defects before booting it?  There should be an option at the first menu.

---

### Post by systemarpi on 2008-03-21
> **InvIsiBlekID said:**
> Did you check the cd for defects before booting it?  There should be an option at the first menu.

No I didn't check that, so, should I cancel the current installation and start again? (I am stuck at ~85% process)

I didn't see any option to re-check the CD, but let me see if I can find something

---

### Post by stream303 on 2008-03-21
64 mb is probably going to be tough to run with.

In any case, you can try Xubuntu with the "alternate" install images and see how that goes.

Failing that, you could perform a very minimal command-line system, and add back some minimal X components.

I've done it with the server installation of Feisty 7.04, and then added back xorg, and some lightweight applications.  I think this can be done from the "alternate" images too, I haven't tried it.

---

### Post by systemarpi on 2008-03-21
> **stream303 said:**
> 64 mb is probably going to be tough to run with.

In any case, you can try Xubuntu with the "alternate" install images and see how that goes.

Failing that, you could perform a very minimal command-line system, and add back some minimal X components.

I've done it with the server installation of Feisty 7.04, and then added back xorg, and some lightweight applications.  I think this can be done from the "alternate" images too, I haven't tried it.

Anyway something is definitely wrong and I don't think 64mb are low to “just install” the kernel, maybe later at boot or daily use, 64mb are going to be overkill but not at install time....

I am not sure, what about the “hdc” I/O Errors?, maybe the HD is dead (?), but is pretty odd the any try finish in the same part, at the kernel installation

---

### Post by cubeeggs on 2008-03-21
I don't know about 64 MB, but with 96 MB it's a little laggy in XFCE and running programs is a little slow. You should try the Xubuntu alternate disc for Feisty (Gibbon has too many problems). Then you can install fluxbox and fluxconf if XFCE doesn't run well.

---

### Post by slacka-vt on 2008-03-21
Are these computers networked ?
I've found that net-install is the way to go.
Requires much less RAM then a CD.
What distro you trying to install?
I think your best bet is Dapper for stability.
Here's the mini.iso link for your type.
Just burn the iso to disc.

[Ubuntu Dapper Net-Install Mini.iso PPC 32bit]("http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-powerpc/current/images/powerpc/netboot/")

Good luck!
~s

---

### Post by systemarpi on 2008-03-21
> **slacka-vt said:**
> Are these computers networked ?
I've found that net-install is the way to go.
Requires much less RAM then a CD.
What distro you trying to install?
I think your best bet is Dapper for stability.
Here's the mini.iso link for your type.
Just burn the iso to disc.

[Ubuntu Dapper Net-Install Mini.iso PPC 32bit]("http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-powerpc/current/images/powerpc/netboot/")

Good luck!
~s

No, they are not networked

I am trying to install Kubuntu 7.10 (Alternate CD for PPC of course)

Let me try yours, thanks for your help.

I can try different setups as long as I have all th machines with me.

---

### Post by slacka-vt on 2008-03-21
From what I understand, Edgy, Feisty, Gutsy are not offcially supported on the PPC architecture.
Yes, they have installers and what not, but they will require more "tinkering" to get 'em going.
Dapper, and the new Hardy, are the only distros officially supported under PPC.
My Dapper live cd is still, by far, the most hassle free of any of the distros I've tried. (all of them)
Just works every time, as a matter of fact, I burned the CD almost 3 years ago and I still use the same burned cd on "dodgey" systems.

[http://releases.ubuntu.com/6.06/]("http://releases.ubuntu.com/6.06/")

~s

---

### Post by systemarpi on 2008-03-21
> **slacka-vt said:**
> From what I understand, Edgy, Feisty, Gutsy are not offcially supported on the PPC architecture.
Yes, they have installers and what not, but they will require more "tinkering" to get 'em going.
Dapper, and the new Hardy, are the only distros officially supported under PPC.
My Dapper live cd is still, by far, the most hassle free of any of the distros I've tried. (all of them)
Just works every time, as a matter of fact, I burned the CD almost 3 years ago and I still use the same burned cd on "dodgey" systems.

[http://releases.ubuntu.com/6.06/]("http://releases.ubuntu.com/6.06/")

~s


I was using this ones:
[http://cdimage.ubuntu.com/kubuntu/ports/releases/7.10/release/](http://cdimage.ubuntu.com/kubuntu/ports/releases/7.10/release/)

Thats the Kubuntu 7.10 Alternate CD for PPC

---

### Post by systemarpi on 2008-03-21
I think this is “almost” solved since I finally could make it after the “installing kernel” step, the problem so far was the CD.

The md5sum was ok, when I checked it, but before the “install” command I tried the “check” commando and that gives me a “failure integrity”

So I use a different burner.

For future reference:
Fail Burn was with: LG CD-RW @ 4x speed
Successful burn was with: Emprex DVD-RW @ 16x speed
(same machine, same OS (Kubuntu 7.10), same software (K3b), same CD manufacturer and speed)

Now I am at 6% of the “install software” step.

If I reach the login screen I would change this topic to SOLVED, thanks for you help.

---

### Post by slacka-vt on 2008-03-21
Please correct me if this is wrong but
- OS install CDs / DVDs should always be burned at 8x or less.
I used to burn at "fastest" only to have OS installs (both Mac and Linux) fail.
After adopting the "8x or less" rule,
Installs seem to be sucessful a much higher of a percentage of the time.

~s

---

### Post by systemarpi on 2008-03-21
> **slacka-vt said:**
> Please correct me if this is wrong but
- OS install CDs / DVDs should always be burned at 8x or less.
I used to burn at "fastest" only to have OS installs (both Mac and Linux) fail.
After adopting the "8x or less" rule,
Installs seem to be sucessful a much higher of a percentage of the time.

~s

The problem in this case (In my own opinion) was the old CD-DRIVE of the iMAC

Since all the 4 CDs I burned worked perfect with my Kubuntu (IBM PC), but couldn't even boot in the iMAC

The “8x or less” rule sound cool, but my first try was at 4x with a CD-RW, and finally what works so far (I am at ~34% “install software” step) was the 16x DVD-RW burn...

Whatever happened, the lesson to learn here is that md5sum is not enough, ALWAYS run “check” command before install.

---

### Post by systemarpi on 2008-03-21
I don't know how to mark this post as SOLVED but.. maybe a moderator could do it, because the installation process was done, everything says was a successful installation

I cant boot... but thats another problem, if wanna help, would be much appreciated
[http://ubuntuforums.org/showthread.php?t=731362](http://ubuntuforums.org/showthread.php?t=731362)

---

### Post by stream303 on 2008-03-22
> **systemarpi said:**
> Now I am at 6% of the &#8220;install software&#8221; step.

If I reach the login screen I would change this topic to SOLVED, thanks for you help.

Hopefully we can get that boot issue resolved, but just a reassurance that during install, you can see what LOOKS like hangs at 6%, 33%, 98% etc, it is usually stilll working - you have to walk away because it knows you are watching it like a pot of water about to boil. :)

I like gas-gauges, but boy I wish Ubuntu / Debian had at least a spinning cursor sometimes with the alternates ( \ - / ) all backspaced on each other...

---

