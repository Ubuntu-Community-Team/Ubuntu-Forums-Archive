---
title: "Ubuntu Boot Fail. What to do?"
date: 2017-12-03
forum: Apple Hardware Users
---

### Post by sterator on 2017-12-03
I gracefully powered down my machine after shutting down software, then booted up minutes later, to receive what I assume is some kind of fail message, below.  Can anyone advise how I can make my computer boot into ubuntu correctly?

Thank you!

WARNING: Failed to connect to lumetad. Falling back to device scanning.
/dev/mapper/ubuntu--vg-root: clean, 885343/29450240, files 51889090/117772288 blocks


There's no prompt..no clue as to anything that I might do to rectify whatever situation this is. No warning of this while I was up in ubuntu..all working normally.

Is there a fix to this and is this a problem?  Thank you!

---

### Post by gordintoronto on 2017-12-04
What you got was a warning message, and warnings generally do not cause the boot to fail.

I don't know what mapper or lunetad are. Can you shed any light?

What version of Ubuntu? Does the system eventually boot up?

---

### Post by yancek on 2017-12-04
What does "shutting down software" mean?  Were you installing or updating some software?  More details on what you were doing before shutting down would help.

---

### Post by sterator on 2017-12-04
> **gordintoronto said:**
> What you got was a warning message, and warnings generally do not cause the boot to fail.

I don't know what mapper or lunetad are. Can you shed any light?

What version of Ubuntu? Does the system eventually boot up?

17.04 - and whatever the most recent little updater was as of 2 or 3 days ago, but 17.04 is the major version I'm on.

I spelled that word incorrectly. It's, "lvmetad"  < I think this might have something to do with disc formatting? file system?

The system does not eventually boot up..I'm trying now...after it throws that warning, it sits there with a blinking cursor, but I have no idea what I need to type to make things proceed.

> **yancek said:**
> What does "shutting down software" mean?  Were you installing or updating some software?  More details on what you were doing before shutting down would help.

It means that I was doing work, and prior to powering down the computer, I quit all software that was running. I wasn't installing or updating anything. I was just doing work (in Scribus.)

We lost electrical power, but my machine is on a UPS, so the computer didn't even see a blip. I saved, quit all open software, and gracefully powered down the computer.

I've done some googling on this warning and tried holding down the Shift key prior to seeing the Ubuntu logo. Makes no difference. I get about 10 seconds of the pink/orange Ubuntu background - no logo - then the black screen with the warning.

the blinking cursor suggests it's ready for commands, but I don't know what I'd type.

The holding down the shift key while restarting is meant to pull up a grub menu, but as I created a single-boot machine, I didn't need, didn't install grub...does Ubuntu install it itself?

The suggestion is once you get the grub menu, you can select "recover"

---

### Post by oldfred on 2017-12-04
Grub2 is both a boot manager (menu) and the boot loader for most Linux systems.
So if booting you are using grub.

If system is newer UEFI, you have to press escape (perhaps more than once) from UEFI but before menu (even if hidden) starts boot.
If BIOS you hold shift key from BIOS until menu appears.

If newer UEFI hardware, you may have fast boot on. That eliminates time from UEFI/BIOS until system starts booting, and you usually do not have time to press any key. 

Have you tried typing exit?
Sometimes that works.

---

### Post by vasa1 on 2017-12-04
> **sterator said:**
> ...

I spelled that word incorrectly. It's, "lvmetad"  < I think this might have something to do with disc formatting? file system?
...
[http://man7.org/linux/man-pages/man8/lvmetad.8.html](http://man7.org/linux/man-pages/man8/lvmetad.8.html)

---

### Post by sterator on 2017-12-05
> **oldfred said:**
> Grub2 is both a boot manager (menu) and the boot loader for most Linux systems.
So if booting you are using grub.

If system is newer UEFI, you have to press escape (perhaps more than once) from UEFI but before menu (even if hidden) starts boot.
If BIOS you hold shift key from BIOS until menu appears.

If newer UEFI hardware, you may have fast boot on. That eliminates time from UEFI/BIOS until system starts booting, and you usually do not have time to press any key. 

Have you tried typing exit?
Sometimes that works.


I tried pressing ESC, probably 20 times total. Also tried typing Exit. Tried holding shift key, both from the time I pressed the power button, as well as immediately after hearing the computer start-up chime (Mac hardware).

The result is the same: the warning loads, I get a blinking cursor, and nothing happens no matter what key I press.

thank you!

---

### Post by oldfred on 2017-12-05
If a Mac, you need to be in Apple sub-forum and they are not like PC. Moved.

I do not know Mac, but are you booting in UEFI boot mode? 
Is drive gpt partitioned as that is the standard with all newer Mac, and EFI boot.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by ratell on 2017-12-05
I get that same error but it doesn't stop the boot process. You would have more info if you turned off quiet splash which you can do by getting the grub menu.

When you reboot the computer you will initially get a light colored screen. Once that screen turns dark press the escape key one time. After a few seconds the Grub menu should appear. The first option should be Ubuntu. If you press e you will be given the option to edit your grub configuration.
If you go down towards the bottom you will see a long line that ends with "quiet splash"
delete quiet splash and press f10. The computer should then continue booting with all the boot messages across the screen. This should give you more info about what is going on.

---

### Post by ratell on 2017-12-05
> **sterator said:**
> I tried pressing ESC, probably 20 times total. !


With the Mac if you press esc during the very initial part of the booting you will be dumped into an EFI prompt that doesn't appear to let you do anything. My guess this is what is happening.

If you wait until the screen turns dark before pressing esc you should get to grub.

---

### Post by sterator on 2017-12-05
OK..I get as far as seeing a

grub> prompt

I typed e and it returned:

"can't find command  'e'

and gives me another

grub>_

prompt..

this is better than it was..also says GNU Grub version 2.02~beta3-4ubuntu2.2 
then
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

I press TAB once and I get a fairly huge (23" monitor, all the way across) paragraph with what look like commands.

'boot' appears to be one of them...I type 'boot' and it returns:

error: you need to load the kernel first

any thoughts on what my next move should be? I'm just sitting here with the screen full of what I just described..

thank you!

---

### Post by ratell on 2017-12-05
If you are getting grub> then I think you are still hitting esc too early. Wait a little longer. What you should get is a colored screen with the grub screen which looks like this
[ATTACH=CONFIG]277749[/ATTACH]

That's when you can type e to edit the configuration and get rid of quiet splash.

Good Luck,

Rob

---

### Post by ratell on 2017-12-05
This page has a lot of instructions of what to at the grub prompt. Most of it's out of my league but you might be able to get things working if you follow the instructions.
[https://www.linux.com/learn/how-rescue-non-booting-grub-2-Linux](https://www.linux.com/learn/how-rescue-non-booting-grub-2-Linux)

Rob

---

### Post by sterator on 2017-12-05
will try again..I did see that dark grub screen *briefly*

---

### Post by ratell on 2017-12-05
the page of instructions mentioned this supergrub rescue disk. 
[https://www.supergrubdisk.org/](https://www.supergrubdisk.org/)

You could go straight to trying that. It says it works with ubuntu, but I don't know anything else about it.

---

### Post by sterator on 2017-12-05
> **ratell said:**
> Once that screen turns dark press the escape key one time. After a few seconds the Grub menu should appear. The first option should be Ubuntu. If you press e you will be given the option to edit your grub configuration.
If you go down towards the bottom you will see a long line that ends with "quiet splash"
delete quiet splash and press f10. The computer should then continue booting with all the boot messages across the screen. This should give you more info about what is going on.

OK...apparently I hit esc at the right time, got the correct menu, arrowed down and over to quiet splash, deleted that, hit F10..now have a black screen...about a minute later..still black.

there was stuff after "quiet splash"  which I didn't delete...did I do this incorrectly?

---

### Post by ratell on 2017-12-05
I believe you did it right. Try it again but replace "quiet splash" with "nomodeset".

If that doesn't work you could try advanced options and try the recovery options there to see if they will fix it. If that doesn't work I think you've exhausted my knowledge. Hopefully, someone more knowledgeable has some suggestions.

---

### Post by sterator on 2017-12-05
OK..doing that now..FYI, after 'quiet splash'  it says

$vt_handoff

I have and am leaving that be.

just put nomodeset in place of quiet splash, hit F10

have the pink/orange "ubuntu color" screen instead of the black screen when I did not type nomodeset

about a minute later..still have the pink/orange screen..nothing else there..no ubuntu logo, no cursor..

---

### Post by ratell on 2017-12-05
I would try advance options and recovery mode and see if that can fix your booting.

Good luck,

Rob

---

### Post by sterator on 2017-12-05
OK..tried the advanced options, selected resume boot from that, was asked for my login credentials, got some disclaimer stuff and now have a prompt which I don't know what to do for:

maker@bento:~$

"maker" is my user name, "bento" is the name of the computer.

hitting "enter" just makes that prompt appear again, so it wants something from me. can you tell me what it's after?

thank you!

---

### Post by sterator on 2017-12-05
^^ then on an educated whim, typed "reboot"

computer obliged and I am now at the same Warning screen that prompted my post!

heh...at least there's some level of communication with the computer.

---

### Post by oldfred on 2017-12-05
You have booted, but you are at a terminal, not at a gui.

Usually before you get to the command line from recovery mode, you get a menu of choices. Do not remember details but some are just continue with boot to gui/desktop, terminal but read only so you can run fsck, terminal with Internet so you can do updates to fix something that is missing.

What mode are you in?

Can you run this?
sudo update-grub

---

### Post by sterator on 2017-12-05
OK..I get all the way to past the recovery (I selected the first version named recovery) then the menu, one of which is grub...fix/repair grub. said it couldn't 

then chose resume, got to the black screen where it asked for my credentials. gave them. got the prompt, typed sudo update-grub and it returned:

/usr/sbin/grub-mkconfig: 255: /usr/sbin/grub-mkconfig: cannot create /boot/grub/grub.cfg.new: Read-only file system

then back to the prompt

---

### Post by sterator on 2017-12-05
right after I typed in my credentials, on that black screen, it gave a line or two about read-only file system, 

/usr/lib/ubuntu-release-upgrader/release-upgrade-motd: 31: /usr/lib/ubuntu-release-upgrader/release-upgrade-motd: cannot create /var/lib/ubuntu-release-upgrader/release-upgrade-available: Read-only file system

unable to create file via template '/var/lib/update-notifier/tmp.XXXXXXXXXX' read-only file system

and some other things that basically sound similar: can't do what's needed

---

### Post by oldfred on 2017-12-06
You are in a read only mode.
If that is your only choice, you may need other repairs from live installer.
But can you choose terminal with Internet?

What video card/chip do you have?

---

### Post by sterator on 2017-12-06
I assume from the menu of about 10 items after I selecte "advanced options" then choose recovery mode?

which, I've been choosing the first one Ubuntu, with Linux 4.10.0-40-generic (recovery mode)

Then I get an eye-squirtingly pink screen with a gray box offering the following:

Recovery Menu (filesystem state: read-only)

resume
clean
dpkg
failsafeX
fsck
grub
network
root
system-summary
<Ok>

---

### Post by oldfred on 2017-12-06
Resume is to just do a normal boot.
But if weird colors, then it probably is a video issue. But I do not know Mac and what video or video settings may be required.

But if you have to add a video driver, you will need network.

You could try failsafex as that is a default video mode. Probably like live installer was.

dpkg would be to allow you to update system.

---

### Post by sterator on 2017-12-06
I can boot into the usb stick I used to install ubuntu...tried the option where it checked disc for defects. no errors found, said press any key to reboot.

I get the warning screen.

do I need to do something else when I get the menu:

Try Ubuntu without installing
Install Ubuntu
OEM install (for manufacturers)
Check disc for defects

---

### Post by sterator on 2017-12-06
OK..I'm in here now under, "Try ubuntu without installing"

shows my internal boot drive as "482GB Volume"  /dev/dm-0 and shows my backup volume as what I named it and /dev/sdb1

I pulled up software and updates> check for drivers. Results seem to discuss 2 things:

Nvidia Geforce 9500GT - shows the machine is using an open source driver, but there are two other, Nvidia choices, which I guess I could choose, then "Apply Changes"

The second thing is more cryptic:

Unknown:Unknown
This device is not working
[unchecked] Using Processor microcode firmware for Intel CPUs from Intel-microcode (proprietary)

[checked] Do not use the device

and below,

No proprietary drivers are in use.

Do I select one of the Nvidia drivers and apply changes?  one is version 340.102, the other 304.135

and do I select, for the unknown thing, the Proprietary intel code?

I don't know how to interpret what I'm seeing and if there are clues as to the issue wherein I can't boot to a desk top.

Thank you!

---

### Post by oldfred on 2017-12-06
You need to know which nVidia is correct for your system.
It probably should say recommended.

       Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

If you install the wrong one, you have to purge or you get conflicts as a new one does not correctly overwrite the previous.
 
I have newer PC and I did install newer Intel microcode with an older install, but thought it now did it correctly?

---

### Post by sterator on 2017-12-06
The one I picked did say "recommended."

seems promising..

;)

---

### Post by sterator on 2017-12-12
> **oldfred said:**
> If a Mac, you need to be in Apple sub-forum and they are not like PC. Moved.

I do not know Mac, but are you booting in UEFI boot mode? 
Is drive gpt partitioned as that is the standard with all newer Mac, and EFI boot.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)


I used boot-repair and got this pastebin link:   

[http://paste.ubuntu.com/26132968/](http://paste.ubuntu.com/26132968/)

thank you!

---

