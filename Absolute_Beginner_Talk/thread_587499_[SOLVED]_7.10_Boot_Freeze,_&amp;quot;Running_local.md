---
title: "[SOLVED] 7.10 Boot Freeze, &amp;quot;Running local boot scripts&amp;quot;"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by mmb1 on 2007-10-22
Hi, I'm a complete newbie to Ubuntu and wanted to give open source a try when I encountered a problem. Gusty Gibbon (7.10) boots regularly until it reaches "running local boot scripts". It then stops and does nothing. I searched the forums and couldn't find anything to help.  I feel really dumb having to ask, but can anyone give me step-by-step instructions on how to fix this?


                        Any help would be much appreciated.:confused:




        Here's my system info:


             Dell Dimension 8100 PC

             Intel Pentium 4 processor

             Graphics Card: NVIDIA GeForce2 MX/MX 400


If anyone needs any more info, I'll be more than happy to oblige.

---

### Post by cfaulkner on 2007-10-22
From: [http://ubuntuforums.org/showthread.php?t=413975](http://ubuntuforums.org/showthread.php?t=413975)

> Re: Feisty freezes at "running local boot scripts" 

--------------------------------------------------------------------------------

The problem probably is not the script.

rdejean found the solution ([http://ubuntuforums.org/newreply.php...e=1&p=2540263](http://ubuntuforums.org/newreply.php...e=1&p=2540263)).

The boot process would hang after the last script in /etc/rc2.d, no matter which script that was. (I have put the nosplash option in /boot/grub/boot/menu.lst, so I can see the boot messages.)
Earlier in the boot process, I would get the messages
init:/etc/event.d/tty1:13: Unknown stanza
init:/etc/event.d/tty2:13: Unknown stanza

The problem was in /etc/event.d/tty1 (and tty2 etc.)
The last two lines were
respawn
/sbin/getty 38400 tty1exec /sbin/getty 38400 tty1

but should have been
exec /sbin/getty 38400 tty1
respawn

After fixing each of the tty files, the machine booted fine, though it needs a little push at the end by pressing enter.

This seems to be a known bug. The release notes ([http://www.ubuntu.com/getubuntu/releasenotes/704](http://www.ubuntu.com/getubuntu/releasenotes/704)) say:
Users who have serial consoles, or have made custom changes to the /etc/inittab file or files in the /etc/event.d directory should be aware that the format of these files have changed slightly and your changes will not be automatically migrated. Bug #89314. The following changes should be made.
"respawn COMMAND" should be changed to "exec COMMAND" with "respawn" on a seperate line.
"on EVENT" should be changed to "start on EVENT"
the "runlevel-X" events should be changed to "runlevel X"

I only changed inittab to comment out all but the first two tty processes (# 3:23:respawn:/sbin/getty 38400 tty3) to not waste the memory. I didn't make the kind of change Ubuntu warned about, but it seems to have been enough.


---

### Post by mmb1 on 2007-10-22
Okay, thanks a million, cfaulkner, appreciate the help!

---

### Post by molly_001 on 2007-10-23
Just so you know, I was helping a guy install Gutsy during the last several days with the same problem of hanging at "Running local boot scripts".  You can very likely get around it by using the Alternate Install CD for installing Gutsy, and not the LiveCD.

---

### Post by PrinceVlad on 2007-10-23
I'm trying to install the SERVER version of Ubuntu 7.10, and it gives me this error. I tried Feisty, same problem. I tried to follow cfaulkner's advice, didnt change a thing.

I am almost completely new to Linux, so I really can't see through what the hell is going on.... what is /etc/event.d/tty1? Also, what is it that does not get completed by the bootup because of this problem? I don't get in the SUDO'ers list, and I expect that it must be because of this freeze..... I easily got around that problem by booting to safe mode and adding myself, but what else is mising from the bootup sequence?

---

### Post by PrinceVlad on 2007-10-23
Allright, I have now figured out what tty does, and also that there were 6 of them..... 6 consoles, as I understand it. I have changed them all, according to the adviced offered here, and it may/may not have done the trick... it still needs a <return> at the end of boot, but wasn't that also the case before...?
But if you guys says that bootup is complete at that, it's good enough for me ;-)

---

### Post by blueskystarfish on 2007-10-23
hi,
I have tried to install 7.10 using Unetbootin on a PC without a CD drive, and have come across the same problem.  However, as this is my first ever contact with linux, I have absolutely no idea how to progress further.  (For example, tty1 thru 6  means absolutely nothing to me) I have used Windows since the Dos days, so am familiar with a command line, but this is new territory to me.  What should my next move be?  How can I load Ubuntu?

---

### Post by blueskystarfish on 2007-10-24
ttt

---

### Post by PrinceVlad on 2007-10-24
I will offer the small help that I am able.....
go to /etc/event.d/, in there you should see the files 'tty1' through 'tty6'. These files are simple textfiles, containing the configuration for the 6 terminals that are started in Linux (as I understand it...? Correct me  if I am wrong). 
Now you must do as suggested further up in this thread, namely edit each of them, to correct them according to cfaulkeners post : 
In each file you will find the two last lines to be :

"
respawn
exec /sbin/getty 38400 tty1
"
or something similar. You should change these lines, so that the word 'respawn' is the last line, like this :

"
exec /sbin/getty 38400 tty1
respawn
"

To do this, use the command 'SUDO VI tty1', which will open the file in the Vi text editor..... and be warned, that VI is a bitch to use, if you have had no prior experience with it..... but, as always with Linux, there is lots of support for it on the net

After all 6 files have been thus corrected, reboot, and all should be well, although I am not myself quite sure...... You will still need to press <return> to get a prompt for login. According to more proficient members of this community than myself, the mentioned boot freeze-problem should now be completely rectified.

---

### Post by blueskystarfish on 2007-10-24
Vlad, thank you so much for replying.

When you say "go to etc/event.d/" , how do I do that?

When I boot, the PC hangs at "Running local boot scripts (etc/rc.local) .... [OK]

When I hit return, I get a line
"Ubuntu7.10 Derek tty1"
then
Derek login:

How do I get from there to 'SUDO VI tty1' (and does it have to be in capitals when I get there?)

---

### Post by gubemton on 2007-10-24
Hey guys, I just installed Gutsy this morning because digg and other sites are flooded with positive reviews and I wanted to check it out myself.

I do however have the same problem: Gutsy freezes after "Running local boot scripts".
I tried the suggested solution here and changed all tty files in /etc/event.d, but still no go.

I have also tried all kinds of boot options in several combinations (noapic, nolapic, acpi=off etc.) and that didn't help either. I looked into /var/log for any errors but wasn't really able to find anything.

If I boot in rescue mode the system starts up just fine, X.org is also working flawlessly.
I really have no idea what else I could do... maybe some of you have any further suggestions?

As always, any help would be greatly appreciated!

---

### Post by PrinceVlad on 2007-10-24
blueskystarfish:
You first have to provide your login name, i.e. the user that you have been creating at installation. Then you are asked for your password, which you also enter. After that, you should get a message that you are now logged in.

Then you go to the aforementioned directory with "cd /etc/event.d", and proceed as instructed with 'sudo vi tty1', and onwards. And no, Linux doesn't care about upper/lowercase, I just wrote it in capitals to show that it is a COMMAND :-)

---

### Post by blueskystarfish on 2007-10-24
Thanks again, Vlad.  

Boy, what a learning curve this is!  After searching on the web, I found out how to use the vi editor, and edited the files as you suggested.  However, the boot process does not get past the "running local boot scripts line". I have checked that the files have been edited correctly, and have powered down and rebooted etc.  In addition, I cannot boot into the rescue mode either.  

Do you think this is all happening because 7.10 is a new release? and these are bugs.  Would I be better off trying to install the 7.04 release, (although I can see from the cfaulkner post that it also affected 7.04.)  

Is there a command from the Command Prompt that will load the desktop? (the Ubuntu equivalent of typing win in Windows).  I feel like this is only just out of reach, most infuriating.

---

### Post by blueskystarfish on 2007-10-24
I want to check that the installation has installed the correct files.  Can anyone tell me how to see what has been installed, and whether the correct files are on the PC.  I ran <sudo dpkg --contents> but got no intelligible reply.

---

### Post by gubemton on 2007-10-24
> Is there a command from the Command Prompt that will load the desktop? (the Ubuntu equivalent of typing win in Windows).

"startx" is what you're searching for.

Oh and btw, if you're looking for something more user-friendly than vi I would suggest "nano", which also comes preinstalled with ubuntu.

---

### Post by blueskystarfish on 2007-10-25
thanks gubemton.  That is exactly what I needed.  By trying that, I eventually discovered that none of the files for the GUI had downloaded.  Following this link

 [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

 then got me up and running.

---

### Post by mmb1 on 2007-10-25
Thanks, bluestarskyfish for the amazing link you provided, i was having trouble interpretting cfaulkners advice and this gave me exactly what I needed.

---

### Post by n1418 on 2007-10-26
I followed advice above regarding correcting the tty files.  

Rebooted, and it still landed me at "running local boot scripts (/etc/rc.local)

Pressing enter at that point does nothing.

All this comes after enabling the ATI restricted drivers for my HD 2600pro.

This error has occurred for me in both AMD64 and x86, to include final and RC versions.

The only thing that I find works to launch the X server is to restore my unaltered-by-ATI xorg.conf backup file.

Anyone making any headway recently on this issue?

---

