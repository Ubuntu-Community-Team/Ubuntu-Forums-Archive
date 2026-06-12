---
title: "[SOLVED] Mounting ...and few other issues"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Walc on 2008-01-02
i have some questions for u guys

1/ how can i mount home & some of my vista partitions on desktop for good? - i mean when i do it with right mouse button->mount then its ok till the next reboot, what shall i do to keep em for good on desktop

2/ [http://i16.tinypic.com/819cbih.png](http://i16.tinypic.com/819cbih.png) --> how can i get rid of that awefull red top border of active window? seems like none of the metacity packs r not working

3/ also u see i have 2 panels, top one and bottom 1. Now id like to get rid of the bottom one, but what do i have 2 do first to make all my active processess, windows appear minimized on the top bar instead on the bottom 1

Thx

---

### Post by thelatinist on 2008-01-02
1) You will have to edit fstab to mount your partitions permanently.  See [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

2) You appear to be running emerald to me, not metacity.  You can configure emerald under System > Preferences > Emerald.   Or you can uninstall emerald if you prefer metacity (as I do).

3) You need to add the applets from the bottom panel that you want on the top panel.  Right-click on the panel and choose Add...

---

### Post by Walc on 2008-01-02
thx a lot m8, im gonna try this out now and report back

---

### Post by Walc on 2008-01-02
srry for bumping..

ad.1 - im gonna practice that 2morrow

ad2 - i did remove emerald <sudo aptitude remove emerald> but when tryin to switch window border styles in appearance preferences, its aint workin at all.........

ad.3 which option shall i add to have my currently active/open windows <firefox, msn, etx> on the top panel? like i do now on the bottom 1 <see pic>

edit: 

ad.1:
Mounting partitions with the script
Script assumptions

    *

      /media/ is an acceptable location for the partitions to be mounted
    *

      there are no entries in your /etc/fstab for windows drives already
    *

      the windows drives are currently not mounted.

NOTE:- I've added the last two script assumptions after dealing with a number of problems in IRC with regards to running this script successfully. The problems were invariably caused by entries being in the /etc/fstab file that were already referring to a windows partition/s and often the drive/s were mounted already (usually without the correct permissions for them to be accessible by the user). If you find you are experiencing problems with the script then, backup your current copy of fstab (this step should always be done when editing system files), remove the entries for window drives in your fstab file, then umount the windows drives, then run the script again.
Acquiring the script

The script must be downloaded before it can be used. Type the following lines.

cd
wget [http://media.ubuntu-nl.org/scripts/diskmounter](http://media.ubuntu-nl.org/scripts/diskmounter)

The file diskmounter will now be in the current user's home directory.
Using the script

The script is non-interactive, and usage is simple. Type the following line.

sudo bash diskmounter

This will execute the script with administrative rights.

The script will generate some output, regardless of whether it succeeds or not. Read the output as it will indicate errors and things you should read.
Cleaning up

The script is no longer needed, so type the following line to get rid of it.

rm diskmounter

All partitions on the system should now be accessible.

To verify access, open Gnome's file browser and direct it to /media/, which can be found by clicking 'File System' under 'Places', and then double-clicking 'media'. Double-click any partition to be examined. If it contains files, the modifications were successful. If no files are found, read the next section.

If the script worked for you, don't stop reading yet! Some tips exist at the end of this article in the Hints, Tips, and Technical Information section to help make your Ubuntu experience even more enjoyable. 

ad2. ->its working fine now after rebooting

ad.3 ->its window list

Thx to [color=red][size=3]thelatinist[/color][/size]

---

