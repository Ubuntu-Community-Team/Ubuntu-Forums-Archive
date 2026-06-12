---
title: "I just want to try it out."
date: 2006-06-09
forum: Apple PPC Users
---

### Post by Blind Buzzard on 2006-06-09
Can anyone assist me with trying out Ubuntu 6.06 on a Mac iBook PowerPC? 

I'm trying to boot up from the disc to take a look but can't seem to get the ISO to boot on startup.

I've tried holding cmd/opt/shift/del on startup but just get the blinking folder.  I've also tried holding down C on startup and it just boots up as normal.

What am I missing here?

I appreciate any assistance, I'm new to Ubuntu.

---

### Post by onehotcutey on 2006-06-09
How did you burn the .iso to the cd?

You need to use a program that will burn a disk from an image.  I use simply burns, because it's free and does the job.  You can get it here:

[http://www.apple.com/downloads/macosx/system_disk_utilities/simplyburns.html](http://www.apple.com/downloads/macosx/system_disk_utilities/simplyburns.html)

This is the first step, and since you already know to hold 'c' down while booting, is probably the cause, however there could be others.

What model and version is your ibook?

---

### Post by aysiu on 2006-06-09
Assuming you have burned it as a disk image, sometimes you have to pick just the right moment to hold down the "C" key.

When I was trying to boot Ubuntu live on my wife's G4 Powerbook, the CD wouldn't boot if I held down the "C" too soon or too late after booting. It was about half a second after pressing the power button.

---

### Post by macheadPDX on 2006-06-10
Try pressing just the Option key on bootup.

---

### Post by Blind Buzzard on 2006-06-12
First off I thank everyone for the quick feedback and assistance.

I have an iBook 12in G4.  (One of the last PPC models to be made.)

To burn my image I used Toast.  It is a fairly simple application, although I have never burned an image from an iso with it.  Let me double check on this.

I tried holding down just the opt key to no resolve.  When I hold down the C key on boot up it goes directly to Tiger.  I have also tired holding down cmd/opt/shift/del on boot up, this gave me the blinking folder, which indicated it was trying to boot from the disc.

Maybe I have a corrupt download of the Ubuntu?

---

### Post by xurios on 2006-06-13
You can easily burn an iso with DiskUtility. Just double-click the .iso from finder so it mounts, then open DiskUtility (in the utilities folder in your Applications folder). Select the .iso from the collumn on the left of the DiskUtility window, and click the burn icon. I have had 100% success with this method of burning various .iso images. You should certainly check your md5sum first though! 

Since OS X does not come with an md5sum utility, you have to go [get one](http://www.microbrew.org/tools/md5sha1sum/). Or you can install the textutils package, which contains an md5sum utility in it, from [fink](http://fink.sourceforge.net/). Either way, it's worth the trouble to have a working md5sum utility on your mac. I like the first option, because you also get sha1sum functionality, wich is not included in textutils. The sha1sum is used by RedHad for checking their .iso files.

---

### Post by Ptero-4 on 2006-06-13
To burn isos in Toast click on the "Copy" tab, then in the drawer select "Image File" and drag the iso WITHOUT mounting it to the desktop.

To burn isos in DiskUtility click on the "Burn" button in the toolbar, then in the dialog that opens navigate to the folder in which you have the iso and click "burn".

And doesn't OSX include the unix cli md5sum util?

---

### Post by je m'ennuie on 2006-06-14
for md5sum, open Terminal, type "md5" , drag your iso to the Terminal window and hit return. A few seconds later, you'll got it.

---

### Post by Blind Buzzard on 2006-06-14
Again - Thanks to everyone for their assistance.

I was able to successfully burn Ubuntu in ISO form last night using the Disk Utility.  (And, I believe I know the mistake I was making in Toast too.)  

The only issue I have now is that when I boot from the newly created ISO on my G4 Laptop is that it attempts to install the OS rather than letting me run from the disk.  (I actually got around this by downloading the ISO for my PC at work and was able to successfully test out the OS their.  And, I have to say that I think I'm going to like it!)

I do have one last question.  I have an older iMac G3, with a 500mhz processor, 256mg ram, and a 20gig hd.  I went ahead and installed the full version of Ubuntu 6.06 ppc desktop on this box, but the speed of the OS is very very slow.  Are the specs on this box not respectible enough to run this operating system?  Or is there an easy way to speed things up?

---

### Post by Ptero-4 on 2006-06-16
Gnome should run fine. I used to have an iBook G3 with a 500mhz CPU, 128MB RAM, 10GB HD and gnome ran o.k. But if gnome is slow in your iMac you can always just install xubuntu-desktop and you'll have xfce ready for you.

---

### Post by linear on 2006-06-16
[quote=Blind Buzzard]but the speed of the OS is very very slow. Are the specs on this box not respectible enough to run this operating system? Or is there an easy way to speed things up?[/quote]
By "very very slow" do you mean so slow as to be unusable? You may need to disable dri. This is done by editing xorg.conf.
 
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. make your edit: in the modules section, put a hash mark (#) at the beginning of the line containing "load dri" (or you could delete the line)
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo killall -HUP gdm (return) to restart Gnome

---

