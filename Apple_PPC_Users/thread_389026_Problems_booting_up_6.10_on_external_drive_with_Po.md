---
title: "Problems booting up 6.10 on external drive with PowerBook G4"
date: 2007-03-20
forum: Apple PPC Users
---

### Post by Bellefonte6718 on 2007-03-20
Hey everyone. After loitering around the forums for a long time and wanting to jump to Ubuntu, I'm finally giving it a shot.

I have a 12" PowerBook G4 800 MHZ with 768 RAM. The internal optical drive is out of commission (the only lasting problem from falling out of my backpack and onto the pavement!!)

I partitioned the HD and put the 6.10 install CD into my external drive. It shows up on the desktop when in Mac OS X, but when I try to restart and hold C to boot up from the disc, it just goes to Mac OS X. Holding option during boot brings up a choice between OS X and Ubuntu, but clicking Ubuntu option doesn't do anything at all (just reloads the page).

How do I boot the install disc from an external drive? Am I missing something obvious? Thanks for any help with what will be the first of MANY questions, I'm sure.

---

### Post by grazie on 2007-03-20
I can't help you with the booting of your externel cdrom at the moment, but if this is your only option I may be able to dig around a bit, unless others can provide you with a solution. However you do have at least 1 other option. I've successfully installed Linux doing a netboot from Open Firmware. Unfortunately, I've only managed to do it with complete success on Debian. From the completed Debian minimal install you can then install Ubuntu or whatever else takes your fancy. I think part of the reason some kernels don't work is due to a limiitation of yaboot and the maximum size of initrd.img that can be handled. There's a bug report in Launchpad IIRC. If you've got another machine and you can set it up as an install server it's an option worth thinking about.

Edit
It is not possible to netboot standard kernels, so a netboot enabled kernel is always required.

---

### Post by Bellefonte6718 on 2007-03-20
Thanks for the response, Grazie. Hmm, I'll see if there are any other suggestions first. That whole idea of an install server and netboot might be too much for my noob self.

---

### Post by ditsch on 2007-03-20
You could try pressing Command-Option-Shift-Delete instead of C at boot time.

---

### Post by Bellefonte6718 on 2007-03-20
I'll try that recommendation when I have a chance tomorrow morning, ditsch. (heading out to a Hold Steady concert in just a couple of minutes :guitar: <-- I normally hate emoticons, but that one just fit so well) 

I tried another option I thought of... I put the install disc into an iMac I have and booted the PowerBook into Firewire target disk mode and hooked it up to the iMac. Then, I booted the iMac with the install disc. Ubuntu recognized the drive and got 94% of the way to completing the installation on the Powerbook before the installer crashed saying it wasn't able to install yaboot on the target disk. Any ideas what that is about? Thanks so much for the help!

---

### Post by pxwpxw on 2007-03-21
> **Bellefonte6718 said:**
> 
I tried another option I thought of... I put the install disc into an iMac I have and booted the PowerBook into Firewire target disk mode and hooked it up to the iMac. Then, I booted the iMac with the install disc. Ubuntu recognized the drive and got 94% of the way to completing the installation on the Powerbook before the installer crashed saying it wasn't able to install yaboot on the target disk. Any ideas what that is about? Thanks so much for the help!


The mac firewire target disk is a good feature if you can use it here.
I have used it (for an ibook and a powermac with linux and macosx on both)
for debugging my self-inflicted problems.

But for the yaboot install you need to have created a NewWorld (Apple_Bootstrap) partition on the target powerbook drive.

You probably need to be using the Alternative install CD (not the desktop), the Expert option, and normally configure the bootstrap partition durng the partitioning stage.
It might be possible to fix it without reinstalling by just running rescue mode, but you will still have to select a boot partition for yaboot.

Would need to see a posting of the Powerbook drive partitions (macosx and linux) before commenting further. Macosx tends to leave some small free partitons between apple partitions, sometimes can be usable for yaboot booting, see example below.

You can get good partition info from Macosx by opening a terminal and using
pdisk in superuser mode, thus:

```

mac03:/Users/max$ sudo pdisk   

Top level command (? for help): L

Partition map (with 512 byte blocks) on '/dev/rdisk1'
 #:                type name                    length   base      ( size )
 1: Apple_partition_map Apple                       63 @ 1        
 2:     Apple_Bootstrap ubootsda                262144 @ 64        (128.0M)
 3:           Apple_HFS Apple_HFS_Untitled_1  25126936 @ 262208    ( 12.0G)
 4:     Apple_UNIX_SVR2 dbroot                39062501 @ 25389144  ( 18.6G)
 5:     Apple_UNIX_SVR2 swap                   5859376 @ 64451645  (  2.8G)
 6:     Apple_UNIX_SVR2 uspare                19531251 @ 70311021  (  9.3G)
 7:     Apple_UNIX_SVR2 uxroot2               39062501 @ 89842272  ( 18.6G)
 8:     Apple_UNIX_SVR2 uspare2               27396715 @ 128904773 ( 13.1G)

Device block size=512, Number of Blocks=156301488 (74.5G)
DeviceType=0x0, DeviceId=0x0

Top level command (? for help): q
mac03:/Users/max$

```

It would probably be just as easy to download Netinstall images from 
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-powerpc/current//images/powerpc/netboot/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-powerpc/current//images/powerpc/netboot/)

 - see the Ubuntu installation guide:
> 
4. Obtaining System Installation Media
    4.2. Downloading Files from Ubuntu Mirrors

(these are just kernel images and yaboot, small download)


Either way, you have to be prepared for a bit of adjustment of the boot files and using open firmware to manually boot initially, until you have it tidy.

But its a good thing to be able to use open firmware to sort out booting problems in general, and not diffficult.

---

### Post by grazie on 2007-03-21
pxw,

That's a really useful post. However, I've not successfully managed to netboot the Ubuntu kernel. I get the following

> Transfer FILE: /install/netboot-initrd.gz method 'load' failed 00000300
ramdisk loadfailed !

I believed this to be to a limitation of yaboot and the maximum size of ramdisk that can be handled. I'm sure there's a Launchpad bug report on this, but I can't seem to find it at the moment. If you can boot the Ubuntu netboot kernel I'd really appreciate you stating how you managed it.

---

### Post by pxwpxw on 2007-03-21
> **grazie said:**
> 
 If you can boot the Ubuntu netboot kernel I'd really appreciate you stating how you managed it.

grazie

I haven't tried a pure network-boot as for a diskless computer.

My post above was referring to a network-install of packages via tcp/ip, done after loading installer files = (yaboot yaboot.conf, vmlinux and initrd.img) from the local file system,  which might include a firewire connected 2nd mac or external firewire drive. 

Your error message looks to be netboot specific, but I could suggest looking at path information and the location and configuration info in the yaboot.conf file and/or any network specific configuration files. Don't know about ramdisk size limitations, never encountered that problem.

I have been able to boot netinstall kernel images from an external firewire drive partition, and continue on to do a network install on the external drive. The simplest configuration was to put all install kernel files in the root of a small boot partition on the external drive, as descrbed in the ubuntu or debian install manual for a usb flash drive or for hard disk install images, and edit the installers yaboot.conf to suit. I would have to look at that again if you think it would help with your issue.

Edit:

Some confusion here between netboot, netinstall, and debian netinstal and buisness card cd's. Hope the general idea got through. Seems I have been downloading  so-called netboot images and using them in a hard drive boot to do a network install, if that helps. Have a few thhgs
I want to re-run  to  clarify.

---

### Post by Bellefonte6718 on 2007-03-21
pxwpxw, my drive is set up like this now:

[FONT="Courier New"]```
Partition map (with 512 byte blocks) on '/dev/rdisk4'
 #:                type name        length   base      ( size )
 1: Apple_partition_map Apple           63 @ 1        
 2:     Apple_Bootstrap untitled      1954 @ 71933531 
 3:           Apple_HFS disk5s2   71924478 @ 9053      ( 34.3G)
 4:     Apple_UNIX_SVR2 untitled  43363282 @ 71935485  ( 20.7G)
 5:     Apple_UNIX_SVR2 swap       1911473 @ 115298767 (933.3M)
 6:          Apple_Free Extra         8989 @ 64        (  4.4M)

Device block size=512, Number of Blocks=117210240 (55.9G)
DeviceType=0x0, DeviceId=0x0
```[/FONT]

Hope this helps clarify!

---

### Post by pxwpxw on 2007-03-21
> **Bellefonte6718 said:**
> pxwpxw, my drive is set up like this now:

[FONT="Courier New"]```
Partition map (with 512 byte blocks) on '/dev/rdisk4'
 #:                type name        length   base      ( size )
 1: Apple_partition_map Apple           63 @ 1        
 2:     Apple_Bootstrap untitled      1954 @ 71933531 
 3:           Apple_HFS disk5s2   71924478 @ 9053      ( 34.3G)
 4:     Apple_UNIX_SVR2 untitled  43363282 @ 71935485  ( 20.7G)
 5:     Apple_UNIX_SVR2 swap       1911473 @ 115298767 (933.3M)
 6:          Apple_Free Extra         8989 @ 64        (  4.4M)

Device block size=512, Number of Blocks=117210240 (55.9G)
DeviceType=0x0, DeviceId=0x0
```[/FONT]

Hope this helps clarify!


That looks good. 

Are you using the Alternate CD? The Desktop CD might be a bit difficult for this sort of stuff.

Partition 2  Apple_Bootstrap untitled      1954 @ 71933531

is the one normally created and used by the installer.
 
Two possible reasons for the yaboot install step failure (probably more but 2 will do for now)
I am assuming that your powerbook/imac system behaves much like my 
ibookG4/powermacG5 here. 

1. The bootstrap partition did not get formatted as macos standard (linux hfs) during partitioning, and the later yaboot install stage requires that.

2. I think more likely it was formatted correctly, but the yaboot installer stage cant find it, because of the unusual configuration.

Probably your install is all complete except for the bootstrap files (unless it was aborted). Also would mean that reinstalling will just do the same thing, because the installer for yaboot (mkofboot) is not very clever at getting the open-firmware paths it needs to install yaboot, and I don't think there is any way you can give it this info in the course of a normal installation.

Should be possible to fix. The aim is to get an initial stand-alone linux system running on the powerbook, so that any initial path difficulties due to the firewire conection will be eliminated from your final system.

Maybe on these lines:

1. Use the imac to run the install cd in rescue mode (dont install or partition anything) with the powerbook in firewire target mode and hopefully that will enable access to your powerbook linux root partition 4 (probably /dev/hda4 as seen by linux) and the bootstrap partition (dev/hda2). The rescue mode should be able to mount both of them if it was able to complete the install except for yaboot. 

You could try that to see what you have there (i.e. something or nothing), without actually changing anything at this stage.

If you can mount the powerbook ubuntu root partition, check the names of /boot directory links (usually named vmlinux and initrd.img) pointing to the kernel images - this info is needed for manual booting using yaboot.

2. Next step would be to try using the rescue cd to manually run the ybin installer program for yaboot, but giving it directions to the target bootstrap partition.
Would need some reading of manual to be sussessful

3. It might be easier to boot linux using only yaboot and a yaboot.conf file in your bootstrap partition, and booting from openfirmware. You can download  yaboot and edit yaboot.conf in macosx and copy them to the bootstrap partition using terminal.

But do step 1 to see what happened. Lets hear how you go with that.

---

### Post by Bellefonte6718 on 2007-03-25
pxwpxw,

Thanks for the help. Sorry it's taken me a few days to get back. Sort of busy right now.

I had some time this morning to try a few things. First, I tried the original install disc. No luck, but wasn't expecting that to work. Was just wasting time while I grabbed the .iso for the alternate disc. Reformatted the HD in the powerbook and tried installing from the alternate. Same problem with the yaboot.

So, I booted into rescue mode and tried to access the linux root partition. None of the /dev/hda drives (including /dev/hda4 and /dev/hda2)would allow any access. It would say, "An error occurred while mounting tho device you entered for your root file system (/dev/hda4) on /target. The only drive that I could access was /dev/sda1, but I'm pretty sure that had nothing to do with the Powerbook but was my thumb drive attached, so I let it be.

Then I went into the partition tool and was able to change various settings for the different partitions, but wasn't exactly sure what I wanted. (settings like: "name," "type," "bootable" etc...). Is this a useful area?

As for copying the yaboot files over using the terminal, two quick questions... 1) Do I only need the yaboot and yaboot.conf files? 2) How do I access the bootstrap partition in the terminal? When I go to /Volumes I only see the Mac HFS+ partition of that HD listed.

Thanks for any help. No rush to respond.

---

### Post by pxwpxw on 2007-03-27
Bellefonte6718

Please pause and reflect.  The method you are using is strictly for masochists. :confused: 

Just for the record here, the situation is:
Using the imac to run the install CD, the target for installation is the powermac with no usable cd drive. The connection is firewire, powermac is target mode.

Having tried several options I can say:

With the firewire configuration, the Imac is at risk if you try any more experiments, and it will just repeat the same prbolem, as you have found. External drives of any kind or changes to drive configuration can create great confusion during installation, particularly if changed.

The installer yaboot stage does not support installing to an external firewire disk, and does not offer options. Similarly, the CD rescue mode menu, showing the partition list, shows only local host (imac) drives and it is not easy to add external drives.  Normally, the rescue mode mounts a local partiton, and then goes to the next rescue menu offering choice of rescue actions. If it cannot mount a partition, it will not continue to that menu. Various solutions are possible, but if everything is running on the same host there is no problem.  

You could probably mount the powerbook root partition manually to see what if anything is there.  There is no point in detailing further options in that direction without that information. 

However, a new install would take around 1 hour or less for the basics, and must be done from the powerbook alone to avoid the problem of the installer using external filesysem paths. This can be done, but only by booting from Open Firmware.

If you would like to try it, here is what I suggest:

1. Disconnect the imac from the powerbook. Check the imac partitoning in macosx using Disk Utility to confirm all OK. 

2. At the powerbook:
(I assume you have macosx installed on the powerbook as shown in the partition  map above.)

2.1 Remove all external drives.
 From macosx on the powerbook, run pdisk in terminal again as before.
**Post the result**
Also check it using Disk Utility.

2.2 Get into Open Firmware by restarting with the 4 keys 
                Command Option O F
held down. Opens to a white screen.

Do this:
```
 
0> printenv boot-device
0> devalias hd
0> devalias first-boot

```
Very carefully note the results of each (or take a picture, but maake sure you can read the fine print).
**Post the result**
This info is needed to ensure the open firmware boot will go.

Then exit open firmware by power off (this is on ibookg4) or
```

0> shut-down 

``` 
When it gets to booting from O/F, all it will need is something like:
```

0> boot hd:2,\yaboot

```
Where macosx is at partition 2. Note that the installer may change partition numbers to list the Bootstrap first.

Once the installation is complete, the boot menu will be available automatically.

Installer files needed  are:

yaboot, yaboot.conf, vmlinux, initrd.gz, from the ubuntu 610 installer images Netboot link below, and optionally the iso image you downloaded for the installer CD , these will go on the Macosx partition. Details later.

yaboot.conf may need some editing for your preferences if you are using the iso image.

The yaboot.conf as downloaded will give you a rescue or an install with options for desktop selection, using only net install down loads. 

A trial run used download of about 80MB for rescue, or around 200MB for a minimal install - no desktop, but that can be added later, the xubuntu I am using now was done that way, all using Open Firmware to boot the rescue/install images on the Macosx partition.

You dont have to use the iso image of the cd, the whole  thing can be done using a net-install downloading from ubuntu mirror. (the iso just makes it faster).

> 
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-powerpc/current/images/powerpc/netboot/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-powerpc/current/images/powerpc/netboot/)
- see the Ubuntu installation guide:
4. Obtaining System Installation Media
4.2. Downloading Files from Ubuntu Mirrors


rev 30march2007-for further revision

---

### Post by mianwright on 2007-03-27
Just wanted to say that I am reading this thread with extreme interest. I too have an iBook (ppc G3) with a disabled optical drive. I can't wait to see what happens. Thanks a lot for your hard work.

---

### Post by Bellefonte6718 on 2007-03-30
pxwpxw,

I appreciate all of your help. I'll give this a shot when a have a free hour this weekend. Work's been a little too crazy for my liking recently.

Oh, and I made a complete, bootable backup of my iMac HD to an external drive using Carbon Copy Cloner before embarking on this. I also back up my Documents folder daily, so I'm not worried about the iMac, but thanks for the words of caution! Just to be sure, I followed your advice I ran Diskwarrior 4 and Disk Utility and everything checked out.

mianwright,

Hope it's useful for you. Even if I never quite get it working, (more likely, "if I give up before I get it working") hopefully it gets you started on the right path!

---

### Post by pxwpxw on 2007-03-30
Have added some revision. The easiest way to give it a try, is to just run a dummy rescue using only net downloads, first the files to be placed on your Macosx partition, then after booting from Open Firmware, the rescue package downloads components from a mirror. The net connection is essential.

The only real hurdle to overcome is booting from open firmware, which is easy once you try it.

Comments or questions welcome.

---

### Post by pxwpxw on 2007-03-31
Completely revised and simplified draft howto is on:
   	
**Install/rescue with no cd drive - O/F booting** 

**[http://www.ubuntuforums.org/showthread.php?t=390770](http://www.ubuntuforums.org/showthread.php?t=390770)**

Please use that for comments on the draft, it might attract some interest from others
with the  CD problem.

---

