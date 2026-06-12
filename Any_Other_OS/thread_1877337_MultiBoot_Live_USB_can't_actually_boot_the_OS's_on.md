---
title: "MultiBoot Live USB can't actually boot the OS's on the flash drive"
date: 2011-11-07
forum: Any Other OS
---

### Post by Mi11z on 2011-11-07
[CENTER]**_MultiBoot Live USB can't actually boot the OS's on the flash drive._**[/CENTER]

Hello, I'm in Mint and well I wanted to have multiple live OS's on my 8GB flash drive that I could plug into any PC and use (going through the boot options of course) and I thought I came across something that could do that seen here:

```
http://liveusb.info/dotclear/index.php?
```

The application installed fine (a tad fiddly maybe). All MultiBoot live appears to have done is copy the extracted distro's/OS's (.iso's) to the flash drive and also created a boot directory.

Now the problem is when I reboot and select boot from USB nothing happens, it doesn't load to a boot menu (like it would if I say used uNETbootin) I was expecting to see Multiboot USB's version of Grub2 with a choice of the two distro's/OS's that were copied to the flash drive.

OK any help or an alternative method in which I can boot multiple OS's (live distro's) from USB would be appreciated, I'll upload screenshots if needed.

Please Reply ASAP!

- regards

- Mi11z.

---

### Post by Perfect Storm on 2011-11-08
Moved to Other OS/Distro Talk.

---

### Post by Mi11z on 2011-11-08
> **Artificial Intelligence said:**
> Moved to Other OS/Distro Talk.

Cheers, A wise decision. :)

---

### Post by oldfred on 2011-11-08
I created several flash drives manually before I found some of the scripts that automate the process.

Post this with flash drive plugged in to see if grub2 was installed correctly.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Manual way which may help in understanding how it is done.
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by Mi11z on 2011-11-08
Well, thank you a wonderful detailed reply there, I think you've covered everything I may need. I'll get back to you, I've also just read about YUMI for windows but your right I'd also like to learn more about the process.

I'd also somehow like to get the new chromeOS on there ([http://chromeos.hexxeh.net/](http://chromeos.hexxeh.net/)) too it's a .img file I've tried to load it on the USB with Multiboot USB but when I tried it, I got an error that said I had specify the file system type. so =/ lol why can't it just be easy. :D

---

### Post by Mi11z on 2011-11-08
OK well funny turn of events.

When using MultiBoot I thought I would use the built in QEMU and then actually load one of the copied/installed distros/.iso's and it worked for both Toorox and Crunchbang I let them load as far as possible (up to the point where it loaded graphics, xorg xserver etc. and obviously it failed there because QEMU isn't designed to handle graphics which is fair enough) so I then quit QEMU in the safest way possible, rebooted, selected boot USB device and hey presto Multiboot's version of Grub2 loaded through I then selected Toorox, I later tried Crunchbang and both loaded without fail as they normally would from a live USB or CD.

So my only problem now is that I'm trying to get ChromeOS (.img downloaded from the link mentioned above) on the flash drive hopefully in the same way, could I please have some help with that please?

---

### Post by oldfred on 2011-11-08
I have not seen a Chrome boot stanza. Each ISO must be designed to be bootable and not all are. Is Chrome directly bootable?

Some of the scripts extract the kernel & init files and boot those then load the rest of the files. I know that was what I had to do to get Puppy to work.

---

### Post by Mi11z on 2011-11-09
> **oldfred said:**
> I have not seen a Chrome boot stanza. Each ISO must be designed to be bootable and not all are. Is Chrome directly bootable?

Some of the scripts extract the kernel & init files and boot those then load the rest of the files. I know that was what I had to do to get Puppy to work.

Ok so how would I go about doing that with ChromeOS? and do you know of any other downloads for it perhaps in .iso form? =/

---

