---
title: "Steps to take before installing Debian based distros???"
date: 2012-03-29
forum: Any Other OS
---

### Post by indigosunrise on 2012-03-29
Hey people.

I've recently wiped my laptop and reinstalled maverick because I let it get too bloated + wanted to get rid of the doze xp partition. 

I'm keen on installing another distro on it to get to know Debian type distros in case I need it down the track, and I'm not too happy with Unity so I won't be moving to the 11.xx and beyond in a hurry unless I magically start liking kde.

Since I am kinda a newbie to Linux and have only been using Ubuntu from the 10.xx's I have never had to deal with any annoyances trying to install a Linux OS.

This particular laptop I was given by my father and it is a brand specific to the company he works for, so I don't have an easy list to grab with all the hardware components.

I'm going to try LMDE first and if I don't like it I will try squeeze. 

Is there an easy command to create an entire list of my hardware devices + details that I imagine I'll need??

Also, I chose the option to encrypt my home folder. I know I will have no problems mounting my Ubuntu file system from LMDE but will I be able to access my home folder??? 

Any other advice before I proceed is welcome.

Thanks.

---

### Post by oldfred on 2012-03-29
Welcome to the forums.

Moved to other OS forum.

I do not use encryption, so others can help you on those issue.

I find fallback in 12.04 to give a gui similar to the older gnome2. It has changes and is not exactly the same but close enough for me.

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

Some tools to list hardware from Ubuntu:
HTML version of info
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html

udevadm info --export-db > file.txt

Similarly, if you run
sudo dmidecode > bios.txt
The last one (dmidecode) lists the machine's DMI or SMBIOS table contents in a friendly format. This DMI or SMBIOS contains a description of the system's hardware components and other useful information such as serial numbers and BIOS revision. This is a really powerful command.

HardInfo is a small application that displays information about your hardware and operating system
hardinfo
system, prefererences, system profiler & performance (hardinfo in synaptic)
sysinfo is a graphical tool that is able to display some hardware and software information about the computer it is run on.
sysinfo

---

### Post by indigosunrise on 2012-03-30
Thank you for your reply oldfred and apologies for posting in the wrong forum.

Thats the exact info I needed re: hardware.

Now just gotta wait for the encrypted home folder issue to be answered as its crucial for me to access my Ubuntu home folder from LMDE but not necessary the other way around...

Cheers for the info about fallback on 12.04 but I'm happy with current version for the time being. Taking the advice from my close friend of staying a bit behind newer  releases for more support/stability... and he runs Linux networks for diagnostic imaging research departments at universities for a living so I try to listen to what he says :).

---

### Post by oldfred on 2012-03-30
I have installed betas for many of the recent versions even though I am still primarily booting 10.10. And some of those betas/new versions had lots of breakage or issues as they were forcing a lot of change. I get the idea they want to start the change several releases before a LTS so by the time the LTS is released it is in good shape.  And it looks like that is working for 12.04.

The beta for 12.04 has been very good. But again I have kept every install since 9.10 on my system in a 25GB / partition with data on other drives. Only with 10.10 did I finally overwrite my old 32 bit install that originally was  6.06 and had updated to 9.04. It was on a separate older drive and I wanted to try gpt partitioning.

The encryption is a different issue. You may want to start a new thread, not sure which forum area, with encryption in the title, so those who know more about it may respond.

---

### Post by HappyLinux on 2012-03-30
I don't know if this might be useful for the OP, but why not try LinuxMint with either MATE and/or Cinnamon user interface. MATE looks and feels like Gnome 2.x, with Cinnamon being a bit more basic, but graphically more easier on the eyes. Neither has the keyboard shortcut nightmare priorities of either Gnome 3.x or Unity.

---

### Post by indigosunrise on 2012-03-31
This thread can be closed. When I went to install I realised that I hadn't stuctured my partition table to the way I needed it to be so I had no choice but to do a clean install of both distros. Now if I wanna set up encryption I can do it in a way that will allow both distros to mount a specific partition and share permissions/encryption settings. 

If I was going to install normal mint I probably wouldn't do it alongside Ubuntu, but instead of. The reason for LMDE is not based on gnome interface (I'm using xfce on it) but more for functionality of a rolling distro that I can keep streamlined and lightweight for my tinkering purposes... and it won't affect my partner that uses Ubuntu on the laptop in the lounge for browsing, and media server purposes.

Thanks for the responses.

p.s. LMDE seems great - havent had too much time to play with it yet but its what I was hoping for.

---

