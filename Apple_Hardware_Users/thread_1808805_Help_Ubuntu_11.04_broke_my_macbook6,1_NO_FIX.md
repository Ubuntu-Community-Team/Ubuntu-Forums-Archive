---
title: "Help Ubuntu 11.04 broke my macbook6,1 NO FIX"
date: 2011-07-20
forum: Apple Hardware Users
---

### Post by alphadogg123 on 2011-07-20
So I installed ubuntu onto my macbook intending to triple boot. 

After finally installing ubuntu off of my CD, I shut it down to reboot into Lion(yes I'm up2date). upon rebooting my screen stays black, the power LED flashes and my macbook BEEPS!(loudly). To get my mac to boot I have to turn it on and off five times. 
I have found a solution to the problem (detailed in the youtube link below), which will fix most other macs, but not mine.
[http://www.youtube.com/watch?v=qPoU8838KDo](http://www.youtube.com/watch?v=qPoU8838KDo)

Any suggestions to fixing this issue?

---

### Post by snafu006 on 2011-07-21
have you tryed what he told you to try

---

### Post by zaebo on 2011-07-21
The problem is, that there is no right EFI firmware for your mac, or?

I have the same problem with an iMac.

I have tried several ways to fix it, but the solution you find seems to
be the only promissing way. At least the only one, one can find via
google.

I issued the problem in a mac-forum, and one guy posted this link
[http://www.insanelymac.com/forum/lofiversion/index.php/t10882.html]("http://www.insanelymac.com/forum/lofiversion/index.php/t10882.html")
as a maybe possible solution.

Although the problem in the link has a different origin, maybe the way works.
But it is very time-consuming, at least with an iMac, and there is no
guarantee for a fix. Maybe one even makes it worse.

Safest way would to wait and hope for an EFI Firmware Update by apple, I think.

---

### Post by alphadogg123 on 2011-07-21
Yeah, i tried that, my macbook is one of the only macs which doesnt have a Firmware update.

I found a firmware.scap file in usr/standalone/i386 and tried to flash it by executing it in terminal as per the method in the youtube video. It didnt work upon turning my macbook back on, it beeped loudly AGAIN and took 4 restarts before i could boot. After this I tried writing the firmware.scap on my install dvd and the one on the efi partition. Neither of these methods worked either.

I cant imagine apple repair/ replacing my logic board(the guy in charge of repairs at my local store is a ****) without payment so I dont know how I'm gonna get this fixed.

---

### Post by zaebo on 2011-07-21
do you still have guaranty or an apple care protection plan?

If so, he should. 

Otherwise you could try contacting apple.

Here:
[https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089")
most ppl with guaranty were able to get the logic board exchanged, when having
guaranty or acpp.

If you don't have guaranty..like me..
I hope that due to new OS X Lion, there will be an EFI Update sooner or later.

And if not, there's still the way to try to solve it with detaching you hdd and so on.

I'm myself pretty perplexed.

---

### Post by alphadogg123 on 2011-07-22
Hopefully this exploit will effect my macbook

[http://www.tuaw.com/2011/07/22/several-apple-notebook-models-susceptible-to-battery-hack/](http://www.tuaw.com/2011/07/22/several-apple-notebook-models-susceptible-to-battery-hack/)

---

### Post by nadro on 2011-07-23
I have the same problem. I installed Lion and next Ubuntu 11.04 (Grub installed on Ubuntu partition) and after it I have an error like You. Now I must 5 times run MacBook for proper boot it. When I had 11.04 near Snow Leopard all works fine. My warranty expired 5 days ago. I think that firmware will solve this problem, but I also can't find update for 6,1...

Maybe someone with working firmware can help us and send Your working firmware (it's located on hidden EFI partition under /EFI/APPLE/EXTENSIONS/Firmware.scap)

Cheers,

---

### Post by alphadogg123 on 2011-07-24
> **nadro said:**
> I have the same problem. I installed Lion and next Ubuntu 11.04 (Grub installed on Ubuntu partition) and after it I have an error like You. Now I must 5 times run MacBook for proper boot it. When I had 11.04 near Snow Leopard all works fine. My warranty expired 5 days ago. I think that firmware will solve this problem, but I also can't find update for 6,1...

Maybe someone with working firmware can help us and send Your working firmware (it's located on hidden EFI partition under /EFI/APPLE/EXTENSIONS/Firmware.scap)

Cheers,

The guy who originally figured this out 
(here) [http://pubmem.wordpress.com/2011/04/09/flash-efi-firmware-update-manually-on-a-macbook-51/]("http://pubmem.wordpress.com/2011/04/09/flash-efi-firmware-update-manually-on-a-macbook-51/")
responded to a question about the firmware.scap file, he says its not the firmware thats corrupt its some EFI flag. 

Any way I tried the command with the firmware.scap file from the efi partition, IT DIDN'T WORK.
I also tried the firmware.scap file on the HDD and the install dvd which comes from the macbook. None of this worked.

I agree if someone could get us a firmware.scap from a working macbook6,1 it may fix it. But we don't know if the firmware.scap file is the same as the update file.

---

### Post by alexmurray on 2011-07-25
If its a corrrupt EFI flag it would be worth trying to dump the output for all of the EFI variables - you can do this from a refit shell with ```
dmpstore -b
``` - you can also actually save this to a file - see [this thread]("http://ubuntuforums.org/showthread.php?t=1076879") for an example - something like ```
dmpstore -s fs0:\efivars
``` *might* work - untested.

---

### Post by alphadogg123 on 2011-07-25
> **alexmurray said:**
> If its a corrrupt EFI flag it would be worth trying to dump the output for all of the EFI variables - you can do this from a refit shell with ```
dmpstore -b
``` - you can also actually save this to a file - see [this thread]("http://ubuntuforums.org/showthread.php?t=1076879") for an example - something like ```
dmpstore -s fs0:\efivars
``` *might* work - untested.

I assume you mean to get this from another macbook6,1 user without this issue.

---

### Post by alexmurray on 2011-07-25
> **alphadogg123 said:**
> I assume you mean to get this from another macbook6,1 user without this issue.

I mean to get it from both a user with this issue and one without so we can compare the differences in the outputs to see which variables are potentially corrupted.

---

### Post by zaebo on 2011-07-29
Were you able to make some progress?

Your posts got me thinking...

I have the same problem, but only with an iMac, as I mentioned.
I've got also a Macbook with which I didn't try to install Ubuntu 11.04. The only thing I did so far, was to compare the size of the EFI Firmware on the hidden partition. It is exactly the same size of my corrupted EFI Firmware from my iMac, which endorse the flag-theory.

Maybe I'm able to produce an output from the working EFI firmware and I can observe some changes.

But on the other hand...
You already tried to flash the original firmware from the standalone folder...why didn't it overrid the flag?
And, if we are able to detect some changes in the firmware, how can we apply changes to the firmware, if flashing it without an apple firmware isn't working?

Appendix:
Another thing I'm thinking about is the number of failed boot operations. It depends on how many partitions you made before trying to install Ubuntu.
I formatted and partitioned the hdd several times since then. If it's only a wrong set flag in the firmware, why did it preserve the information of the old
partitions...

---

### Post by Allsixcolours on 2011-07-29
This might sound silly, but have you tried formatting your OS X partition and reinstalling lion...? I had some issues after installing 11.04 (I dual boot ubuntu and OS X) and ended up having to just reinstall. Luckily most of my stuff was backed up so i didn't lose much data, but the reinstall restored all the defaults to the various files and such and both ubuntu and OS X worked fine afterwards. I did not have this issue that you are having so I can't say for sure but it seems like it would work just as well as it did for me.

---

### Post by nadro on 2011-07-30
I send my MacBook to apple service (guy from Apple support said that he can't find firmware for 6,1 so I must send my MacBook to service, they will probably replace motherboard; my warranty was expired 5 days ago, but he said that they will replace it under warranty terms, because expired time is very short), so when I will get it back I will do trick with dmpstore and I will send You firmware from hidden EFI partition.

---

### Post by pierreyy on 2011-07-30
> **nadro said:**
> I send my MacBook to apple service (guy from Apple support said that he can't find firmware for 6,1 so I must send my MacBook to service, they will probably replace motherboard; my warranty was expired 5 days ago, but he said that they will replace it under warranty terms, because expired time is very short), so when I will get it back I will do trick with dmpstore and I will send You firmware from hidden EFI partition.

guys have you tried to re run the live cd and remove ubuntu off your system maybe it'll go back to normal?

---

### Post by alphadogg123 on 2011-07-30
First of all yes I tried the commands that were in this thread, didn't really understand the code system so I didn't execute any others, they seemed to run but didn't save the log to somewhere I could see it. 

Allsixcolours, there are several other threads on and off this website linked to this issue. I really wish it was so simple but yes I did it yesterday, you wouldn't believe how many times It restarts during an os install. oh and BTW its possible to run the app store version of lion from a USB and do a fresh install.

nadro you awesazing guy.

Yes I did, I then mounted and deleted the ubuntu GRUB that installs to the efi partition, made no difference whatsoever.

Thanks for keeping the thread active guys!


(BTW the avatar  gets changed back either when ubuntu comes up with a solution for this issue or apple does)

---

### Post by johnmurrayvi on 2011-07-31
I can dump the variables from firmware.scap for comparison with Zaebo's, I have an iMac 8,1.

---

### Post by alphadogg123 on 2011-07-31
> **johnmurrayvi said:**
> I can dump the variables from firmware.scap for comparison with Zaebo's, I have an iMac 8,1.


I'll speak for Zaebo , Yes Please, this issue seems to be effecting a lot of people although not everyone is missing a firmware file. Any help of this nature would be appreciated by me and I hope the rest of the community.

---

### Post by blane2 on 2011-08-01
Odd
I was able to install 11.04 on the same hardware in a dual-boot config without any problems.


Differences/ My process

I use SL, not lion
I partitioned the drive with disk utility
installed the loader on the same partition as as Ubuntu 

Use rEFIt as the bootloader

Everything works as expected no problems booting into either OS.


Could be an issue with lion, could be that you installed the loader on the wrong partition.

If you can get into lion try to add rEFIt bootloader and see if that makes a difference 

[http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html)

> 
If you don&#8217;t want to use the installer package, you can do a manual install instead. This section explains how to do a manual install to your Mac OS X installation volume, which requires no additional volumes or disks. It is possible to install rEFIt elsewhere; see the following sections for that.

Here are the steps for a manual install:

    Download the &#8220;Mac disk image&#8221; or any of the other two binary distributions from the home page. Double-click to mount or unpack them.
    Copy the &#8220;efi&#8221; folder from the rEFIt distribution to the root level of your Mac OS X volume.
    Open Terminal and enter the following commands:

    cd /efi/refit
    ./enable.sh

    When prompted, enter the password for your user account.

If everything went well, you&#8217;ll see the rEFIt boot menu on the next restart.

Note: If you get a message saying &#8220;No such file or directory&#8221; in the last step, then you didn&#8217;t put the &#8220;efi&#8221; folder in the right place in step 2. 

Root level is just the top directory of the hard drive. (i.e. click on your hard drive and put it right there. also has library and such folders)

---

### Post by johnmurrayvi on 2011-08-01
Here's my MacBook Pro 5,1:
[[COLOR="Blue"]_mbp51-efivars_[/COLOR]]("http://dl.dropbox.com/u/26254886/mbp51-efivars")

And here's my iMac 8,1:
[[COLOR="blue"]_imac81-efivars_[/COLOR]]("http://dl.dropbox.com/u/26254886/imac81-efivars")

Interestingly, you can load EFI variables from a file using the command:
```
dmpstore -l
```

---

### Post by zaebo on 2011-08-03
sorry, weren't able to come by due to too much work.

Thanks a lot, johnmurrayvi!
As soon as I know how to read the files properly and
not getting weird text, I'll try to find some differences
regarding my corrupted firmware.

@blane2:
Did you used the desktop or the alternative version?
Because I'm running SL, too. And although I told the
installer, to install the loader on the same partition
as Ubuntu, it was installed somewhere else.


I also tried to format everything and made a clean install,
but it didn't changed anything for me.


Does anyone know how to gain the information from the
dumped output?
I will try to get an answer to that in the next days in a
mac forum.

Thank you guys! :)

Do you have any news, alphadogg123?

---

### Post by blane2 on 2011-08-03
> **zaebo said:**
> 

@blane2:
Did you used the desktop or the alternative version?
Because I'm running SL, too. And although I told the
installer, to install the loader on the same partition
as Ubuntu, it was installed somewhere else.



32-bit Ubuntu 11.04 x86 standard version

It was on the first option after you customize your install
near the bottom, i almost missed it.

Format ext4
mount / 
installed loader on the ubuntu partition i created with disk utility as opposed to the swap (i also created) or mac boot partition (which is there by default).

---

### Post by zaebo on 2011-08-03
[https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089")

The bug concerns the x64 version.

The installer ignores the user input.

---

### Post by johnmurrayvi on 2011-08-03
I started exploring the EFI shell a fair amount yesterday and I'd be interested in trying to solve this as well. Could you post your dmpstore output? It might have to be done through the EFI shell to get de-garbled output

---

### Post by blane2 on 2011-08-03
> **zaebo said:**
> [https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089")

The bug concerns the x64 version.

The installer ignores the user input.

feel like i dodged a bullet then.

---

### Post by zaebo on 2011-08-04
> feel like i dodged a bullet then.

You probably did :)



> I started exploring the EFI shell a fair amount yesterday and I'd be interested in trying to solve this as well. Could you post your dmpstore output? It might have to be done through the EFI shell to get de-garbled output

I think I will find some time at the weekend to do so :) Sorry for my slow reactions, I have not
other choice at the moment.

---

### Post by Jaxilian on 2011-08-05
I installed 11.04 on my Macbook Pro 5.5 and it worked great. However I didn't mess with the EFI Bios in anyway (no rEFIt). I have tried to install back to MacOS and it works too.

Apple should be able to restore EFI bios at a service center

---

### Post by johnmurrayvi on 2011-08-05
zaebo, for the dumped nvram variable files, try ```
hd -Cv <efivarfile> > <filetosaveoutput>
```

---

### Post by nadro on 2011-08-08
Hi,
Today I get back my MacBook 6.1 (late2009) from Apple service. They replaced motherboard in my MB and now it runc without problem (only refit boot time is long ~20 seconds, but now I will be reinstall MacOS X and I think that after it boot time will be back to normal). Here You have efivars from my MB6.1 here:
[http://www.sendspace.com/file/b7vzep](http://www.sendspace.com/file/b7vzep)
As I wrote in readme.txt one efivars file was stored before MB was repaired repair and second after repair. Both files have got other size so this is good sign and I hope that it will be usefull for all users with this problem.
Cheers,

---

### Post by zaebo on 2011-08-09
> **johnmurrayvi said:**
> I started exploring the EFI shell a fair amount yesterday and I'd be interested in trying to solve this as well. Could you post your dmpstore output? It might have to be done through the EFI shell to get de-garbled output

What do you mean with EFI shell? Booting from Installation DVD?

I only tried the dmpstore/hd-command from the normal shell with the backed-up Firmware,
but he doesn't know the command.

---

### Post by johnmurrayvi on 2011-08-09
Sorry I meant to put ```
hexdump -Cv
```I realized *hd* doesn't have the "-C" flag. 
You can access the EFI shell from the REFIT menu. Apple doesn't include an EFI shell, but the EFI specification mandate that it has a shell I believe. Anyways, if you install REFIT, on the second row of its menu, i.e. the small icons, on the far left, is the EFI shell icon. That would get you into the EFI shell.

> **nadro said:**
> Hi,
Today I get back my MacBook 6.1 (late2009) from Apple service. They replaced motherboard in my MB and now it runc without problem (only refit boot time is long ~20 seconds, but now I will be reinstall MacOS X and I think that after it boot time will be back to normal). Here You have efivars from my MB6.1 here:
[http://www.sendspace.com/file/b7vzep](http://www.sendspace.com/file/b7vzep)
As I wrote in readme.txt one efivars file was stored before MB was repaired repair and second after repair. Both files have got other size so this is good sign and I hope that it will be usefull for all users with this problem.
Cheers,

Thanks for posting this! I'm gonna take a look asap. Quick question, do you know if the EFI firmware version for the new logic board is the same as before you got it replaced?

---

### Post by nadro on 2011-08-09
I'm not 100% sure, but when I see efi version on my new mb it looks like before (I didn't remember 2 sign from efi version before repair, but other signs in current version are the same as before, so I'm 95% sure that this is the same).

---

### Post by johnmurrayvi on 2011-08-11
Zaebo, could you post the file from the following run through the EFI shell?

```
dmpstore BootFFFF > fs0:\bootffff
```

---

### Post by fqowehf on 2011-08-11
Try booting to the Mac OS X Installation DVD and format the all partitions with Disk Utility and re-install Mac OS X, then use Boot Camp to re-install Ubuntu.

Make sure you use a firewire cable to bypass booting the Hard Drive and boot up the installation DVD.

---

### Post by alphadogg123 on 2011-08-14
> **NullCity said:**
> Try booting to the Mac OS X Installation DVD and format the all partitions with Disk Utility and re-install Mac OS X, then use Boot Camp to re-install Ubuntu.

Make sure you use a firewire cable to bypass booting the Hard Drive and boot up the installation DVD.

The macbook6,1 model has no firewire port. that has been taken out in this model.

---

### Post by nadro on 2011-08-18
Any progress in fixing this issue?

---

### Post by zaebo on 2011-08-24
Sorry, a bit late again. Work...the usual problem...


> **johnmurrayvi said:**
> Zaebo, could you post the file from the following run through the EFI shell?

```
dmpstore BootFFFF > fs0:\bootffff
```

I did it but I can't find it? Where does fs0:\ direct it to?
Can't I simply direct the dmpfile to the Desktop somehow?

Edit:
When I try to access fs0 or fs1 he says me 'no mapping'...?

---

### Post by zaebo on 2011-08-30
I know that it is probably useless, but I just found on

[http://ubuntuguide.org/wiki/Ubuntu:Natty#Dual-Booting_Mac_OS_X_and_Ubuntu]("http://ubuntuguide.org/wiki/Ubuntu:Natty#Dual-Booting_Mac_OS_X_and_Ubuntu")

this:

> Reboot your Mac and go to the terminal in Max OS X (if you have any issues booting, boot from your Mac OS X DVD). Press F8 and enter -s. Enter:
```
fdisk -e /dev/rdisk0
flag 2 <--note that flag 2 is my Mac partition number two
quit
y
reboot
```


As they are missing out on mention the bug in this section, I assume that this is no help,
but I find it interesting to flag the mac partition. Maybe EFI then searches directly on the 
right partition instead of failing several times before?

I haven't tried it, because I don't know what the flag '-e' is doing. Couldn't find it on the fdisk
manual page...


Update:
Ok, as far as I understand it now, it is just the same as setting the mac partition as the
startup partition in the dialog under mac os? 
If so..it's really no help at all..

---

### Post by Markrtfm on 2011-08-31
I am so glad I read this post first!!!!!! I have a MacBook Pro with Lion installed as well. Since Lion I have decided to sell everything Apple that I own. The only exception was to install Ubuntu on this laptop. My main computer is a Dell quad core i7 with Linux Mint 11. I have been thinking about trying Ubuntu again.

This problem is with Lion specifically. When you install Lion it creates a partition for restores without the Lion disk. It is so bad that the computer will not even let me reinstall SL which is what it came with. If I see anything that fixes this I will be sure to post. If I end up having the courage to do it to my laptop I will also post the results.

---

### Post by johnmurrayvi on 2011-09-01
> **zaebo said:**
> Sorry, a bit late again. Work...the usual problem...




I did it but I can't find it? Where does fs0:\ direct it to?
Can't I simply direct the dmpfile to the Desktop somehow?

Edit:
When I try to access fs0 or fs1 he says me 'no mapping'...?

Sorry for the delayed reply, I haven't been able to check in on this thread for awhile. fs0:\ is the EFI system partition. 

Question, were you trying to access fs0 through the EFI Shell or while booted on Mac or booted on a Mac install disk?

---

### Post by zaebo on 2011-09-01
> **johnmurrayvi said:**
> 
Question, were you trying to access fs0 through the EFI Shell or while booted on Mac or booted on a Mac install disk?

Through the EFI Shell. I reinstalled rEFIt, after deleting it at the beginning.

Do I first need to mount the required partitions?

And can't I use my mac partition as the target location for the text-output? 
Or what kind of output will it be?

I'm sorry, all of this is new for me and a mixture of missing knowledge and fear ;)

---

### Post by zaebo on 2011-09-01
Ah, ok. 
It worked.

```

Dump Variable BootFFFF
Variable NV+RT+BS 'Efi:BootFFFF' DataSize = A2
  00000000: 01 00 00 00 9A 00 00 00-02 01 0C 00 D0 41 03 0A  *.............A..*
  00000010: 00 00 00 00 01 01 06 00-00 0B 03 12 0A 00 01 00  *................*
  00000020: 00 00 00 00 04 01 2A 00-03 00 00 00 BA CF 08 00  *......*.........*
  00000030: 00 00 00 00 DE 95 35 00-00 00 00 00 00 00 00 00  *......5.........*
  00000040: 00 00 00 00 00 00 00 00-00 00 00 00 20 00 04 04  *............ ...*
  00000050: 50 00 5C 00 53 00 79 00-73 00 74 00 65 00 6D 00  *P.\.S.y.s.t.e.m.*
  00000060: 5C 00 4C 00 69 00 62 00-72 00 61 00 72 00 79 00  *\.L.i.b.r.a.r.y.*
  00000070: 5C 00 43 00 6F 00 72 00-65 00 53 00 65 00 72 00  *\.C.o.r.e.S.e.r.*
  00000080: 76 00 69 00 63 00 65 00-73 00 5C 00 62 00 6F 00  *v.i.c.e.s.\.b.o.*
  00000090: 6F 00 74 00 2E 00 65 00-66 00 69 00 00 00 7F FF  *o.t...e.f.i.....*
  000000A0: 04 00                                            *..*


```

---

### Post by edwinorc on 2011-09-02
Hey guys,
I have the same problem as zaebo iMac(10,1).
I tried bless flashing the firmware from /usr/standalone/i386/. No dice.

I tried to do 
dmpstore BootFFFF > fs0:\bootffff

but I don't know how to get the dump file to show you guys.
I will be monitoring this thread and happy to do anything to sort this out..

---

### Post by zaebo on 2011-09-02
First of all...I'm sorry to read that :(

As johnmurrayvi said, fs0 direct the output to the hidden EFI partition.
So what I did to get it was:

(taken from here: [https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089/comments/94]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089/comments/94"))

1. While in MacOS, create a folder to mount the EFI partition to.
For example, I created it on my desktop, but you can also create it elsewhere:

```
sudo mkdir /Users/Your-Username/Desktop/efi
```

2. Use the folder as mount point for the EFI partition and mount it:

```
sudo mount -t msdos /dev/disk0s1 /Users/Your-Username/Desktop/efi
```

3. Then you can access the EFI partition and copy the output file.

4. Umount the partition:

```
sudo umount /Users/Your_Username/Desktop/efi
```

The unmounting can take a few seconds...at least with my mac..

---

### Post by edwinorc on 2011-09-02
Thanks.
attached is the output.

---

### Post by untmdsprt on 2011-09-05
I think I will run Ubuntu on my old peecee until this thing is sorted out. I have a working Macbook 2,1 and would like to keep it that way.

I'm sorry you guys are having issues, but thank you so much in posting here. I will keep this thread bookmarked in case someone finds a good solution.

---

### Post by edwinorc on 2011-09-06
I just restarted my iMac today and it started doing some sort of firmware thing!
Grey progress bar below apple logo.

It didn't seem to finish but booted into Lion....and then showed me the login screen (I never set the login screen in my preferences I think firmware changes some settings). When I logged in, there were all these weird graphical errors.

I restarted to see if it was fixed...but then it went back to normal...long beep button pressing game and no login screen.

---

### Post by zaebo on 2011-09-06
That sounds strange!

Do you still have the same ROM-version? Mine (with Snow Leopard) is:

IM101.00CC.B00

Just checked out if there is an EFI update availible, but
can't find anything. Neither in the software-update-app nor
on the apple homepage.

I'm hoping that soon some of the better informed poster are finding
back to this thread :(

---

### Post by edwinorc on 2011-09-07
Yep same Boot Rom.
Maybe around December I will have time to take my iMac to the apple store...

---

### Post by FatalityBoyZahy on 2011-09-08
I REALLLLLY hope this issue gets worked out soon! :(

I ruined my MacBook 6.1 today by trying to install Ubuntu on it.. I even wiped my hdd, and reinstalled OS X... I also tried a different hard drive. Still takes 5 tries to boot up. :(

I'm so upset! $999 POS

---

### Post by zaebo on 2011-09-09
Oh damn. 
Did you also tried to remove the RAM, and try to reset 
the PRAM while RAM and HDD are removed?

This was my last hope, if Apple doesn't release the right
EFI Firmware Update.

[http://www.insanelymac.com/forum/lofiversion/index.php/t10882.html]("http://www.insanelymac.com/forum/lofiversion/index.php/t10882.html")

---

### Post by FatalityBoyZahy on 2011-09-09
> **zaebo said:**
> Oh damn. 
Did you also tried to remove the RAM, and try to reset 
the PRAM while RAM and HDD are removed?

This was my last hope, if Apple doesn't release the right
EFI Firmware Update.

[http://www.insanelymac.com/forum/lofiversion/index.php/t10882.html]("http://www.insanelymac.com/forum/lofiversion/index.php/t10882.html")

Yes, I tried that last night. I tried doing a clean install of OS X.. I also tried a different hard drive :(

---

### Post by alphadogg123 on 2011-09-12
Removing the hard drive and ram won't work. Neither will reinstalling your os or a different hard drive. 
The fault is that the ubuntu install has corrupted the efI(mac version of bios). According to the apple geniuses the long beep you experience at boot is the board looking for an efi update/rewrite.
Currently to fix the problem all you can do is wait for apple to bring out a efi update, the alternative is to pay apple to replace your board which could cost about £250 in GBP

---

### Post by zaebo on 2011-09-12
yeah, reinstalling does not work. I think that was the first thing
we all tried several times ;)

But I thought that with missing hdd and ram a PRAM reset could finally be
performaned. As described in the link, it was able to solve a 
corrupt EFI in the past.

But if you all already tried that... :(

My last hope is that someone is able to find the wrongly written new
parameters and find a way to upload the right ones, since I'm not willing
to pay so much money for a new logic board.

---

### Post by FatalityBoyZahy on 2011-09-12
I REALLY hope Apple releases the firmware... :( It sucks that the firmware for older models is up there.

---

### Post by MartinMac on 2011-09-29
> **alphadogg123 said:**
> Removing the hard drive and ram won't work. Neither will reinstalling your os or a different hard drive. 
The fault is that the ubuntu install has corrupted the efI(mac version of bios). According to the apple geniuses the long beep you experience at boot is the board looking for an efi update/rewrite.
Currently to fix the problem all you can do is wait for apple to bring out a efi update, the alternative is to pay apple to replace your board which could cost about £250 in GBP

I dont understand. They put a EFI firmware on their products and they dont have the original firmware? it seems a joke to replace a mother board for this problem...

> 
For all
I'm guessing if the Macbook7,1 firmware can solve the problem...Because 7,1 is very similar to 6,1 hardware? did anyone try it?

And what about the idea of someone to replace original [nadro]("http://ubuntuforums.org/member.php?u=1043192")'s firmware on our corrupted EFI?

---

### Post by zaebo on 2011-09-29
Yeah, it's all very strange.

As far as I understand, please correct me if I am wrong:


> And what about the idea of someone to replace original nadro's firmware on our corrupted EFI? 
if there wasn't an EFI update performed on the machine, the 
firmware version is the one which can be found on the macOS
installation disc or in the standalone-folder.
But blessing this firmware version does not work.


> I'm guessing if the Macbook7,1 firmware can solve the problem...Because 7,1 is very similar to 6,1 hardware? did anyone try it?
I have an iMac, so I don't know what to do... but I think that
here:
[https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089")

someone tried to bless a firmware upate from a different machine,
and it was successfull. If I remember right.
It should be somewhere near the end of the comments.

---

### Post by MartinMac on 2011-09-30
> **zaebo said:**
> Yeah, it's all very strange.

As far as I understand, please correct me if I am wrong:



if there wasn't an EFI update performed on the machine, the 
firmware version is the one which can be found on the macOS
installation disc or in the standalone-folder.
But blessing this firmware version does not work.

Yeah, now I understand the real problem.

> **zaebo said:**
> I have an iMac, so I don't know what to do... but I think that
here:
[https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089](https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089)

someone tried to bless a firmware upate from a different machine,
and it was successfull. If I remember right.
It should be somewhere near the end of the comments.

OMG! there is the _**workaround**_ _**for our Macbook 6,1 !!!!**_ Thank you so much zaebo!!
I hope I can put here the explanation of that user [Matteo M.]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089/comments/111") 
> 
                 Correct
 Hi all, David,
I own Macbook 6,1 and how I fixed the issue.
 Download Firmware Update 1.7 [http://support.apple.com/downloads/MacBook_Pro_EFI_Firmware_Update_1_7_](http://support.apple.com/downloads/MacBook_Pro_EFI_Firmware_Update_1_7_)
MacBookPro5,5 the same hardware MacBook6,1, to extract MBP55_00AC_03B_LOCKED.scap.
 mv MBP55_00AC_03B_LOCKED.scap MB61_00C8_B00_LOCKED.scap
 sudo bless -mount / -firmware MB61_00C8_B00_LOCKED.scap --verbose
 Shutdown and restart Mac update the firmware and restart automatically.
 Attention consequences, the MacBook6,1 as new model identifier  MacBookPro5,5 but works well, possible problems could rise with future  firmware update.
 Thanks for all, The Power of Community.

        
Remains the question about the possibility to bless with the 7,1 firmware. Could be great if someone tries it before replacing the mac's board (of those can do it under warranty period) at the apple center.

---

### Post by FatalityBoyZahy on 2011-10-13
> **MartinMac said:**
> Yeah, now I understand the real problem.



OMG! there is the _**workaround**_ _**for our Macbook 6,1 !!!!**_ Thank you so much zaebo!!
I hope I can put here the explanation of that user [Matteo M.]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089/comments/111") 
Remains the question about the possibility to bless with the 7,1 firmware. Could be great if someone tries it before replacing the mac's board (of those can do it under warranty period) at the apple center.

Has anyone confirmed that this works?!?! The instructions are very confusing, could somebody please help me with them? THanks!

---

### Post by MartinMac on 2011-10-13
> **FatalityBoyZahy said:**
> Has anyone confirmed that this works?!?! The instructions are very confusing, could somebody please help me with them? THanks!

I think the procedure is the same of [http://pubmem.wordpress.com/2011/04/09/flash-efi-firmware-update-manually-on-a-macbook-51/](http://pubmem.wordpress.com/2011/04/09/flash-efi-firmware-update-manually-on-a-macbook-51/) but with a different firmware and he rename the filename with the command "mv MBP55_00AC_03B_LOCKED.scap MB61_00C8_B00_LOCKED.scap". I trust on it.

 
I dont do it yet because I'm still waiting a reply from the apple store for a MB replace...I'd like to try also with the 7,1 EFI but I'm scared of the apple store...

---

### Post by FatalityBoyZahy on 2011-10-15
> **MartinMac said:**
> I think the procedure is the same of [http://pubmem.wordpress.com/2011/04/09/flash-efi-firmware-update-manually-on-a-macbook-51/](http://pubmem.wordpress.com/2011/04/09/flash-efi-firmware-update-manually-on-a-macbook-51/) but with a different firmware and he rename the filename with the command "mv MBP55_00AC_03B_LOCKED.scap MB61_00C8_B00_LOCKED.scap". I trust on it.

 
I dont do it yet because I'm still waiting a reply from the apple store for a MB replace...I'd like to try also with the 7,1 EFI but I'm scared of the apple store...

Where should I place the .scap files?

---

### Post by MartinMac on 2011-10-16
Ok, I tried until their reply because I wanted to help the community.

Here you are the news.

I tried in order:

I. to flash with 6,1 EFI backup and it doesn't work...but I'm going to think it isn't a real backup because all the other .scap files are 4,3MB and this one is 15,7MB large.
II. to flash with 5,5 MBP EFI and went well.
III. After latter positive flashing I tried 7,1 EFI and another time 6,1 EFI but they don't change anything.

At the end the only working solution I tested is the 5,5 MBP EFI. Now my MacBook White _starts always_ with the only cons that on "system informations" it is recognized like a MBP 5,5.

[SIZE="3"][COLOR="Red"]Until the entire right procedure I tested, be careful! because I'm noticing a little display refreshing bug (you can see a sort of a nearly undetectable slow horizontal refresh from the lower part to the top) during boot startup and during Desktop visualization with wallpapers "Lake", "Mt. Fuji", "Pink Forest", "Ducks on a Misty Pond", "Eagle & Waterfall". "Moon". I don't remember this problem before the flash. On Windows 7 I'm not finding the same issue [/COLOR]

[INDENT][LIST=1]
[*]Download the .dmg file of 5.5 MBP EFI and mount it.
[*]Use unpkg 4.5 to unpack the .pkg file
[*]Go to /Users/<user_name>/Desktop/MacBookProEFIUpdate/Applications/Utilities/MacBook Pro EFI Firmware Update.app/Contents/Resources
[*]Rename MBP55_00AC_03B_LOCKED.scap to MB61_00C8_B00_LOCKED.scap and copy it
[*](PLEASE noted I find this directory on Mac OS X Lion) Go to /System/Library/CoreServices/Firmware Updates
[*]Paste the .scap file
[*]Open Terminal and type "cd /System/Library/CoreServices/", then "cd Firm" and press TAB key. You should see "cd Firmware\ Updates/" . Press Enter.
[*]Type "sudo bless -mount / -firmware MB61_00C8_B00_LOCKED.scap --verbose", press Enter
[*]Reboot and enjoy your working new 5,5 Mac Book Pro White ;)[/SIZE]
[/LIST][/INDENT]

Hope to help someone.

P.S. hint for Ubuntu 11.04 installation: don't use a USB drive but only the CD. Once you have rEfit you can choose between "Boot Linux form CD" or "Boot EFI\boot\bootx64.efi from". The FIRST one is the correct choice that doesn't break the firmware.

---

### Post by FatalityBoyZahy on 2011-10-20
> **MartinMac said:**
> Ok, I tried until their reply because I wanted to help the community.

Here you are the news.

I tried in order:

I. to flash with 6,1 EFI backup and it doesn't work...but I'm going to think it isn't a real backup because all the other .scap files are 4,3MB and this one is 15,7MB large.
II. to flash with 5,5 MBP EFI and went well.
III. After latter positive flashing I tried 7,1 EFI and another time 6,1 EFI but they don't change anything.

At the end the only working solution I tested is the 5,5 MBP EFI. Now my MacBook White _starts always_ with the only cons that on "system informations" it is recognized like a MBP 5,5.

[SIZE="3"][COLOR="Red"]Until the entire right procedure I tested be careful because I'm noticing a little display refreshing bug (you can see a sort of a nearly undetectable slow horizontal refresh from the lower part to the top) during boot startup and during Desktop visualization with wallpapers "Lake", "Mt. Fuji", "Pink Forest", "Ducks on a Misty Pond", "Eagle & Waterfall". "Moon". I don't remember this problem before the flash. On Windows 7 I'm not finding the same issue [/COLOR]

[INDENT][LIST=1]
[*]Download the .dmg file of 5.5 MBP EFI and mount it.
[*]Use unpkg 4.5 to unpack the .pkg file
[*]Go to /Users/<user_name>/Desktop/MacBookProEFIUpdate/Applications/Utilities/MacBook Pro EFI Firmware Update.app/Contents/Resources
[*]Rename MBP55_00AC_03B_LOCKED.scap to MB61_00C8_B00_LOCKED.scap and copy it
[*](PLEASE noted I find this directory on Mac OS X Lion) Go to /System/Library/CoreServices/Firmware Updates
[*]Paste the .scap file
[*]Open Terminal and type "cd /System/Library/CoreServices/", then "cd Firm" and press TAB key. You should see "cd Firmware\ Updates/" . Press Enter.
[*]Type "sudo bless -mount / -firmware MB61_00C8_B00_LOCKED.scap --verbose", press Enter
[*]Reboot and enjoy your working new 5,5 Mac Book Pro White ;)[/SIZE]
[/LIST][/INDENT]

Hope to help someone.

P.S. hint for Ubuntu 11.04 installation: don't use a USB drive but only the CD. Once you have rEfit you can choose between "Boot Linux form CD" or "Boot EFI\boot\bootx64.efi from". The second one is the correct choice that doesn't break the firmware.

OH MY GOD. THANK YOU SO MUCH! It worked perfectly!

---

### Post by johnmurrayvi on 2011-10-20
> **zaebo said:**
> That sounds strange!

Do you still have the same ROM-version? Mine (with Snow Leopard) is:

IM101.00CC.B00

Just checked out if there is an EFI update availible, but
can't find anything. Neither in the software-update-app nor
on the apple homepage.

I'm hoping that soon some of the better informed poster are finding
back to this thread :(

Do you still have access to the original firmware? If so, can you upload it? Also, with that, could you upload the file created from ```
dmpstore -b fs0:\efivars
``` run in the EFI shell?

---

### Post by MartinMac on 2011-10-20
> **FatalityBoyZahy said:**
> OH MY GOD. THANK YOU SO MUCH! It worked perfectly!

You're welcome! ;)

---

### Post by zaebo on 2011-10-25
> **johnmurrayvi said:**
> Do you still have access to the original firmware? If so, can you upload it? Also, with that, could you upload the file created from ```
dmpstore -b fs0:\efivars
``` run in the EFI shell?

What do you mean with the original firmware? 
I'm currently not home to check out my iMac, but as far as I 
remember, I've got the firmware.scap from the hidden EFI partition
which should be the same as in the /standalone/i386 folder and
as on the SnowLeopard Installation DVD.

Edit (1)
I hope that I remember this right, but I think that the firmware.scap 
from my iMac was exactly the same as on my MacBook (?). It was a ~15Mb
big file.

I will post the dmpstore-output when I'm back home!

Sorry for my late reply, wasn't really expecting something new here :)

Can I ask you what you are hoping to find?
Though I don't understand hardly anything, I'm interested in it :)


Edit (2)
I hope that my information is not entirely wrong.. it's quiet some time ago
since I've done anything in this concern.

---

### Post by zaebo on 2011-10-26
Ok, so here's my dmpstore output.

I checked the firmware.scap from the EFI partition and it is
to the byte exact the same size as the firmware.scap from
the installation DVD.

Edit:
I had to zip the txt-file. I was too big..

---

### Post by adii_711 on 2011-10-29
> **FatalityBoyZahy said:**
> OH MY GOD. THANK YOU SO MUCH! It worked perfectly!
@MartinMac: I tried your solution but for some reason its not working for me. 

any thoughts on it?

---

### Post by MartinMac on 2011-10-30
[INDENT]> **adii_711 said:**
> @MartinMac: I tried your solution but for some reason its not working for me. 
[/INDENT] 
any thoughts on it?

Which OS do you use?
Are you working on a 6,1 Macbook White?

---

### Post by katya90 on 2012-02-09
hello!
i have a macbook 6,1 with this problem...work the martinmac's soluction???or brick the macbook?????

please!!!!!!!!

---

### Post by MartinMac on 2012-02-09
> **FatalityBoyZahy said:**
> OH MY GOD. THANK YOU SO MUCH! It worked perfectly!

> **katya90 said:**
> hello!
i have a macbook 6,1 with this problem...work the martinmac's soluction???or brick the macbook?????

please!!!!!!!!


At least two guys did it.
Read carefully the display refreshing problem...

---

### Post by sergiomr88 on 2012-02-28
Didn't work, all I get is this on the console:

```
EFI found at IODeviceTree:/efi
GPT detected
No auxiliary booter partition required
System partition found
Returning booter information dictionary:
<CFBasicHash 0x1002011f0 [0x7fff704f2ee0]>{type = mutable dict, count = 3,
entries =>
	0 : <CFString 0x100019a60 [0x7fff704f2ee0]>{contents = "System Partitions"} = <CFArray 0x100201d90 [0x7fff704f2ee0]>{type = immutable, count = 1, values = (
	0 : <CFString 0x100201ac0 [0x7fff704f2ee0]>{contents = "disk0s1"}
)}
	1 : <CFString 0x10001a2a0 [0x7fff704f2ee0]>{contents = "Data Partitions"} = <CFArray 0x100201cf0 [0x7fff704f2ee0]>{type = immutable, count = 1, values = (
	0 : <CFString 0x7fff704d79b0 [0x7fff704f2ee0]>{contents = "disk0s2"}
)}
	2 : <CFString 0x100019a20 [0x7fff704f2ee0]>{contents = "Auxiliary Partitions"} = <CFArray 0x100201810 [0x7fff704f2ee0]>{type = immutable, count = 0, values = ()}
}

Substituting ESP disk0s1
Mounting at /Volumes/bless.nyo0
Executing "/sbin/mount"
Returned 0
Creating /Volumes/bless.nyo0//EFI/APPLE/FIRMWARE if needed
Deleting previous contents of /Volumes/bless.nyo0//EFI/APPLE/FIRMWARE
Deleting /Volumes/bless.nyo0//EFI/APPLE/FIRMWARE/MB61_00C8_B00_LOCKED.scap (4260464 bytes)
Opened dest at /Volumes/bless.nyo0//EFI/APPLE/FIRMWARE/MB61_00C8_B00_LOCKED.scap for writing
preallocation not supported on this filesystem for /Volumes/bless.nyo0//EFI/APPLE/FIRMWARE/MB61_00C8_B00_LOCKED.scap

Type/creator set to     /     for /Volumes/bless.nyo0//EFI/APPLE/FIRMWARE/MB61_00C8_B00_LOCKED.scap
/Volumes/bless.nyo0//EFI/APPLE/FIRMWARE/MB61_00C8_B00_LOCKED.scap created successfully
Relative path of /Volumes/bless.nyo0//EFI/APPLE/FIRMWARE/MB61_00C8_B00_LOCKED.scap is \EFI\APPLE\FIRMWARE\MB61_00C8_B00_LOCKED.scap
IOMedia disk0s1 has UUID 03ED5E32-BC8D-42B9-BE85-07F52E396DD5
Setting EFI NVRAM:
<CFBasicHash 0x100201220 [0x7fff704f2ee0]>{type = mutable dict, count = 1,
entries =>
	1 : <CFString 0x100019a80 [0x7fff704f2ee0]>{contents = "efi-boot-next"} = <CFString 0x10010ef10 [0x7fff704f2ee0]>{contents = "<array><dict><key>IOMatch</key><dict><key>IOProviderClass</key><string>IOMedia</string><key>IOPropertyMatch</key><dict><key>UUID</key><string>03ED5E32-BC8D-42B9-BE85-07F52E396DD5</string></dict></dict><key>BLLastBSDName</key><string>disk0s1</string></dict><dict><key>IOEFIDevicePathType</key><string>MediaFilePath</string><key>Path</key><string>\EFI\APPLE\FIRMWARE\MB61_00C8_B00_LOCKED.scap</string></dict></array>"}
}

Executing "/sbin/umount"
Returned 0
```

I'm still with a broken macbook6,1.

Edit: 

It finally worked! 

I first did a clean install of lion and tried your method again. When I finished I chose the Shut Down... option. When I turned on the computer I got the same beeping again and had to do the same 4-5 on/off cycle I had to do when my computer was broken. After turning my computer on for the last time, the screen stayed black for several seconds (maybe minutes?) before actually showing the gray welcome screen (showing the firmware update progress bar). 

As another poster said, THANK YOU SO MUCH!!!!!

---

### Post by MartinMac on 2012-02-29
;)

---

### Post by katya90 on 2012-03-16
> **sergiomr88 said:**
> Didn't work, all I get is this on the console:

```
EFI found at IODeviceTree:/efi
GPT detected
No auxiliary booter partition required
System partition found
Returning booter information dictionary:
<CFBasicHash 0x1002011f0 [0x7fff704f2ee0]>{type = mutable dict, count = 3,
entries =>
    0 : <CFString 0x100019a60 [0x7fff704f2ee0]>{contents = "System Partitions"} = <CFArray 0x100201d90 [0x7fff704f2ee0]>{type = immutable, count = 1, values = (
    0 : <CFString 0x100201ac0 [0x7fff704f2ee0]>{contents = "disk0s1"}
)}
    1 : <CFString 0x10001a2a0 [0x7fff704f2ee0]>{contents = "Data Partitions"} = <CFArray 0x100201cf0 [0x7fff704f2ee0]>{type = immutable, count = 1, values = (
    0 : <CFString 0x7fff704d79b0 [0x7fff704f2ee0]>{contents = "disk0s2"}
)}
    2 : <CFString 0x100019a20 [0x7fff704f2ee0]>{contents = "Auxiliary Partitions"} = <CFArray 0x100201810 [0x7fff704f2ee0]>{type = immutable, count = 0, values = ()}
}

Substituting ESP disk0s1
Mounting at /Volumes/bless.nyo0
Executing "/sbin/mount"
Returned 0
Creating /Volumes/bless.nyo0//EFI/APPLE/FIRMWARE if needed
Deleting previous contents of /Volumes/bless.nyo0//EFI/APPLE/FIRMWARE
Deleting /Volumes/bless.nyo0//EFI/APPLE/FIRMWARE/MB61_00C8_B00_LOCKED.scap (4260464 bytes)
Opened dest at /Volumes/bless.nyo0//EFI/APPLE/FIRMWARE/MB61_00C8_B00_LOCKED.scap for writing
preallocation not supported on this filesystem for /Volumes/bless.nyo0//EFI/APPLE/FIRMWARE/MB61_00C8_B00_LOCKED.scap

Type/creator set to     /     for /Volumes/bless.nyo0//EFI/APPLE/FIRMWARE/MB61_00C8_B00_LOCKED.scap
/Volumes/bless.nyo0//EFI/APPLE/FIRMWARE/MB61_00C8_B00_LOCKED.scap created successfully
Relative path of /Volumes/bless.nyo0//EFI/APPLE/FIRMWARE/MB61_00C8_B00_LOCKED.scap is \EFI\APPLE\FIRMWARE\MB61_00C8_B00_LOCKED.scap
IOMedia disk0s1 has UUID 03ED5E32-BC8D-42B9-BE85-07F52E396DD5
Setting EFI NVRAM:
<CFBasicHash 0x100201220 [0x7fff704f2ee0]>{type = mutable dict, count = 1,
entries =>
    1 : <CFString 0x100019a80 [0x7fff704f2ee0]>{contents = "efi-boot-next"} = <CFString 0x10010ef10 [0x7fff704f2ee0]>{contents = "<array><dict><key>IOMatch</key><dict><key>IOProviderClass</key><string>IOMedia</string><key>IOPropertyMatch</key><dict><key>UUID</key><string>03ED5E32-BC8D-42B9-BE85-07F52E396DD5</string></dict></dict><key>BLLastBSDName</key><string>disk0s1</string></dict><dict><key>IOEFIDevicePathType</key><string>MediaFilePath</string><key>Path</key><string>\EFI\APPLE\FIRMWARE\MB61_00C8_B00_LOCKED.scap</string></dict></array>"}
}

Executing "/sbin/umount"
Returned 0
```I'm still with a broken macbook6,1.

Edit: 

It finally worked! 

I first did a clean install of lion and tried your method again. When I finished I chose the Shut Down... option. When I turned on the computer I got the same beeping again and had to do the same 4-5 on/off cycle I had to do when my computer was broken. After turning my computer on for the last time, the screen stayed black for several seconds (maybe minutes?) before actually showing the gray welcome screen (showing the firmware update progress bar). 

As another poster said, THANK YOU SO MUCH!!!!!



you have a problem with the display refresh???

---

### Post by BL4zD on 2012-04-28
Was anyone able to get the original 6,1 firmware?

I tried this method and now my macbook says it's a MBP 5,5. It's a small detail but annoying so I'd like to flash back to the original if I could. The 15mb Firmware.scap is not working for me unless someone else has come upon a solution.

---

### Post by FatalityBoyZahy on 2012-10-01
> **BL4zD said:**
> Was anyone able to get the original 6,1 firmware?

I tried this method and now my macbook says it's a MBP 5,5. It's a small detail but annoying so I'd like to flash back to the original if I could. The 15mb Firmware.scap is not working for me unless someone else has come upon a solution.

I was wondering the same thing. hmph

---

