---
title: "how to fix the iBook wake problem?"
date: 2004-10-27
forum: Apple PPC Users
---

### Post by diabolo on 2004-10-27
My iBook suffers from the wake problem; that is, whenever it wakes from sleep the system freezes and is unrecoverable. There's a bug report for it:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=1940](https://bugzilla.ubuntu.com/show_bug.cgi?id=1940)

On the bugzilla webpage it looks like there's a simple script to fix the problem, I'm wondering if it's possible to use this script and if so where should it be installed?

---

### Post by grover on 2004-10-29
Here's what I did.  I hope this is helpful for someone:

(1)  Created the file /etc/apm/scripts.d/dbus-1:

#!/bin/sh
# hald prevents proper resume after sleep-wake cycle
# stopping dbus at suspend and restarting at resume
# fixes this

INIT="/etc/init.d/dbus-1"
[ -x "${INIT}" ] || exit 0

case "${1},${2}" in
(suspend,*)
[INDENT]"${INIT}" stop
echo "stopped dbus-1"
;;[/INDENT]
(resume,suspend)
[INDENT]"${INIT}" start
echo "started dbus-1"
;;[/INDENT]
esac

exit 0


(2) Made the new file executable:  
sudo chmod 755 /etc/apm/scripts.d/dbus-1


(3) Created a symlink from /etc/apm/suspend.d/98dbus-1 to /etc/apm/scripts.d/dbus-1:
cd /etc/apm/suspend.d/
sudo ln -s /etc/apm/scripts.d/dbus-1 98dbus-1


(4) Created a symlink from /etc/apm/resume.d/01dbus-1 to /etc/apm/scripts.d/dbus-1:
cd /etc/apm/resume.d/
sudo ln -s /etc/apm/scripts.d/dbus-1 01dbus-1


My iBook is an 800 MHz G3 dual-USB model, and sleep/wake works reliably with these changes.  If your system is similar, then this may work for you.  I don't think this will help with newer (G4) iBooks; I think they have a different problem.


I think the patch posted on the bugzilla page ([https://bugzilla.ubuntu.com/show_bug.cgi?id=1940](https://bugzilla.ubuntu.com/show_bug.cgi?id=1940)) does more or less the same thing as my work-around.

---

### Post by diabolo on 2004-10-30
Thank you for posting that, grover. =D>

---

### Post by SyL on 2004-11-01
I confirm that no work on powerbook g4 12"
   
   
   ](*,)[url="http://www.ubuntuforums.org/images/smilies/eusa_wall.gif"]
  [/url]

---

### Post by spoetnik on 2005-02-07
I confirm that it works on my powerbook g4 12"

SORRY, I made a mistake. It works on my iBook G3 12"

:)

---

### Post by grover on 2005-02-07
I thought I read somewhere that G4 suspend/resume support only got added to the kernel recently, with 2.6.10.  Do you mind telling what kernel you're running?

---

### Post by Castaa on 2005-02-08
linux.debian.ports.powerpc has a lot of info on this subject:
  
  [http://groups-beta.google.com/group/linux.debian.ports.powerpc]("http://groups-beta.google.com/group/linux.debian.ports.powerpc")
  
  
  All though don't post to the Usenet forum directly because it probably won't get a reply.
 You need to subscribe to the mailing list to ask questions that will get an answer. A copy of the mailing list is put into this Usenet forum.
  
  [http://lists.debian.org/debian-powerpc/]("http://lists.debian.org/debian-powerpc/")

---

### Post by stereo on 2005-02-08
i'm a owner of an g3-800 too.

thank you.  very nice, so I don't have to kill hald before sending the ibook into sleep.

---

### Post by robsta on 2005-02-10
Thanks very much grover!
It works flawlessly on my g3/600 (Hoary).
- Rob

---

### Post by bob_h on 2005-03-25
Thanks - working on G3 800 dual USB iBook

Bob

---

### Post by zojas on 2005-05-22
this almost worked for me... my 700MHz g3 ibook resumed, but X was dead, and it wouldn't let me log in to the text console, it was trying to respawn gdm too fast. so I still can't suspend.

---

### Post by Rinnan on 2005-06-20
This did not work at all on my 700Mhz G3 iBook.  Out of ideas of what to try now...

---

### Post by TheRitz on 2005-06-29
G3 800Mhz over here with no luck after making the changes Grover suggested. How unfortunate. I installed Ubuntu yesterday because I wanted to try out Linux for a change (used OS X for the past 2 years). It's a bit of a cold shower for me  :-#  but I'll keep hacking at this one for a while. However, I am a newbie when it comes to Linux. So be gentle....

---

### Post by zojas on 2005-06-29
this seems to me to be an issue with dbus. the reason I say that is because I've had both ubuntu and gentoo linux on my ibook. I've had gentoo on my ibook literally for years. I had never seen this problem before on gentoo, until one day I decided to try kde 3.4. this problem came up!

then I installed ubuntu and had this issue too.

turns out that kde 3.4 uses dbus, and ubuntu is set up to use dbus. so if there were a way to completely disable dbus in ubuntu, I bet the wake problem wouldn't show up.

in gentoo, when I'm not running kde 3.4, the ibook will suspend and resume just as fast as it does when booted in OS X!

---

### Post by styrke on 2005-07-05
Yes, the /etc/apm/scripts.d/dbus-1 trick used to work for me up until recently. Turns out that my X session also starts a dbus-daemon of its own. Killing that one too makes my system (iBook G3) suspend and resume nicely.  :grin:  So it's definitely related to dbus.

Now the question is: what is dbus-daemon used for?

---

### Post by mattcam on 2005-09-20
Can someone give me a step by step on how to apply the 
patch  on the bugzilla page ??([https://bugzilla.ubuntu.com/show_bug.cgi?id=1940](https://bugzilla.ubuntu.com/show_bug.cgi?id=1940))
I download it this way:
I right-clicked on 'Fix ibook wake up problem 'under the word Attachment and i
'save target as'...How i have a file on my desktop PC called
(pbbuttonsd-0[1].6.2_ibook-suspend.patch).
What do i do now??
thanks
Matt

---

### Post by cubox on 2005-09-22
It work with my iBook G4 new world

---

### Post by TuckWat on 2005-10-12
I'm running breezy on an iBook g3... how do I install the script?  And I read somewhere that "/etc/apm/scripts.d/dbus-1" must be changed to "/etc/apm/scripts.d/dbus".. is this true?

---

### Post by grover on 2005-10-13
The instructions are in post #2 of this thread.  Just follow them, but change every instance of "dbus-1" to "dbus" (the initscript changed names between hoary and breezy).

Even better than this, the cause of this bug was identified, and there is a kernel patch which fixes this problem (and makes this scripting hack unnecessary).  You can read about it and get the patch here:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=1940](http://bugzilla.ubuntu.com/show_bug.cgi?id=1940)
You will need to patch and compile a kernel, but this is a fix, not simply a work-around.

Or you could wait patiently for the fix to make in into an Ubuntu kernel.

---

### Post by TuckWat on 2005-10-13
Thanks Grover... I tried it the first time using dbus-1 and it did not work, second time with dbus and it still had problems so I deleted the dbus-1 files from script.d, suspend.d, and resume.d and restarted the process and it worked correctly.  Thanks guys!

Now I just need to get java 1.5 working!

---

### Post by mbits on 2005-12-23
An alternative (albeit lazier) solution to building the kernel yourself is downloading a kernel from the following web-site that has already been optimised and built for Macs...

[http://www.ppckernel.org/kernel.php?id=74](http://www.ppckernel.org/kernel.php?id=74)

follow the install instructions on the site and change your yaboot file accordingly (don't forget to run ybin -v) so it boots the new kernel - and sleep will be working. I run an ibook 700Mhz and sleep was working fine after I did this. If anyone is aware of any lost functionality with using these kernels please let me know.

---

### Post by grover on 2005-12-25
[QUOTE=grover]The instructions are in post #2 of this thread.  Just follow them, but change every instance of "dbus-1" to "dbus" (the initscript changed names between hoary and breezy).

Even better than this, the cause of this bug was identified, and there is a kernel patch which fixes this problem (and makes this scripting hack unnecessary).  You can read about it and get the patch here:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=1940](http://bugzilla.ubuntu.com/show_bug.cgi?id=1940)
You will need to patch and compile a kernel, but this is a fix, not simply a work-around.

Or you could wait patiently for the fix to make in into an Ubuntu kernel.[/QUOTE]
There may be some people interested interested in the fix I mentioned, which requires patching & compiling a kernel, but who have never patched and compiled a kernel.  These instructions are intended for people who want to do this, but aren't really sure how.  It's really not hard to do, just a bit time consuming (compiling a kernel on a low powered laptop will take a bit of time).  If you do it right there's zero chance of messing up your system, so worry about trying it.

The wiki page at [https://wiki.ubuntu.com/KernelByHandHowto](https://wiki.ubuntu.com/KernelByHandHowto) has instructions on how to compile a kernel and install manually.   This list adapts those instructions for the powerpc, and also shows how to patch the kernel.  I've tried to remember to include all the steps you need to go through, but it's possible I've forgotten something.  If you try these instructions and get stuck, or if you've done this before and notice that I left something out, please post back to this thread for clarification/correction.

Before you get started, make sure you have enough free space in the root (/) partition of your hard drive.  You will need about 300 MB of free space.

1. Make sure you've installed all the packages you need for compiling:

	sudo apt-get install build-essential gcc-3.4

2. Install the kernel source code package:

	sudo apt-get install linux-source-2.6.12

The linux-source package will place a compressed and tarred file in /usr/src/ named "linux-source-2.6.12.tar.bz2".  This is assuming you're running "breezy" (ubuntu 5.10).  If you're running an earlier release (hoary, warty) you can try installing the "linux-source" package (leave off the kernel version number).  NOTE:  I'm not sure if the patch (see step 5, below) applies cleanly to older kernels, since I haven't tried it.

3. Get and save the patch that you will be applying later on in this process.  Copy and paste the text below into the text editor that you normally use (if you don't have a favorite editor and you use the gnome desktop you might try "gedit", or if you use KDE try "kate").  Save the file out of your text editor.  It doesn't really matter what you name it or where you save it, so long as you remember both.  I call the patch "ide-wakeup-fix.diff" and saved it in my home directory under /home/grover/downloads/kernel/

```

Index: linux-work/drivers/ide/ide-io.c
===================================================================
--- linux-work.orig/drivers/ide/ide-io.c        2005-09-22 14:06:31.000000000 +1000+++ linux-work/drivers/ide/ide-io.c     2005-10-06 10:49:53.000000000 +1000
@@ -1101,6 +1101,7 @@
        ide_hwif_t      *hwif;
        struct request  *rq;
        ide_startstop_t startstop;
+       int             loops = 0;

        /* for atari only: POSSIBLY BROKEN HERE(?) */
        ide_get_lock(ide_intr, hwgroup);
@@ -1153,6 +1154,7 @@
                        /* no more work for this hwgroup (for now) */
                        return;
                }
+       again:
                hwif = HWIF(drive);
                if (hwgroup->hwif->sharing_irq &&
                    hwif != hwgroup->hwif &&
@@ -1192,8 +1194,14 @@
                 * though. I hope that doesn't happen too much, hopefully not
                 * unless the subdriver triggers such a thing in its own PM
                 * state machine.
+                *
+                * We count how many times we loop here to make sure we service
+                * all drives in the hwgroup without looping for ever
                 */
                if (drive->blocked && !blk_pm_request(rq) && !(rq->flags & REQ_PREEMPT)) {
+                       drive = drive->next ? drive->next : hwgroup->drive;
+                       if (loops++ < 4 && !blk_queue_plugged(drive->queue))
+                               goto again;
                        /* We clear busy, there should be no pending ATA command at this point. */
                        hwgroup->busy = 0;
                        break;

```

4. In order to patch and compile the kernel, you must uncompress and untar the kernel source.  Run the following two commands:

	cd /usr/src
	sudo tar jxf linux-source-2.6.12.tar.bz2

The linux-source-2.6.12.tar.bz2 file is big (about 40 MB compressed, over 250 MB uncompressed) so be patient.  On an older, slower laptop it may take several minutes for the "tar" command to finish.

5. Now that you have uncompressed and extracted the the kernel source, you are ready to patch it:

	cd /usr/src/linux-source-2.6.12
	sudo patch -p1 < /home/grover/downloads/kernel/ide-wakeup-fix.diff

NOTE:  you will need to change the second command (the "patch" command) to include the correct path to the directory where you saved the patch file, and the file name you gave to the patch; this command is the one I use on my system -- it will not work on your system unless you modify it (well, it will work if your username is "grover" and you follow my naming conventions, but otherwise it won't work).

If the patch succeeds, you will see one line of output:

	patching file drivers/ide/ide-io.c

6. Now you are ready to configure and compile the kernel.  

First, I recommend you edit the Makefile to set the EXTRAVERSION variable.  This will give your kernel a unique name.  This step isn't strictly necessary, but if you end up building more than one custom kernel, you can set EXTRAVERSION to a different value for each kernel so you can have a different name for each custom kernel.  For example, if you set EXTRAVERSION to "-custom-1", the name of the kernel will be "2.6.12-custom-1".

You will need to use a text editor for this.  I use vim, but you can use any text editor, just substitute it's name (eg, "gedit" or "kate") in place of "vim".

	sudo vim Makefile

Change the line that reads "EXTRAVERSION =" so that it reads "EXTRAVERSION = -custom-1", then be sure to save the Makefile.

Second, you need to configure the kernel.  This is a step where you can specify many, many optional features for your kernel, but the simplest way to do this is to use the same configuration that comes with the Ubuntu kernel.  This configuration file is located in the /boot directory.  You need to copy it into the kernel source directory:

	 sudo cp /boot/config-2.6.12-10-powerpc .config

Don't forget the "." before "config".  The kernel config file should be a hidden file (filename begins with ".").

To configure the kernel using the .config file you just created, run the "make" command with the "oldconfig" option:

	sudo make oldconfig

It may take a while for this command to finish, so be patient (on my system, an 800 MHz G3, it takes about a minute and a half).

Finally, you will compile the kernel itselt.  This is far and away the most time consuming step of this entire process (on my 800 MHz G3, this takes 1.5 - 2 hours):

	sudo make

As the kernel compile runs, you will see many lines of output in the terminal window.  Some of these lines may include a "warning:".  Don't worry about these, they are harmless.  

7. Once your compile is finally finished, you are ready to install the files, make an initial ram filesystem (used during booting) and configure the bootloader so that it knows about your new kernel.  

Install the files:

The compiled kernel contains a number of files which need to be put in the proper places.  Running the command:

	sudo make modules_install

will copy all the compiled kernel modules (there are many hundreds!) into the correct place in the filesystem.  They will end up under /lib/modules/2.6.12-custom-1 (if you set EXTRAVERSION to "-custom-1" as I did).

Next you need to copy two files from the top level of your kernel source directory (eg, /usr/src/linux-source-2.6.12) into the /boot directory.  

	sudo cp System.map /boot/System.map-2.6.12-custom-1
	sudo cp vmlinux /boot/vmlinux-2.6.12-custom-1

Make an initial ram filesystem:

If you forget this step, even if you've done everything correctly up to this point, your system won't be able to boot the new kernel.  Your old, existing kernels will still boot, it's just the new kernel which won't boot, so if you forget to do this step, you can still get back into your system and do this later (for some reason, I always forget this step, so that's why I know about this).

Here's why you need to make an intial ram filesystme.  In order for your kernel to boot the system, it must be able to read the files on your hard drive in the root (/) filesystem.  Your root filesystem is probably formated as ext3, but the default Ubuntu kernel configuration makes the ext3 drivers as kernel modules, which are stored in the root filesystem itself.  Since the kernel can't read the root filesystem without the ext3 driver, and the drive is stored in the root filesystem, you're stuck... unless you make the ext3 driver available to the kernel in an inital ram filesystem:

	sudo mkinitramfs -o /boot/initrd.img-2.6.12-custom-1 2.6.12-custom-1

The "-o /boot/initrd.img-2.6.12-custom-1" option tells the mkinitramfs command where to send its output, and the "2.6.12-custom-1" at the end of the command line (be sure to preceed this with a space) tells the mkinitramfs command which set of kernel modules to use.

Configure the bootloader:

The final step in the process (before rebooting and testing your new kernel), is configuring the bootloader.  To do this you will need to edit a configuration file, and run the "ybin" command.  To edit the configuration file, run this command (again, feel free to substitue the editor of your choice in place of "vim"):

	sudo vim /etc/yaboot.conf

Once you load the yaboot.conf file in your editor, take a look at the format of the file.  It is largely self-explanatory.  The first section specifies a number of options, the remaining sections (beginning with "image=... " each specify some information about each of the installed kernels.  You need to add a new "image" section for the kernel you just compiled and installed.

The safest way to add a new "image" section is to copy and paste an existing section, and then make a few edits.  You should end up with a new "image" section reading (assuming you followed the naming scheme I suggested above):

	image=/boot/vmlinux-2.6.12-custom-1
        	label=custom-1
        	read-only
        	initrd=/boot/initrd.img-2.6.12-custom-1
        	append="quiet splash"

The last step, before rebooting, is to run the "ybin" command:

	sudo ybin -v

The "-v" option just makes the "ybin" command use verbose output, which may be helpful in case you made a mistake in editing the "yaboot.conf" file (and, of course, you don't want to miss the line of output which mentions "Holy Penguin Pee").

8. Now you want to reboot and test your new kernel.  If you followed my instructions, the new kernel you installed will *not* boot by default.  You will need to specify which kernel to boot from the command line.  Very early during the boot up process you will get a prompt that reads:

	Welcome to yaboot version 1.3.13
	Enter "help" to get some basic usage information
	boot:

If you do nothing here, it will boot the old, default kernel.  To boot the new kernel, enter the "label" value you gave for the new kenel when you edited the yaboot.conf file.  If you are following my instructions verbatim, it will be "custom-1".  You can get a listing of the available kernels by hitting the tab key when you get the "boot:" prompt.

If the new kernel boots correctly, and the system starts up normally, you will want to test the suspend/resume fix (the patch you applied early in this process).  To test this you will first need to remove the work-around scripts I posted early in this thread -- if you  have installed them -- or simply chmod them so they are not executable.  If you are running breezy:

	sudo chmod 600 /etc/apm/scripts.d/dbus

or if you are on warty or hoary:

	sudo chmod 600 /etc/apm/scripts.d/dbus-1

Now you are ready to test the suspend/resume function.  Suspend your laptop the way you normally do (simply closing the lid with the power adapter unplugged should do it).  Once the laptop is fully suspended, wake it back up (eg, open the lid).  Did your system resume correctly?  If so, congratulations... now you can enjoy your laptop the way it is made to function.

If everything is working correctly now, you may want to edit your yaboot.conf file one more time to make the new kernel the default.  To do this, edit the yaboot.conf file so that the line starting "default=" reads "default=custom-1" (of whatever value you inserted for "label" in the "image" section which you created for your new kernel).  Be sure to run the "ybin" command after editing and saving the yaboot.conf file, or your changes will not be applied!

This process may seem like a lot of work, but it is not really all that hard to do.  If your iBook is not resuming properly from a suspend (sleep), the time and effort you invest in fixing your system is well spent.  This is also a great way for you to exercise the power and freedom provided so generously by the linux kernel developers.

---

### Post by disabled_20220313 on 2006-01-02
I suggest you wrap the patch text in code tags, as it looks like the formatting of the forum changed the patch.

When I copied and pasted from the code you posted here I got the error "malformed patch at line 5".

Though if I copied it from bugzilla, it was fine.

Also note - you need to have the GCC 3.4 compiler installed (that's caught me a croper too)

---

### Post by disabled_20220313 on 2006-01-02
Woo finally got it to work! Thanks Grover.

Took an afternoon to compile on my 333Mhz G3 Clamshell thought :D

I used the alternative kernel suggested by mbits - which worked fine for the sleep and awake, but for some reason no longer mounted my USB pen drive. 

So I decided to use Grovers solution instead, though it was a lot more time consuming, I am still able to mount my USB pen drive.

Wouldnt me able to do this with Windows or Mac OS :D

---

### Post by grover on 2006-01-04
ciaran.mooney, thanks for pointing out the formatting problem with my post, and the need for gcc-3.4.  I made some edits to fix these.  I'm glad you figured it out and got your laptop working.

One thing though:  this isn't my solution and I can't take any credit for it.  Credit for the patch goes to danny and Benjamin Herrenschmidt (see [http://bugzilla.ubuntu.com/show_bug.cgi?id=1940](http://bugzilla.ubuntu.com/show_bug.cgi?id=1940)).

---

### Post by zojas on 2006-05-20
on tuesday, my wife's new black macbook will be arriving, and I'll get my old 700MHz ibook back.... does anyone know if the current dapper kernel includes the fix?? I'll let you know next week if no one else has tried it yet. :-D

---

### Post by zojas on 2006-05-27
well, it works great in dapper. the only thing I have had to tweak was X; I had a booger of a time getting my xorg.conf set up (it kept insisting on 640x480) but now all is well. sound works, suspend/resume is fast, and I have the native display resolution running. yay!

---

### Post by robsta on 2006-06-01
[QUOTE=zojas]on tuesday, my wife's new black macbook will be arriving, and I'll get my old 700MHz ibook back.... does anyone know if the current dapper kernel includes the fix?? I'll let you know next week if no one else has tried it yet. :-D[/QUOTE]

On my 12" g3/600 it works out of the box. Pretty impressed i must say.

---

### Post by el3ktro on 2006-06-03
Hello,
the original poster's solution also worked on my G4 iBook, but now that I've switched to Dapper, I don't have this problem anymore :-)

I have another question though: I'm NFS-mounting my desktop's file system on the iBook, and I want it to unmount/remount this file system when I put the iBook to sleep or when I wake it up again. Couldn't I modify the given script so that in the case of a resume, the remote filesystem is mounted, and in the case of sleep, it's unmounted. I think it would be a good idea to wait a few seconds after wakeup with mounting the remote filesystem (DHCP and such), so could I just place a "wait" before the actual mount command?

Hm actually I'm using NetworkManager on this iBook, and it would be nice if the remote dir would be mounted/unmounted according to if NetworkManager finds a remote network or not - is that possible?

Tom

---

### Post by Ptero-4 on 2006-08-29
> **ciaran.mooney said:**
> I suggest you wrap the patch text in code tags, as it looks like the formatting of the forum changed the patch.

When I copied and pasted from the code you posted here I got the error "malformed patch at line 5".

Though if I copied it from bugzilla, it was fine.

Also note - you need to have the GCC 3.4 compiler installed (that's caught me a croper too)

Hi ciaran. Is that patch compatible with the breezy kernel (2.6.12)? Also can you pls email me that patch (the ubuntu bugzilla site is asking autentication info and won't load in opera), my address is [email]Ptero.4@gmail.com[/email]

Thanks.

---

