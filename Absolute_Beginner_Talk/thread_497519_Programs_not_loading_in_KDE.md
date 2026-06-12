---
title: "Programs not loading in KDE"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by dexter.lives on 2007-07-10
Recently, I have had problems with three programs--Firefox, Movie Player, and Archive Manager.  Sometimes, if I use one of the programs it will load and run properly the first time I use it, but if I close the program and try to run it again it won't load.  It will show up on the bottom tool bar with an hourglass as if it's loading, but then it disappears and I can't use the program until I reboot.  This happens more often with Movie Player and Archive Manager.  Any ideas?

Thanks in advance.

---

### Post by Rede on 2007-07-10
Same problem, with Firefox and the VMWare Server Console. Running from command line doesn't yeild any extra output, and the CPU doesn't even spike when they're launched. 

I'm using Feisty. Running with or without Beryl doesn't have any effect.

---

### Post by Sparkster185 on 2007-07-10
If you initiate the application from the command line, are there strange error messages?

As for it not starting up again, have you tried killing it via command line or the process manager?  Process Manager is easy to find under the menus.

Command line:
```

ps -u USERNAME | grep PROCESS NAME

```

Substitute your username and process name, respectively.  If you don't know the entire process name, you can use * matching.  Example:  grep "*firefox*".  From here, you can get the PID and issue a kill command to it.

---

### Post by Happy_Man on 2007-07-10
Actually, that seems to happen every now and then with me, too. Whenever it does, and the problem persists (generally it doesn't happen more than once or twice), I reboot. Fixes it for me, although a reboot may be overkill.

---

### Post by Rede on 2007-07-10
I killed all instances of firefox-bin, then attempted to load it from the command line:

```

me@my-computer:~$ firefox
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

Thats the usual output before an application launches. However, Firefox doesn't launch.

---

### Post by Pragmatist on 2007-07-10
[http://kubuntuforums.net/forums/index.php?topic=7964.0;topicseen](http://kubuntuforums.net/forums/index.php?topic=7964.0;topicseen)
[http://ubuntuforums.org/showthread.php?p=1762954](http://ubuntuforums.org/showthread.php?p=1762954)

---

### Post by Happy_Man on 2007-07-10
Hmmm..... as I said, does a reboot fix anything?

And about those errors.... they're harmless, not the issue.

---

### Post by dexter.lives on 2007-07-10
> **Sparkster185 said:**
> 

As for it not starting up again, have you tried killing it via command line or the process manager?  Process Manager is easy to find under the menus.

Command line:
```

ps -u USERNAME | grep PROCESS NAME

```
.

Thanks a lot, I've been wondering how to access the process list. I just gave it a shot...and Terminal does not load.  Looks like I have to reboot.

BTW, I applaud your taste in music.

---

### Post by dexter.lives on 2007-07-10
> **Happy_Man said:**
> Hmmm..... as I said, does a reboot fix anything?

And about those errors.... they're harmless, not the issue.

I can run the programs after rebooting, but only until the problem rears its head again.  I'm hesitant to call it a fix.

If the errors are harmless do I not need to try the fixes posted by **Pragmatist**?  That would be nice since I can't seem to save changes to the xorg.conf file.

---

### Post by Pragmatist on 2007-07-10
> **dexter.lives said:**
> ...I can't seem to save changes to the xorg.conf file.
Are you using a LiveCD?  Which one?  Normally, you need to use **sudo** or **su** to have permission to change the xorg.conf file.

---

### Post by dexter.lives on 2007-07-10
I'm not using a live cd, Kubuntu is primary OS.  If xorg.conf needs to be opened though Terminal, can you please tell me the code?  I'm still not very handy with Sudo...but I'm trying.  Thanks for your help.

---

### Post by Happy_Man on 2007-07-10
> **dexter.lives said:**
> I'm not using a live cd, Kubuntu is primary OS.  If xorg.conf needs to be opened though Terminal, can you please tell me the code?  I'm still not very handy with Sudo...but I'm trying.  Thanks for your help.
Quite simple. ```
kdesu kate /etc/X11/xorg.conf
```

---

### Post by dexter.lives on 2007-07-10
Cool, thanks.  What does "kdesu" and "kate" stand for?  I'll understand if you don't feel like explaining this to me.

---

### Post by Happy_Man on 2007-07-10
No problem. "kdesu" is the KDE version of "graphical sudo" that is, it tells the computer to pop up a window asking for your password to grant sudo access. "kate" is simply the name of the KDE text editor, and of course, the rest is the xorg.conf filepath.

In short, what that command says is, "Pop up a window asking for the password so I can open xorg.conf using Kate with root permissions."

---

### Post by dexter.lives on 2007-07-10
Commented out "wacom" stuff...no change.

---

### Post by dexter.lives on 2007-07-13
Seems that others are having this problem...has anyone figured out a fix?  **Pragmatist** seemed to suggest that commenting out "wamco" references from xorg.conf file would fix the prob, unfortunately it didn't.  Any other ideas?

Thanks!

---

### Post by Pragmatist on 2007-07-13
Please post your **/etc/X11/xorg.conf** file, so we can examine it.

---

### Post by dexter.lives on 2007-07-13
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"stylus"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"eraser"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"cursor"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"NVIDIA GeForce FX 5200"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Synaps"
	Option		"DPMS"
	HorizSync	28-60
	VertRefresh	60-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce FX 5200"
	Monitor		"Synaps"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Pragmatist on 2007-07-13
Did you try Sparkster185's suggestion about killing the application from the command line?

If  you can't open a terminal, try using a virtual terminal by typing CTRL+ALT Fx where x is a number from 1 to 6.  For example:  **CTRL+ALT+F3**  Then you log in and try Sparkster185's suggestion of closing the application with the kill or killall commands.  When you are finished, just type **exit **and go back to your main virtual terminal by typing **CTRL+ALT+F7**

---

### Post by Pragmatist on 2007-07-13
Here is how you use the **ps** the **killall** and the** kill** commands:

Find the process name and process ID:
```
ps -ef |grep firefox
```> 
desktop:~$ ps -ef |grep firefox
me     **5846**  5776  5 09:29 ?        00:01:41 /usr/lib/firefox/**firefox-bin**
me     6631  5862  0 10:00 pts/0    00:00:00 grep firefox
The process name is firefox-bin and the process ID is 5846

To use **killall** you use the process name:
```
killall firefox-bin
```To use **kill** you use the process ID:
```
kill -9 5846
```kill is usually more powerful (especially with -9), but killall is easier since you only need to know the name which doesn't change (its name will always be firefox-bin but its ID will change)

Check if the process is still there by using the ps command:
> 
desktop:~$ ps -ef |grep firefox
me     6631  5862  0 10:00 pts/0    00:00:00 grep firefox
This line:  *me     **5846**  5776  5 09:29 ?        00:01:41 /usr/lib/firefox/*[B]*firefox-bin*
[/B]is gone so you ended the process.  Ignore the line with the process name of "grep firefox"  That is the process you started when you ran the ps and grep commands.

---

### Post by dexter.lives on 2007-07-15
> **Pragmatist said:**
> Did you try Sparkster185's suggestion about killing the application from the command line?

I finally had a chance to try this, and, unfortunately, it did not solve the problem.

The following is copied from Terminal
> xxx@desktop:~$ ps -ef |grep movieplayer
xxx     6289  6270  0 21:26 pts/1    00:00:00 grep movieplayer
xxx@desktop:~$ kill -9 6289
bash: kill: (6289) - No such process
xxx@desktop:~$ killall movieplayer-bin
movieplayer-bin: no process killed


---

### Post by Pragmatist on 2007-07-15
Actually, this is not the process for movieplayer: 
 xxx     6289  6270  0 21:26 pts/1    00:00:00 grep movieplayer

It is the process for a program called "grep".  When you typed:
**ps** -ef |**grep** movieplayer

It includes two commands (**ps **and** grep**)  **ps **generated the process list and passed it to **grep** which is a program that filters.  **grep** filtered the process list using the keyword you supplied "movieplayer".  Since **grep** started before **ps** did (in this case it is in reverse order: first grep starts, then it is fed the list), the **grep** process is included in the list and finds itself when it filters because the **grep** command (**grep** movieplayer) contains the keyword "movieplayer".  Once you see the results, the **grep** process is finished.  That is why you got a "no such process" when you tried to kill it.

Do you know what movieplayer's executable is called?  If it doesn't contain the word "movieplayer", then **grep** won't find it in the process list. if you want to try this with movieplayer,  I can explain how to find out the executable name, but let's try firefox first, since I know the executable for that.  The executable is called "firefox-bin".  
Use the exact same command as before, but use the keyword "firefox":
```
ps -ef |grep firefox
```

---

### Post by dexter.lives on 2007-07-18
I was lucky enough to have Firefox and Totem (the movieplayer) die at the same time.  This is what happened when I tried to kill the Firefox process after I was unable to re-open the program...

> ~$ ps -ef |grep firefox
xxx     **8531**  8514  0 15:31 pts/1    00:00:00 grep firefox
~$ kill -9 8531
bash: kill: (8531) - No such process
~$ killall firefox
firefox: no process killed
killall firefox-bin
firefox-bin: no process killed

I'm either doing something wrong--which is possible--or the problem is not quite what we think it is.  I have noticed that others have mentioned Berryl in their comments.  I recently installed Compiz...think the problems are related to Compiz?  I don't want to install it, but I think that is my next step...

---

### Post by Pragmatist on 2007-07-18
> **dexter.lives said:**
> ...I tried to kill the Firefox process after I was unable to re-open the program...
Let's make sure of exactly what your doing

1.) You start firefox from a terminal by typing this:
```
firefox&
```

2.) You DO NOT CLOSE firefox.  Instead you kill firefox from the command line:
```
killall firefox-bin
```

> **dexter.lives said:**
>  I'm either doing something wrong...
In my last post I explained, in detail, why you should ignore this line:
> xxx     **8531**  8514  0 15:31 pts/1    00:00:00 **grep firefox**
This is **not** the **firefox** program, **it is** the **grep** program.  Your system responded correctly:
>  bash: kill: (8531) - No such process
**grep firefox **is finished so there is nothing to kill.  All you need to know is this:
[B][I]Ignore processes with the word grep

[/I][/B][I]Your looking for a process that looks like this:
[/I]> ~$ ps -ef |grep firefox
xxx     **6063**  5993  0 06:54 ?        00:02:18 /usr/lib/firefox/**firefox-bin**
[COLOR=Silver]xxx     6780  6096  0 17:33 pts/0    00:00:00 grep firefox[/COLOR]


---

### Post by dexter.lives on 2007-07-18
I appreciate the detailed explanation of grep...but it's going right over my n00bie brain.  I'll read about it some more when I have time.

As to the suggestions of opening and closing programs with terminal...this would not be a problem if I lived alone.  However, I do not, and my partner will *not* tolerate the command line.  She's a point and click type o' gal and fiercely resists change.  

How a program opens--clicking vs command line--should be irrelevant.  Something is...broken...and I really would like to know the root of the problem rather than applying the band-aid you've so patiently been walking me through.

Thanks again.

---

### Post by Pragmatist on 2007-07-18
> **dexter.lives said:**
> ...rather than applying the band-aid you've so patiently been walking me through...

My suggestions aren't remotely like a band-aid.  They're function is to diagnose and solve your problem.  I wasn't suggesting that you always start firefox from the command line.  Just once!  These are tests to narrow down the cause of your problem and it is necessary for you to do them so we can help you solve your problem.

---

### Post by Pragmatist on 2007-07-18
Also, if you really don't want to run any commands at all (you should learn it soon since it is essential to solve problems), then have you tried this:

1.) Did you update your system?

2.) Did you try updating your version of Firefox?
OR
3.) Did you try a reinstall of firefox?

---

### Post by dexter.lives on 2007-07-19
> I wasn't suggesting that you always start firefox from the command line. Just once!
Started and killed Firefox from command line several times last night...it was fun. Is there something I should look for?

> ...have you tried this:

1.) Did you update your system?

2.) Did you try updating your version of Firefox?
OR
3.) Did you try a reinstall of firefox?

The system is updated frequently, and I'm running FF v.2.0.0.4.  No updates were available when I woke up this morning.

---

### Post by Pragmatist on 2007-07-19
> **dexter.lives said:**
> Started and killed Firefox from command line several times last night...it was fun. Is there something I should look for?

So you don't have the problem when you start and stop firefox from the command line??  There are no long delays when restarting firefox?  If that is true, what does it tell you?  

It tells me that there is nothing wrong with firefox, or even X.  The problem most likely has something to do with GNOME--at least that is where I would troubleshoot next.

---

### Post by dexter.lives on 2007-07-19
The problem isn't isolated to FF.  I have also had the same problem with GAIM, Totem, k3b, and even Terminal.

I'll use a program and close it when I no longer need it.  A few hours later, I'll decide to run it again, and *sometimes* it won't fully load.  It will start to load, but suddenly quits and will not fully load until after I reboot.

> The problem most likely has something to do with GNOME
I run KDE...is GNOME doing some kind of work in the background?

---

### Post by Pragmatist on 2007-07-19
> **dexter.lives said:**
> I run KDE...is GNOME doing some kind of work in the background?
Whoops! :oops:  Sorry about that.  In that case, the issue would be KDE.  KDE and GNOME are both "desktop environments"  That is a fancy word for "a collection of programs and settings"  So neither GNOME nor KDE are a single program.  My reasoning goes like this:
1.) Firefox, and the other programs you've mentioned, are all X programs (an X program is a program that only operates on top of X, which is a graphical interface (GUI)).  Clearly X works, or you couldn't run these programs at all.

2.) Firefox works since you can consistently start and stop it using a terminal.  Assuming this is true of the other programs, then the issue is not the individual program

3.) My current view is that your problem is due to some settings of your desktop environment (the logic is the same whether your using KDE or GNOME or XFCE, or some other desktop environment)

One simple test to determine if something is askew with your user settings, is to add a user, log in as that user, and see if you get the same problem.  The reason for this test is that the new user will have new, default, settings for the various programs, and for GNOME.  If you want to see how many configuration files are specific to your current user, try this:
```
ls -a $HOME
```Most programs will create a hidden directory (a directory beginning with a period) in your home folder.  The program then uses these directories to record your individual settings and preferences, your bookmarks if it is a browser, and anything the program records that is specific to your user.  KDE also has hidden folders in your home folder.  KDE records its settings for your individual user.  So, if you make another user, you can easily test if your problems are due to your regular user's settings.

Here is how you can add a user:
```
sudo adduser tempuser
```Give your password when prompted and then answer the questions and remember the password you gave.  Now you have a user called: tempuser
with the password you gave.

Edit: In my original version of this post I suggested using the su command to switch to the new user.  This won't help us since we want to test these programs by running them from the desktop.  Logging out and logging back in as the new user is the correct method.

Now logout (you have this choice on the same menu you use to shutdown)and login as the new user.  Run the various programs and see if your problem still exists.

After you are done testing with the new user, just logout and log back in as your regular user.
To delete the new user you created, make sure your logged in as your normal user, and just type this:
```
sudo deluser tempuser
```

---

### Post by dexter.lives on 2007-07-23
> One simple test to determine if something is askew with your user settings, is to add a user, log in as that user, and see if you get the same problem.

I've spent the past few days trying to duplicate the problem in Gnome with a different user, and was unable to do so.  I guess this is some kind of success...

---

### Post by Pragmatist on 2007-07-23
> **dexter.lives said:**
> I've spent the past few days trying to duplicate the problem in Gnome with a different user, and was unable to do so.  I guess this is some kind of success...

Definitely!  It means the problem is due to user settings and that is very easy to fix.  The only strange thing is that the problem occurs with more than one application.  This confirms my view that the problem is with some lower-level desktop software like gtk (a library of widgets used by all gtk applications).  There is a simple test you can do, however.  Backup your user settings for the troublesome applications, and then remove the original.  The application should then generate new, default, settings for you.  For firefox, the hidden folder (i.e. directory) you want is [B].mozilla

[/B]Change to your home directory:
```
cd
```

rename the **.mozilla **directory and call it "mozilla.backup":
```
mv **.mozilla** mozilla.backup
```

Now start firefox the way you always do.  If this worked, you should not have your normal bookmarks (we can easily fix that, but for now we are testing).  See if you can duplicate the problem you've been having.

You can follow this same procedure for the other problematic applications.  If this doesn't work, we will try the same thing, but with settings that apply to a whole category of applications, such as gtk apps.

---

### Post by RomeReactor on 2007-07-23
Hi. Just a comment:

> **Pragmatist said:**
> If this doesn't work, we will try the same thing, but with settings that apply to a whole category of applications, such as gtk apps.

All the problematic applications--well, except k3b--are GTK apps. It could be related to the theme **dexter.lives** is using; it may help to change the theme for GTK applications from the control center (can't remember the correct name, as I don't have KDE on my system right now).

---

### Post by dexter.lives on 2007-07-23
Thanks, **Pragmatist**

I followed your instructions, and FF loaded as it should have (without bookmarks, extensions, etc) so I went to work to "break" it.  It didn't take long--second or third time I opened and closed it--before it stopped loading.  

On a side note, I had to fix my brother's my brothers computer this weekend, and had forgotten how awful it is to work on a Windows system.  Even though I don't really understand what I'm doing in K/Ubuntu yet, I much prefer this way and haven't given a second thought to switching back.:)

---

### Post by Pragmatist on 2007-07-23
Since we already know you don't have this problem when you start the applications from a terminal (please correct me if I'm remembering this incorrectly), let's try and work on that before working on the user settings of your environment.

How do you start your applications?  Do you use a menu? A launcher? An Icon?  Regardless, I'd like you to try a launcher for this test.  In GNOME, you just right-click the panel, select "add to panel", choose "application launcher", and pick the application from the menu list.  Now there will be a small icon on your panel.  Right-click the launcher, and choose properties, choose the drop-down-box labeled "Type:" and select "application in terminal".  Close out of properties and click the launcher.  In addition to the application loading, a terminal window will open.  Just ignore it.  Can you duplicate your problem now?

Edit: I know you use KDE, but I don't know how to create a launcher in KDE.  It shouldn't be hard to figure out though.

---

### Post by Pragmatist on 2007-07-23
I also agree with RomeReactor's suggestion.  You might try the "backup then delete the hidden user settings directory" for KDE as a whole.  I think the directory you want is called **.kde**  Here are some instructions for the SUSE distribution:
[http://en.opensuse.org/SDB:Restoring_KDE's_Default_Settings]("http://en.opensuse.org/SDB:Restoring_KDE%27s_Default_Settings")

---

### Post by dexter.lives on 2007-07-24
Entered this code from the [SUSE page]("http://en.opensuse.org/SDB:Restoring_KDE's_Default_Settings")
```
tar -czvf backup_kde.tar.gz .kde*/ .skel/ *Desktop/
```

and, after a whole lotta lines, got this 
> tar: .skel: Cannot stat: No such file or directory
Desktop/
Desktop/Wii Games.ods
Desktop/.directory
tar: Error exit delayed from previous errors


The 'error exit' message makes me a little nervous...is everything backed up?  Can I delete the directories?

Thanks, Pragmatist and RomeReactor

---

### Post by Pragmatist on 2007-07-24
Forget the SUSE instructions for now; they must have slightly different user directories.  Just backup the **.kde** directory and then delete it (follow the exact same method in the earlier post--i.e. the way you did it for **.mozilla** except just name the backup file .kde.backup or anything else you find memorable)

The basic idea here is that many programs create a hidden directory, within your home directory, to store your user settings.  If you delete such a directory, the program will create a new one with default settings.  You are backing up your current directory so you have the option of "rolling back" to your previous settings.

---

### Post by dexter.lives on 2007-07-24
Problem still exists...FF failed to load.


Thanks!

---

### Post by Pragmatist on 2007-07-24
> **dexter.lives said:**
> Neat!  Is there anyway I can get my old firefox profiles back?  It seems like I should be able to...

I haven't been able to "break" any programs yet, so it seems like this worked.  If I feel like investigating how things went awry in the first place, how would I go about that?

Thanks!

The way you get your old firefox profiles back is you reverse the procedure:

Change to your home directory:
```

     cd 

```rename the **mozilla.backup **directory and call it ".mozilla":
```

     mv  **mozilla.backup** .mozilla 

```Did you followed my suggestion and back up and then remove the .kde directory?

The way you determine the setting or settings that caused the problem, is you make changes one-by-one and write them down on a piece of paper.  Write down the default setting and what you changed it to.  Then, when the problem occurs, check your paper and undo your last change.  If the problem goes away again, you have just found the setting that caused all the trouble.  

If you want to guarantee that you find the setting that caused all of the trouble, then you need to **make all of the changes you made in the past** and record  them one-by-one.  If you only want to know the cause if it happens again, then just record each change you make (whether or not is a change you've made in the past) and if the problem recurs, reverse the change and see if it goes away; if it does, you know the cause.

---

### Post by dexter.lives on 2007-07-24
Argh...renaming **mozilla.backup** to **.mozilla** should have been obvious...sorry

Also, I spoke too soon when I said the problem went away...I am experiencing the same problem with FF. :(

---

### Post by Pragmatist on 2007-07-24
> **dexter.lives said:**
> Argh...renaming **mozilla.backup** to **.mozilla** should have been obvious...sorry

Also, I spoke too soon when I said the problem went away...I am experiencing the same problem with FF. :(

Just Firefox?  Did the problem happen with firefox's default settings, or after you reverted to your old settings?

---

### Post by dexter.lives on 2007-07-24
It happened before I reverted to FF's old settings--haven't done that yet--and other programs have not yet failed to load.  The only modification I made to FF was adding a New Tab icon to the menu bar...all else was default.  If there is a pattern to when/why a program fails, I haven't recognized it.  This makes testing somewhat unscientific...I simply open and close a program until it fails to load.  Usually this doesn't take longer than half a dozen tries, and as we've just seen can lead to incorrect  conclusions.

---

### Post by Pragmatist on 2007-07-24
> **dexter.lives said:**
> It happened before I reverted to FF's old settings--haven't done that yet--and other programs have not yet failed to load.  The only modification I made to FF was adding a New Tab icon to the menu bar...all else was default.  If there is a pattern to when/why a program fails, I haven't recognized it.  This makes testing somewhat unscientific...I simply open and close a program until it fails to load.  Usually this doesn't take longer than half a dozen tries, and as we've just seen can lead to incorrect  conclusions.
The basis for these suggestions is that new users on your system do not have the problem.  Are you really sure that is true??  If it is true, then absolutely your problem has something to do with changes unique to your user.  We have not yet examined all such changes, but it may not be the best approach if the cause isn't guaranteed to be something specific to your user

---

### Post by dexter.lives on 2007-07-24
> The basis for these suggestions is that new users on your system do not have the problem. Are you really sure that is true??

I'm fairly certain it is true, but to make sure it is, I'll create a new user and use it for one week; I think this is enough time to test the hypothesis.  If nothing happens, I'll let you know in seven days.

---

### Post by sagui on 2007-07-25
I've been having the same problem when trying to load some of my apps, like adept, FF, and others.  I haven't been able to figure it out myself, but I'm happy that I'm not the only one.  Hope we can fix this!

---

### Post by dexter.lives on 2007-07-25
Sagui, do you remember when things went wrong for you?  What changes did you make before it started happening?

**Edit:** I think it's happening to me after I use Totem.  Last night everything went sideways after using it to stream music, and this afternoon  it all went wrong after using it to watch some vids.  How 'bout you?

GL...

---

### Post by sagui on 2007-07-25
It seems that my problems arise after using KDE for a while, especially after several rounds of suspend/recover.

At first I thought it was a problem with the kdesu command, because at first it was only adept package manager and wine-doors and such, but then firefox started acting up.

I don't know, it's weird.  Only happens in KDE, when I start Gnome it works fine,

---

### Post by Pragmatist on 2007-07-26
> **sagui said:**
> 
I don't know, it's weird.  Only happens in KDE, when I start Gnome it works fine,

What happens if you run KDE with a new user?  Refer to post #31 in this thread for instructions on creating a new user.

---

### Post by Happy_Man on 2007-07-26
Guys..... it is a bug. It has been listed over in the Kubuntu Forums as such. The KDE folks have been made aware of it.

---

### Post by Pragmatist on 2007-07-26
> **Happy_Man said:**
> Guys..... it is a bug. It has been listed over in the Kubuntu Forums as such. The KDE folks have been made aware of it.
Please provide a link.

Also, "what" is the bug?  The problem doesn't exist when running as a new user and the OP hasn't figured out yet what changes from the defaults cause the problem.

---

### Post by Happy_Man on 2007-07-26
Actually, it is on the Kubuntu Forums, but I linked to the page, and as I don't save history... :(

But I have been able to replicate it on a fresh Kubuntu install..... and when I have been lucky to get it from a terminal.... it reports back that "the program is taking too long to start!" and that's all.

---

### Post by Pragmatist on 2007-07-26
> **Happy_Man said:**
> Actually, it is on the Kubuntu Forums, but I linked to the page, and as I don't save history... :(
Well, you found it once, see if you can find it again! :)  It is appropriate to provide a link when notifying others of a known bug.

> **Happy_Man said:**
>  But I have been able to replicate it on a fresh Kubuntu install

Again you need to provide details.  **What do you do to replicate the problem?**  The OP has not been able to duplicate the problem using a new user with default settings.

---

### Post by Happy_Man on 2007-07-26
> **Pragmatist said:**
> Well, you found it once, see if you can find it again! :)  It is appropriate to provide a link when notifying others of a known bug.



Again you need to provide details.  **What do you do to replicate the problem?**  The OP has not been able to duplicate the problem using a new user with default settings.
Nothing..... I just am doing my work as usual.... generally I don't need to install stuff on a fresh Kubuntu install, as all I need is there...... and apparently randomly, some application just won't start. It'll make like it's starting, and then.... nothing. No processor spikes, nada. And usually that stays the same app won't start until I reboot. Then everything's OK. Until it happens again. And so on.....

I will get back to you on those bugs, though.

---

### Post by dexter.lives on 2007-07-27
I searched Kubuntu Forums--didn't know it existed until Happy Man mentioned it--and found [this]("http://kubuntuforums.net/forums/index.php?topic=3081953.0") piece of advice.  Before I do any editing I thought I would run it by the people who seem to know what they're doing.

One of the respondents from the Kub Forum mentions that there are several threads regarding this topic...I've searched using the terms listed below and found three relevant discussions.  [This]("http://kubuntuforums.net/forums/index.php?topic=3082355.0") one references the URL posted above, and [this]("http://kubuntuforums.net/forums/index.php?topic=6816.0") one.  Neither of these seem to be very useful, nor do they reference a bug.
[LIST]
[*]programs do not load
[*]programs not loading
[*]programs not starting
[/LIST]

---

### Post by Happy_Man on 2007-07-27
Here's something I just noticed: Amarok started to not start for me, and as I can't live without my music, I decided to get two birds with one stone and test this out a bit. What I noticed is that *Amarok was still running in the process list.* Apparently, the last time I closed it, it didn't actually quit itself. So, naturally, KDE saw that it was still running and didn't spike anything up, because *it was still there.* By manually killing the process, I was able to get Amarok back. Hope this little anecdote helps.

---

### Post by Pragmatist on 2007-07-27
dexter.lives are you still testing with the new user?  If you are, and you can't replicate the problem, try gradually modifying the new user's settings to your regular user's settings.  See when it breaks.

---

### Post by sagui on 2007-07-28
> **dexter.lives said:**
> I searched Kubuntu Forums--didn't know it existed until Happy Man mentioned it--and found [this]("http://kubuntuforums.net/forums/index.php?topic=3081953.0") piece of advice.  Before I do any editing I thought I would run it by the people who seem to know what they're doing.


This seems to have actually worked for me, since making the changes all the programs that used to give me grief now open up no problem.  I'll let you know if things revert to not opening.

Thanks dexter.lives

---

### Post by Pragmatist on 2007-07-28
> **sagui said:**
> This seems to have actually worked for me, since making the changes all the programs that used to give me grief now open up no problem.  I'll let you know if things revert to not opening.

Thanks dexter.lives
What worked for you?  The advice on that link says:
> 
add "timestamp_timeout=0" to the Defaults set in /etc/sudoers.

Is that what you did?

The above thread also says:
> ....The problem occurs when you are trying to open programs that require the sudo password....
Are you guys running your programs with sudo?

---

### Post by andyho on 2007-07-28
Just thought I'd jump in here too.. I'm still not having much luck with my firefox or thunderbird... here's the link to my original post; [http://ubuntuforums.org/showthread.php?t=511317](http://ubuntuforums.org/showthread.php?t=511317)

I just tried editing /etc/sudoers and it did nothing.. still can't open firefox or thunderbird! Think I might go jump over to the irc channel! :)

---

### Post by Pragmatist on 2007-07-28
Try creating a new user and see if the problem still exists.  I explain how to do this back in post #31.

---

### Post by andyho on 2007-07-28
did I need to specify a user name?? I just hit enter for the default and when I tried to log back in it kept giving me incorrect login..

EDIT: OK nevermind.. that was a user error... but upon logging in with tempuser it loads using gnome and firefox still doesn't work.

---

### Post by Pragmatist on 2007-07-28
> **andyho said:**
> ....but upon logging in with tempuser it loads using gnome and firefox still doesn't work.

Your regular user loads KDE and the new user loads GNOME?

---

### Post by andyho on 2007-07-28
CRAP!! Everything is running SUPER glitchy now that I signed in back under my user name.. my keyboard, mouse, and konqueror are all lagging?!?

---

### Post by Pragmatist on 2007-07-28
> **andyho said:**
> CRAP!! Everything is running SUPER glitchy now that I signed in back under my user name.. my keyboard, mouse, and konqueror are all lagging?!?
Please reply to my previous question.

---

### Post by andyho on 2007-07-28
> **Pragmatist said:**
> Your regular user loads KDE and the new user loads GNOME?

Yes.. I was originally just using Ubuntu and then yesterday I installed the kubuntu-desktop to see how it was.

---

### Post by Pragmatist on 2007-07-28
> **andyho said:**
> Yes.. I was originally just using Ubuntu and then yesterday I installed the kubuntu-desktop to see how it was.

Try rebooting and then logging in to your regular user.  Are things still haywire after you do that?

---

### Post by andyho on 2007-07-28
I'll try that.. be right back :)

---

### Post by andyho on 2007-07-28
alrighty.. I deleted the tempuser, rebooted,  and things are responding normally again! Still no firefox or thunderbird though.. the only thing I haven't tried yet is uninstalling and reinstalling them. On the thread I created, I mentioned for some reason I have in my usr/bin a mozilla-firefox and a mozilla-firefox.ubuntu file. Same thing for thunderbird. Is that causing the problem since they're pointing to different locations?? I actually was able to get firefox to open after clicking on one of them several times.. does that make sense?!

---

### Post by Pragmatist on 2007-07-28
> **andyho said:**
> alrighty.. I deleted the tempuser, rebooted,  and things are responding normally again!

That is not what I suggested.  You are assuming that creating tempuser was the cause of your problem.  I asked you to reboot and login as your regular user for a specific reason.  If all of the "super glitchy" behavior was gone, it means that switching from KDE to GNOME and back to KDE again was the problem since some GNOME apps were still running.  This would be useful knowledge and could help solve your main problem.

---

### Post by andyho on 2007-07-28
> **Pragmatist said:**
> That is not what I suggested.  You are assuming that creating tempuser was the cause of your problem.  I asked you to reboot and login as your regular user for a specific reason.  If all of the "super glitchy" behavior was gone, it means that switching from KDE to GNOME and back to KDE again was the problem since some GNOME apps were still running.  This would be useful knowledge and could help solve your main problem.

No, I didn't think that creating the tempuser was the problem. I was under the assumption that it was gnome as well. I had already logged in with the tempuser and that's when it logged in using gnome and then I re-logged in using my regular user name  and that's when things became glitchy. Then I deleted the tempuser, rebooted, logged back in under my user name and things are working fine, just still no firefox or thunderbird.. I can recreate a tempuser if needed. :)

---

### Post by Pragmatist on 2007-07-28
> **andyho said:**
> No, I didn't think that creating the tempuser was the problem.
Then why delete tempuser if you didn't think it was the problem?  Obviously you are free to do as you wish, but, if you want my help, you need to try my suggestions.

---

### Post by andyho on 2007-07-28
> **Pragmatist said:**
> Then why delete tempuser if you didn't think it was the problem?  Obviously you are free to do as you wish, but, if you want my help, you need to try my suggestions.

Sorry, just didn't see the sense in keeping it around after I had tried your suggestion. A couple more keystrokes to setup another tempuser if needed doesn't bother me none. :) Like I said, I HAD logged in with tempuser and it still wouldn't load firefox or thunderbird. So not really sure why I would need a tempuser when it's not the problem, and I won't be using it, other than trying to diagnose problems that seem to be somewhat figred out; gnome issue, not tempuser.. not trying to step on anyones toes.. I just don't want to forget about it being there and have it around for no reason.

---

### Post by Pragmatist on 2007-07-28
> **andyho said:**
> Sorry, just didn't see the sense in keeping it around after I had tried your suggestion. A couple more keystrokes to setup another tempuser if needed doesn't bother me none. :) Like I said, I HAD logged in with tempuser and it still wouldn't load firefox or thunderbird. So not really sure why I would need a tempuser when it's not the problem, and I won't be using it, other than trying to diagnose problems that seem to be somewhat figred out; gnome issue, not tempuser.. not trying to step on anyones toes.. I just don't want to forget about it being there and have it around for no reason.

Make a note and stick it to your monitor.  That is what I do if I really don't want to forget! :)

You didn't test tempuser under the same conditions as your regular user.  Your regular user logs in to KDE and tempuser logs into GNOME.  Create tempuser again, and when you login as tempuser, first choose "select session" in GDM and choose "KDE".  This way you should log tempuser into KDE.

---

### Post by andyho on 2007-07-28
> **Pragmatist said:**
> Make a note and stick it to your monitor.  That is what I do if I really don't want to forget! :)
 LOL!!! yeah... I'm so bad I've color categorized my post its!!! :lol:
> 
You didn't test tempuser under the same conditions as your regular user.  Your regular user logs in to KDE and tempuser logs into GNOME.  Create tempuser again, and when you login as tempuser, first choose "select session" in GDM and choose "KDE".  This way you should log tempuser into KDE.
Alrighty.. will let ya know how it goes in a couple!! thanks again!!

---

### Post by andyho on 2007-07-28
Ok.. I'm using tempuser in kde.. right off the bat I have no desktop icons and my sound mixer is missing. Firefox and thunderbird are still a no go. and I still get.. tempuser@andyho-ubuntu:~$ firefox
Segmentation fault (core dumped)
tempuser@andyho-ubuntu:~$ thunderbird
Segmentation fault (core dumped)

---

### Post by Pragmatist on 2007-07-28
> **andyho said:**
> Ok.. I'm using tempuser in kde.. right off the bat I have no desktop icons and my sound mixer is missing.
That doesn't concern me too much since you may have added those features for your main user, but not tempuser.

> **andyho said:**
>  Firefox and thunderbird are still a no go. and I still get.. tempuser@andyho-ubuntu:~$ firefox
Segmentation fault (core dumped)
tempuser@andyho-ubuntu:~$ thunderbird
Segmentation fault (core dumped)

That is what I wanted to find out.  dexter.lives couldn't replicate the problem with tempuser, but you can.

btw, what happens now when you logout and then login to your main user?  Are things crazy with your main user?

---

### Post by andyho on 2007-07-28
Just logged back in under my user name and so far things are running fine.. I guess I should mention that yesterday I had also tried using "fix broken packages" but that didn't seem to do anything either.. I have backed up my favorites so if I need to uninstall firefox and thunderbird and reinstall them it won't be too big of a deal, I'll just lose my plugins since for some reason I can't find the file that stores them.

---

### Post by Pragmatist on 2007-07-28
> **andyho said:**
> ....I'll just lose my plugins since for some reason I can't find the file that stores them.

To easily find files, I like to user the **locate** command.  **locate **searches a database which contains a list of all the files currently on your system.  The only disadvantage is that you need to update that database anytime you make a change (if your search depends on those changes).  [I]**edit: **Your system will regularly update the database, at least once-a-day, but you need to manually update it if you make changes and you don't want to wait for your system to update it.
[/I]
 Here is how you do it:

Run this command and wait until it finishes.  Since this is the first time your running it, it has to build the whole database which takes a few minutes.
```
sudo updatedb
```Next do a simple keyword search:
```
locate plugins
```You'll get any files or directories on your system that contain the keyword "plugins".  To filter the results to plugins related to firefox, you use the **grep** command:
```
locate plugins | grep firefox
```On my system, the plugins are located at: **/usr/lib/firefox/plugins**

---

### Post by andyho on 2007-07-28
> **Pragmatist said:**
> Run this command and wait until it finishes.  Since this is the first time your running it, it has to build the whole database which takes a few minutes.
```
sudo updatedb
```
 Not the first time I've run it! LOL! ;) However when I did run it this time it didn't appear to do anything?! Doesn't it usually say something like building dependancies??
> 
Next do a simple keyword search:
```
locate plugins
```You'll get any files or directories on your system that contain the keyword "plugins".  To filter the results to plugins related to firefox, you use the **grep** command:
```
locate plugins | grep firefox
```On my system, the plugins are located at: **/usr/lib/firefox/plugins**

Here's what I got:
andyho@andyho-ubuntu:~$ locate plugins | grep firefox
/usr/share/firefox/chrome/toolkit/content/mozapps/plugins
/usr/share/firefox/chrome/toolkit/content/mozapps/plugins/pluginInstallerWizard.css
/usr/share/firefox/chrome/toolkit/content/mozapps/plugins/pluginInstallerWizard.xul
/usr/share/firefox/chrome/toolkit/content/mozapps/plugins/pluginInstallerService.js
/usr/share/firefox/chrome/toolkit/content/mozapps/plugins/pluginInstallerWizard.js
/usr/share/firefox/chrome/toolkit/content/mozapps/plugins/pluginInstallerDatasource.js
/usr/share/firefox/chrome/toolkit/content/global/plugins.html
/usr/share/firefox/chrome/classic/skin/classic/mozapps/plugins
/usr/share/firefox/chrome/classic/skin/classic/mozapps/plugins/pluginInstallerWizard.css
/usr/share/firefox/chrome/classic/skin/classic/global/plugins.css
/usr/share/firefox/chrome/en-US/locale/en-US/mozapps/plugins
/usr/share/firefox/chrome/en-US/locale/en-US/mozapps/plugins/plugins.dtd
/usr/share/firefox/chrome/en-US/locale/en-US/mozapps/plugins/plugins.properties
/usr/share/firefox/chrome/en-US/locale/en-US/global/plugins.properties
/usr/share/firefox/searchplugins
/usr/share/firefox/searchplugins/creativecommons.xml
/usr/share/firefox/searchplugins/amazondotcom.xml
/usr/share/firefox/searchplugins/wikipedia.gif
/usr/share/firefox/searchplugins/yahoo.xml
/usr/share/firefox/searchplugins/google.xml
/usr/share/firefox/searchplugins/wikipedia.src
/usr/share/firefox/searchplugins/answers.xml
/usr/share/firefox/searchplugins/debsearch.src
/usr/share/firefox/searchplugins/eBay.xml
/usr/share/firefox/searchplugins/debsearch.gif
/usr/lib/firefox/plugins
/usr/lib/firefox/plugins/libtotem-mully-plugin.xpt
/usr/lib/firefox/plugins/libtotem-narrowspace-plugin.so
/usr/lib/firefox/plugins/libtotem-basic-plugin.xpt
/usr/lib/firefox/plugins/libtotem-narrowspace-plugin.xpt
/usr/lib/firefox/plugins/libtotem-basic-plugin.so
/usr/lib/firefox/plugins/libtotem-gmp-plugin.so
/usr/lib/firefox/plugins/libunixprintplugin.so
/usr/lib/firefox/plugins/libtotem-gmp-plugin.xpt
/usr/lib/firefox/plugins/libtotem-mully-plugin.so
/usr/lib/firefox/searchplugins
/opt/firefox/plugins_2007-07-24T18:48:38-0400
/opt/firefox/plugins_2007-07-24T18:48:38-0400/libnullplugin.so
/opt/firefox/plugins
/opt/firefox/searchplugins
/opt/firefox/searchplugins/creativecommons.xml
/opt/firefox/searchplugins/amazondotcom.xml
/opt/firefox/searchplugins/yahoo.xml
/opt/firefox/searchplugins/google.xml
/opt/firefox/searchplugins/answers.xml
/opt/firefox/searchplugins/eBay.xml

So I went through them but I still couldn't any of the plugins I actually installed!? It just seemed to be the default ones. I also have the ubuntuzilla script installed too. Could that be the issue?!? Even doing the search seemed a little off because if I just go into usr/lib I have a firefox, mozilla, and mozilla-firefox folder and they all seem to be pretty much the same. Is that normal??

---

### Post by Pragmatist on 2007-07-28
> 
/usr/lib/firefox/plugins/libtotem-mully-plugin.xpt
/usr/lib/firefox/plugins/libtotem-narrowspace-plugin.so
/usr/lib/firefox/plugins/libtotem-basic-plugin.xpt
/usr/lib/firefox/plugins/libtotem-narrowspace-plugin.xpt
/usr/lib/firefox/plugins/libtotem-basic-plugin.so
/usr/lib/firefox/plugins/libtotem-gmp-plugin.so
/usr/lib/firefox/plugins/libunixprintplugin.so
/usr/lib/firefox/plugins/libtotem-gmp-plugin.xpt
/usr/lib/firefox/plugins/libtotem-mully-plugin.so

Aren't these your plugins?  If not, please list the contents of those other /usr/lib directories.

---

### Post by andyho on 2007-07-28
I don't think they're my plugins.. they seem to be default ones since the same ones are listed in the other folders. I would think the name would help somewhat since I have foxytunes and colorful tabs, unless ALL the plugins are somehow affixed to one file?

---

### Post by nichipet on 2007-07-28
> **andyho said:**
> I don't think they're my plugins.. they seem to be default ones since the same ones are listed in the other folders. I would think the name would help somewhat since I have foxytunes and colorful tabs, unless ALL the plugins are somehow affixed to one file?

I've been watching this thread since I use KDE as well. If I'm not mistaken, colorful tabs, foxytunes, etc. are extensions, add-ons to change or improve the performance of Firefox. Plugins are a little different, they mostly enable multimedia in the browser, such as the Totem-related ones you listed and other programs such as Flash install plugins.

---

### Post by andyho on 2007-07-28
> **nichipet said:**
> I've been watching this thread since I use KDE as well. If I'm not mistaken, colorful tabs, foxytunes, etc. are extensions, add-ons to change or improve the performance of Firefox. Plugins are a little different, they mostly enable multimedia in the browser, such as the Totem-related ones you listed and other programs such as Flash install plugins.

Ohh yeah you are right about that one! They are categorized as extensions!! ](*,) just pulled up the search and hopefully can save them! :)

---

### Post by andyho on 2007-07-28
Well I think I may have just figured it out and it's related to SCIM!! I'm also using the Ubuntuzilla script, and just hopped over there to see if I could find any other info. I just got them both to open, now I just need to fix the shortcuts! :)

---

