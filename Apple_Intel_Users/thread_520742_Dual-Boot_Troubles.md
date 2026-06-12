---
title: "Dual-Boot Troubles"
date: 2007-08-08
forum: Apple Intel Users
---

### Post by Wee_Guy on 2007-08-08
I intend to dual-boot my IiMac with Mac OS X and Ubuntu, the problem is that the partitioner doesn't see the OS X partition, it just sees:

/dev/sda1, size: 200MB format Linux-swap flags: Boot
/dev/sda2 size: 152.35GB format HFS+
unallocated size: 121.34MB


I assume that the HFS+ partition is the one with OS X on it, but i doubt that i've filled all that space with data. Also, will running the partitioner format the drive, or can it partition it without deleting the OS X partition?

EDIT: On the HFS+ partition, it also says "Incorrect magic values in the journal header."

---

### Post by Wee_Guy on 2007-08-08
Anyone?

---

### Post by Tomshaq on 2007-08-08
Hmm.. no experience with partitioning HFS+ in particular, but that partition is the one that OSX is on. It seems to be seeing it fine.
Just because a partition is that big does not mean that it is full.
Think of a partition like a bucket that you fill with water?(data)
You may have a 5 gallon bucket for your water, but only have one gallon of water.
So you could resize this bucket to only being half as big, with a capacity of 2.5 gallons, and take the remaining material and build a different 2.5 gallon bucket that runs linux.

So, in other words, you just need to resize that partition to make room for your linux install. I recommend a gparted live cd. And always, always always back up your data before you screw with the partition tables.

---

### Post by Wee_Guy on 2007-08-08
I've backed up, but will 'resizing the bucket' delete the 'water' that's already in it?

Also, because of the error (Incorrect magic values in the journal header.) i can't partition it from the Ubuntu installer. I suppose that i'll partition it via Disk Utility, so, will partitioning a drive with OS X's Disk Utility delete the data already on it? And if it does, what free ways are there to partition a drive without deleting data already on it?

---

### Post by benanzo on 2007-08-08
The safest way to repartition a Journaled HFS+ disk is with Apple's Disk Utility.  My advice would be to use Disk Utility in OS X to split the HFS+ paritition into two parts.  You can just shrink the part that OS X is currently installed on (which wont delete any data) then partition the second part as Fat32 (while in Disk Utility) then use the Ubuntu partitioner to convert that to EXT3 and install Ubuntu.  That is the least potentially destructive way.

---

### Post by russo.mic on 2007-08-08
I 2nd benzo's motion.

---

### Post by cyberdork33 on 2007-08-08
wait, wait, wait. As far as I know, using disk utility to repartition the drive will WIPE the drive... This is why everyone uses Bootcamp to do this, because it can non-destructively partition (and it actually uses the 'diskutil resizeVolume' command)

Please look around at the various threads, and in the community help as there are several guides explaining the process.
[https://help.ubuntu.com/community/iMacCoreDuo](https://help.ubuntu.com/community/iMacCoreDuo)

I would suggest NOT using any other partitioners to resize the HFS+ partition as this will read to corruption most likely. It is actually likely that you have already created errors by trying to resize it with gparted. boot the osx install dvd and repair the volume, then use bootcamp.

---

### Post by benanzo on 2007-08-08
Resizing HFS+ volumes non-destructively is perfectly safe in Disk Utility since the 10.4.6 update last year.  The difference is that they added the *resizeVolume* verb to the *diskutil* command specifically so Bootcamp could create a Windows partition without hosing OS X.  You don't, however, need to use Bootcamp to do this.  The function is still callable on the CLI with *diskutil resizeVolume ...* or via the GUI application **Disk Utility**.  I've done it many times and never once used Bootcamp.

But as with any tinkering of your disk, take a backup of your important files beforehand.

Good Luck!

---

### Post by cyberdork33 on 2007-08-08
> **benanzo said:**
> Resizing HFS+ volumes non-destructively is perfectly safe in Disk Utility since the 10.4.6 update last year.  The difference is that they added the *resizeVolume* verb to the *diskutil* command specifically so Bootcamp could create a Windows partition without hosing OS X.  You don't, however, need to use Bootcamp to do this.  The function is still callable on the CLI with *diskutil resizeVolume ...* or via the GUI application **Disk Utility**.  I've done it many times and never once used Bootcamp.

But as with any tinkering of your disk, take a backup of your important files beforehand.

Good Luck!

I have seen several methods using the resizeVolume command and using bootcamp, but never anything with disk utility. Can you point in the right direction? This is all new to me.

---

### Post by Wee_Guy on 2007-08-09
In Disk Utility, the only button that isn't faded is 'options', the rest of the buttons and text boxes are faded, locked for editing isn't checked.
If i need to erase it first, i cant do that either, all the buttons there are faded out as well.

---

### Post by russo.mic on 2007-08-09
I'm afraid I've had to disagree with cyberdork and side with benanzo (sorry for the name mispell last post)

I've never had good luck with bootcam or diskutil (which are the same thing, really).  I've 3 or 4 times i've seen it work are when the OS X install is almost BRAND NEW.  I can only guess that it's because diskutil is attempting to move system or swap information that is actively in use by the system.  (yes, yes, I know it's supposed to work, i've just never seen it myself).  

HOWEVER, I have seen the disk utility program work more than a few times WHEN BOOTING UP and running it from the OS X Disc one.  

Of course, always ALWAYS back up your personal data, and it's not as if you can't just restore OS X in a matter of 30 min along with your personal data.

Just my $0.02  Good luck, and remember to post your results for everyone!

Russo

---

### Post by Wee_Guy on 2007-08-09
So you want me to partition it from the Disk Utility on the install disk? I'll try that then.

---

### Post by Wee_Guy on 2007-08-09
I Booted from the install disk, partitioned, booted from backup, restored the OS X partition, so far so good. Only problem is that some icons appeared on my HD which i think are meant to be hidden, so i'll have a look on version tracker/macupdate etc and see what they've got. I haven't got as far as installing Ubuntu, i'll do that later. I'll maybe put a thread up about how i did this so that others can too, but i'll leave that 'til after i get any problems sorted out.

---

### Post by Wee_Guy on 2007-08-09
I tried to install it, but now it tells me that it didn't install GRUB!!! This is what it told me when i tried to install Ubuntu on my external HD, so i gave up and went to install it on the internal HD, assuming that it'd be a lot easier/simpler, and the stupid thing goes and tells me that it cant be bothered installing GRUB for me!!!!!

Why oh why does Ubuntu hate me???!!!

---

### Post by Wee_Guy on 2007-08-09
I told it to install on a 30+ GB partition and install swap on a 500 MB partition, if that helps

---

### Post by Wee_Guy on 2007-08-09
The most annoying part is that it 'tried' to install GRUB *after* installing the rest of the OS, so i had to wait all that time just to find out that it was going to tell me that it couldn't be bothered with the most important part of the whole thing, and make me do the whole thing all over again!

---

### Post by cyberdork33 on 2007-08-09
> **Wee_Guy said:**
> The most annoying part is that it 'tried' to install GRUB *after* installing the rest of the OS, so i had to wait all that time just to find out that it was going to tell me that it couldn't be bothered with the most important part of the whole thing, and make me do the whole thing all over again!

If the system installed, then you do not have to reinstall the whole thing, just install grub. BTW, nobody I know of has had much luck installing to an external drive.
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html)

[quote=Wee_Guy]         I Booted from the install disk, partitioned, booted from backup, restored the OS X partition, so far so good.[/quote]

So, what you are saying is that using Disk Utility did not leave your OSX install intact... so it is not non-destructively partitioning your drive? Am I missing something here? Having a full backup is handy and kind of makes it irrelevant as you could simply restore the image.

---

### Post by Wee_Guy on 2007-08-09
Disk utility via the live CD erased all data on the disk, so i had to restore it from my backup. I'll try the GRUB manual install link you sent, but don't expect any feedback soon, as i have a feeling it will require a lot of twiddling with stuff to get it working, if i get it working.

---

### Post by Wee_Guy on 2007-08-09
I tried to install again, as the link that Cyberdork33 didn't work (no surprise, nothing seems to be working) and it gave me the same error:

We're sorry; the installer crashed. Please file a new bug report at [https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug) (do not attach your details to any existing bug) and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/syslog and /var/log/partman:

Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 166, in ?
    main()
  File "/usr/bin/ubiquity", line 161, in main
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 57, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 305, in run
    self.process_step()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 856, in process_step
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 628, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s\n%s" %
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1404, in ?
    install.run()
  File "/usr/share/ubiquity/install.py", line 385, in run
    self.configure_bootloader()
  File "/usr/share/ubiquity/install.py", line 1163, in configure_bootloader
    raise InstallStepError(
InstallStepError: GrubInstaller failed with code 1

---

### Post by cyberdork33 on 2007-08-09
well this looks similar:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/75010](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/75010)

Which install CD are you using? and what iMac is this?

---

### Post by Wee_Guy on 2007-08-09
Its the 17' 1.(something) Ghz Intel iMac, not the new ones, one of the first Intel ones.

I'm using the Live CD

---

### Post by cyberdork33 on 2007-08-09
> **Wee_Guy said:**
> I'm using the Live CD

Ok one more manual install technique. May give you better error message if it fails. You can get to the grub shell by typing 'grub' at the commandline.
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html)

You might just try the alt CD too.

---

