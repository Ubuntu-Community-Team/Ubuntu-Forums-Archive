---
title: "PowerPC - Installing Intrepid (8.10) - No common CD-ROM drive was detected"
date: 2008-10-31
forum: Apple Hardware Users
---

### Post by tiresia on 2008-10-31
**The ubuntu-8.10-alternate-powerpc Installer-CD failes to detect the CD-ROM Drive.**

After choosing Language, Country and Keyboard-Layout, the Installer tries to detect the CD-ROM, but you get following massage:  

[I]"No common CD-ROM drive was detected
You may need to load additional CD-ROM drivers from a floppy... Otherwise you willl be give the option to manually select CD-ROM modules. Load drivers from Floppy? - Yes - No"[/I]
Answer 'No' to the question and 

**SOLUTION**
**1.**
Switch to a second console pressing ctrl+alt+F2
Press Enter to activate that console
Type:```
modprobe ide-scsi
```

**2.**
Switch back to the first console pressing ctrl+alt+F1
You got another question:
*"Manually select a CD-ROM module and device?"*
Say 'Yes' and choose the right option for you.
Most probably you have to choose 'cdrom' or 'cdrom0'

**3.**
If it fails again, go back to the 'Debian Installer Main Menu' 
and choose again the option 'Detect and mount a CD-ROM'
Now it should work!

::::::: ::::::: ::::::: ::::::: ::::::: :::::::
For more information:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608)
[COLOR="Red"]***Thanks to [olalirole]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608/comments/5") for this workaround!!!***[/COLOR]

---

### Post by Elephex on 2008-10-31
> **tiresia said:**
> **The ubuntu-8.10-alternate-powerpc Installer-CD failes to detect the CD-ROM Drive.**

After choosing Language, Country and Keyboard-Layout, the Installer tries to detect the CD-ROM, but you get following massage:  

[I]"No common CD-ROM drive was detected
You may need to load additional CD-ROM drivers from a floppy... Otherwise you willl be give the option to manually select CD-ROM modules. Load drivers from Floppy? - Yes - No"[/I]
Answer 'No' to the question and 

**SOLUTION**
**1.**
Switch to a second console pressing crtl+alt+F2
Press Enter to activate that console
Type:```
modprobe ide-scsi
```

**2.**
Switch back to the first console pressing ctrl+alt+F1
You got another question:
*"Manually select a CD-ROM module and device?"*
Say 'Yes' and choose the right option for you.
Most probably you have to choose 'cdrom' or 'cdrom0'

**3.**
If it fails again, go back to the 'Debian Installer Main Menu' 
and choose again the option 'Detect and mount a CD-ROM'
Now it should work!

::::::: ::::::: ::::::: ::::::: ::::::: :::::::
For more information:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608)
[COLOR="Red"]***Thanks to [olalirole]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608/comments/5") for this workaround!!!***[/COLOR]



CONFIRMED! this works perfectly. I am installing on a PPC ( powerpc) Apple Titanium g4 Powerbook and had to use 

Switch to a second console pressing crtl+alt+F2
Press Enter to activate that console
Type:```
modprobe ide-scsi
```

Then it did not find it, then i tried to redetect again and it found my CD-Rom flawlessly. 

Three Cheers!!

~elephex

---

### Post by calebio on 2008-10-31
> **Elephex said:**
> CONFIRMED! this works perfectly. ...

Yes, this worked for me as well. But after completing the install and rebooting, yaboot loads and boot starts and then the screen fades into white and nothing further happens. A bit scary....

---

### Post by tiresia on 2008-10-31
Can you please give more information about your computer?

---

### Post by calebio on 2008-10-31
> **calebio said:**
> Yes, this worked for me as well. But after completing the install and rebooting, yaboot loads and boot starts and then the screen fades into white and nothing further happens. A bit scary....

Problem solved: at the yaboot prompt, run "Linux video=ofonly". Then once booted, edit /etc/yaboot.conf to include the following:
```
  append="video=ofonly"
```

---

### Post by ncudmore on 2008-11-08
Hi,

I got the same problem with the no-cdrom detected.  However, I can not switch to the terminal screen to run the probe.  I've tried the (Alt+F2) (Ctrl+Alt+F2) etc., and I've gone back and changed the keyboard - tried Macintosh, MacBook/MacBook Pro, Macintosh Old, and finally the MacBook Int.  as well as generic 101.

None of these allow the terminal switch to get a console and run the probe .

It's a 12" 867mhz, PowerBook G4

---

### Post by calebio on 2008-11-08
> **ncudmore said:**
> Hi,

I got the same problem with the no-cdrom detected.  However, I can not switch to the terminal screen to run the probe.  I've tried the (Alt+F2) (Ctrl+Alt+F2) etc., and I've gone back and changed the keyboard - tried Macintosh, MacBook/MacBook Pro, Macintosh Old, and finally the MacBook Int.  as well as generic 101.

I believe that computer has a function (fn) key. Try including that in Ctrl-Alt-F2 (so, Ctrl+Alt+Fn+F2). I remember it was either that, or using '2' instead of 'F2', though I can't remember which exactly.

---

### Post by ncudmore on 2008-11-08
Cheers Ctrl+Alt+Fn+F2 of something like it worked...  Installing the base system now :)

---

### Post by rangnar on 2008-11-12
The current (2008-10-30) alternate-install iso-image has this error. Same bug on the LiveCD (2008-10-27)?

When will it be fixed?

Beside this nasty questions. Very good work!

Ralf

---

### Post by Leslie Viljoen on 2008-11-12
Can a forum moderator perhaps sticky this note, or add it to a FAQ or something? Methinks it's going to keep coming up...

---

### Post by natebeaty on 2008-11-15
I can confirm this is happening also on a PowerBook G4 DVI 800mhz (tibook), and a G4 Cube. It took me a while to find this post, and the fix is simple, but certainly seems silly to have to do that.

---

### Post by ba5e on 2008-11-19
happend to me too with a 2000 imac...will try the workaround as soon as osx is finished installing...zzz

---

### Post by farmer ck on 2008-11-20
I'm fixing up a tired old clamshell I bought for my 4 year old daughter on eBay, and I was beginning to think I wasted 60 bucks. She will be so happy to know that dad got her laptop going again. Thanks for the help.

---

### Post by kritstov on 2008-11-23
Hey,

I had this same problem so I'm glad I found this thread. The only problem is I can't get this to work for me. I hit no for the floppy drive question, and then I try pressing Ctrl+Opt+Fn+F2 and nothing happens. I have a iBook G3 500 dual usb. I have a feeling I'm missing something, any help would be appreciated.

---

### Post by Leslie Viljoen on 2008-11-23
Should be ctrl-alt-f2 or just alt-f2. After that alt-f1 should take you back to the installer.

---

### Post by kritstov on 2008-11-23
> **Leslie Viljoen said:**
> Should be ctrl-alt-f2 or just alt-f2. After that alt-f1 should take you back to the installer.

Thanks for the help, but unfortunately it still isn't working. Could I have selected the wrong keyboard type? I just did USA.

---

### Post by Yegg on 2008-11-23
> **kritstov said:**
> Thanks for the help, but unfortunately it still isn't working. Could I have selected the wrong keyboard type? I just did USA.

I'm going to say it would be best to select the "USA - Macintosh" option when configuring Ubuntu. As someone mentioned on page 1, try Ctrl+Alt+Fn+F2. This is also the only technique that works for me as well. Depending on your Mac, you may have to get your fingers in an awkward position to reach all of these keys.

---

### Post by kritstov on 2008-11-23
> **Yegg said:**
> I'm going to say it would be best to select the "USA - Macintosh" option when configuring Ubuntu. As someone mentioned on page 1, try Ctrl+Alt+Fn+F2. This is also the only technique that works for me as well. Depending on your Mac, you may have to get your fingers in an awkward position to reach all of these keys.

Still no luck. =( I don't understand what I could be doing wrong. Could something be wrong with my Fn key? Because when I hold it down in Mac OS X and press F2 it still changes my brightness settings.

---

### Post by Yegg on 2008-11-23
> **kritstov said:**
> Still no luck. =( I don't understand what I could be doing wrong. Could something be wrong with my Fn key? Because when I hold it down in Mac OS X and press F2 it still changes my brightness settings.

Did you end up selecting "USA - Macintosh" as your keyboard type when completing the early steps involved in the Ubuntu installation? Are you sure you're holding down Ctrl, Alt, Fn, and hitting F2 while they are held down?

If you answer yes to both of those, then perhaps you are simply at the wrong screen? One of the screens mentions to hit Alt-F2 (or maybe it said Ctrl-F2), even though following its directions don't work, this is the screen you need to be doing Ctrl+Alt+Fn+F2 at.

Other than that, not sure what else to tell you.

---

### Post by kritstov on 2008-11-24
> **Yegg said:**
> Did you end up selecting "USA - Macintosh" as your keyboard type when completing the early steps involved in the Ubuntu installation? Are you sure you're holding down Ctrl, Alt, Fn, and hitting F2 while they are held down?

If you answer yes to both of those, then perhaps you are simply at the wrong screen? One of the screens mentions to hit Alt-F2 (or maybe it said Ctrl-F2), even though following its directions don't work, this is the screen you need to be doing Ctrl+Alt+Fn+F2 at.

Other than that, not sure what else to tell you.

While none of this worked, luckily I figured out a workaround. I feel kinda stupid for not thinking of this before, I just grabbed a USB keyboard from another computer and used that. Thanks for trying though, I appreciate it. I have a feeling my Fn key is messed up or something.

---

### Post by Yegg on 2008-11-24
> **kritstov said:**
> While none of this worked, luckily I figured out a workaround. I feel kinda stupid for not thinking of this before, I just grabbed a USB keyboard from another computer and used that. Thanks for trying though, I appreciate it. I have a feeling my Fn key is messed up or something.

Well, at least the problem is solved and anyone else looking for a solution now has another possible fix.

---

### Post by Brierley24 on 2008-11-24
Hi

I am having the same problem trying to install Ubuntu 8.10 on a G4 Mac Mini. I have followed the instructions in the previous threads but cannot switch using the Ctrl+Alt-F2 key strokes.

It worked once but did not recognise the CDRom. When I tried it again the screen went blank with a thin line of white static 1/2" from the top of the screen. 

Despite numerous attempts using Ctrl+Alt+Fn+F2 & Alt+F2 it always results in the same blank screen.

Any help would be appreciated

---

### Post by stream303 on 2008-11-24
The catch with the black screen prior to the cd-rom detection problem might be solved by trying the following at the second-stage yaboot boot: prompt (hit TAB to stop the countdown)

```
Linux video=ofonly nosplash
or
Linux nosplash
```

This might now allow you to reach the stage where the cdrom isn't detected, but you can now do ctrl-alt-f2

I know the mac-mini's are a bit finicky.. :)

---

### Post by zahillyard on 2008-11-28
> **tiresia said:**
> **The ubuntu-8.10-alternate-powerpc Installer-CD failes to detect the CD-ROM Drive.**

After choosing Language, Country and Keyboard-Layout, the Installer tries to detect the CD-ROM, but you get following massage:  

[I]"No common CD-ROM drive was detected
You may need to load additional CD-ROM drivers from a floppy... Otherwise you willl be give the option to manually select CD-ROM modules. Load drivers from Floppy? - Yes - No"[/I]
Answer 'No' to the question and 

**SOLUTION**
**1.**
Switch to a second console pressing ctrl+alt+F2
Press Enter to activate that console
Type:```
modprobe ide-scsi
```

**2.**
Switch back to the first console pressing ctrl+alt+F1
You got another question:
*"Manually select a CD-ROM module and device?"*
Say 'Yes' and choose the right option for you.
Most probably you have to choose 'cdrom' or 'cdrom0'

**3.**
If it fails again, go back to the 'Debian Installer Main Menu' 
and choose again the option 'Detect and mount a CD-ROM'
Now it should work!

::::::: ::::::: ::::::: ::::::: ::::::: :::::::
For more information:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608)
[COLOR="Red"]***Thanks to [olalirole]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608/comments/5") for this workaround!!!***[/COLOR]

You bloody rock! I have been trying to get this to work for days and and days, and then some. I heart you.

---

### Post by shekhark on 2008-11-29
Thanks, this worked. Now I can upgrade my mom's iMac from Breezy Badger, which was still running smoothly from two years ago. Happy Thanksgiving all. :)

---

### Post by meinzy on 2008-12-03
First reply worked for my PPC G5.  Thanks for the info.:D

---

### Post by usielt05 on 2008-12-10
thanks for your help. its been 3 days of trying to install a small fileserver for my parents on a 2001 Sony VAIO. I think there were rats in it! This community is awesome! you saved me 300 dollars or so on a christmas present this year.

---

### Post by eraker on 2008-12-16
How is it that this loading the kernel module problem popped up? I've been installing debian-flavors for years on my clamshell and only now has this problem occurred. Isn't it sort of a ridiculously simple problem that should have been caught and fixed by now?

---

### Post by stream303 on 2008-12-16
Unfortunately, the bug seems to stay with us as I've never seen a respin for ppc.

About the only thing we can do is try not to let it happen again.  Establish an account on launchpad, and fire up the daily release of Jaunty Jackalope:

[http://cdimage.ubuntu.com/ports/](http://cdimage.ubuntu.com/ports/)

Or daily-live if you want to test out the live desktop installer.

Hopefully if problems like this are seen, we can identify them early, and alert the devs.  How they respond to that is another matter unknown to us unless we get really involved with Launchpad.  I think that some might think that if there is a problem, that Debian will magically fix it and it will roll down to Ubuntu without any notice.

Since I haven't kept up with Launchpad much beyond Hardy, I can't really say for sure - all I know is if we really care, perhaps fire up Jaunty and scream like a banshee. :)

---

### Post by eraker on 2008-12-16
Hmm. I've never complained about any linux development before (I've never felt justified complaining when I don't do any work to produce any Linux distros except use "popularity contest," which truly cannot be called "doing work"), so I even felt bad saying something here. 

It just seems like such an amazing problem that has never occurred with any Linux distro I've ever seen before (in my genuinely short 6 years of installing) and with such a fundamental thing it also seems like a colossal piece of negligence (which also, when debian worked, is why I thought it must be a kind of willful negligence).

---

### Post by stream303 on 2008-12-17
It isn't really just negligence, it is just a major lack of resources now that ppc is a community-supported port for Canonical, rather than an officially supported commercial architecture like x86 etc.  It is no surprise that the commercial architectures take precedence, and major things like this slip.

All we can do is try and notify devs early, and post work-around patches.  Eventually, if things get really rough, like they are doing with Xubuntu, one can try taking all their learned knowledge to perhaps Debian XFCE.

Don't worry about not participating.  You are doing that now even if the only accomplishment is that you've helped just ONE person out there.

---

### Post by cyberdork33 on 2008-12-17
> **stream303 said:**
> It isn't really just negligence, it is just a major lack of resources now that ppc is a community-supported port for Canonical, rather than an officially supported commercial architecture like x86 etc.  It is no surprise that the commercial architectures take precedence, and major things like this slip.
Ha, there has been a bug in the Ubuntu installer for the last three releases that leaves Intel Macs unbootable.

---

### Post by stream303 on 2008-12-18
I didn't know the lack of resources is hitting Intel mac too.

This is really strange, since I would think that with Ubuntu's extra emphasis to become more OSX-like, that an Intel Mac would be the perfect platform to show it off, and would therefore be the leader in this regard.

I guess the question is do other distros share these same bugs on the Intel Macs?  Could the EFI firmware updates I have seen recently released on the 10th help any?  (I obviously don't know what I'm talking about here with EFI, so this is a total shot in the dark!)

What worries me the most is that it seems as if our PPC and Intel/Mac architectures are suffering from the same lack of resources, or possibly something else beyond a dev or user's control.

Man, I don't know what to say.  How many more cycles of show-stopper bugs do we put up with, if solutions are presented by either devs or users, but don't get fixed.  Small bugs are one thing, but being unable to boot at all with subsequent release after release may be someone trying to send us all a message. :)

At this stage, are we just performing technical exercises, and maybe just expressing the Ubuntu spirit with each other getting over hurdles?  Maybe that's enough, but at some point one wonders if "community-supported" is just a one-way street.

---

### Post by pindham on 2008-12-18
Thanks. We are a rural school system in middle Georgia, USA, repurposing some old G3 iBooks, and we couldn't have moved forward without this tip.

---

### Post by cyberdork33 on 2008-12-19
> **stream303 said:**
> I guess the question is do other distros share these same bugs on the Intel Macs?  Could the EFI firmware updates I have seen recently released on the 10th help any?  (I obviously don't know what I'm talking about here with EFI, so this is a total shot in the dark!)Just Ubuntu-based ones that I know of. It is really not a Firmware issue (Apple isn't really interested in fixing Linux-related issues anyway, though they did fix keyboard issues once). The problem is that the Ubuntu installer properly updates the partition table for the EFI side of things (the GPT), but clears out the MBR partition table. The legacy table is required to use GRUB and thus boot Ubuntu, so after install you are left with an unbootable OS. fortunately, there is a tool that can sync the MBR table with the GPT which gets things working again.

> **stream303 said:**
> What worries me the most is that it seems as if our PPC and Intel/Mac architectures are suffering from the same lack of resources, or possibly something else beyond a dev or user's control.I think it is just the lack of Apple hardware using Linux Developers. They are really the only ones that care about such issues, and can test fixes properly.

> **stream303 said:**
> Man, I don't know what to say.  How many more cycles of show-stopper bugs do we put up with, if solutions are presented by either devs or users, but don't get fixed.  Small bugs are one thing, but being unable to boot at all with subsequent release after release may be someone trying to send us all a message. :)It has basically been a game of "not our fault".

---

### Post by technolalia on 2009-01-12
Has a bug been filed for these problems? A search on launchpad has turned up [https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/273510](https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/273510) as being the closest for the display problems, but not for the undetected cd drive.

The cd detection on Xubuntu Jaunty Alpha 2 is fine, although I boot up into a blank screen, so the display problems are still live.

---

### Post by tiresia on 2009-01-12
> **technolalia said:**
> Has a bug been filed for these problems? A search on launchpad has turned up [https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/273510](https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/273510) as being the closest for the display problems, but not for the undetected cd drive.

Please, read the first post of this thread

> The cd detection on Xubuntu Jaunty Alpha 2 is fine, although I boot up into a blank screen, so the display problems are still live.
Glad to hear that. Have you tried to give at bootup the option 'video=ofonly'

---

### Post by stream303 on 2009-01-12
Also try one of my favorite kernel parameters, *nosplash*

Example - at the second-stage of the yaboot boot: prompt, hit TAB to stop the countdown, and then you can try entering

```
Linux video=ofonly
or
Linux nosplash
or
Linux video=ofonly nosplash
```

That should get you a bit further hopefully.

---

### Post by DurocShark on 2009-01-12
I'd just like to say that the posted fix (modprobe ide-scsi) worked perfectly. In fact, it can be done at any point prior to the CD-ROM detection, and then when the installer tries to detect it, it will work fine with no errors. 

Thanks!

EDIT: The system is an iBook G3 500 w/640mb. If it matters to anybody.

---

### Post by Simply Stupid on 2009-01-12
i know this is a little random but please just click the link

[http://www.brotherlyrevenge.com/index.php?c=viral&m=index&id=6c0d5e55d75ec5244fb990d19dcb77c1](http://www.brotherlyrevenge.com/index.php?c=viral&m=index&id=6c0d5e55d75ec5244fb990d19dcb77c1)

---

### Post by airwhen on 2009-01-22
OK, I followed the instructions to the T and my results were not what is to be expected.

I loaded the CD and I went through the Country, Keyboard, and other screens finally ending at the "No Common CD-ROM drive was detected"

Answered the "no" to he question, opened up the new window, typed in modprobe ide-scsi and the DVD-ROM starts to go:  "Click.......Click.......Click Click" over and over.  When I return back the previous window, try to detect again, it ust keeps going in a loop back to the "No common CD-ROM drive detected"

Possible deviations: I used a DVD instead of a CD for the ISO?

Otherwise I am lost.  Anybody have any ideas???

I have a PowerBook G3 Pismo (2000) Firewire with DVD-ROM.

Thanks!

---

### Post by avtolle on 2009-01-22
You should not, IMO, click on "No"; rather, just go to the new terminal, input the command, come back to the prior screen, and select "Yes". That's what I recall I did, with success.

---

### Post by avtolle on 2009-01-22
Also, you have apparently downloaded and are trying to install the server version. If it were me, I would go back to the download site and get the alternate iso. From other posts, it appears that there is no final Desktop edition for 8.10 ppc.

---

### Post by airwhen on 2009-01-22
Thanks!

It was changing the ISO that fixed it.  The server one DID NOT work!

---

### Post by DrFarnsworth on 2009-01-25
After installing 8.4 and having it be really odd and buggy i am trying to install 8.10. 

System Ibook G4 900 mhz 

I am getting the same problems as other people with not finding the cd drive. But the given advice does not work for me.  After doing it and going back to the main screen if fails to find the cd drive. Also the CD drive keeps reading over and over in a loop. 

if i try again detecting hangs at 0%

---

### Post by mattnewham on 2009-02-01
Just as a note for 12" powerbook users - the key sequence for me was Fn+Apple+F2/F1

This then switched consoles

Matt

---

### Post by Yellowpolkadot1040 on 2009-02-01
> **tiresia said:**
> **The ubuntu-8.10-alternate-powerpc Installer-CD failes to detect the CD-ROM Drive.**

After choosing Language, Country and Keyboard-Layout, the Installer tries to detect the CD-ROM, but you get following massage:  

[I]"No common CD-ROM drive was detected
You may need to load additional CD-ROM drivers from a floppy... Otherwise you willl be give the option to manually select CD-ROM modules. Load drivers from Floppy? - Yes - No"[/I]
Answer 'No' to the question and 

**SOLUTION**
**1.**
Switch to a second console pressing ctrl+alt+F2
Press Enter to activate that console
Type:```
modprobe ide-scsi
```

**2.**
Switch back to the first console pressing ctrl+alt+F1
You got another question:
*"Manually select a CD-ROM module and device?"*
Say 'Yes' and choose the right option for you.
Most probably you have to choose 'cdrom' or 'cdrom0'

**3.**
If it fails again, go back to the 'Debian Installer Main Menu' 
and choose again the option 'Detect and mount a CD-ROM'
Now it should work!

::::::: ::::::: ::::::: ::::::: ::::::: :::::::
For more information:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608)
[COLOR="Red"]***Thanks to [olalirole]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608/comments/5") for this workaround!!!***[/COLOR]

ok...I am trying to load this on an old emac g4 ppc. I get to the screen that reads 

"No common CD-ROM drive was detected
You may need to load additional CD-ROM drivers from a floppy... Otherwise you willl be give the option to manually select CD-ROM modules. Load drivers from Floppy? - Yes - No"

i select no, and immediately another screen pops up that reads 

No common cd-rom drive wass detected. 
your cd-rom may be an old Mitsumi or another non-IDE, non-SCSI cd-rom drive. In that case you should choose which module to load and the device to use. If you dont know which module and device are needed, look for some documentation or try a network installation instead of a cd-rom installation.
manually select a cd-rom drive module and device? <yes> <no>

I have tried the ctrl+alt+f2 a number of times on this, and the first screen, and have tried every additional combination of alt, ctrl, apple, and f2 at both screens as well. I don't have an fn key on my keyboard. I might be completely missing something here, and would appreciate any help.

Also, if it helps, if I select <yes> after the second screen it takes me to this...

the automatic detection didn't find a cd-rom drive. you can try to lad a specific module if you have an unusual cd-rom drive (that is neither IDE nor SCSI). 
Module needed for accessing the cd-rom:   <none>       <cdrom>

if I select no then it tells me that it failed and to try detecting again...which starts the whole cycle over again.

---

### Post by caleb12 on 2009-02-04
@tiresia - you are a scholar and a gentleman!! Thank you for figuring this out... I actually have a use for this old powerbook - and I mean old...

Also, just FYI, I had to use FN+ALT+F2 to switch to console. I just kept playing with the keys... now, that I think of it though - you could also, drop to a command prompt from the main menu and issue the modprobe - then go back to mounting the cd... just a thought... 

thanks!

---

### Post by louvann on 2009-02-05
Add me to the thread. CDROM not detected. The terminal command fixes my PPC 450 dual install of 8.10 alternate ISO.

thanks

---

### Post by satiropan on 2009-02-09
Well well well, I have this 266MHz PPC 256MB ram strawberry Imac, I am trying to install Ubuntu Intrepid Ibex, I have downloaded the alternative version.
I had this 'no cdrom' problem and the 'modprobe ide-scsi' works perfectly (I do Alt+F2 to get to the other console, and Alt+F3 opens a third console...).
Anyway, after finishing installation, I reboot and I see the colored Ubuntu splash screen with progression bar moving. Then the progression bar finishes and the screen goes blank (actually the Imac seems going in stand-by, since the power switch turns from green to orange).
I still can hear HD activity but nothing happens.
As soon as I touch the power button, Imac turns off.
I have tried then to start (and also install) Ubuntu with 'video=ofonly' option but it is the same.
I am not so expert in ground linux, in one of my attempts I got a console request for userid and password, gave them and then I had the prompt, but I didn't now what to digit to get it start, I tried 'start x' but says I need to be root, I try to log as root, but it didn't get the password (actually I setted only one password during installation, it should work...
Can some of you experts help me?
Thanx

---

### Post by latchkeyed on 2009-02-09
> **calebio said:**
> I believe that computer has a function (fn) key. Try including that in Ctrl-Alt-F2 (so, Ctrl+Alt+Fn+F2). I remember it was either that, or using '2' instead of 'F2', though I can't remember which exactly.

Thanks! This did the trick.

12" G4 Powerbook here.

---

### Post by Yellowpolkadot1040 on 2009-02-10
ctrl/apple/shift(no fn key available) + f2 didn't work on my eMac G4. I had to go into the installer main  menu (just pressed enter until it got me there) 
arrow down to 'execute a shell' press enter
at the next dialogue, select <continue>
type modprobe ide-scsi 
enter
type exit
enter
it takes me back to the installer main menu where I detect and mount cdrom successfully, and am then able to complete the install without any other problems...

until I try to start up after the install completes. It goes through all of the loading screens all the way through where it says ubuntu with the progress bar, and when the progress bar is done, everything just goes black...the fan is still running and the computer seems to be on, but there is nothing else. I tried letting it sit like this for quite a while...just to see what would happen...still nothing. I even tried reinstalling from scratch two more times, and still had the same problem both times. I am hoping someone here can help with this...I don't know if i did something wrong with the modprobe (i don't know why it would continue to load perfectly if I had). Or if there is just some other issue that I don't know about on these eMac G4s....Please help

---

### Post by tiresia on 2009-02-10
[QUOTE=Yellowpol]
until I try to start up after the install completes. It goes through all of the loading screens all the way through where it says ubuntu with the progress bar, and when the progress bar is done, everything just goes black... [/QUOTE]
When you reboot after the installation, at the first (Yaboot) prompt type:
```
video=ofonly nosplash
``` 
After that, if you get a working X (grafic interface) you should edit your file /etc/X11/xorg.conf
For further help, please post a new thread, since your issue has nothing to do with install process :)
Let us know, how Intrepid works for you

---

### Post by ccressman on 2009-02-11
Hello Everyone,

I have been trying to install it on a G3 New world Mac.

I get the same problem as everyone else with the modprobe issue but i can get past that. The issue I am getting is that before the partition stage of the installation it does a hardware detect by the end of the hardware detect it gives me a warning that it failed to copy some files from the cd rom it will give me the option to retry or not. No matter how many retry's it seems to be stuck i a loop. Then when i select no it proceeds to the partion aspect of the install. I can go through this stage and partion the hard drive at this point the screen goes red and says that it can't not find a cd rom.

I have burned different cd's i have redownloaded the iso. I am running out of ideas. Has any one else ran into this issue?

Thanks

---

### Post by tiresia on 2009-02-11
How did you burn the iso image? Do you still have a Mac OS on your g3?

---

### Post by ccressman on 2009-02-11
I burned the images on my G5 Toast 9 Titanium. Also all the installs fail at the same spot. I was able to get a base gentoo installed on the G3

---

### Post by tiresia on 2009-02-11
In those old g3 the cd-rom's are quite 'sensitive'. 
The easiest solution is to use the same drives you will boot from.
So, if you still have gentoo on it use it to burn at low speed the iso image (as root would be better) 
Otherwise try to burn the image in your g5 with the apple disk utility.
If you still get problems, try with Ubuntu hardy (8.04) and update it.
....
How much RAM do you have, and the Processor? I must say, on old hardware, I find that the best solution is Debian (may be Lenny) using Xfce as Desktop.

---

### Post by ccressman on 2009-02-11
Hey thanks for the help!

So i burned it at 2x and i got through pretty much the whole thing until I got to the server settings. I selected everything i wanted to install for the server. It installed a lot of the things and then it failed so i fired up the gentoo cd and ran the boot configuration and now it works.

Thanks

---

### Post by ant2ne on 2009-02-11
iBook and and eMac. This solution worked on the emac, but not the iBook. Still hoping for a solution.

EDIT: Hmm.. I restarted and did the modprobe stuff before the CD had a chance to spin down. It then worked. Thanks

EDIT: Hmm.. Well I got to Configurint apt 12% and it stopped. I think the CD stopped spinning again.

EDIT: Yep, used the CD on my eMac. It worked fine. So I can't blame the CD. Tried install again. Why would it hang at 12% every time. I don't think this is a CD or CD-ROM problem.

---

### Post by primeq on 2009-02-14
Yes - thanks x 1000

we just have to love open-source, and especially Ubuntu. 

Great post  you :guitar: (rock)

---

### Post by thalavoy on 2009-02-16
This is the answer what I had been looking for some time now.
First, I tried Jaunty live cd. It would not proceed.
When I tried 8.10, I got this missing CDrom error. Thanks to you, I am able to proceed a little further.
But looks like my CD is corrupt. It fails on some corrupt .deb files.
Will have to reburn?
Any way to fix the live cd problem too? Thanks

---

### Post by dodle on 2009-02-17
Thanks, worked for me.

---

### Post by ghostz on 2009-02-19
> **calebio said:**
> Problem solved: at the yaboot prompt, run "Linux video=ofonly". Then once booted, edit /etc/yaboot.conf to include the following:
```
  append="video=ofonly"
```

i have tried this and now it starts up and tells me ubuntu is going to start in low video mode i tried to edit the yaboot.conf but i dont think it will help me solve my problem is there any way to get it set to the right properties

i have an ibook g3 dual usb it has ati rage mobility m3 agp 2x video card is hter any fix for my problem ?

---

### Post by DonaldJ on 2009-02-20
Maybe the solution is to maintain both OS-10, and Ubuntu on the same hard drive.. to prevent these clock contradiction "no-boot issues"..?

It's worth a try given that nothing else works... 
It's to be my next attempt...  Do a clean OS-10 install, plus update, in one of two partitions.. then install Ubuntu 810 in the other, then try to make a bootable image CD of the hd..  then do the Ubuntu updates... I guess..?

Has Anyone managed to get the latest Ubuntu-810 running in an iMac-G3..?

---

### Post by fusk on 2009-03-03
> **calebio said:**
> Problem solved: at the yaboot prompt, run "Linux video=ofonly". Then once booted, edit /etc/yaboot.conf to include the following:
```
  append="video=ofonly"
```


happens to me too, i'll try your solution, just know, that this is the first time i've ever touched linux, so might return for help :)

---

### Post by Roshow on 2009-03-03
Wonderful, Works great

---

### Post by fusk on 2009-03-03
How do i edit the yaboot.conf ? when i open it, and add append="video=ofonly" and then save it, it says that i don't have permissions.
Another thing is that after i rebooted, my top menubar dosn't appear, and i can't use home or file system because they only appear for a sec, then they close again.

---

### Post by tiresia on 2009-03-03
> **fusk said:**
> How do i edit the yaboot.conf ? when i open it, and add append="video=ofonly" and then save it, it says that i don't have permissions.
To edit yaboot.conf ```
sudo nano /etc/yaboot.conf
```
When you are ready, exit (ctrl-X) and say 'Yes'
Now run```
ybin -v
```

---

### Post by cj0hns0n on 2009-03-14
> **tiresia said:**
> **The ubuntu-8.10-alternate-powerpc Installer-CD failes to detect the CD-ROM Drive.**

After choosing Language, Country and Keyboard-Layout, the Installer tries to detect the CD-ROM, but you get following massage:  

[I]"No common CD-ROM drive was detected
You may need to load additional CD-ROM drivers from a floppy... Otherwise you willl be give the option to manually select CD-ROM modules. Load drivers from Floppy? - Yes - No"[/I]
Answer 'No' to the question and 

**SOLUTION**
**1.**
Switch to a second console pressing ctrl+alt+F2
Press Enter to activate that console
Type:```
modprobe ide-scsi
```

**2.**
Switch back to the first console pressing ctrl+alt+F1
You got another question:
*"Manually select a CD-ROM module and device?"*
Say 'Yes' and choose the right option for you.
Most probably you have to choose 'cdrom' or 'cdrom0'

**3.**
If it fails again, go back to the 'Debian Installer Main Menu' 
and choose again the option 'Detect and mount a CD-ROM'
Now it should work!

::::::: ::::::: ::::::: ::::::: ::::::: :::::::
For more information:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608)
[COLOR="Red"]***Thanks to [olalirole]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608/comments/5") for this workaround!!!***[/COLOR]

I have this same problem that has bugging me for days. I found this thread and thouht ahha..Found the issue, but when I tried modprobe ide-scsi, it the system returned FATAL: Module ide_scsi not found..Any suggestions?

---

### Post by goldblattster on 2009-03-15
Thanks for this!:popcorn:

---

### Post by Tommmyboy on 2009-03-21
yes, months later after the original post, but much thanks to the OP because I was tearing my hair out.  thank you!

---

### Post by rodney757 on 2009-04-01
Thanks, this worked flawlessly for  intrepid server install on a G3

---

### Post by mSebrasky on 2009-04-03
> **cj0hns0n said:**
> I have this same problem that has bugging me for days. I found this thread and thouht ahha..Found the issue, but when I tried modprobe ide-scsi, it the system returned FATAL: Module ide_scsi not found..Any suggestions?

I'm having the same issue. Any ideas on how to proceed from here?

---

### Post by tiresia on 2009-04-03
> **cj0hns0n said:**
> I have this same problem that has bugging me for days. I found this thread and thouht ahha..Found the issue, but when I tried modprobe ide-scsi, it the system returned FATAL: Module ide_scsi not found..Any suggestions?

I'm not sure, but try to boot this way
```
install append="modprobe ide-scsi"
```

---

### Post by Davirus on 2009-04-11
No one of the 3 options works for me u.u

the 1st one froze the computer
the 2nd and 3th option does the same:

it pop up a window where I have to type where is my drive location.
"In order to access your CD-ROM drive, please enter the device file that should be used. Non-Standard CD-ROM drives use non-standard device files (such as /dev/mcdx).

You may switch to the shell on the second terminal (alt+f2) to check available devies in /dev with "1s /dev, You can return to this screen by pressing alt+f1.

Devices file for accessing the CD-ROM:

----------------------------------------------------
"

and there I dont know what to do.

---

### Post by maluka on 2009-04-25
The first answer worked on my G4 mac mini. :guitar:

---

### Post by Can-of-Bees on 2009-04-30
I'm finding that none of these options work on my iBook G3 500mhz, 384MB of ram -- any other suggestions?

I'm using Ubuntu 8.04.1 alternate install CD, burned at 4x w/ Mac OS X's Disk Utility.

Thanks,
C-o-B

---

### Post by abeyer on 2009-06-02
I have had this problem with both intrepid and jaunty. Some machines will work after loading ide-scsi, but I've never gotten it to work on my imac G4 700. The ide-scsi module loads but doesn't help, and the drive doesn't even show in the dmesg issue. I assume there is something strange in the drive or controller on this machine.
A workaround I've used to get cd booting to work is to boot off an external usb cdrom drive. I'm not sure open firmware will always cooperate in doing this, and it may only work with some drives, but it's worked for me on the aforementioned imac.

[LIST=1]
[*]Attach an external usb cdrom drive. (I'd use a built-in usb port for better chance of success here.) It will make step 3 easier if you detach any other external disks while doing this.
[*]Boot into open firmware. (Cmd-Opt-o-f during boot)
[*]Find the device path. At the ok> prompt, enter ```
show-devs /
``` It will print the tree of devices on your machine. You need to find the path to the usb cdrom. It will vary from one machine to another, but will be something like /pci/usb/disk. On mine it is /pci@f2000000/usb@18/disk@2
[*]Boot from this device. Again at the ok> prompt, type ```
boot *device-path*:,\install\yaboot
``` where *device-path* is the path you found in step 3. (In my case the whole command was [FONT=Courier New]boot /pci@f2000000/usb@18/disk@2:,\install\yaboot[/FONT]
[/LIST]
[LEFT][FONT=Courier New][FONT=Verdana]If all goes well, it should load to the yaboot boot prompt and you can start the live image or installer from there as usual.[/FONT]
[/FONT][/LEFT]

---

### Post by D0ri on 2009-07-02
I've got a problem with Powerbook G3.

I write "modrobe ide=scsi", and then press ctral+fn+alt+F2.
and then choose to manually select cdrom, choose the right one (there is "none" and "cdrom" and press enter to mount: "/dev/cdrom"
press enter and it doesn't work! :(

What can I do?

thanks guys ;)

---

### Post by krozzie on 2009-07-23
worked a treat for my imac g3 (ubuntu - powerpc 8.10)

for my 2 cents, just wait till the cdrom errors come up. Change the install menu to [command prompt] type modprobe ide-scsi {enter} than type " exit " {enter}... give it ago again and presto :D ignore  the ctrl+plus crap, this method is simple and works (for me on my 350Mhz g3 imac)!

it worked very well for myself! I suggest to speed up the install remove your network cable!!! :D

Also the imac g3 doesn't support kingston 512mb pc133 sd-ram :( I've heard 256mb works ok but depends on the brand...

2&3/4 cents ended

---

### Post by Exodist on 2009-08-07
> **tiresia said:**
> **The ubuntu-8.10-alternate-powerpc Installer-CD failes to detect the CD-ROM Drive.**

After choosing Language, Country and Keyboard-Layout, the Installer tries to detect the CD-ROM, but you get following massage:  

[I]"No common CD-ROM drive was detected
You may need to load additional CD-ROM drivers from a floppy... Otherwise you willl be give the option to manually select CD-ROM modules. Load drivers from Floppy? - Yes - No"[/I]
Answer 'No' to the question and 

**SOLUTION**
**1.**
Switch to a second console pressing ctrl+alt+F2
Press Enter to activate that console
Type:```
modprobe ide-scsi
```**2.**
Switch back to the first console pressing ctrl+alt+F1
You got another question:
*"Manually select a CD-ROM module and device?"*
Say 'Yes' and choose the right option for you.
Most probably you have to choose 'cdrom' or 'cdrom0'

**3.**
If it fails again, go back to the 'Debian Installer Main Menu' 
and choose again the option 'Detect and mount a CD-ROM'
Now it should work!

::::::: ::::::: ::::::: ::::::: ::::::: :::::::
For more information:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608)
[COLOR=Red]***Thanks to [olalirole]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608/comments/5") for this workaround!!!***[/COLOR]


When I do this it shows only 'cdrom' on step 2 but will not use it, then I try step 3 and when choosing 'detect and mount a CD-ROM' it hangs the system.

Any suggestions?

---

### Post by mliebo on 2009-10-26
Worked perfectly on an Xserve G5 Cluster node system.

---

### Post by omarjimz on 2009-11-24
Hello!
 
This is not working for me. I don't know if this is because the version but I would not think that, please confirm. 
 
I am trying to install the Ubuntu Server 8.04.3 on an hp Proliant DL320 G6 but the same error happens.
 
I have tried the modprobe ide-scsi on a secondary console but nothing is better.
 
Can someone help?
 
Thanks!

---

### Post by krozzie on 2009-11-25
> **omarjimz said:**
> 
I am trying to install the Ubuntu Server 8.04.3 on an hp Proliant DL320 G6 but the same error happens.
 
I have tried the modprobe ide-scsi on a secondary console but nothing is better.


I've noticed your hardware is intel xeon based. Also there is this:
Infrastructure management/iLO Standard and HP Systems Insight Manager (SIM) - There maybe no support for it on the 8.04 version

The 9.04 version looks like the go:

[http://www.ubuntu.com/news/hp-proliant-servers-certified-ubuntu](http://www.ubuntu.com/news/hp-proliant-servers-certified-ubuntu)

---

### Post by TheSmokingGNU on 2010-01-07
Hi, thanks for all the help so far. I had the CD problem, but the modprobe fixed it. My problem, however, is that the base system won't install. Any ideas? It either hangs the system up, or fails to install indefinitely. It's an old Imac G3 500mhz I think. I had a little trouble trying to identify the exact specs.

---

### Post by tiresia on 2010-01-08
> **TheSmokingGNU said:**
> My problem, however, is that the base system won't install. Any ideas? It either hangs the system up, or fails to install indefinitely. It's an old Imac G3 500mhz I think. I had a little trouble trying to identify the exact specs.
I guess the battery is dead - or not? If it's so, try to set date and time following this link. Please, let me know, if this helps
[http://www.macosxhints.com/article.php?story=20060814075952448&mode=print](http://www.macosxhints.com/article.php?story=20060814075952448&mode=print)

---

### Post by TheSmokingGNU on 2010-01-09
thanks, that did help me set the clock right, but not really the issue here. :)

I can't install ubuntu on the system. It's an iMac G3 and I am using the PowerPC alternate install for Intrepid. It won't install the base system, I don't know why, but it hates me. I mean, I got the thing for free, so I guess I can't complain, but... it'd be nice to have this working. :)

---

### Post by tiresia on 2010-01-09
> **TheSmokingGNU said:**
> My problem, however, is that the base system won't install. Any ideas? It either hangs the system up, or fails to install indefinitely. It's an old Imac G3 500mhz I think. I had a little trouble trying to identify the exact specs.
Just to understand if it is a hardware related problem, try to install another version or debian lenny (stable)
May be you can start another thread

---

### Post by TheSmokingGNU on 2010-01-09
well, I'd really rather have ubuntu on there, cause I am more familiar with it, but... alright I'll try lenny. Thanks!

---

### Post by apt29 on 2010-03-30
The solution to this issue:
 
The cd-rom is detected as /dev/hdc during my PPC MAC G4 installation. Do a manual selection of CDROM and replace /dev/cdrom0 with /dev/hdc.
 
Hope this helps.

---

### Post by rumel1988 on 2010-04-08
hello,
first think i'm unable to open an thread on ubuntu forum.(wts the problem?) :(

recently i'm installed xubuntu on my iBook G3(700Mhz). and got an problem! it's hearting me continually. :@
my problem is, my iBook work grate on xubuntu but my CD ROM won't working!!
but VLC played Video CD great. i'm confused! when i insert a data cd xubuntu don't show cd drive also don't eject CD drive(Fn+F12). previous time of installing xubuntu i was try ubuntu powerpc edition on my iBook and CD ROM work great. :)
please tell me how to get CD ROM driver/Icon on xubuntu?
please. :)
thanks in advance.

---

### Post by linuxopjemac on 2010-04-08
You probably have to link something

You have to find out what your cdrom is, probably something like /dev/hdb..Find this out first. If you know it, then go to /dev:
```
cd /dev
```
and link hdb with cdrom:
```
sudo ln -s hdb cdrom
```

it could also be cdrom0:
```
sudo ln -s hdb cdrom0
```
replace hdb by your device id.

reboot and your CDROM has to show up automatically

---

### Post by rumel1988 on 2010-04-08
thank u very match :)
I'm gonna try. and feedback u so soon as possible. :)

---

### Post by rumel1988 on 2010-04-09
hey,
it's already known  hdb as cdrom(see sysinfo on Screenshot). when i insert a data(or anything else)cd my cdrom show as half invisible(see Screenshot). and if trying to mount, that shoe a error msg. please what can i do?

[[IMG]http://img339.imageshack.us/img339/691/screenshot1gp.jpg[/IMG]](http://img339.imageshack.us/i/screenshot1gp.jpg/)

---

### Post by linuxopjemac on 2010-04-09
what happens if you go to /dev/cdrom0 in the terminal ?

---

### Post by rumel1988 on 2010-04-09
> **linuxopjemac said:**
> what happens if you go to /dev/cdrom0 in the terminal ?
see attachment.
is I'm do ok?

---

### Post by linuxopjemac on 2010-04-09
give me the output of 
```
ls -al /dev
```

and paste it here

---

### Post by rumel1988 on 2010-04-10
> **linuxopjemac said:**
> give me the output of 
```
ls -al /dev
```

and paste it here

sorry for late. 

here is output:

```
salman@ubuntu:~$ ls -al /dev
total 4
drwxr-xr-x  14 root root        3640 2010-04-10 15:05 .
drwxr-xr-x  21 root root        4096 2010-04-07 07:50 ..
crw-rw----   1 root root     56,   0 2010-04-10 15:00 adb
crw-------   1 root video    10, 175 2010-04-10 15:00 agpgart
crw-rw----   1 root root     10, 134 2010-04-10 15:00 apm_bios
crw-rw----+  1 root audio    14,   4 2010-04-10 15:00 audio
drwxr-xr-x   2 root root         680 2010-04-10 15:05 block
drwxr-xr-x   3 root root          60 2010-04-10 15:00 bus
lrwxrwxrwx   1 root root           3 2010-04-10 15:00 cdrom -> hdb
drwxr-xr-x   2 root root        2980 2010-04-10 15:05 char
crw-------   1 root root      5,   1 2010-04-10 15:00 console
lrwxrwxrwx   1 root root          11 2010-04-10 15:00 core -> /proc/kcore
crw-rw----   1 root root     10,  63 2010-04-10 15:00 cpu_dma_latency
drwxr-xr-x   6 root root         120 2010-04-10 15:00 disk
drwxr-xr-x   2 root root          60 2010-04-10 15:00 dri
crw-rw----+  1 root audio    14,   3 2010-04-10 15:00 dsp
crw-rw----   1 root video    29,   0 2010-04-10 15:00 fb0
lrwxrwxrwx   1 root root          13 2010-04-10 15:00 fd -> /proc/self/fd
crw-rw-rw-   1 root root      1,   7 2010-04-10 15:00 full
crw-rw-rw-   1 root fuse     10, 229 2010-04-10 15:00 fuse
brw-rw----   1 root disk      3,   0 2010-04-10 15:00 hda
brw-rw----   1 root disk      3,   1 2010-04-10 15:00 hda1
brw-rw----   1 root disk      3,   2 2010-04-10 15:00 hda2
brw-rw----   1 root disk      3,   3 2010-04-10 15:00 hda3
brw-rw----   1 root disk      3,   4 2010-04-10 15:00 hda4
brw-rw----+  1 root cdrom     3,  64 2010-04-10 15:00 hdb
crw-rw----   1 root dialout 229,   0 2010-04-10 15:00 hvc0
crw-rw----   1 root dialout 229,   1 2010-04-10 15:00 hvc1
crw-rw----   1 root dialout 229,   2 2010-04-10 15:00 hvc2
crw-rw----   1 root dialout 229,   3 2010-04-10 15:00 hvc3
crw-rw----   1 root dialout 229,   4 2010-04-10 15:00 hvc4
crw-rw----   1 root dialout 229,   5 2010-04-10 15:00 hvc5
crw-rw----   1 root dialout 229,   6 2010-04-10 15:00 hvc6
crw-rw----   1 root dialout 229,   7 2010-04-10 15:00 hvc7
drwxr-xr-x   3 root root         100 2010-04-10 15:00 .initramfs
-rw-r--r--   1 root root           0 2010-04-10 15:00 .initramfs-tools
drwxr-xr-x   2 root root         280 2010-04-10 15:01 input
crw-rw----   1 root root      1,  11 2010-04-10 15:00 kmsg
srw-rw-rw-   1 root root           0 2010-04-10 15:00 log
brw-rw----   1 root disk      7,   0 2010-04-10 15:00 loop0
brw-rw----   1 root disk      7,   1 2010-04-10 15:00 loop1
brw-rw----   1 root disk      7,   2 2010-04-10 15:00 loop2
brw-rw----   1 root disk      7,   3 2010-04-10 15:00 loop3
brw-rw----   1 root disk      7,   4 2010-04-10 15:00 loop4
brw-rw----   1 root disk      7,   5 2010-04-10 15:00 loop5
brw-rw----   1 root disk      7,   6 2010-04-10 15:00 loop6
brw-rw----   1 root disk      7,   7 2010-04-10 15:00 loop7
crw-r-----   1 root kmem      1,   1 2010-04-10 15:00 mem
crw-rw----+  1 root audio    14,   0 2010-04-10 15:00 mixer
drwxr-xr-x   2 root root          60 2010-04-10 15:00 net
crw-rw----   1 root root     10,  62 2010-04-10 15:00 network_latency
crw-rw----   1 root root     10,  61 2010-04-10 15:00 network_throughput
crw-rw-rw-   1 root root      1,   3 2010-04-10 15:00 null
crw-r-----   1 root kmem     10, 144 2010-04-10 15:00 nvram
crw-rw----   1 root video    10, 154 2010-04-10 15:00 pmu
crw-r-----   1 root kmem      1,   4 2010-04-10 15:00 port
crw-------   1 root root    108,   0 2010-04-10 15:00 ppp
crw-rw----   1 root root     10,   1 2010-04-10 15:00 psaux
crw-rw-rw-   1 root tty       5,   2 2010-04-10 15:06 ptmx
drwxr-xr-x   2 root root           0 2010-04-10 15:00 pts
brw-rw----   1 root disk      1,   0 2010-04-10 15:00 ram0
brw-rw----   1 root disk      1,   1 2010-04-10 15:00 ram1
brw-rw----   1 root disk      1,  10 2010-04-10 15:00 ram10
brw-rw----   1 root disk      1,  11 2010-04-10 15:00 ram11
brw-rw----   1 root disk      1,  12 2010-04-10 15:00 ram12
brw-rw----   1 root disk      1,  13 2010-04-10 15:00 ram13
brw-rw----   1 root disk      1,  14 2010-04-10 15:00 ram14
brw-rw----   1 root disk      1,  15 2010-04-10 15:00 ram15
brw-rw----   1 root disk      1,   2 2010-04-10 15:00 ram2
brw-rw----   1 root disk      1,   3 2010-04-10 15:00 ram3
brw-rw----   1 root disk      1,   4 2010-04-10 15:00 ram4
brw-rw----   1 root disk      1,   5 2010-04-10 15:00 ram5
brw-rw----   1 root disk      1,   6 2010-04-10 15:00 ram6
brw-rw----   1 root disk      1,   7 2010-04-10 15:00 ram7
brw-rw----   1 root disk      1,   8 2010-04-10 15:00 ram8
brw-rw----   1 root disk      1,   9 2010-04-10 15:00 ram9
crw-rw-rw-   1 root root      1,   8 2010-04-10 15:00 random
crw-rw----   1 root root    254,   0 2010-04-10 15:00 rtc0
brw-rw----   1 root disk      8,   0 2010-04-10 15:05 sda
brw-rw----   1 root disk      8,   1 2010-04-10 15:05 sda1
crw-rw----+  1 root audio    14,   1 2010-04-10 15:00 sequencer
crw-rw----+  1 root audio    14,   8 2010-04-10 15:00 sequencer2
crw-rw----   1 root disk     21,   0 2010-04-10 15:05 sg0
drwxrwxrwt   2 root root          40 2010-04-10 15:00 shm
crw-rw----   1 root root     10, 231 2010-04-10 15:00 snapshot
drwxr-xr-x   3 root root         160 2010-04-10 15:00 snd
lrwxrwxrwx   1 root root          24 2010-04-10 15:00 sndstat -> /proc/asound/oss/sndstat
lrwxrwxrwx   1 root root          15 2010-04-10 15:00 stderr -> /proc/self/fd/2
lrwxrwxrwx   1 root root          15 2010-04-10 15:00 stdin -> /proc/self/fd/0
lrwxrwxrwx   1 root root          15 2010-04-10 15:00 stdout -> /proc/self/fd/1
crw-rw-rw-   1 root tty       5,   0 2010-04-10 15:00 tty
crw--w----   1 root root      4,   0 2010-04-10 15:00 tty0
crw-------   1 root root      4,   1 2010-04-10 15:01 tty1
crw--w----   1 root tty       4,  10 2010-04-10 15:00 tty10
crw--w----   1 root tty       4,  11 2010-04-10 15:00 tty11
crw--w----   1 root tty       4,  12 2010-04-10 15:00 tty12
crw--w----   1 root tty       4,  13 2010-04-10 15:00 tty13
crw--w----   1 root tty       4,  14 2010-04-10 15:00 tty14
crw--w----   1 root tty       4,  15 2010-04-10 15:00 tty15
crw--w----   1 root tty       4,  16 2010-04-10 15:00 tty16
crw--w----   1 root tty       4,  17 2010-04-10 15:00 tty17
crw--w----   1 root tty       4,  18 2010-04-10 15:00 tty18
crw--w----   1 root tty       4,  19 2010-04-10 15:00 tty19
crw-------   1 root root      4,   2 2010-04-10 15:00 tty2
crw--w----   1 root tty       4,  20 2010-04-10 15:00 tty20
crw--w----   1 root tty       4,  21 2010-04-10 15:00 tty21
crw--w----   1 root tty       4,  22 2010-04-10 15:00 tty22
crw--w----   1 root tty       4,  23 2010-04-10 15:00 tty23
crw--w----   1 root tty       4,  24 2010-04-10 15:00 tty24
crw--w----   1 root tty       4,  25 2010-04-10 15:00 tty25
crw--w----   1 root tty       4,  26 2010-04-10 15:00 tty26
crw--w----   1 root tty       4,  27 2010-04-10 15:00 tty27
crw--w----   1 root tty       4,  28 2010-04-10 15:00 tty28
crw--w----   1 root tty       4,  29 2010-04-10 15:00 tty29
crw-------   1 root root      4,   3 2010-04-10 15:00 tty3
crw--w----   1 root tty       4,  30 2010-04-10 15:00 tty30
crw--w----   1 root tty       4,  31 2010-04-10 15:00 tty31
crw--w----   1 root tty       4,  32 2010-04-10 15:00 tty32
crw--w----   1 root tty       4,  33 2010-04-10 15:00 tty33
crw--w----   1 root tty       4,  34 2010-04-10 15:00 tty34
crw--w----   1 root tty       4,  35 2010-04-10 15:00 tty35
crw--w----   1 root tty       4,  36 2010-04-10 15:00 tty36
crw--w----   1 root tty       4,  37 2010-04-10 15:00 tty37
crw--w----   1 root tty       4,  38 2010-04-10 15:00 tty38
crw--w----   1 root tty       4,  39 2010-04-10 15:00 tty39
crw-------   1 root root      4,   4 2010-04-10 15:00 tty4
crw--w----   1 root tty       4,  40 2010-04-10 15:00 tty40
crw--w----   1 root tty       4,  41 2010-04-10 15:00 tty41
crw--w----   1 root tty       4,  42 2010-04-10 15:00 tty42
crw--w----   1 root tty       4,  43 2010-04-10 15:00 tty43
crw--w----   1 root tty       4,  44 2010-04-10 15:00 tty44
crw--w----   1 root tty       4,  45 2010-04-10 15:00 tty45
crw--w----   1 root tty       4,  46 2010-04-10 15:00 tty46
crw--w----   1 root tty       4,  47 2010-04-10 15:00 tty47
crw--w----   1 root tty       4,  48 2010-04-10 15:00 tty48
crw--w----   1 root tty       4,  49 2010-04-10 15:00 tty49
crw-------   1 root root      4,   5 2010-04-10 15:00 tty5
crw--w----   1 root tty       4,  50 2010-04-10 15:00 tty50
crw--w----   1 root tty       4,  51 2010-04-10 15:00 tty51
crw--w----   1 root tty       4,  52 2010-04-10 15:00 tty52
crw--w----   1 root tty       4,  53 2010-04-10 15:00 tty53
crw--w----   1 root tty       4,  54 2010-04-10 15:00 tty54
crw--w----   1 root tty       4,  55 2010-04-10 15:00 tty55
crw--w----   1 root tty       4,  56 2010-04-10 15:00 tty56
crw--w----   1 root tty       4,  57 2010-04-10 15:00 tty57
crw--w----   1 root tty       4,  58 2010-04-10 15:00 tty58
crw--w----   1 root tty       4,  59 2010-04-10 15:00 tty59
crw-------   1 root root      4,   6 2010-04-10 15:00 tty6
crw--w----   1 root tty       4,  60 2010-04-10 15:00 tty60
crw--w----   1 root tty       4,  61 2010-04-10 15:00 tty61
crw--w----   1 root tty       4,  62 2010-04-10 15:00 tty62
crw--w----   1 root tty       4,  63 2010-04-10 15:00 tty63
crw--w----   1 root root      4,   7 2010-04-10 15:00 tty7
crw--w----   1 root tty       4,   8 2010-04-10 15:01 tty8
crw--w----   1 root tty       4,   9 2010-04-10 15:00 tty9
crw-rw----   1 root dialout 204, 192 2010-04-10 15:00 ttyPZ0
crw-rw----   1 root dialout 204, 193 2010-04-10 15:00 ttyPZ1
drwxr-xr-x   7 root root         160 2010-04-10 15:05 .udev
crw-r-----   1 root root     10, 223 2010-04-10 15:00 uinput
crw-rw-rw-   1 root root      1,   9 2010-04-10 15:00 urandom
crw-rw----   1 root root    253,   0 2010-04-10 15:00 usbmon0
crw-rw----   1 root root    253,   1 2010-04-10 15:00 usbmon1
crw-rw----   1 root root    253,   2 2010-04-10 15:00 usbmon2
crw-rw----   1 root tty       7,   0 2010-04-10 15:00 vcs
crw-rw----   1 root tty       7,   1 2010-04-10 15:00 vcs1
crw-rw----   1 root tty       7,   2 2010-04-10 15:00 vcs2
crw-rw----   1 root tty       7,   3 2010-04-10 15:00 vcs3
crw-rw----   1 root tty       7,   4 2010-04-10 15:00 vcs4
crw-rw----   1 root tty       7,   5 2010-04-10 15:00 vcs5
crw-rw----   1 root tty       7,   6 2010-04-10 15:00 vcs6
crw-rw----   1 root tty       7,   7 2010-04-10 15:00 vcs7
crw-rw----   1 root tty       7,   8 2010-04-10 15:00 vcs8
crw-rw----   1 root tty       7, 128 2010-04-10 15:00 vcsa
crw-rw----   1 root tty       7, 129 2010-04-10 15:00 vcsa1
crw-rw----   1 root tty       7, 130 2010-04-10 15:00 vcsa2
crw-rw----   1 root tty       7, 131 2010-04-10 15:00 vcsa3
crw-rw----   1 root tty       7, 132 2010-04-10 15:00 vcsa4
crw-rw----   1 root tty       7, 133 2010-04-10 15:00 vcsa5
crw-rw----   1 root tty       7, 134 2010-04-10 15:00 vcsa6
crw-rw----   1 root tty       7, 135 2010-04-10 15:00 vcsa7
crw-rw----   1 root tty       7, 136 2010-04-10 15:00 vcsa8
crw-rw-rw-   1 root root      1,   5 2010-04-10 15:00 zero

```

---

### Post by linuxopjemac on 2010-04-10
I don't understand it. It looks good. cdrom is linked to hdb. Soon I will install Xubuntu on a PowerBook G3. I will have the same problem then I guess. I will update when I know the answer to this....

---

### Post by rumel1988 on 2010-04-10
> **linuxopjemac said:**
> I don't understand it. It looks good. cdrom is linked to hdb. Soon I will install Xubuntu on a PowerBook G3. I will have the same problem then I guess. I will update when I know the answer to this....

OK. thank you :)
and i'm waiting....

---

### Post by rumel1988 on 2010-04-11
hey, if u assist me also [this problem]("http://ubuntuforums.org/showpost.php?p=9097114&postcount=7") it's very helpful for me.
thank u.

---

### Post by rumel1988 on 2010-04-20
I'm waiting so long. :|

---

