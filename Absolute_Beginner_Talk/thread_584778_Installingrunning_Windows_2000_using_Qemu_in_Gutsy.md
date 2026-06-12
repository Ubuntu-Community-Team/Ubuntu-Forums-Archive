---
title: "Installing/running Windows 2000 using Qemu in Gutsy"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by boomtisk on 2007-10-21
First of all, I must say I'm really impressed with the new Ubuntu release, it literally took my breath away with how fast and stable its!

However, I have some programs that'll probably never work in Wine so I thought it would be neat if I could install the copy of Windows 2k I have laying around using Qemu, but I'm having trouble pulling it off.

I installed the "Qemulator" frontend and the farthest I've ever got was getting Windows to format the image I specified but it would always abort the formatting process and tell me my hard disk was probably broken. Is there something I might have overlooked? Does the exact type of image you can create matter and which one is the best to choose for an nfts Win2k partition? I also tried to enable the "win2k-hack" option which didn't help, either.

Is there anything I can do or should I try VMWare Server instead? I looks like a bit of a pain to install, though! Thanks a lot in advance!

Besides: is there a way to force the Firefox upload file picker to display thumbnails of images? I kind of miss this feature as it makes uploading pictures difficult-ish.

---

### Post by bubbalouie on 2007-10-21
I have tried Qemu and managed to make t work, however I found it to be a low performer. Virtual Box is very easy to install, and border line on totally automatic with everything, it even includes a very nice mode which looks like windows isn't really running, applications blend into your own desktop. A link is below, they now have a gutsy installer too by the look of it:

[http://www.virtualbox.org/](http://www.virtualbox.org/)
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

The second option is VMWare player, again free, it has a simple install 'script' (it happens to be the whole download) which you run as root from a console and the whole install is guided there after. Setting up a copy of windows 2000 is fairly painless. I use easyvmx to build the virtual machine configuration ahead of installing windows into it, link below:

[www.easyvmx.com](www.easyvmx.com)

Be warned however, you need a copy of the VMWare tools to get full performance out of your guest OS, VMWare tools are basically a few drivers etc you install on the guest copy of windows. I do not know what the licensing restrictions are, but you should be able to get a copy with a VMWare workstation demo, it is up to you to check the license out though.

Personally I use VMWare as it is more of a 'standard' and I need to use it at work, so it is nice to keep to the one tool set where possible. However, I found virtual box to be quite nice all the same and would recommend it over VMWare if you have no ties to anything else. It also happens to be easier to use and configure (although I used it some time ago during the Gutsy alpha stages).

As an aside, you will find everyone will get into the debate over which tool is best, they all have their merits and you will need to decide which is best for your needs. Personally I use VMWare.

Good Luck :)

Ryan

PS:

**Q** Besides: is there a way to force the Firefox upload file picker to display thumbnails of images? I kind of miss this feature as it makes uploading pictures difficult-ish.
**A** Yes there is, I use KDE (Kubuntu) however, use kgtk-wrapper, My copy of firefox now uses all KDE dialogs which allow you to use thumbnails etc (you might need to hunt for a deb file, I can email if needed though):
          [http://www.kde-look.org/content/show.php/KGtk+%28Use+KDE+Dialogs+in+Gtk+Apps%29?content=36077](http://www.kde-look.org/content/show.php/KGtk+%28Use+KDE+Dialogs+in+Gtk+Apps%29?content=36077)

---

### Post by boomtisk on 2007-10-22
Thanks a lot for the advice, bubbalouie, I really appreciate it! I think I'm gonna try Virtualbox first, I'd love to be able to use my midi keyboard without having to boot into Windows.

It's too bad that there doesn't seem to be a solution for my second problem, as I wanted to stick with Gnome this time around. I actually kinda like KDE more but I always had stability issues with it. I'm definitely gonna try KDE 4 once it rolls around though.

---

### Post by boomtisk on 2007-10-22
.... aaaaand I'm already stuck with Virtualbox, it tells me in order to use it, I need to become member of a certain group, namely "vboxusers". How in blazes do I do this? :o

---

### Post by KCPokes on 2007-10-22
> **boomtisk said:**
> .... aaaaand I'm already stuck with Virtualbox, it tells me in order to use it, I need to become member of a certain group, namely "vboxusers". How in blazes do I do this? :o

```

sudo adduser <youruser> vboxusers

```

This will add an existing user to an existing group, in this case vboxusers.  Now if vboxusers doesn't exist, then you'll want to issue:

```

sudo addgroup vboxusers
sudo adduser <youruser> vboxusers

```

---

### Post by bubbalouie on 2007-10-22
KCPokes looks to be more or less on the money, maybe the following will help:

> 
sudo apt-get install libxalan110 libxerces27 libc6
sudo dpkg -i virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb
sudo adduser <youruser> vboxusers
sudo gpasswd -a <youruser> vboxusers


You may require only one of the last 2, however, running both seemed to work for me :)

If you have no luck let me know as I need to set this up for someone else anyway and can take notes on how I get there.

Ryan

*EDIT: In theory only the last command is needed to add the user, by creating an admin you can have 'full' permission with that particular module
*EDIT 2: USBFS is disabled by default in Gutsy, to address this use: [http://www.virtualbox.org/ticket/747](http://www.virtualbox.org/ticket/747)
*EDIT 3: VMWare is much easier to install and configure now, VirtualBox is nicer once it is up and running, but is not what I would call 'easy' to get there... It looks like a lot has changed in the last few months. I sincerely apologize for wasting your time, VMWare Player is rougher around the edges, and more difficult to make a VM with, but it seems better on the Gutsy final than VirtualBox. Sorry :(

---

