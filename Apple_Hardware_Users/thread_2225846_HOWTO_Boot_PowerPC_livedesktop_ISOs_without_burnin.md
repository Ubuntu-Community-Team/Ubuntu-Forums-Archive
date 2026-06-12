---
title: "HOWTO: Boot PowerPC live/desktop ISOs without burning a CD"
date: 2014-05-23
forum: Apple Hardware Users
---

### Post by rsavage on 2014-05-23
So you don't want to waste a CD/DVD, but so far you can't figure out how to boot from USB.....

If you have an external USB hard/flash drive that cannot be seen from openfirmware....

Well, if you have Mac OS X installed then the solution it is pretty simple.  This is what to do: 

1.  Download the iso and save it somewhere on a regular [COLOR=#333333][FONT=Ubuntu]ntfs/fat/vfat/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]ext2/ext3/ext4 formatted USB drive.  The important part is that it should not be hfs+ formatted because it won't work.
[/FONT][/COLOR]
2.  Create a new folder somewhere on your Mac OS X install.  For ease it is best to place it on the root of the partition and call it 'casper'.  Btw, this time it should be a hfs/hfs+ partition.

3.  Mount the iso.  In MAC OS X Panther I 'right click', select 'Open With >' and choose 'DiskImageMounter'.

4.  You'll see the iso also has a folder called casper.  Contained in there are two further folders 'powerpc' and 'powerpc64'.  If you have a G3/G4 then copy the powerpc folder to the new casper folder.  If you have a G5 then copy the powerpc64 folder.

5.  On the root of the iso there is an 'install' folder.  In there are the files 'yaboot' and 'yaboot.conf'.  Copy both of these to your new casper folder.

6.  So you should now have a casper folder with powerpc/powerpc64, yaboot and yaboot.conf.  All that is left to do now is make a note of the partition number.

7.  Reboot into openfirmware.  When you hear the startup chimes hold down the four keys: command + option/alt + o + f and keep them pressed until you see the openfirmware prompt.

8.  Type (replace 3 with your partition number, and 'hd' with something else if you've not installed it to the first hard drive):

```

boot hd:3,\casper\yaboot

```

9.  Yaboot should load.  It will complain about the partition type which is a bit off putting.  Press TAB to get your options.

10.  Type your option and use the boot parameter [COLOR=#000000]iso-scan/filename=ubuntu-desktop.iso (changing the name and adding any folder paths as necessary)
[/COLOR]
e.g.

```

live [COLOR=#000000]iso-scan/filename=/downloads/ubuntu-desktop.iso
[/COLOR]
```

Note: You can add this parameter to your yaboot.conf file if your prefer.  

11.  The system will boot and your drives will be automatically scanned to find the iso file.  You should see the desktop.

---

### Post by cyberjr on 2014-06-04
I followed your instructions and they worked for me. I used Ubuntu 12 tho.
So finally it worked and got installed and after i tried to update(over 600 updates ô_Ô) my updater told me to restart the system.

After it restarted i got the login screen and at the top next to my clock i have 2 white file icons with a red cross in the middle.
When i log in i get a couple of errors and i only get a titlebar saying Ubuntu Desktop and the hour, a black screen and at the right side of the screen a blue bar as if it's an empty launch bar.

When i report the error i get another one that says The application Metacity has closed unexpectedly
Another error says that the previous problem report was damaged and could not be processed    ```
TypeError(Error('Incorrect padding',),)
```

After i relaunch it repeats itself.

---

### Post by rsavage on 2014-06-04
Without wishing to state the obvious, it sounds like something screwed up in the update process.  Did you upgrade to 14.04 as part of the update process (if that is possible on PPC)?  I don't run normal *ubuntu, so I don't know if everything is working at the mo in 12.04.  All I can suggest is to look at the graphics issues listed on the PPC known issues page.

For what it's worth I recently installed Lubuntu 12.04 (as part of some testing I was doing) and updated without problems.

---

### Post by cyberjr on 2014-06-04
So how do i boot it now, i can't create a folder or place an iso on my hard drive.
I did manage to get into the configuration center but found nothing to repair it.
I have a netbook with lubuntu 14.04 and a usb sandisk 4gb to use since the dvd isn't an option.

Any tips are welcome

---

### Post by rsavage on 2014-06-05
Boot to a command line - [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_into_single_user_mode.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_into_single_user_mode.3F)

Install Lubuntu

```

sudo apt-get install lubuntu-desktop

```

Start the login manager

```

sudo start lightdm

```

Choose Lubuntu before you log in (click on the cog type symbol)

Remove ubuntu - [http://www.psychocats.net/ubuntu/purelubuntuprecise](http://www.psychocats.net/ubuntu/purelubuntuprecise)

---

### Post by cyberjr on 2014-06-05
After i booted up this morning it gave me a partial updater all of the sudden, (didn't happen the countless times before)
then for no reason everything booted up.

I'm very new to ubuntu and got it running at 12.04 fully updated now without a clue how :D but it works.
I also installed the lubuntu desktop but i wonder if i could keep both and what the effect of this would be on my system will it affect speed so much?
I just like to check it all out before i discard something.

Thanks again for the guide it's the only one that worked for my situation and for the help afterwards.

---

