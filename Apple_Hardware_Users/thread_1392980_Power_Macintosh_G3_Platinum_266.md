---
title: "Power Macintosh G3 Platinum 266"
date: 2010-01-28
forum: Apple Hardware Users
---

### Post by papabill on 2010-01-28
Has anyone been able to set up and run Ubuntu on this setup? I have a Power Macintosh G3 266Mhz, 6Gb HD, floppy, Zip.

Do I stand a chance in making it go??

Thanks

---

### Post by llamabr on 2010-01-28
I'd think about debian, running something very light, like wmaker.  ubuntu no longer supports the ppc architecture, and the issues are going to get worse with such an old machine.

---

### Post by linuxopjemac on 2010-01-29
Is it OldWorld or NewWorld ? If it is OldWorld (which I think it is), you might wanna try the new Karmic Koala installer for this:

[http://oldworldpowermacs.homeip.net/](http://oldworldpowermacs.homeip.net/)

If it is NewWorld, and you definitely need Ubuntu and your normall installer does not recognize your hard disk (heard that with early G3 PowerMacs), you can have a look at the following thread:

[http://mac.linux.be/content/installation-karmic-koala-when-hard-disk-not-recognised-g3-bw](http://mac.linux.be/content/installation-karmic-koala-when-hard-disk-not-recognised-g3-bw)

If you just like to have Linux, Debian is a very good one indeed.

---

### Post by UniverseA7X on 2010-01-29
The Beige G3 is an Oldworld mac.

---

### Post by UniverseA7X on 2010-01-29
You may want to check out the other thread on a similar macintosh.

[http://ubuntuforums.org/showpost.php?p=8726761&postcount=18](http://ubuntuforums.org/showpost.php?p=8726761&postcount=18)

Apparently, the above poster made a custom download with what you may need to install on this machine. Read through it and see if it's for you. Maybe he can confirm?

---

### Post by LtPitt on 2010-01-29
I did it for my Powerbook g3 300mhz 128mb ram and I did achieve a good result, imho :D

Here's how:

I installed mac os 9 on a small partition (1 gb)... You could use a smaller one but I boot into mac os 9 sometimes because I love it and use it as a jukebox with the marvellous [audion]("http://www.panic.com/audion").
Then I installed [bootx]("http://penguinppc.org/historical/benh/BootX_1.2.2.sit") and configured it to boot my ubuntu server ppc cd (get it here: [http://cdimage.ubuntu.com/ports/releases/9.10/release/]("http://cdimage.ubuntu.com/ports/releases/9.10/release/") )

You have to configure BootX this way:

(i do copy'n'paste from [ubuntuforum's guide]("https://help.ubuntu.com/community/Installation/OldWorldMacs"))
unpack it, open the resulting folder and drop it's contents into the System Folder to properly install it. It will configure itself as a startup and Applemenu item.

Insert the ubuntu PPC install disk and navigate to the /install/powerpc folder. Copy vmlinux (the linux kernel) to &#8220;System Folder/Linux Kernels&#8221;. Copy initrd.gz (the init ramdisk image) to &#8220;System Folder&#8221; and rename it to ramdisk.image.gz

BootX should appear on the apple menu, and also run on every reboot. When you run BootX it should have &#8220;Use Ramdisk&#8221; checked and show vmlinux as an available kernel. If this is all in order go ahead and click the &#8220;Linux&#8221; button and in a short while you should be looking at the regular Ubuntu install dialogs.

Partitioning

When it gets to partitioning the drive Ubuntu will suggest using the entire disk for Linux. Don't do that because you still need MacOS to run BootX to boot Linux. Select the &#8220;Use Free Space&#8221; option or partition manually.

WRITE DOWN where's your / (root partition) located.
for me it was hda10.

Go on with your ubuntu install :)

When it's done reboot...
Now you just have to get rid of the "use ramdisk" option in bootx and add the / partition location:
hda10 in my case: did you write down yours? :)

Now your ubuntu should be asking for username and password.
Once you're in you can install anything you like/prefer.

My choice (and I got a pretty fast machine, imho) was:

sudo apt-get install xorg gdm lxde firefox pidgin abiword gnumeric

Have fun and let us know how did it go (or if you need further help)



Final performance tweaks:
If you have a slow disk this could help: [http://ubuntuforums.org/showthread.php?t=692318&highlight=noatime]("http://ubuntuforums.org/showthread.php?t=692318&highlight=noatime")

If you get gabled graphics or bad colors or can't get 24 bit depth:
[http://ubuntuforums.org/showthread.php?t=1208335#6]("http://ubuntuforums.org/showthread.php?t=1208335#6")

---

