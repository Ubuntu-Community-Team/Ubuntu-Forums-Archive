---
title: "Error creating child process"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by keyset on 2007-09-13
I'm having some trouble after the latest kernel upgrade and hoping someone can point me in the right direction. I'm a bona fide n00b, but I'm willing to go try stuff on my own (as long as I'm given enough to go on).

I originally had trouble with my nVidia drivers; having fixed that, X will launch and let me log in, but shortly after I enter my login information, I get a terminal window and an error box over it saying: "There was an error creating the child process for this terminal." At this point, everything seems to freeze and I have to manually shut down the machine.

Obviously that error message isn't helping much. I had a look at /var/log/xorg.0.log, but there doesn't seem to be much there (last entry is "Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!" whatever that means). 

What I want to know is, where can I find a log file that will tell me what child process is kicking the error message? Or does anyone have any other suggestions? Thanks in advance!

---

### Post by keyset on 2007-09-16
OK I've found the log file I needed in /home/[username] as .xsession-errors, which is peachy. I don't understand the errors though, and searching the forums didn't yield anything either. Top of the log says:

/etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: 128: cannot create /dev/null: Permission Denied (This line repeats a few times with different numbers)
/etc/gdm/Xsession: Executing default failed, will try to run x-terminal-emulator

Everything after that appears to be ALSA errors. Anyone have any ideas? :confused:

---

### Post by keyset on 2007-09-16
Full .xsession-errors file attached.

---

### Post by jw5801 on 2007-09-16
It appears to be a permissions error. Can you boot up in recovery mode? Actually before you try that, change your session at the login screen to "failsafe gnome" and see if that makes a difference. Regardless, once you make it to the command-line can you give us the output of ```
ls -l /etc/gdm
```which will tell us the owner of all the files within (they should all be owned by root) as well as other useful information.

---

### Post by keyset on 2007-09-16
Thanks for replying! I can boot to recovery OK, but I'm not too swift on the command line just yet. Switching to failsafe-gnome just gives me a blank screen after I log in, and again I have to force the machine down.

Here's the results of that command:

drwxr-xr-x 2 root root  4096 Apr 15 13:01 Init
drwxr-xr-x 2 root root  4096 Apr 15 13:01 PostLogin
drwxr-xr-x 2 root root  4096 Apr 15 13:01 PostSession
drwxr-xr-x 2 root root  4096 Apr 15 13:01 PreSession
-rwxr-xr-x 1 root root  4003 Apr 10 21:42 XKeepsCrashing
-rwxr-xr-x 1 root root  6534 Apr 10 21:42 Xsession
-rw-r--r-- 1 root root 32002 Apr 10 21:42 factory-gdm.conf
-rw-r--r-- 1 root root 32002 Apr 10 21:42 gdm.conf
-rw-r--r-- 1 root root  2142 Sep 11 23:02 gdm.conf-custom
-rw-r--r-- 1 root root  1564 Apr 10 21:42 gdmprefetchlist
-rw-r--r-- 1 root root 10739 Apr 10 21:41 locale.conf
drwxr-xr-x 2 root root  4096 Apr 15 13:01 modules

As a side note, I had gotten my mouse to work again using dpkg-reconfigure xserver-xorg, but when I was trying again just now, it's died again :( I'll see what I can do to get it going again.

---

### Post by schorsch on 2007-09-16
What is the output of
```
ls -l /dev/null
```

---

### Post by keyset on 2007-09-16
Hi schorsch,

crw-rw---- 1 root root 1, 3 Sep 16  2007 /dev/null

Thanks!

---

### Post by schorsch on 2007-09-16
After typing
```
sudo chmod 666 /dev/null
```
it should be fixed.

---

### Post by keyset on 2007-09-16
The saga continues...

Thanks schorsch, you got me a step further. Now when I log in, I'm immediately prompted with 'your session only lasted less than 10 seconds' etc etc. The .xsession-errors log now shows just one failure:

PRNG is not seeded

I booted into Failsafe GNOME, and then got internal error: failed to initialize HAL! I couldn't do much else, so I rebooted, then found that the chmod command had been reversed! I'm starting to wonder if I've got major hardware failure on my hands?

---

### Post by schorsch on 2007-09-16
Hmm .... have you tweaked your udev rules for some reason? The PRNG (PseudoRandom Number Generator) message means that you do not have enough entropy in your system to do some things like encryption or other processes that need random numbers. The entropy is created by /dev/random or /dev/urandom with the help of keystrokes, mouse movements or even sound ...
Please post the output of
```
ls -l /dev/null
ls -l /dev/random
ls -l /dev/urandom
grep null /etc/udev/rules.d/*
grep random /etc/udev/rules.d/*
```

---

### Post by keyset on 2007-09-16
I haven't touched my udev rules as far as I'm aware. I don't even know what they are.

ls -l /dev/null is back to:

crw-rw---- 1 root root 1, 3 Sep 16  2007 /dev/null

I get the same results for /random and /urandom as well (of course except they end differently).

grep null /etc/udev/rules.d/*:

/etc/udev/rules.d/40-permissions.rules:KERNEL=="null", [blank space] MODE="0666"

grep random /etc/udev/rules.d/*:

/etc/udev/rules.d/20-names.rules:KERNEL=="hw_random", [blank space] NAME="hwrng"
/etc/udev/rules.d/40-permissions.rules:KERNEL=="random", [blank space] MODE="0666"
/etc/udev/rules.d/40-permissions.rules:KERNEL=="urandom", [blank space] MODE="0666"
/etc/udev/rules.d/85-pcmcia.rules:# are so broken that we need to read out random bytes of it

---

### Post by schorsch on 2007-09-16
O.K. your rules look fine. As a possible workaround just for the moment:
Please type
```
sudo udevtrigger
```
in a terminal window and try to start the GUI via
```
sudo /etc/init.d/gdm start
```
and check if you can login now.
If this works we have to check why udev is not running at bootup:
```
ls -l /etc/rcS.d/S10udev
```

---

### Post by keyset on 2007-09-16
Tried sudo udevtrigger, and I'm back to the original child process error. I'll need to run
```
sudo chmod 666 /dev/null
```
again since as you saw my permissions reversed themselves. Shouldn't the permissions be the same for /dev/random and /dev/urandom as well?

Also, since I'm logged in in Recovery Mode, I'm running everything as root so I don't need sudo, do I?

---

### Post by schorsch on 2007-09-16
Yes, all three files (/dev/null, /dev/random and /dev/urandom) should have the same permissions 666. But the udevtrigger command should have set them according to your rules. Is there a udev daemon running?
```
ps -ef|grep udev
```
Perhaps you can login after setting the permissions to 666 on all three mentioned files?
Reagrding the use of sudo in recovery mode: It is not necessary but it does not hurt anyway ... and I forget to mention it sometimes so just to be on the safe side ;-)

---

### Post by keyset on 2007-09-16
Manually setting permissions for those three /dev folders let me log in, but I still got the could not initialize HAL error. When I tried to launch a terminal after logging in, I'm getting the Error Creating Child Process. So I'm getting in, but I'm still a ways away from proper functionality (oh and my mouse still doesn't want to work either, but first things first).

I'm guessing there must be a udev daemon since udevtrigger didn't work and your command yields this:

root      3249  3247  0 18:25 tty1     00:00:00 grep udev

And, after I rebooted (back to recovery, *sigh*) I checked the permissions on /dev/null, /random, and /urandom again, and they're all reset to crw-rw----. I didn't forcibly reboot this time either, I was actually able to reboot from the console.

Thanks again for all of your help schorsch, I've learned more today than I've learned in the past 3 months!

---

### Post by schorsch on 2007-09-16
Well, once upon a time I had to learn all of this, too .. :-)
What happens if you start the udev daemon manually in recovery terminal:
```
sudo /etc/init.d/udev start
```

---

### Post by keyset on 2007-09-16
Def looks like it's already running:

cp: cannot create special file `/dev/console': File exists
cp: cannot create special file `/dev/kmem': File exists
cp: cannot create special file `/dev/loop0': File exists
cp: cannot create special file `/dev/net/tun': File exists
cp: cannot create special file `/dev/null': File exists
cp: cannot create special file `/dev/ppp': File exists

I take it that means we have to kill it and recheck the rules? I'm just guessing....

---

### Post by schorsch on 2007-09-16
O.K., let's get a step deeper into it ...
```
sudo sh -x /etc/init.d/udev restart
```
The "sh -x" will show you every step the script is executing with the corresponding messages so we will get mor output. Please post the output here .... this is really a weird behavoiur ...

---

### Post by keyset on 2007-09-16
OK this might take a while because I gotta figure out how to print the results to a file (told you I'm a noobie). However, I can type the last few lines which show a failure:

+ printf \r
+ /usr/bin/tput hpa 73
+ [ 1 - eq 0 ]
+ printf [
[+ /usr/bin/tput setaf 1
+printf fail
fail+ /usr/bin/tput op
+ echo ]
]
+ return 1
+ exit 0

---

### Post by schorsch on 2007-09-16
Uhm, sorry .... I forgot you are on the failsafe teminal ...
```
sudo sh -x /etc/init.d/udev restart > /tmp/udev.txt 2>&1
```
will put the output to the file /tmp/udev.txt.

---

### Post by keyset on 2007-09-16
*whew* thanks for that! File is attached.

---

### Post by schorsch on 2007-09-16
I checked the output but I could not find anything that looks like a hint .... Just another idea:
What is the output of
```
ls -l /etc/rcS.d/*udev
```
This is really a weird problem ... do you have network in failsafe terminal? Perhaps it is just better to reinstall the udev package ... if this is the reason for this behaviour ...

---

### Post by keyset on 2007-09-16
Output:

lrwxrwxrwx 1 root root 14 May  5 11:09 /etc/rcS.d/S10udev -> ..init.d/udev

I can hook it to the network and I've used apt-get on it before from Recovery terminal, so I would be happy to try an uninstall/reinstall of udev. What's the apt-get command for that?

---

### Post by schorsch on 2007-09-16
I just did a dry run on my system and an uninstall will remove a whole bunch of applications so that would be a very bad idea!!
Please try
```
sudo aptitude reinstall udev
sudo /etc/init.d/udev stop
sudo /etc/init.d/udev start
```
This did no harm to my system .. ;-) If this still does not work I am running out of ideas ...

---

### Post by keyset on 2007-09-16
Eureka! It's alive! OK, well my mouse still doesn't work and I'm getting HAL errors once my desktop is displayed, but hey, at least it gets that far, and I can launch Terminal from my desktop without error. And that's plainly a separate issue, so I think I'll mark this one as solved and set to tackling the rest of these problems.

Many, MANY thanks again schorsch! If you're ever in Glasgow, send me a PM and I'll buy you a beer.

---

### Post by schorsch on 2007-09-16
Hey, I always wanted to spend some days in Glasgow, hehe :-) ... Glad to hear that it works partly now for you! I hope you even learned a little bit in the last hours. Udev is a really powerful tool to assign permissions, owners and names when connecting devices either at bootup or to the running system but it can also be quite disturbing. Regarding your mouse and HAL error ... perhaps we can take a look at it tomorrow .... or another guy on this forum will teach you something .. ;-)

---

### Post by keyset on 2007-09-16
ARGH spoke to soon. No sooner did I reboot, but everything went right back to where it was. I'm going to try a couple other things, but first I need to eat something. A quarter-bottle of scotch can make you a bit loopy on an empty stomach.

---

### Post by schorsch on 2007-09-16
Alright ..... have you really updated everything that's possible?
```
sudo apt-get update
sudo apt-get upgrade
```

... sorry, I have to leave now ....

---

### Post by keyset on 2007-09-16
Tried both of those, 0 to upgrade/install/update/remove.

I retried sudo aptitude reinstall udev. This borked (did last time too, but since it booted, I didn't think anything of it):

dpkg: regarding .../udev_108-0ubuntu4_i386.deb containing udev:
  package uses Breaks; not supported in this dpkg
dpkg: error processing /var/cache/apt/archives/udev_108-0ubuntu4_i386.deb (--unpack):
  unsupported dependency problem - not installing udev
Errors were encountered while processing:
  /var/cache/apt/archives/udev_108-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:

Of course it doesn't recover. I tried what seemed to be the logical next step:

sudo aptitude reinstall dpkg

This borked as well with the following (exerpt):

Writing extended state information... Error!
E: I wasn't able to locate file for the dpkg package. This might mean you need to manually fix this package
E: Couldn't lock list directory..are you root?

However, I ran this as sudo and of course from the recovery console (as usual) so I'm root anyway. I also tried the above command with a -f switch, to no avail.

I'd like to keep troubleshooting (because it's kinda fun and I'm learning a lot), but I understand if I might be pushing the resources of the forum. Anybody got any more suggestions, or should I give up and reinstall?

---

### Post by schorsch on 2007-09-17
Hi,

after a quick search on the forum I found [this thread]("http://ubuntuforums.org/showthread.php?t=425317"). Perhaps this can help you. To be honest I never saw an error message like this before ....
Sorry, but I am really running out of ideas regarding your problem .. :-(

---

### Post by redbob on 2007-09-17
Hi, Keyset and Schorsch.

I was accompaining your dialogue, and I am passing by this same experience... I didn't anything Keyset did yet, but I was thinking... what does make a computer lead Ubuntu to "Failed to create child process...". Firstly I installed Feisty in my computer by Live-CD, everything gone right till the moment when all boxes and bars began to "distort". I applied the first automatic updates and rebooted the computer, then this error came on. Even if I disconnect my hard drive and boot by Live-CD, the only thing I see is just one distorted window with the message "Failed to create child process...".
I suppose it's RAM or VGA error, because I changed HD, downloaded new iso, burned Desktop and Alternate CD and I can't do nothing!!!

---

### Post by keyset on 2007-09-17
Well unfortunately I'm at the point where I can't even make the child process error go away. Because of that, everything I'm trying to do has to be done through the recovery console, which has far too many options for me to be able to pick between them. I had a look at the thread schorsch posted, but unfortunately I can't make the downloaded package install... aptitude refuses to install with the package on my machine, as does dpkg, despite the --force flag and pretty much every other flag available. Unfortunately, I'm stuck, so I'm afraid I'm down to a complete reinstall, which is a shame because it took a lot of work to get to where I'm at right now. I guess the biggest lesson I've learned is "never upgrade your kernel" since that's what started this whole episode. Oh well, I did learn gobs about Terminal, and lots of thanks to schorsch for the immeasurable help (I still owe you a beer!).

---

### Post by Ozztopia on 2007-09-17
Same with me. I updated system (7.04) with sudo apt-get update and it updated kernel etc. but returned an error with rsync. Then I couldnt get into gdm because I had installed NVIDIA drivers earlier to upgrade of kernel headers. I ran "dpkg-reconfigure -phigh xserver-xorg" which let me into Gnome login page. But when I type in username and password, I get "There was an error creating the child process for this terminal'. What should I do? Do I reinstall? It will be the 3rd reinstall if I do. This doesn't look as stable as its touted to be. I really don't want to go back to Windows XP.:(

---

### Post by redbob on 2007-09-17
I tryed to go back to Windows XP, not by frustating with Ubuntu (because I have other machine running Ubuntu very well!!), but for making a test. Believe in me, neither XP nor Ubuntu wants to work on my computer anymore!!! Right now I changed my RAM, I put a Kingston DDR400 256Mb, with the same result. My VGA is a NVIDIA Geforce MX 4000. As I already read about this card, it may be the vilain of this history!!

---

### Post by redbob on 2007-09-18
Right now I changed VGA card, installed a ATI Rage Pro 32Mb in place of NVIDIA, even so, the problem remains. When I go to command-line shell by clicking Alt-Ctrl-F2 there's a lot of "Permission denied" listed. It's because I booted with Live-CD. I cleared CMOS, changed processor speed, but nothing! I think something damned my computer hardware. I'll begin to deactivate alll onboard devices...

---

### Post by redbob on 2007-09-18
well well well... while Ubuntu bar is sliding left-right and vice-versa, I pressed Alt-Ctrl-F1 to see textual commands... the first line is "Loading, please wait..." it's interesting to see some messages... what do you know about them???
cp: memory exhausted (??? what does itm means???)
* Mount point '/dev/shm' does not exist. Skipping mount.
* Mount point '/dev/pts' does not exist. Skipping mount.
(...)
* Starting powernowd...
/etc/rc2.d/S20powernowd: 156: cannot create /sys/devices/system/cpu/cpu0//cpufreq/scalling_governor: Directoy nonexistent
* CPU frequency scalling not supported

Is this the source of the crash???

---

### Post by BLTicklemonster on 2007-09-18
Here's my story:

Upgaded a while back to kernel 2.6.20-16-Generic

Got the error creating child process after logging in.

I click the ok button, and the terminal is still there. But I can't type in it.

I click to close it, and it goes right back to the log in screen again.

Hmm.

I try every WM on it (several :) ), same thing. I try failsafe gnome, same thing. I try failsafe terminal, same thing.

So I figure wth, ctrl+alt+f1 so I can try to reinstall udev and stop it and start it.

I type in my name and password and I get very many lines of this:

**-Bash: /dev/null: Permission Denied**

I think I see a problem. (ya think?)

So how is it I use a live cd to set up my user name and password on that drive again? 

That installation is totally unusable. There's nothing I can do with it. No way to edit anything (well, other than to go in the drive from here [gutsy] and edit stuff, then try to boot. But I think if I set my username and password, I'll be able to at least get to the command line and try stuff from there.

Oh, and recovery does the same thing as normal boot.

*edit: wow, I can't sudo gedit on that hard drive in the fstab. No permission. WTF.

---

### Post by redbob on 2007-09-19
Let's add some new facts...
- My third computer is a PCChips Celeron 600MHz running a command-line Ubuntu 7.04 with no errors... i took its hd and put in my faulting computer, then in the startup log we see the message 
> 
mv: memory exhausted
mv: memory exhausted

otherwise the computer is working in command-line
I read that it would be APCI configurarion... I disabled, but not changed.

---

### Post by redbob on 2007-09-19
Keyset and guys: My problem was solved. I've got to change the processor. After several tryouts, troubles gone away!!! Now the question is: what did it happened to my processor? My daugther was navigating on it, while ubuntu was downloading automatic updates, when the windows began to distort...

---

### Post by Ozztopia on 2007-09-27
> **BLTicklemonster said:**
> Here's my story:

Upgaded a while back to kernel 2.6.20-16-Generic

Got the error creating child process after logging in.

I click the ok button, and the terminal is still there. But I can't type in it.

I click to close it, and it goes right back to the log in screen again.

Hmm.

I try every WM on it (several :) ), same thing. I try failsafe gnome, same thing. I try failsafe terminal, same thing.

So I figure wth, ctrl+alt+f1 so I can try to reinstall udev and stop it and start it.

I type in my name and password and I get very many lines of this:

**-Bash: /dev/null: Permission Denied**

I think I see a problem. (ya think?)

So how is it I use a live cd to set up my user name and password on that drive again? 

That installation is totally unusable. There's nothing I can do with it. No way to edit anything (well, other than to go in the drive from here [gutsy] and edit stuff, then try to boot. But I think if I set my username and password, I'll be able to at least get to the command line and try stuff from there.

Oh, and recovery does the same thing as normal boot.

*edit: wow, I can't sudo gedit on that hard drive in the fstab. No permission. WTF.

I faced exactly the same problem. Couldn't even get into Gnome failsafe without getting the 'error creating child process....' and I simply had to reinstall. I tried automatic updates and this time excluding any of updates which had anything to do with the Linux kernel. After I updated, I got the same error. Maybe this does not have anything to do with the kernel updates? I am running Ubuntu now without updating anything, and it seems to be doing fine. (Keeping fingers crossed)

---

### Post by BLTicklemonster on 2007-09-27
Rather than keep beating my head against this one, I just used gparted to format this drive and use it for storage now.

Thanks for the help anyway.

---

