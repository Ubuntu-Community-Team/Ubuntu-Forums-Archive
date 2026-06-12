---
title: "PPC, Ubuntu 11.10, giving a mirrorserver error."
date: 2011-10-28
forum: Apple Hardware Users
---

### Post by Pondake on 2011-10-28
Hello y'all,

I've came upon a problem and I'd really like to get this solved.

I recently burned a copy of Ubuntu 11.10 for PPC versions:
Downloaded here: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
"[Mac (PowerPC) and IBM-PPC (POWER5) desktop CD]("http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-powerpc.iso")"
It said it was oversized and wasn't capeable of being on a CD, but I put it on a DVD.

Put it in my Powerbook and booted it up while pressing 'C'.
Then I came up with a terminal where I had to press enter, well you know the drill.

The error came upon during the installation, while getting/configuring the APT I guess.
It said that the Mirror Server wasn't working, 'Ubuntu-archive-mirrorserver'. 
It's giving errors in a loop while the installation process saying it's done and ready for a reboot.

While I reboot I came upon an error that linuxvm is missing (No such file or directory).

What do I need to do?
Ps. Sorry if this question is quite simple, I just started learning Linux and yeah, don't be too hard on me :).

---

### Post by rsavage on 2011-10-28
Not a silly question at all since nobody as yet has reported getting the live cd to work!  It's pretty new and the errors keep changing!
 
Have no idea about the linuxvm.
 
If you are up for a re-install then possibly there is a manual option for setting the mirror?  You could try changing the mirror to "ports.ubuntu.com" with directory "/ubuntu-ports/".
 
An alternative way to install is described here [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1) .
 
Sorry, 11.10 is all a bit up in the air at the moment until there is feedback on what works and what doesn't.
 
Hope that helps!

---

### Post by Pondake on 2011-10-28
> **rsavage said:**
> Not a silly question at all since nobody as yet has reported getting the live cd to work!  It's pretty new and the errors keep changing!
 
Have no idea about the linuxvm.
 
If you are up for a re-install then possibly there is a manual option for setting the mirror?  You could try changing the mirror to "ports.ubuntu.com" with directory "/ubuntu-ports/".
 
An alternative way to install is described here [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1) .
 
Sorry, 11.10 is all a bit up in the air at the moment until there is feedback on what works and what doesn't.
 
Hope that helps!

Sure I'm up for a re-install, I tried re-installing it 7/8 times already.
I'm currently using Firefox from the BootCD using a LAN cable, lol.

As I said, I'm quite new to Linux.
Where do I change the Mirror Server, which directory, and where?

---

### Post by rsavage on 2011-10-28
Sorry, I'm telling you wrong.  It's late here in the UK and my brain if fried!  Totally forgot how the live cd works.  Hmm... sorry can't be much help with the live cd.

---

### Post by Pondake on 2011-10-28
> **rsavage said:**
> Sorry, I'm telling you wrong.  It's late here in the UK and my brain if fried!  Totally forgot how the live cd works.  Hmm... sorry can't be much help with the live cd.

Uhm okay, well.. that's ok.

But, I was trying to get Linux working on my Powerbook..
Is it better if I install the previous version first, then when everything is stable, install 11.10?
Should that be the best solution ?

---

### Post by Pondake on 2011-10-28
Shall I use either
**10.10 Maverick Meerkat**


or
[B]10.04 Lucid Lynx LTS  ??
[/B]

---

### Post by rsavage on 2011-10-28
Live cd: If this was an installed system I'd be saying look at the file /etc/apt/sources.list in a text editor.  It will look something like this [http://ubuntuforums.org/showpost.php?p=11266820&postcount=11](http://ubuntuforums.org/showpost.php?p=11266820&postcount=11) although you'll have oneric written instead of natty.  You could possibly try changing it to point to the mirror I gave earlier?  It is the UK mirror.
 
Otherwise, just run through the other link I gave.  You can try the 11.10 mini cd or play safe with 11.04 mini and upgrade.  When you have the 11.10 base you then install the GUI you want.  Pointless installing the 11.04 GUI to then upgrade to 11.10 GUI immediately afterwards.

---

### Post by rsavage on 2011-10-28
Not much difference between maverick and lucid except lucid is supported a lot longer.  If you are going to upgrade versions then start with the higher which is maverick.

---

### Post by Pondake on 2011-10-28
> # /etc/apt/sources.list

deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release powerpc (20111012)]/ oneiric main
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) oneiric main restricted universe multiverse
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) oneiric main restricted universe multiverse #Added by software-properties
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) oneiric-security main restricted universe multiverse
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) oneiric-security main restricted universe multiverse #Added by software-properties
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) oneiric-updates main restricted universe multiverse
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) oneiric-updates main restricted universe multiverse #Added by software-properties

This is the list, but it's quite short isn't it?
What do I need to change/add to make it go trough the installation?
(I will just try one more)

---

### Post by Pondake on 2011-10-29
> **rsavage said:**
> Live cd: If this was an installed system I'd be saying look at the file /etc/apt/sources.list in a text editor.  It will look something like this [http://ubuntuforums.org/showpost.php?p=11266820&postcount=11](http://ubuntuforums.org/showpost.php?p=11266820&postcount=11) although you'll have oneric written instead of natty.  You could possibly try changing it to point to the mirror I gave earlier?  It is the UK mirror.
 
Otherwise, just run through the other link I gave.  You can try the 11.10 mini cd or play safe with 11.04 mini and upgrade.  When you have the 11.10 base you then install the GUI you want.  Pointless installing the 11.04 GUI to then upgrade to 11.10 GUI immediately afterwards.


I think you made a slight mistake, because there is no 11.04?

---

### Post by rsavage on 2011-10-29
There is here: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) .  I gave you a link with instructions on how to use it.

Btw, your sources.list looks fine so I don't think it is that.  There must be something else on the install cd that sets the mirror.  Have you tried setting your location as the UK to try and fool it?

---

### Post by Pondake on 2011-10-29
> **rsavage said:**
> There is here: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) .  I gave you a link with instructions on how to use it.

Btw, your sources.list looks fine so I don't think it is that.  There must be something else on the install cd that sets the mirror.  Have you tried setting your location as the UK to try and fool it?

Oh lol, I couldn't find the version in the Ubuntu PPC list, so I downloaded 10.10 and now it's busy upgrading to 11.4.

I hope it'll work, thank you so much!

---

### Post by rsavage on 2011-10-29
A few people have reported problems with 11.04 (very high CPU usage that freezes things or makes it incredibly slow).  The fixes are linked on the instructions I gave you, but you may have to upgrade to 11.10 to truly fix it.....

---

### Post by rsavage on 2011-10-29
Also, the unity interface did have horrible colours in 11.04, but that is fixed in 11.10.

---

### Post by Pondake on 2011-10-29
> **rsavage said:**
> Also, the unity interface did have horrible colours in 11.04, but that is fixed in 11.10.

A'ight I'm upgrading from 11.04 to 11.10 at the moment. :P

---

### Post by pauljwells on 2011-10-29
> **rsavage said:**
> Also, the unity interface did have horrible colours in 11.04, but that is fixed in 11.10.

If you can't get past 11.04 the colours were fixed in the ppa. You have to compile yourself from source but it's easy.

[http://ubuntuforums.org/showpost.php?p=11110818&postcount=2]("http://ubuntuforums.org/showpost.php?p=11110818&postcount=2")

---

### Post by Pondake on 2011-10-29
WARNING bootdevice may be renamed. Try root=/dev/sda3
Gave up waiting for root device device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= 9did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/hda3 does not exist. Dropping to a shell!


Busybox v1.18.4 (Ubuntu 1:1.18.4-2ubuntu2) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _


What the ****, this came when I tried to reboot it when it was done with upgrading to 11.10. =/

---

### Post by rsavage on 2011-10-29
Yep, expected.  See link I gave you.

---

### Post by Pondake on 2011-10-29
> **rsavage said:**
> Yep, expected.  See link I gave you.

No offense, but you gave me plenty links. :o

---

### Post by rsavage on 2011-10-30
I gave you 3 links I think, and only one (the first link) has a big long list of workarounds.  It has a contents, one section is labelled "yaboot/busybox error".  I'm struggling to see how I can make it any easier for people?!  It's caused because you went through the arduous route of upgrading from 10.10.

---

### Post by Pondake on 2011-10-30
> **rsavage said:**
> I gave you 3 links I think, and only one (the first link) has a big long list of workarounds.  It has a contents, one section is labelled "yaboot/busybox error".  I'm struggling to see how I can make it any easier for people?!  It's caused because you went through the arduous route of upgrading from 10.10.

As. I. already. said. I don't understand 1 thing about Linux.
Now it's not booting at all, I don't have the busy box.
And I give up, I'll install 10.10 and explore that, I'll see whenever 11.10 is stable.

---

### Post by rsavage on 2011-10-30
> **Pondake said:**
> Now it's not booting at all, I don't have the busy box.
And I give up, I'll install 10.10 and explore that, I'll see whenever 11.10 is stable.
 
I don't think that is necessary.  Explain what you did so that you now don't get the busybox error.  Are you dual-booting?

---

### Post by Pondake on 2011-10-30
> **rsavage said:**
> I don't think that is necessary.  Explain what you did so that you now don't get the busybox error.  Are you dual-booting?

No, I installed 10.10 first, then upgraded to 11.04 without any problems.
And then, I upgraded to 11.10 with 1 error that man-db or mandb or something couldn't been installed, and also I noticed a lot of errors in the terminal log.
After it was done, I tried rebooting and came upon the busybox error, but now when I tried to boot I couldn't even go trough the boot, it couldn't load the kernel.

Well, anyway, I installed 10.10 and upgraded to 11.04 but I won't upgrade to 11.10...

---

### Post by rsavage on 2011-10-30
> **Pondake said:**
> 
While I reboot I came upon an error that linuxvm is missing (No such file or directory).

It's been bugging me this has.  Did you mean vmlinux?  There's usually a link file called 'vmlinux' (in the /boot directory) which points to another file with a longer name (which has vmlinux at the start).  

If somebody is in this position again (not a newbie to linux) then I think I could have another crack at solving this.  I think I was pretty close with my answer on this thread [http://ubuntuforums.org/showthread.php?p=11357322](http://ubuntuforums.org/showthread.php?p=11357322) .  I think the solution is quite easy if a vmlinux file does exist.

---

### Post by Quattro5 on 2011-10-30
I have the exact same issue on a Powermac G5 ALS. The Mirror is not good. Now, I don't know much about linux either. I run Lubuntu and Ubuntu on my laptop pc, I used to run Debian Wheezy on this PPC machine. With Cut & paste, I was able to get the airport card to work. 

I have reported the error through the logs 6 or 7 times.

I'd really like to have 11.10 as this way, the system would work fine. 

If you have a solution, I'm interested to learn about it!  (Btw, tried fooling the install gui by saying I was in New York, still had this bad mirror error).

Thanks!

---

### Post by rsavage on 2011-10-30
I said try fooling it with setting your location as the UK not USA!  You want London, but you'll probably have the same error.....it was just an idea, but I know nothing about the mirrors in reality.

If your error is vmlinux related then can you boot up from the live cd and see what is in the installed (the one on the hard drive) /boot directory?  Any files with vmlinux in the name?

---

### Post by rsavage on 2011-10-30
There is a possible solution to the mirror error on this thread [http://ubuntuforums.org/showthread.php?t=1770355](http://ubuntuforums.org/showthread.php?t=1770355) . I don't think very highly of the content of the rest of the post, so I've quoted the relevant bit of the post below:

> Workaround: just *ping ports.ubuntu.com* [Editors note: the italics is a command.  Press Ctrl+C to stop it running] and take note of its IP address. Then edit/create the */etc/hosts*  file and add this line faking an hostname "mirror", alias for  "ports.ubuntu.com", with the actual ports.ubuntu.com address you just  found:

     91.189.92.175 ports.ubuntu.com mirror 

(change the 91.189.etc with the actual IP you got from "ping").So before you install try this:

When I entered the command "ping ports.ubuntu.com" I got the same numbers he did so you can probably just use those.

To open the file /etc/hosts type:

```
gedit /etc/hosts
```Add the line:

```
91.189.92.175 ports.ubuntu.com mirror
```Save the file.  If you can't save it, you may have to open it first with root privileges.  Use the command:

```
sudo gedit /etc/hosts
```If it asks for a password just press the enter key.

When you get the installed system running you'll need to edit the sources.list file.  You'll want to replace 'mirror' with 'ports.ubuntu.com'.  It should look something like this [http://ubuntuforums.org/showpost.php?p=11266820&postcount=11](http://ubuntuforums.org/showpost.php?p=11266820&postcount=11) except you'll have oneiric written instead of natty.

---

### Post by Quattro5 on 2011-10-30
So I tried a mirror on the same continent I am, I thought there might be an issue using London, UK as a mirror. I am in Canada (Ontario), nor so far from new England thus why I tried to pass as a New Yorker :-) .

---

### Post by Quattro5 on 2011-10-30
> **rsavage said:**
> There is a possible solution to the mirror error on this thread [http://ubuntuforums.org/showthread.php?t=1770355](http://ubuntuforums.org/showthread.php?t=1770355) . I don't think very highly of the content of the rest of the post, so I've quoted the relevant bit of the post below:

So before you install try this:

When I entered the command "ping ports.ubuntu.com" I got the same numbers he did so you can probably just use those.

To open the file /etc/hosts type:

```
gedit /etc/hosts
```Add the line:

```
91.189.92.175 ports.ubuntu.com mirror
```Save the file.  If you can't save it, you may have to open it first with root privileges.  Use the command:

```
sudo gedit /etc/hosts
```If it asks for a password just press the enter key.

When you get the installed system running you'll need to edit the sources.list file.  You'll want to replace 'mirror' with 'ports.ubuntu.com'.  It should look something like this [http://ubuntuforums.org/showpost.php?p=11266820&postcount=11](http://ubuntuforums.org/showpost.php?p=11266820&postcount=11) except you'll have oneiric written instead of natty.
I will add the new port to the gedit file and let you know how it goes. I have 10.10 working (dual booted with Debian Wheezy for backup - 50 Go to Debian and 200Go for Ubuntu), in the process of upgrading to 11.04; Am worried about having to start all over if the upgrade to 11.10 goes wrong. Oh well, there always next week-end...lol

Thanks for the help! 

Cheers!

---

### Post by Quattro5 on 2011-11-07
> **Quattro5 said:**
> I will add the new port to the gedit file and let you know how it goes. I have 10.10 working (dual booted with Debian Wheezy for backup - 50 Go to Debian and 200Go for Ubuntu), in the process of upgrading to 11.04; Am worried about having to start all over if the upgrade to 11.10 goes wrong. Oh well, there always next week-end...lol

Thanks for the help! 

Cheers!


Update: Added the new port to the gedit file , and got a system. Now running  11.10 on my iMac G5. 

Thanks for the help!

---

### Post by rsavage on 2011-11-08
Quattro, did you use the live cd to install? Editing the hosts file was just a hack for the live cd. It is not needed for an upgrade.

---

### Post by MacPenguin1972 on 2011-11-09
> **Pondake said:**
> Hello y'all,

I've came upon a problem and I'd really like to get this solved.

I recently burned a copy of Ubuntu 11.10 for PPC versions:
Downloaded here: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
"[Mac (PowerPC) and IBM-PPC (POWER5) desktop CD]("http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-powerpc.iso")"
It said it was oversized and wasn't capeable of being on a CD, but I put it on a DVD.

Put it in my Powerbook and booted it up while pressing 'C'.
Then I came up with a terminal where I had to press enter, well you know the drill.

The error came upon during the installation, while getting/configuring the APT I guess.
It said that the Mirror Server wasn't working, 'Ubuntu-archive-mirrorserver'. 
It's giving errors in a loop while the installation process saying it's done and ready for a reboot.

While I reboot I came upon an error that linuxvm is missing (No such file or directory).

What do I need to do?
Ps. Sorry if this question is quite simple, I just started learning Linux and yeah, don't be too hard on me :).


I ran into a bad mirror error myself. Even tried 12.04, same thing

Suffice to say 12.04 is definitely "off the table" for me right now until 11.10  can be figured out.

So much for the "ouf of the box" claims! lol!

---

### Post by freechelmi on 2011-11-12
> **MacPenguin1972 said:**
> I ran into a bad mirror error myself. Even tried 12.04, same thing

Suffice to say 12.04 is definitely "off the table" for me right now until 11.10  can be figured out.

So much for the "ouf of the box" claims! lol!

Do you mean you are surprised that PPC isos don't work out of the Box ? You know they are not supported at all ?

---

### Post by Farinet on 2012-02-13
> **rsavage said:**
> There is a possible solution to the mirror error on this thread [http://ubuntuforums.org/showthread.php?t=1770355](http://ubuntuforums.org/showthread.php?t=1770355) . I don't think very highly of the content of the rest of the post, so I've quoted the relevant bit of the post below:

So before you install try this:

When I entered the command "ping ports.ubuntu.com" I got the same numbers he did so you can probably just use those.

To open the file /etc/hosts type:

```
gedit /etc/hosts
```Add the line:

```
91.189.92.175 ports.ubuntu.com mirror
```Save the file.  If you can't save it, you may have to open it first with root privileges.  Use the command:

```
sudo gedit /etc/hosts
```If it asks for a password just press the enter key.

When you get the installed system running you'll need to edit the sources.list file.  You'll want to replace 'mirror' with 'ports.ubuntu.com'.  It should look something like this [http://ubuntuforums.org/showpost.php?p=11266820&postcount=11](http://ubuntuforums.org/showpost.php?p=11266820&postcount=11) except you'll have oneiric written instead of natty.

How should that work, given that i'm starting from a live-cd???

TIA

---

### Post by rsavage on 2012-02-13
Exactly how it is described except if you are using lubuntu then use leafpad instead of gedit.
 
I tried setting my location to Zurich and it failed, but setting to London installs fine - so that is another workaround.
 
A fix should be available to test tomorrow.

---

### Post by Farinet on 2012-02-13
> **rsavage said:**
> Exactly how it is described except if you are using lubuntu then use leafpad instead of gedit.
 
I tried setting my location to Zurich and it failed, but setting to London installs fine - so that is another workaround.
 
A fix should be available to test tomorrow.

Thanks a lot! Zurich was exactly my case ;-) 

So, i'll wait for an updated live iso? Would you announce it here when it is done? TIA

---

### Post by rsavage on 2012-02-14
Should be available now.  Please give feedback here [https://bugs.launchpad.net/ubuntu/+source/choose-mirror/+bug/919356](https://bugs.launchpad.net/ubuntu/+source/choose-mirror/+bug/919356) .

---

### Post by Farinet on 2012-02-15
Thanks for the info. I did report over there.

---

