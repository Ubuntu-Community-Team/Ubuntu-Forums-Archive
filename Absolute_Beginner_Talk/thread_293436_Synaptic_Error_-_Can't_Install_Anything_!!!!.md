---
title: "Synaptic Error - Can't Install Anything !!!!"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by LLRNR on 2006-11-05
Hello !

I have the following problem: I was trying to install Java and some IDEs from Add/Remove Applications, but I accidentally left the box labelled "Show unsupported applications" checked. I got an install error telling me that one or more packages couldn't be installed properly and suggesting to switch to the advanced mode (Synaptic Package Manager) to solve the problem. In Synaptic, I found a broken package, after a few attempts I somehow managed to fix it or remove it, I don't remember exactly, and now I'm stuck with a package that is not fully installed and because of that I can't install anything else. The package is called **libcommons-pool-java**.

I have tried re-installing it, upgrading it, removing and completely removing it... none of these seemed to work. It jusk keep telling me that it's in a very bad and inconsistent shape and that I should try re-installing it before attempting a removal. And then it tells me: "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem" and after this message Synaptic Package Manager closes.

So here's what I get in a terminal when trying to fix the problem:

```
alex@UDD606:~$ sudo dpkg --configure -a
Password:
alex@UDD606:~$ sudo apt-get remove libcommons-pool-java
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  libcommons-pool-java
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libcommons-pool-java (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
alex@UDD606:~$ Errors were encountered while processing:
 libcommons-pool-java 
```

Alright, here I go trying to reinstall it :

```
alex@UDD606:~$ sudo apt-get install libcommons-pool-java
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
alex@UDD606:~$ sudo dpkg --configure -a
alex@UDD606:~$ sudo apt-get install libcommons-pool-java
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  libcommons-pool-java
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/42.2kB of archives.
After unpacking 90.1kB of additional disk space will be used.
E: Sub-process gzip returned an error code (1)
E: Prior errors apply to /var/cache/apt/archives/libcommons-pool-java_1.2-5_all.deb
debconf: apt-extracttemplates failed: Bad file descriptor(Reading database ...
dpkg: serious warning: files list file for package `libcommons-pool-java' missing, assuming package has no files currently installed.
89029 files and directories currently installed.)
Preparing to replace libcommons-pool-java 1.2-5 (using .../libcommons-pool-java_1.2-5_all.deb) ...
Unpacking replacement libcommons-pool-java ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
E: Sub-process /usr/bin/dpkg received a segmentation fault.


```

I have the slight feeling this doesn't work either. So I look in the Synaptic Help file and I see, under "Limitations and known bugs", that if a package fails installing, no more packages can be installed until I fix the problem ; I'm suggested to try **apt-get install -f**... Alright, here it is :

```
alex@UDD606:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
alex@UDD606:~$ sudo dpkg --configure -a
alex@UDD606:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libcommons-pool-java
The following packages will be upgraded:
  libcommons-pool-java
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/42.2kB of archives.
After unpacking 90.1kB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Sub-process gzip returned an error code (1)
E: Prior errors apply to /var/cache/apt/archives/libcommons-pool-java_1.2-5_all.deb
debconf: apt-extracttemplates failed: Bad file descriptor(Reading database ...
dpkg: serious warning: files list file for package `libcommons-pool-java' missing, assuming package has no files currently installed.
89029 files and directories currently installed.)
Preparing to replace libcommons-pool-java 1.2-5 (using .../libcommons-pool-java_1.2-5_all.deb) ...
Unpacking replacement libcommons-pool-java ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
E: Sub-process /usr/bin/dpkg received a segmentation fault.

```

You see, my problem is that I can't install anything anymore... :( I don't know what to do, I'm out of ideas, and I'm quite desperate, I almost customized my Dapper as I've wanted it, I was let's say halfway done, and now the only solution I see is a re-install... Dammit! And then again, who knows, maybe after reinstallation the same thing will happen... I don't know what to do, I hope someone can give me a clue.

Thanks in advance !

---

### Post by Iarwain ben-adar on 2006-11-05
Have you tried purge?
```
sudo aptitude purge libcommons-pool-java
```


Iarwain

---

### Post by LLRNR on 2006-11-05
Thank you, Iarwain ! (By the way, I didn't hear anything about "purge" before - I guess it is used to 'purify' the package, to do a clean install of that package, or what ?! :) )

When I try ```
sudo aptitude purge libcommons-pool-java
``` in a terminal, I get the following :
```
alex@UDD606:~$ sudo aptitude purge libcommons-pool-java
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
alex@UDD606:~$ sudo dpkg --configure -a
alex@UDD606:~$ sudo aptitude purge libcommons-pool-java
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REMOVED:
  libcommons-pool-java{p}
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing libcommons-pool-java (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
alex@UDD606:~$ Errors were encountered while processing:
 libcommons-pool-java

```
I guess it's a serious problem, huh?! :( As it pointed out, "You should try reinstalling before attempting a removal", I tried ```
sudo apt-get install libcommons-pool-java
``` again, but it didn't work, the output was the same as the one in my previous post (bad file descriptor, failed to write to pipe, error exit status 2, subprocess /usr/bin/dpkg received a segmentation fault and so on).

---

### Post by LLRNR on 2006-11-05
Whoopsie! There's another problem I encountered just now, I don't want to start a new thread with it because I think they're somehow related... Sure it's a dull problem... but err... what happened to my screensavers?! I can acces them from the menu but they don't work (of more than 70 screensavers, the default, only ~15 work, and the rest only prompt me with a beautiful black screen). This is strange... I don't know if they can be reinstalled, but even if that's possible, I can't do anything about it, because as I told you I can't install anything right now (not even from the terminal), any install process breaks when it encounteres the inconsistent package **libcommons-pool-java**.

So please tell me, do I really need to reinstall Ubuntu?! Is there no other way to bypass my problem :confused:

---

### Post by Iarwain ben-adar on 2006-11-05
Hi,
sorry that didn't work out :?

Don't know anything more..

Don't reinstall ubuntu just yet,
wait some more,
try some more,
and if that doesn't work, maybe try IRC.

Sorry for the stupid advice,
but that's all i know :?


Iarwain

---

### Post by LLRNR on 2006-11-05
Thanks, Iarwain ! It was very kind of you... alright, I'll listen to your advice, I won't reinstall Ubuntu just yet, I'll wait maybe there's someone else around that knows a "healing formula" for my problem... by the way, I never used IRC before... errr.... ummm... what do I need to do to enter on a IRC channel (and which IRC channels should I use) ? :oops:

---

### Post by LLRNR on 2006-11-05
Alright, so let me put it this way : is there a way to ROLLBACK all the changes I have done to my repositories... i.e. to go back to the original configuration, that I got right after the install ? Please help me, I really don't want to start over again with reinstalling Ubuntu... ](*,)

---

### Post by djroadrash on 2006-11-05
i would go back to synaptic and check all the same things u first checked and  reinstall those. are u looking for sunjava?, do a search with java and all that is there will come up. it should not be to difficult to fix, just check all the repositories and the extra ones and it should work i thinks?..good luck:)

---

### Post by pseudologically on 2006-11-05
Hey! :D

In Synaptic, have you tried > Settings (menu) > Preferences > Files (tab) > Delete Cached Package Files (button) > then reboot for safe measure? After booting, in Synaptic, > Status (button near bottom) > Not Installed (residual?) > then made sure that libcommons-pool-java is not in listed. If it is, right-click > Mark for Complete Removal > Apply?

:-k

If it still doesn't fix, try > Edit (menu) > Fix Broken Packages > Apply

:???:

And, if it still doesn't work (forbid), try searching for libcommons-pool-java in Synaptic's History (File (menu) > History) and see if you can find any kind of helpful info in there.

:neutral:

Hope something of this helps!

:)

---

### Post by LLRNR on 2006-11-05
I did what djroadrash suggested... and it doesn't seem to be effective : I tried to completely remove **java-commons** from Synaptic, with all its dependencies, it said that the removal was completed successfully, and when I clicked the OK button it told me that dpkg was interrupted and that I should run "dpkg --configure -a" to correct the problem, I did that, and when I started Synaptic again, the **libcommons-pool-java** package was still there, waiting to be upgraded... ](*,) I can't remove it and I can't upgrade it and I can't reinstall it and I can't purge it. Also, when I try ```
sudo apt-get update
``` it's ok, and when I issue ```
sudo apt-get upgrade
``` it can't upgrade because of the **libcommons-pool-java** package... Any ideas ?

---

### Post by LLRNR on 2006-11-05
Whoa!! Pseudologically, thank you very much (I'm sorry I didn't see your post, you submitted while I was writing) :D I'm trying this right now and see if it works... Thanks for the tip, mate !

---

### Post by LLRNR on 2006-11-05
Alright - so I did as pseudologically said :
- first I tried to delete chached package files and then I rebooted ;
- after rebooting nothing happened i.e. in Synaptic, in the status bar, it says: "1254 installed, 0 broken, 1 to install/upgrade, 0 to remove" ;
- note : I already tried to mark libcommons-pool-java for removal and for complete removal and click Apply, it then tells me "Successfully applied all the changes", and when I click Close, I get an error message telling me that dpkg was interrupted and that I should manually run "dpkg --configure -a" to correct the problem (at this point Synaptic closes). In a terminal I then issue ```
sudo dpkg --configure -a
``` and nothing happens and when I start Synaptic again, the libcommons-pool-java package just stays there waiting to be upgraded ;
- I find **libcommons-pool-java** in Synaptic, in the "Status" view, under the **Installed (upgradable)** heading (it's the only package there), and when I right-click on it and select either "Mark for Removal" or "Mark for Complete Removal" and then hit Apply, I get a "Successfully applied all changes" box and when I click Close, I get the error "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem", I click OK, Synaptic closes, and the same thing goes on and on and on and on and on...... I just don't get it !! I must be sooooo stupid !

---

### Post by LLRNR on 2006-11-05
OK, that's solved !!! :D :D I actually did it by mistake, I think - here's what happend : while browsing the forum, I desperately wanted to listen to some music and whilst VLC is a pretty good player, I wanted to try Beep Media Player (which I already had installed) and found out it just "hanged" my Ubuntu at certain moments (I actually had to switch to tty1 and issue **ps -e**, find the PID for Beep Media Player and then issue a **kill** command in order to keep my session - I didn't want to terminate xwindows and start all over again...). So I figured I had to reinstall Beep Media Player and I tried a ```
sudo aptitude purge beep-media-player
``` and, by doing this, I actually _accidentally_ managed to reinstall (this time *correctly*) the **libcommons-pool-java** package... WOW :D ain't it strange ?! I mean, when I tried to purge libcommons-pool-java (the faulty package), it didn't work, but it worked when trying to purge something else... [Oh and YES I finally got it : I now know what "purge" means and does... \\:D/ I'm soooo happy !! ]

---

### Post by Iarwain ben-adar on 2006-11-06
I'm glad you worked it out :D

It's nice to hear.


Iarwain

---

### Post by djroadrash on 2006-11-06
ok i just had the same problem as you but i did solve it, so u were doing the first step correctly as the synaptic error told u, so if u want synaptic to work correctly do this, go to console and type as u have already
```
sudo dpkg --configure -a

```
then instead of trying to use synaptic again to install what ever u wanted to install in the first place, go back to console and in my case i wanted to install sun-java5-bin so i typed
```
sudo apt-get install sun-java5-bin
```
the console told me what i already knew, that the package was half way installed (ofcourse cuz my son pulled the cord of my laptop and the battery was off), so i answered yes reinstall and errase the old unfinished file. and that was it. all fine now, synaptic works fine and registered the file as checked. so just remember to use the console to get that file and it will be fine. :)

---

### Post by LLRNR on 2006-11-06
Wow, djroadrash !! I think it would have had to happen to me all over again in order to understand what actually went on... Thank you for pointing this out and yes, I already tend to use the terminal more often than other synaptic-like facilities (I've always been a "keyboard-lover", lol).

Best regards,

LLRNR

---

