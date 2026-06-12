---
title: "Use same home directory for OS X/Ubuntu?"
date: 2007-05-31
forum: Apple Intel Users
---

### Post by thully on 2007-05-31
Hi,

I'm curious - is it possible to use the same home directory with OS X and Ubuntu?
If so, how? Is it a good idea to do this?

I keep nearly all the data I'd like to share in my home directory, and this seems like a logical
way to do it.  I've done it before with other Linux distros, but not for two different OSes(albeit both UNIX-type OSes).

If not, what would be the recommended way to share this data?  I know I'm either doing an OS X/Ubuntu dual-boot, only OS X (+fink/darwinports/maybe even gentoo for OS X for my GNU/FOSS fix), or only Ubuntu.  I decided against VMs because I figure I'll be using Ubuntu quite a bit if I keep it around.

---

### Post by adampyre on 2007-05-31
I am not sure if this is possible? Yet, you claim to have done it with 2 Linux distros so maybe it is, as isn't OSX essentially just another Linux distro now?

I suppose the biggest obstacle would be that the OS'es each use a different file system. Plus they would be set up on different partitions or disks......

Good luck and cheers if you figure it out!

---

### Post by tgalati4 on 2007-05-31
This sounds good on paper but probably not in practice.  OS X is based on BSD Unix and Ubuntu is based on Linux.  There are lots of configuration files that are kept in the home directory.  Some with similar names which could cause confusion between the operating systems.

If you create an EXT2 data partition with an HFS partition for OS X and an EXT3 partition for Ubuntu, then both systems would be able to read and write to the data partition.  You can create symbolic links (for documents, music, pictures, movies, etc) that point to this data partition.  These links can be labeled the same on the OS X side and the Ubuntu side--so that they appear to be the same layout within your home directory of each OS.

I run Tiger with XDarwin in one of my 8 windows (via Deskop Manager).  I run gnome-panel and I have essentially Ubuntu running in one panel with another 4 panels provided by gnome.  Then you can load just about any package using FINK.  The advantage is that you have all of these applications running under the native Cocoa environment and you don't have to reboot to change apps.  (and you can run iTunes)

---

### Post by Seamyst on 2007-05-31
I just made small partitions for Tiger and Feisty and a large shared (HFS+) partition for everything I want to access from either OS.  It's a little complicated, but it works like a charm.

---

### Post by ivesjd on 2007-05-31
Why did you use HFS+?

---

### Post by ronocdh on 2007-05-31
> **ivesjd said:**
> Why did you use HFS+?
Good question. I'd've used ext3 myself, but perhaps Seamyst has had trouble with it in the past on OS X. I think I've read people here using either MacFUSE or the ext2IFS and having bad luck. I've never toyed around with MacFUSE, but mean to soon, just to experiment with all the options it offers. I'm going to stick with ext2IFS for ext3 support in OS X.

That said, I've disabled journaling on my OS X volume and I just use its user folder contents, e.g. Documents, Movies, etc. and r/w from Ubuntu to it. I added it to fstab so it mounts automatically, and it's like I'm just using one computer. I love it! 

I highly recommend this course of action. Post back if you've any trouble or questions. I could post a how-to, I guess, if  people are interested.

---

### Post by thully on 2007-05-31
tgalati4: Regarding Desktop Manager and gnome-panel - how do you do this?
I knew you could run Unix apps on OS X, but I never knew how to run X full-screen with a full desktop
environment (i.e. KDE/GNOME).  

I'd say I have the same issue w/ running Ubuntu full-time - I want to do it, but I'd miss iTunes and other multimedia support.   Conversely, though, OS X lacks the ability to tweak your system to the degree you can on Ubuntu... 

As a result, I've been looking for a good setup to use once I get my MacBook back.  I figure that either I'll do something like that (running a GNU-type environment alongside OS X) or I'll take the total Ubuntu plunge.

---

### Post by ronocdh on 2007-05-31
> **thully said:**
> I'd say I have the same issue w/ running Ubuntu full-time - I want to do it, but I'd miss iTunes and other multimedia support.   Conversely, though, OS X lacks the ability to tweak your system to the degree you can on Ubuntu...
What specifically are you referring to? Tracks purchased through the iTunes Music Store? If so, you've probably heard about iTunes Plus, which is a nice sign, but if you're too impatient (or don't want to pay for it), you can always burn your tracks to a CD and rerip. Yes, small quality loss. But small price to pay to hear them in Ubuntu, no?

---

### Post by tgalati4 on 2007-06-01
My setup is on a G4, 15", 1 GHz powerbook, so your intel-mac may behave differently.

Here's a synopsis:

Load an X Windows system onto Tiger.  There are 3 or 4 that work.  I use XDarwin which comes on the "XTools" CD on Tiger.  You can also download it from the web and there are some repositories that have it.  There  is also freeX86 and a few flavors of xorg.  I can't comment on how well they work.

Load Fink Commander.  I think it is still available at apple.com This is a synaptic-like package manager that will check dependencies and install packages.  Be aware that some packages need to be compiled from scratch and can take several hours.  Some programs work well, others are buggy--such is open source.

Load Desktop Manager.  This will give you 8 desktops.

I have several Ubuntu machines at home--so this works for me wirelessly.

In a Terminal, run startx (this starts XDarwin)

I ssh into one of them:  ssh -2 -Y username@machinename

Then run:

gnome-panel &

Up pops a complete gnome desktop of the remote machine.  Now I have "multi-processing" because the remote machine is doing all the work and only the xserver locally is updating the screen.  It's snappy this way.

You will have to set up a sound server (ESD) to push sound effects and music from that remote session to your local machine.

You can also install gnome locally, but it requires an extensive build.  Since I have not encountered any problems running gnome remotely, I can't image that it would not work.  You really don't need it though since you can simply install the GTK2 toolkit and run any gtk application and use the Windowmaker window manager that comes with XDarwin.

There are several window managers to choose from.  Windowmaker is small and light and looks like NextStep.

If there is a particular application that you like to use (like Audacity for sound editing) then that is available as a native Mac port.  Use that since it will run in a native Cocoa graphics environment.

In the end, you will have a hybrid of Tiger, XDarwin, Fink ports, native FOS ports.  It would be nice to have One Operating System, but this is a compromise until we get there.

Because of the BSD foundation of Tiger, ports are relatively painless to perform so more applications are showing up every day.

I ran Dapper for a few weeks on my powerbook, but I had too many fiddly problems.  Tiger is worth the $129 if you've already spent $2k on mac hardware.  

As far as system tweaking, you can do quite a bit of tweaking under Tiger, but you have to google search to find some interesting hacks.  I installed iScroll2 for trackpad, 2-finger scrolling, smart drive monitoring, Cocoanut battery logging, ATI overclocking (15%), Netgear wireless card driver (so I can run both the Airport and the Netgear A band card at the same time)--double the wireless bandwidth!  Kismet and gps for wandering around the neighborhood--amazed at how many hotspots there are.

Since Ubuntu development has stopped on PPC, I'm comfortable using remote machines on my pbook to access Ubuntu apps when I need them.  For instance Limewire music shares show up under iTunes 7.  So I leave Limewire running (but disconnected from the internet) so I can listen to my Ubuntu music collection under iTunes as a stream without loading everything into iTunes' brain-dead database.

If I want to listen to iTunes music on my Ubuntu desktop, then I load up a 1GB shuffle and plug it into Ubuntu machine and play it though Rhythmbox.  iTunes 7 won't share music to Ubuntu machines through DAAP the way iTunes 6 did.  Can't downgrade iTunes 6 because it won't work with the new Nanos.  Don't you love lock-in?

My wishlist:

Simple music sharing through iTunes 7
iPods that play ogg natively
Simple iTunes database that doesn't fold up on itself and take all of your music with it.
An OS X operating system that runs 95% of the Synaptic packages natively

---

### Post by Seamyst on 2007-06-01
I used HFS+, following the advice of [this how-to]("http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Shared_Partition"), because it said it was the best way.  Also, the wiki said that you needed the Ext2 File Extension to view the partition on the OS X side, and I'd had trouble with that in the past.

My wishlist is very simple:
I want Ubuntu to play *.m4v files (movies purchased through iTunes) easily, preferably through VLC or Movie Player.  You know why?  Because you can't burn iTunes-purchased movies via iTunes, and I can't figure out how to burn it otherwise.

---

### Post by vh1 on 2007-06-01
hmm, I just created a FAT32 shared partition because I didn't think linux had good support for writing to HFS+, and because the ext driver I was using in OSX (extfsmanager) wouldn't show my already created ubuntu ext3 partition. now osx shows ALL partitions on the desktop (including the EFI??)

so, there is reliable write support for HFS+ filesystems in ubuntu?

---

### Post by ronocdh on 2007-06-01
> **Seamyst said:**
> My wishlist is very simple:
I want Ubuntu to play *.m4v files (movies purchased through iTunes) easily, preferably through VLC or Movie Player.  You know why?  Because you can't burn iTunes-purchased movies via iTunes, and I can't figure out how to burn it otherwise.I do not believe this is possible, sorry. Such are the woes of DRM.

---

### Post by Seamyst on 2007-06-03
> **vh1 said:**
> hmm, I just created a FAT32 shared partition because I didn't think linux had good support for writing to HFS+, and because the ext driver I was using in OSX (extfsmanager) wouldn't show my already created ubuntu ext3 partition. now osx shows ALL partitions on the desktop (including the EFI??)

so, there is reliable write support for HFS+ filesystems in ubuntu?

I suppose you could call it reliable - I've been using it for a few weeks at least (probably closer to a month), with no problems.  I can easily play my music from the shared partition, access and make changes to documents, transfer stuff over to the shared partition, etc.  After I made the partition I had to go into OS X and change the permissions for "Other" to read/write, instead of read-only.... but yeah, it works just fine for me.

OS X doesn't show my Ubuntu partition, but it shows the shared one.  (Ubuntu, of course, shows all three partitions.)

---

### Post by ronocdh on 2007-06-03
> **Seamyst said:**
> OS X doesn't show my Ubuntu partition, but it shows the shared one.  (Ubuntu, of course, shows all three partitions.)
Do you have [ext2fsx]("http://sourceforge.net/projects/ext2fsx/") installed? Or were you using MacFUSE? I hear the latter's ext3 support isn't great.

---

### Post by Seamyst on 2007-06-03
> **ronocdh said:**
> Do you have [ext2fsx]("http://sourceforge.net/projects/ext2fsx/") installed? Or were you using MacFUSE? I hear the latter's ext3 support isn't great.

Neither.  I'd tried to install the former the last time, but was having some trouble with it - not sure what, at this point, but it wasn't working correctly.

---

### Post by eros82ca on 2007-07-04
Ok, for those of you with iTunes wanting to run on Ubuntu, check out Songbird.  It's still beta right now, but it's much better than anything that I've seen.  Furthermore, you should be able to have a shared music folder in iTunes that would recognize it?

---

