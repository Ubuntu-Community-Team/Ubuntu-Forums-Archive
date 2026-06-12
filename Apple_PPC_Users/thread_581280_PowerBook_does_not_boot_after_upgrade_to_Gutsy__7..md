---
title: "PowerBook does not boot after upgrade to Gutsy / 7.10"
date: 2007-10-19
forum: Apple PPC Users
---

### Post by mbrennwa on 2007-10-19
Dear all

I upgraded my G4-PowerBook from 7.04 to 7.10 using the Software Update tool (System -> Administration -> Software Update). When I tried to reboot the machine, I got the Ubuntu logo with the progress bar. The progress bar shows no progress at all for a while (maybe a minute or so), then I get a black screen with the following:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Type 'help' to see list of available commands
(initramfs)

I can type 'help' and other commands to the prompt, but can't make any sense of it.

Can someone help me get my machine back to work?

Matthias

---

### Post by stmiller on 2007-10-19
See if this is the problem:

[http://ubuntuforums.org/showpost.php?p=3566460&postcount=9](http://ubuntuforums.org/showpost.php?p=3566460&postcount=9)

At the prompt that you get try

```
modprobe ide_core
```

to get it to boot, then

add

ide_core to /usr/share/initramfs-tools/modules

EDIT: Or to /etc/initramfs-tools/modules (?)

and then run

update-initramfs -u

to make the fix.

---

### Post by horobi on 2007-10-20
> **stmiller said:**
> See if this is the problem:

[http://ubuntuforums.org/showpost.php?p=3566460&postcount=9](http://ubuntuforums.org/showpost.php?p=3566460&postcount=9)

At the prompt that you get try

```
modprobe ide_core
```

to get it to boot, then

add

ide_core to /usr/share/initramfs-tools/module and running

update-initramfs -u

to make the fix.

how can i add ide_core to /usr/share/initramfs-tools/module and running from the busy box?

---

### Post by ubuntubrian on 2007-10-20
I can't even get to Busybox on my TiBook and on my G3Powerbook I do but I get nothing from the modprobe command, just a return to the prompt. "exit" also just returns to prompt.

---

### Post by trash on 2007-10-20
> **horobi said:**
> how can i add ide_core to /usr/share/initramfs-tools/module and running from the busy box?

EDIT:
/etc/initramfs-tools/modules is what worked for me too!

ok in busybox type and hit enter:

modprobe ide_core

after that

exit

boot will continue, but before you login hit keys
control/alt and F1, this will take you to a terminal where you will login and type

sudo vim /etc/initramfs-tools/modules

hit I to add text(add it to the bottom), add:

ide_core

hit esc to exit and :x to save. EDIT lol, the angry face is actually supposed to be : x together;)

Then run

sudo update-initramfs -u

then control/alt F7 to go back to login screen

Hope that helps!

---

### Post by trash on 2007-10-20
sadly after this fix i still get dumped to the busybox:(

---

### Post by dbeach7 on 2007-10-20
Hate to just say, "Me too," but I have the same problem with my old TiBook. When I try to boot I eventually get dropped to the busybox shell. At that point if I do

modprobe ide_core
exit

... the system boots. However, I edited /usr/share/initramfs-tools/modules by adding ide_core at the bottom, then did sudo update-initramfs -u, but I get no joy. Same situation on reboot.

OK, I got done typing this, and then I went and edited /etc/initramfs-tools/modules by adding ide_core and updating the initramfs again, and now it works. So the file you need to edit is the one in /etc, not the one in /usr/share. I'm not clear exactly as to why some advice I saw on this issue said to edit the wrong file, but there it is. Maybe editing /usr/share... works if the one in /etc does not exist (ie the system looks in /etc first and uses the first one it finds)?

---

### Post by stmiller on 2007-10-20
Thanks for the tips, dbeach. 
My old power adapter just crapped out from my Tibook, so I have to wait and order a new one now before any Gutsy love will happen for me. Grrrrr....

---

### Post by ubuntubrian on 2007-10-20
As before, on my old G3 I get a little graphic stuff then busybox. The commands just return to prompt so my question is what should happen after the "exit" command? Does the prompt return like happens for me and then the boot continue after some time? I waited a couple of minutes and the prompt just blinks away.
On my TiBool I get nothing past the initial "display found". Screen goes black and CD stops spinning and waiting for 3-4 minutes does nothing.

---

### Post by trash on 2007-10-20
> **dbeach7 said:**
> Hate to just say, "Me too," but I have the same problem with my old TiBook. When I try to boot I eventually get dropped to the busybox shell. At that point if I do

modprobe ide_core
exit

... the system boots. However, I edited /usr/share/initramfs-tools/modules by adding ide_core at the bottom, then did sudo update-initramfs -u, but I get no joy. Same situation on reboot.

OK, I got done typing this, and then I went and edited /etc/initramfs-tools/modules by adding ide_core and updating the initramfs again, and now it works. So the file you need to edit is the one in /etc, not the one in /usr/share. I'm not clear exactly as to why some advice I saw on this issue said to edit the wrong file, but there it is. Maybe editing /usr/share... works if the one in /etc does not exist (ie the system looks in /etc first and uses the first one it finds)?

Thanks for double checking that! It worked for me too:)

---

### Post by horobi on 2007-10-21
> **dbeach7 said:**
> Hate to just say, "Me too," but I have the same problem with my old TiBook. When I try to boot I eventually get dropped to the busybox shell. At that point if I do

modprobe ide_core
exit

... the system boots. However, I edited /usr/share/initramfs-tools/modules by adding ide_core at the bottom, then did sudo update-initramfs -u, but I get no joy. Same situation on reboot.

OK, I got done typing this, and then I went and edited /etc/initramfs-tools/modules by adding ide_core and updating the initramfs again, and now it works. So the file you need to edit is the one in /etc, not the one in /usr/share. I'm not clear exactly as to why some advice I saw on this issue said to edit the wrong file, but there it is. Maybe editing /usr/share... works if the one in /etc does not exist (ie the system looks in /etc first and uses the first one it finds)?

worked for my iMAC G3 too, thanks :)

---

### Post by Win2Mac2Linux on 2007-10-21
For what it's worth, I'm having the same problem with my Powerbook G4 17".  I was running Feisty 7.04 (fully updated) for the most part without any problems.  I upgraded through the Synaptic Package manager when it indicated that the newer version (Gutsy 7.10) was available.  After upgrading, upon reboot, well, you know what happened.  I'm just adding my 2c in case anyone is tracking how big (or small) a problem it really is.  It's late so I'm going to bed and going to try some of the suggestions here after I get up.  I'll post if I have success in trying what others have done...

---

### Post by codeman38 on 2007-10-21
Having the same issue here on a PowerBook G4 1.67GHz; just posted about it in [this thread](http://ubuntuforums.org/showthread.php?t=579487&page=3). I can't even get out of BusyBox by running 'modprobe ide_core'; it just kicks me right back into BusyBox after a failed attempt at mounting. And using the 'break=top' parameter in the boot loader makes it so that I can't even *type* at the BusyBox prompt, which makes running the modprobe just a bit difficult...

---

### Post by ChillMonkey on 2007-10-21
worked for me great on a TiBook Mercury. it was /etc/initramfs-tools/modules

---

### Post by Win2Mac2Linux on 2007-10-22
I've been having trouble figuring out how to edit the /etc/initramfs-tools/modules.  Whenever I try to add the ide_disk (I think that's correct) at the end and save it, it tells me I don't have proper clearance (so to speak).  I would do something else that requires me to login as root figuring that I would have access to anything, but still no go.  I was tempted to just reinstall 7.04 and wait till the bug fix, but I'm going to be a trooper and stick this out and learn.  
To review, when I boot it barely starts the "Ubuntu" screen and the progress bar stops almost immediately.  I eventually get the busybox part and enter both modprobe ide_core and modprobe ide_disk entries (not 100% sure what that is all about, but that's okay for now) and it continues to boot.  However, during the final steps my clock shows a date from 1903 and when I click on the option to configure it manually it says I can't access my config file.  The desktop eventually comes up after logging in, but a couple of things are missing including my network icon in the upper right.  
Any suggestions are greatly appreciated regarding how to get myself "cleared" to edit the modules file.  I figure I will see what happens after I am able to do that and hopefully that will be it.  Otherwise I'll be back with more questions.  Thanks again.

---

### Post by Caraibes on 2007-10-22
Thanks for the ide_core trick, as it worked for me on my G3 iBook.

Now, Gnome starts, and gives me an error message about not being able to start some daemons so there's no sound...

And the system is dog slow, it is scary...

I still have a Dapper PPC instll cd, shall I just go back to Dapper ?

---

### Post by dbeach7 on 2007-10-22
> **Win2Mac2Linux said:**
> I've been having trouble figuring out how to edit the /etc/initramfs-tools/modules.  Whenever I try to add the ide_disk (I think that's correct) at the end and save it, it tells me I don't have proper clearance (so to speak).

So the following line doesn't work for you?

sudo nano -w /etc/initramfs-tools/modules


>  I eventually get the busybox part and enter both modprobe ide_core and modprobe ide_disk entries (not 100% sure what that is all about, but that's okay for now)

The issue is that Gutsy evidently does not have the ide kernel bits available at boot, so it can't find the root filesystem. modprobe ide_core loads the relevant modules and the drives are detected. Putting "ide_core" in the aforementioned file tells the system to load these modules automatically.

I still find it a bit unbelievable that Gutsy could have been released with such an egregious bug that affects so many users.

---

### Post by juggle5 on 2007-10-23
Hi, I hope I don't come across as whiny but I also cannot upgrade to 7.10. Now I just got ubuntu maybe 10 days ago - just to give Linux a whirl and all was great then the system automatically updated to 7.10 and since then I cannot get it to run any more. After some time in the forums I have figured out that there IS indeed a problem with that install image and it's not just me being an incompetent stupid fool. Chalk it up to my stubbornness that I have not given up yet (I have wiped my machine, downloaded multiple copies of gutsy and failed to get them to run) 

Now, being a more or less total Linux newbie, I just don't see myself typing in all those sudo commands and the other magic that I see in the forum. I simply am not up to it right now. My level of linux expertise is to just play with the menus and learn that way. 

So I really want to a) share that issue with the forum and b) ask if anybody knows when there will be probably a correct installer image posted and where? How to recognize it? Honestly, I don't think I'll be successful trying to emulate all the various magic commands I read about on the forum to get gutsy to install. Imagine somebody who is using linux for the very first time as a gui user. Not the type of person who starts hacking around in sudo mode... And now I'm of course even hesitant to try a regular install CD somebody might sell...

Any advice? Should I just wipe the machine again, install Feisty (of which I have a good copy here) and wait a few weeks before I try again to get an image?

Juggle5

---

### Post by pxwpxw on 2007-10-23
[B]juggle5
[/B]
If you upgraded from 704 to 710, you should still have the old kernel as an option on the yaboot startup menu, tab key at the boot:  prompt should show it, try that.

Edit:
Just discoverd my upgrade does not provide a menu option to boot the old kernel.

 But the old 704 kernel is still in /boot, so you would need to edit /etc/yaboot.conf to add a menu option to boot the old vmlinux and initrd.img, and then run ybin to update the bootstrap files. 
Or you could just change the links in the /boot directory, that would be easier from a rescue cd..
Sorry, not as easy as I thought.
Grub does it much better for i386 boxes.

---

### Post by ubuntubrian on 2007-10-23
Gutsy is a mess if this is what is happening! different results and variations of the bug on different ppc boxes. A guy asks for gui fixes and there aren't any.gutsy is definitely not ready for prime time on the ppc platform. I will wait and stay with Dapper or my Feisty live cd.

---

### Post by ag0g0girl on 2007-10-23
Awwww, 

This is wierd.  I have a Titanium PowerBook G4.  I also came up with the busybox prompt on first boot after install of Gutsy.

I had to erase my os 10 to do the install since moving partitions with ipartition had broken my Fiesty...I was unable to upgrade.

I reinstalled the os 10 to view the fix for this, and copied it down and prepared to reboot Gutsy and type in the mod probe etc.

I didn't have to.  The Gutsy booted up.  The icon in the menu bar doesn't show the airport as an active network, but I do have internet just fine. First run of firefox crashed the app, but the update manager fixed that just fine.

I'm pleased with the increased screen resolution, but my sound is still not working...same as in Feisty.

Just to let you know... I had the same problem as you guys, but it fixed itself.

---

### Post by dennisdunbar on 2007-10-24
OK my machine works great if everytime i type in the modeprobe

I do not understand how to make the change to the file

I do the vim thing and I get a screen

I type I and the word inser appears at the botttom of terminal

If I type it types at the top and I sure cant digure out how to exit and save as my terminal does not make smiling faces.

Please help

---

### Post by arthurson on 2007-10-24
thx all guys, so my ibook g3 can use xubuntu now, it seems all powerpc users have this busybox problem, what a pity of this if ubuntu didn't fix it quickly. 
and now my airport can use wifi, but without wpa option, no idea  how to solve it.

---

### Post by trash on 2007-10-24
> **dennisdunbar said:**
> OK my machine works great if everytime i type in the modeprobe

I do not understand how to make the change to the file

I do the vim thing and I get a screen

I type I and the word inser appears at the botttom of terminal

If I type it types at the top and I sure cant digure out how to exit and save as my terminal does not make smiling faces.

Please help


Vim is very easy once you get the hang of it... ok once you inserted the text press the escape key(you'll see the insert disappear) now to save what you just typed you need to enter this command : x
no space between them!.. hit enter and you should be back to the terminal.

---

### Post by BladeMelbourne on 2007-10-24
IMO nano is an easier text editor to use.

sudo nano /path/to/file.ext

Ctrl o saves the file.
Ctrl x exits the editor.

Ctrl y scrolls up.
Ctrl v scrolls down.

Ctrl k cuts a line.
Ctrl u uncuts (pastes) a line.

---

### Post by Win2Mac2Linux on 2007-10-25
> **dbeach7 said:**
> So the following line doesn't work for you?

sudo nano -w /etc/initramfs-tools/modules



Unfortunately, no.  When I save the file it tells me "Error writing /etc/intramfs-tools/modules: No such file or directory"

Also lately my seems is locking up after a short time, not to mention that after logging in I get errors on a bunch of modules that load asking if I want to delete them or not with my home screen missing all of them.  I think my best bet may be to reload 7.04 and keep an eye out for a bug fix in an update patch or something.  "Thank you" to you and others who have been trying to help me and others with this problem.  I've noticed others have been able to get the problem fixed, but apparently not for me.  I agree with you about how this version was released with what appears to be a pretty widespread problem.  Thanks again.

---

### Post by Win2Mac2Linux on 2007-10-25
So I am back to installing 7.04 and now when the system boots from the live cd and goes to the desktop, I start getting the same errors I had after installing 7.10.  Multiple errors about various applets such as gnome, sound, etc.(whether I want to delete them or not) and my desktop has no icons, specifically the "install" option to install to the hard drive.  The icons at the top left are present (firefox, etc.), but those on the main part of the desktop are MIA. At first I thought maybe it wasn't booting from the cd, but I used the "force" option and the text screen comes up with the boot command waiting for which option I want to use from the cd.  I've tried both just hitting "enter" and also trying using the "live-powerpc" option and both give me the same results.  How can this possibly be happening off an install cd?  Now I can't even get my system back to 7.04.  Frustrated,but sticking with it.  Any help is appreciated.  Is there any way it is somehow jumping back over to the 7.10 version when booting, even if I'm working off the live cd?  This stuff is over my head, but just trying to guess at this point.  Thanks...

---

### Post by pxwpxw on 2007-10-25
> **Win2Mac2Linux said:**
> Unfortunately, no.  When I save the file it tells me "Error writing /etc/intramfs-tools/modules: No such file or directory"

Also lately my seems is locking up after a short time, not to mention that after logging in I get errors on a bunch of modules that load asking if I want to delete them or not with my home screen missing all of them.  I think my best bet may be to reload 7.04 and keep an eye out for a bug fix in an update patch or something.  "Thank you" to you and others who have been trying to help me and others with this problem.  I've noticed others have been able to get the problem fixed, but apparently not for me.  I agree with you about how this version was released with what appears to be a pretty widespread problem.  Thanks again.

Spelling error initramfs not intramfs

---

### Post by pxwpxw on 2007-10-25
> **Win2Mac2Linux said:**
> So I am back to installing 7.04 and now when the system boots from the live cd and goes to the desktop, I start getting the same errors I had after installing 7.10.  Multiple errors about various applets such as gnome, sound, etc.(whether I want to delete them or not) and my desktop has no icons, specifically the "install" option to install to the hard drive.  The icons at the top left are present (firefox, etc.), but those on the main part of the desktop are MIA. At first I thought maybe it wasn't booting from the cd, but I used the "force" option and the text screen comes up with the boot command waiting for which option I want to use from the cd.  I've tried both just hitting "enter" and also trying using the "live-powerpc" option and both give me the same results.  How can this possibly be happening off an install cd?  Now I can't even get my system back to 7.04.  Frustrated,but sticking with it.  Any help is appreciated.  Is there any way it is somehow jumping back over to the 7.10 version when booting, even if I'm working off the live cd?  This stuff is over my head, but just trying to guess at this point.  Thanks...

It  seems to be still running the installed 710, see previous post.

---

### Post by Win2Mac2Linux on 2007-10-25
> **pxwpxw said:**
> Spelling error initramfs not intramfs

Oh boy...I hope that wasn't what happened, but it most likely was...

I just reinstalled 7.04 (although with a wee bit of trouble) and everything seems back to normal.  However, now after seeing that I might be missing out on 7.10 because I couldn't spell/copy correctly :( , maybe I'll upgrade to 7.10 again and retry making sure I type CORRECTLY!!!  Thanks for pointing that out.  Bedtime for me, work in a couple of hours.  Might not get a chance until Friday or Saturday to try it out (again), but I'll post how it goes.  Thanks for your help.

---

### Post by vmabus on 2007-10-25
I applied the initramfs fix on my G3 iBook Clamshell and was able to boot the new kernel.  However, wireless and sudo are now broken, and the thing is horribly slow.  I went back to the old kernel.

Seems to work fine on my G4 Pismo.  I'll keep the new kernel.

---

### Post by Win2Mac2Linux on 2007-10-26
I updated 7.4 to 7.10.  I eventually get the busybox and enter "modprobe ide_core" then "exit".  Boot process continues and I login.  On the desktop my network seems to be missing.  The only option is for "manual configuration".  I use the "sudo nano..." command (spelling the entire line CORRECTLY this time) and add the line "ide_core" to the etc/initramfs-tools/modules" file.  I hit CTRL O to save, hit enter, then CTRL X to exit.  When I run the "update-initramfs -u" command I get the following response:

mv: cannot move '/boot/initrd.img-2.6.22.14-powerpc' to '/boot/initrd.img-2.6.22.14-powerpc.dpkg.bak'  :Permission denied

Suggestions?  I hope I typed everything correctly.  Again, since updating to 7.10 I have no wireless or wired network.  When I click on the "manual configuration" option from the network icon options, the outer frame of that window appears, but the interior is blank.  No text, nothing...

Thanks again for any help you (or anyone for that matter, feel free to join the party) can provide.

---

### Post by pxwpxw on 2007-10-27
You need to run all such commands as the Super User (root), which you do by the "sudo"
prefix, which does the command as super user, ( if you are in the sudoers file ).
Any time a command bounces due to insufficient authority etc, run it with sudo. But be sure that it is safe to run before using super user powers.

---

### Post by Win2Mac2Linux on 2007-10-27
> **pxwpxw said:**
> You need to run all such commands as the Super User (root), which you do by the "sudo"
prefix, which does the command as super user, ( if you are in the sudoers file ).
Any time a command bounces due to insufficient authority etc, run it with sudo. But be sure that it is safe to run before using super user powers.

That didn't cross my mind since I thought I had read somewhere that when you login as root in Ubuntu that you have administrative priveleges for 5min.  The important thing is I ran the update command with sudo and it now boots just fine.  However, I am still having the network issue.  Other times when I had installed 7.10 the network setup was fine.  For some reason, this time when I click on the network icon in the upper right corner, the only choice is "manual configuration" and when I click on that I get the "network settings" box, but it is a blank box.  The title bar is there, but the main box is gray with a smaller blank white box inside.  None of the usual options are there.  It's just a blank box.  I was thrilled it boots without a problem, but frustrated that I'm having the network issue.  I even attached my wired ethernet hoping that maybe it will connect but not show it graphically.  Unfortunately, no connection.  Looking forward to getting this last problem solved.  Thanks to all who have been helpful in getting me this far.

---

### Post by x2l2 on 2007-10-27
this works for my ibook g3 ^_^ 
i change the file botting whit the cd , mouting my hd , editing the file whit gedit 

them i use the shell for make a "chroot /mnt/myhd" and "update-initramfs -u"

^___^

i dont understand why they dont put ide-core in module inside the kernel in place of the module way 

sorry for my bad english and thanks for the help

---

### Post by stmiller on 2007-11-09
Bumping this thread, as I see many posts about this issue coming about.

---

### Post by Hoby on 2007-11-11
> **ubuntubrian said:**
> Gutsy is a mess if this is what is happening! different results and variations of the bug on different ppc boxes. A guy asks for gui fixes and there aren't any.gutsy is definitely not ready for prime time on the ppc platform. I will wait and stay with Dapper or my Feisty live cd.

I agree completely.. I'm a bit shocked that #1 Ubuntu has abandoned PPC users and #2 the kind people who maintain the PPC release have fallen on their faces with this release. Granted, it's not as bad as Apple's worst update that erased files and wiped external drives.. but still, this is pretty bad - and still no official fix from the people who manage the OS? No notice posted as a sticky in the forums? No notice posted on the release (downloads) page?

What gives?

---

### Post by stmiller on 2007-11-12
Hey Hoby, I'm a bit upset at this too. Most bug reports for PowerPC are marked 'unassigned' in launchpad so they are sort of floating out there in space with no ubuntu persons working on a fix. Only someone affiliated with ubuntu can 'assign' the bug to a team. And this is not happening for some reason.


FWIW Edgy PowerPC had mega issues, too. And that's when it was 'officially' supported by Canonical tech support. One of Edgy's biggest issues is that it would not boot properly *at*all* on any G5 machine. The kernel image was misconfigured and did not load the correct thermal modules. A "simple" fix was a reconfigured kernel, which loaded the correct modules.

I have a long email correspondence with Ben Collins over this issue, which he said was *not* an issue, despite tons of threads about the problem. (Search forum for something like 'G5 fans' for the many threads). And xorg.conf was not automatically set up in Edgy, like it is in Feisty. So X was a mess for almost everyone.

So this Gutsy thing is a PITA, but overall the distro seems better than problems in the past. I just hate that there are no apparent powerpc developers who are making the discs and kernel images giving feedback or responding to their bug reports. :( We need communication.

---

### Post by driven1 on 2007-11-15
Thanks everyone. I just loaded Gutsy last night and when I rebooted this morning discovered the issues. This fix worked like a charm. I am a little disappointed at the bugs, but hey I learning and I am having fun, usually.

---

### Post by driven1 on 2007-11-15
> **ag0g0girl said:**
> Awwww, 

This is wierd.  I have a Titanium PowerBook G4.  I also came up with the busybox prompt on first boot after install of Gutsy.

I had to erase my os 10 to do the install since moving partitions with ipartition had broken my Fiesty...I was unable to upgrade.

I reinstalled the os 10 to view the fix for this, and copied it down and prepared to reboot Gutsy and type in the mod probe etc.

I didn't have to.  The Gutsy booted up.  The icon in the menu bar doesn't show the airport as an active network, but I do have internet just fine. First run of firefox crashed the app, but the update manager fixed that just fine.

I'm pleased with the increased screen resolution, but my sound is still not working...same as in Feisty.

Just to let you know... I had the same problem as you guys, but it fixed itself.

Any luck on the sound issue. I haven't had sound on Feisty and still don't with Gutsy

---

### Post by ssam on 2007-11-15
> **stmiller said:**
> Hey Hoby, I'm a bit upset at this too. Most bug reports for PowerPC are marked 'unassigned' in launchpad so they are sort of floating out there in space with no ubuntu persons working on a fix. Only someone affiliated with ubuntu can 'assign' the bug to a team. And this is not happening for some reason.

i don't think there is anyone to asign them to. none of the canonical employees have time to fix powerpc stuff. none of the people in here are kernal programmers.

---

### Post by ubuntubrian on 2007-11-17
Regarding the Feisty sound issue, I have a Beta Feisty LiveCD that works great, sound and all, networking, etc, but have held off on upgrading to Feisty because of the "sound issue". I also tried a final  release CD that wouldn't boot much less make a whimper. I'm staying with Dapper until this Gutsy thing gets resolved, yet how will we know?
Hello Developers........:confused:

---

### Post by Archaeology_Student on 2007-12-23
> **trash said:**
> EDIT:
/etc/initramfs-tools/modules is what worked for me too!

ok in busybox type and hit enter:

modprobe ide_core

after that

exit

boot will continue, but before you login hit keys
control/alt and F1, this will take you to a terminal where you will login and type

sudo vim /etc/initramfs-tools/modules

hit I to add text(add it to the bottom), add:

ide_core

hit esc to exit and :x to save. EDIT lol, the angry face is actually supposed to be : x together;)

Then run

sudo update-initramfs -u

then control/alt F7 to go back to login screen

Hope that helps!

Got to the last little bit of adding "ide_core" but when I hit esc to exit, it does nothing :( Any tips? (Using a Powerbook Lombard G3)

---

### Post by ubuntubrian on 2007-12-24
I have all kinds of Gutsy issues and have not installed it but just run it from a live cd-no recognition of my PC card for wireless on the Lombard I have.
Anyway, I got it to boot by typing at the prompt for kernel:

live-nosploash-powerpc video=ofonly break=top

and hit enter

then:
modprobe ide-core
exit

and the boot continues fine. Works on my tibook too.

---

### Post by SonicJMC on 2008-01-24
At the BusyBox prompt, type

modprobe ide-core

NOT ide_core
It's - not _

Once you've got it booted, add
ide-core
to /etc/initramfs-tools/modules

Then run
$ sudo update-initramfs -u

Note: On my Mac, once booted the first time, my Gnome's appearance was trashed. It should be fine later.

---

### Post by mekanya on 2008-01-24
I am having a similar issue. I was able to get the live cd to boot with all the help that I found on the forums. But, after I installed it the screen goes grey at the same area as in the live cd. There are no other kernel options for me after the install when I try to boot. I'm a noob to Ubuntu and somewhat familiar with Linux, but this is not making sense to me because there is no error, no message, no nothing. I just get a screen saying "please wait, loading..." then the screen goes black and slowly fades in to grey. If anyone knows what this is please help me. I can't get into osx or anything, to my knowledge, if I can't boot up this Ubuntu.  Any help would be greatly appreciated.

Hardware: Powerbook G4, 1.5Gb Ram, 80 Gb hard drive, dual-boot Mac OSX and Ubuntu 7.10 (Gutsy)

---

### Post by stream303 on 2008-01-24
I got a feeling that most PPC development in Ubuntu is really coming from upstream Debian so that may be the reason that bug reports seem back-burner.  I could be wrong.  I like to keep an eye on the Debian PPC mailing list archives:

[http://lists.debian.org/debian-powerpc/](http://lists.debian.org/debian-powerpc/)

Rather than upgrade, how many of us are doing clean installs with the "Alternate" text-based Gutsy installer?

My little 12" iBook loves it now, although I had to add snd-powermac to /etc/modules, kill the ESD in sound preferences, and edit out the video=ofonly lines in yaboot.conf to get my virtual terminals back.  NM was hogging the cpu, so I disabled (not removed) NM and all is well now.  Details in the earlier threads.  I was expecting to have to use ide-core, but was surprised that I didn't need to, although I'm not running a TiBook, but a plain iBook from 2004.

It looks like a lot, but I'm happy to have used the alternate CD - just wondering how much further TiBook users would get with a clean install using this method.

---

### Post by ubuntubrian on 2008-01-24
The alternate cd may work, but it may not and I am loathe to do a clena install to find out. Plus, I want to keep all of the customization that I have done in Dapper as I have many hundreds of hours involved.
Maybe hardy will be an improvement? Maybe this will all get resolved?

---

### Post by stream303 on 2008-01-25
> **ubuntubrian said:**
> I want to keep all of the customization that I have done in Dapper as I have many hundreds of hours involved.

I can't argue with that!  I'm amazed that you have upgraded from dapper to edgy to feisty rather than doing fresh installs?

Have you considered doing a dual-boot scenario where you can test out a fresh install of whatever the current distribution is, yet still keep your massively upgraded system as an option?  If the fresh-install boot works, maybe it would be a lot easier to transition all your hard work from the old one...

Maybe I'm pessimistic, but the variables of a fresh install are enough for me, nevermind the possible introduction of upgrade variables.  Not enough hairs left for me to lose. :)

---

### Post by mekanya on 2008-01-25
So installing from the alternate cd does work for 7.10!? I just went back to 7.04 and did an alternate install with that. I had to change the snd-powerpc as well. Excuse the noob question, but what does NM refer to and why would you disable it? I have alot more questions but I won't bother you with the litany of them.

---

### Post by stream303 on 2008-01-25
> **mekanya said:**
> So installing from the alternate cd does work for 7.10!? I just went back to 7.04 and did an alternate install with that. I had to change the snd-powerpc as well. Excuse the noob question, but what does NM refer to and why would you disable it?

I have two Macs, a 20" G5 late 2004 iMac, and a late 2004 G4 iBook.  Each had different yet small issues to resolve.  Both work with Gutsy 7.10 just fine, but a tweak is needed here and there.  In all cases, I recommend the "alternate" text-based installer rather than the live cd.

The only problem that was a showstopper was the Network Manager, and ONLY on the G4 iBook.  In both cases, after install I lost network connectivity and all I had to do was re-enable or activate the ethernet connection in network prefs. (I don't run wireless)  However, on the iBook, everything was going sooooo slowly that I decided to run "top" in a terminal and saw that NM was hogging the cpu.  Instead of removing it, I decided to just disable it using the procedures outlined here:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5)

I only disabled it since it appears that NM is so tightly intertwined with the operating system.

So unless you have a need to not use Network Manager, I'd leave it as is, or disable it for troubleshooting purposes if you feel that it is the source of the problem.

Since I don't own a PowerBook, this may not even be an issue.

---

### Post by mekanya on 2008-01-26
> **stream303 said:**
> So unless you have a need to not use Network Manager, I'd leave it as is, or disable it for troubleshooting purposes if you feel that it is the source of the problem.

Since I don't own a PowerBook, this may not even be an issue.

Yeah, this is a bug with with NM. [_[COLOR="DarkOrange"]NM_BUG[/COLOR]_]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/82335")

 Before reading the report I was trying to figure out why my wireless couldn't connect to a network even though it was detected and broadcasting.

I might try to do a full re-install of osx on my main partition and a full reinstall of Gutsy on my linux partition with the alternate installer.

The wi-fi is my only real issue right now, and if I can get that up and running I'll be an ubuntu-addict.

---

### Post by ag0g0girl on 2008-01-27
ok, I know I posted a while ago that my machine just starting booting without the ide-core in the module...now all of the sudden it won't 

i did all the ide-core stuff, and now I can't boot gutsy and it goes to openfirmware.

This really sucks.  I need to know what to type really quick at yaboot to make it boot, so I can then double check things...I see that you guys have put some good stuff in here, so I'll try again, and let you know.

---

### Post by Ripfox on 2008-01-29
Well, typing modprobe ide-core OR modprobe ide_core at the busybox shell works to boot the machine every time. BUT, I have tried adding either line to both of the suggested modules files and neither one works. I am positive it is saving the file correctly and this is not my first rodeo, so is there anyone else here who this fix does not work for? Am I doing something wrong, because it seems that it just needs to load this module at boot...is there an alternative way to make this module load?

Help :)

---

### Post by Ripfox on 2008-01-29
I have to bump this, I need to get this installed by tomorrow for someone...#-o

---

### Post by shawnhcorey on 2008-01-29
OK, I read this thread.

I'm running Ubuntu 6.10 (Edgy) on my PowerBook G4.

I see no reason to update.  (7.04 doesn't have audio.)

In short, all the updates beyond 6.10 DON'T WORK!

Why should I care?

---

### Post by mekanya on 2008-01-30
> **shawnhcorey said:**
> OK, I read this thread.

I'm running Ubuntu 6.10 (Edgy) on my PowerBook G4.

I see no reason to update.  (7.04 doesn't have audio.)

In short, all the updates beyond 6.10 DON'T WORK!

Why should I care?

I just did an alternate install on my powerbook g4 to 7.04. After some small fixes that were mentioned in these threads almost everything works like a dream the way it is supposed to (sound, suspend, wireless, etc.). The only thing I don't have is right-click and I haven't configured the trackpad, but I hardly think those can be considered issues.

---

### Post by jjmcmillion on 2008-02-01
I've read through all the posts in this thread and have tried all the tips, but still can't get Gutsy to boot.

I have a PowerBook G4 (Gigbit Ethernet) with 1 GB RAM and a 667 MHz PPC CPU. I was running Tiger previously but wanted to try Ubuntu so I tried the Alternate Install CD and got Gutsy installed. First boot led to the infamous "BusyBox Boot Error" we all seem to be experiencing so I trawled the forums till I found this thread. I tried the /etc/initramfs-tools/modules fix but it still throws me out to BusyBox. Here's what I've done so far:

In Busybox typed the following ("->" means "Press Enter"):
*"modprobe ide_core" ->*
When the promt reappeared, typed
*"exit" ->*
The boot sequence continues back to the graphical user interface, but before I logged in pressed *Ctrl+Alt+F1.*
This takes me to a terminal where I will first login with my username and password and then type:
*"sudo vim /etc/initramfs-tools/modules" ->*
This brings me to the Vim Editor. Pressed "i" to add text. Added the following to the bottom, under the last line:
*"ide_core"* (Also tried with ide-core)
(Note: Since there's no "# " on that line I added it.)
To exit and save pressed the following: first pressed Esc, the pressed "shift-q" ->, then "w" -> to save the file, then "q" -> again to exit Vim.
Then ran:
*"sudo update-initramfs -u" ->*
Pressed Ctrl+Alt+F7 to get back to the login screen and logged in.
After a reboot, I get back to the same BuisyBox error.

Any tips after that? I really want to try Ubuntu, but feel like this is not worth the trouble.

---

### Post by jjmcmillion on 2008-02-01
Solved it!

In the modules file I shouldn't have put "# " in front of "ide-core". The UNIX system apparently doesn't approve of that and disregards every line starting with a "#".
Took it (and the space) away, saved and exited, then reboot. Joyousness! A solid boot.

Also, to all PowerBook G4 users out there, check [this site]("https://wiki.ubuntu.com/PowerPCFAQ#head-80b3759a67892a1cd602386a1cad3bae8cb1835e") if you want to get proper display and sound drivers.

---

### Post by stream303 on 2008-02-02
Allright!  Glad you hung in there.  A somewhat friendlier alternative to the vi editor is nano, so you could substitute nano instead.  (although I'm a vi fan myself)

Small discoveries like the # sign can make your day!  We'll make you a command-line junkie soon enough! :)

---

### Post by shawnhcorey on 2008-02-03
> **jjmcmillion said:**
> Solved it!

In the modules file I shouldn't have put "# " in front of "ide-core". The UNIX system apparently doesn't approve of that and disregards every line starting with a "#".
Took it (and the space) away, saved and exited, then reboot. Joyousness! A solid boot.

Also, to all PowerBook G4 users out there, check [this site]("https://wiki.ubuntu.com/PowerPCFAQ#head-80b3759a67892a1cd602386a1cad3bae8cb1835e") if you want to get proper display and sound drivers.

This fix does not work on Titanium PowerBooks; I tried it and it locks up during boot.

More and more my poor PowerBook is looking like an expensive paperweight.  Sigh.

BTW, lines starting with a '#' are comments and are ignored by most programs.

---

### Post by Novalus on 2008-02-03
I probably should have just posted this here instead of starting a new thread:

[http://ubuntuforums.org/showthread.php?t=686310](http://ubuntuforums.org/showthread.php?t=686310)

but I worked through getting my powerbook to start after getting this 'busybox' problem. 

it should be the same on g3's i would think. hope it helps!

---

### Post by shawnhcorey on 2008-02-03
> **Novalus said:**
> I probably should have just posted this here instead of starting a new thread:

[http://ubuntuforums.org/showthread.php?t=686310](http://ubuntuforums.org/showthread.php?t=686310)

but I worked through getting my powerbook to start after getting this 'busybox' problem. 

it should be the same on g3's i would think. hope it helps!

So, what is this 'ide-core' and why does it suddenly work?  Yes, I'm skeptical.

Everything worked in 6.10.  Why do I have to do something special for later version?  What has changed?  Why has it changed?  And why isn't there a version that "just works"?

---

### Post by Cows on 2008-02-19
On my powerbook g4 I did the following :

sudo gedit /etc/initramfs-tools/modules 


I added the "ide-core" to the bottom of the file and rebooted. Then I did :

sudo update-initramfs -u

and I still get dropped to the Busybox shell but all I have to type is "exit"

for some reason when I press ctrl+option+f1 my (tty1) screen is all black and I cant do anything in it.. any fix for this and for the busybox. 

Note : I also tried to add ide-core to the /usr/share/initramfs-tools/modules as well and it didn't work.

This is my post :

[http://ubuntuforums.org/showthread.php?p=4356070#post4356070](http://ubuntuforums.org/showthread.php?p=4356070#post4356070)

---

### Post by ubuntubrian on 2008-02-21
> **stream303 said:**
> I can't argue with that!  I'm amazed that you have upgraded from dapper to edgy to feisty rather than doing fresh installs?

Have you considered doing a dual-boot scenario where you can test out a fresh install of whatever the current distribution is, yet still keep your massively upgraded system as an option?  If the fresh-install boot works, maybe it would be a lot easier to transition all your hard work from the old one...

Maybe I'm pessimistic, but the variables of a fresh install are enough for me, nevermind the possible introduction of upgrade variables.  Not enough hairs left for me to lose. :)

Well I don't have the hair left either! sorry about the late reply but i did try having a triple boot set up once with OS X and 2 linux distros but the yaboot config was a nightmare and Inever continued to explore it. Maybe I could do a remote drive? anyone know how to do this or point out an existing thread?
Thanks!:popcorn:

---

### Post by ubuntubrian on 2008-02-21
Here's a real kick! I downloaded and burned the latest Hardy Heron live CD and it boots right up and I'm posting this from Firefox3!
No modprobe, live-nosplash, blah, blah at all. It just runs on my TiBook! Sound is flaky though but that may be due it being a live cd and maybe it's fixable.
F-Spot runs great and is as good as iPhoto as far as I can tell.Can upload to Flickr and Picasa.
If the sound issue is solvable then this version may be the answer and it's still alpha so the developers have been working hard and doing a great job!!

---

### Post by Fer Servadu on 2008-03-20
I want to add that this thread has solved my problem.

I upgraded to Xubuntu 7.10 from 7.04 via update manager. I decided to do it overnight, since the download and installation takes so long. Well, this morning the secure screensaver wouldn't recognize my user name and password, so I had to do a forced shutdown via the power button.

On reboot, I ran into the problems described in this thread. Booting from 'old' worked normally, but the default 'Linux' sent me into Busybox.

In Busybox: modprobe ide-core
At the cl: sudo vim /etc/initramfs-tools/modules
Added ide-core to the end
At the cl: sudo update-initramfs -u

And everything seems to be fine now. I suspect that the forced shutdown caused the troubles, since the system wasn't able to properly shutdown after the upgrade.

I'm running a PowerBook G3 Pismo, with no mods other than a D-Link WNA-2330 replacing the original Airport card.

Thanks to everyone!

---

