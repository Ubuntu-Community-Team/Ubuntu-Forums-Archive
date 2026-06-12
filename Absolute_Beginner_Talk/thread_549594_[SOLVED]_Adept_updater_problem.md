---
title: "[SOLVED] Adept updater problem"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by snevensmores on 2007-09-12
Hey, I'm using Kubuntu Gutsy and I'm having some Adept Updater issues. It originally had some problems during a package installation the database is now locked. Restarting the computer doesn't help

Off the top of my head, I can remember using following commands in konsole, and the only one that got me anywhere is last one:
*sudo apt-get install -f* (complained about dpkg)
*sudo apt-get update* (same complaint)
*sudo apt-get upgrade* (same complaint)
*sudo killall dpkg* (said that there was no such process running)
*sudo dpkg --configure -a*

That last one begins a little installation of "debconf." It says that it has to restart certain services for PAM library upgrade. These are the services that it lists: kdm, cupsys, cron, and atd. When I click next, kdm shuts down and all I can see is a black screen with all the text from my original boot (I assume). From this point on, the computer does nothing. It just sits there. It's like the debconf installation "remembers" to shut down kdm, but it "forgets" to install.

Anyone have any idea how I can get this thing fixed so that I can apply the 229 package updates that are awaiting me? Thanks in advance!

---

### Post by diatribe on 2007-09-12
what are the actual errors

---

### Post by snevensmores on 2007-09-12
> **diatribe said:**
> what are the actual errors

When I originally open up adept updater, it says:
[I]"Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude).
Would you like to attempt to resolve this problem? 'No' will enter read-only mode and 'Cancel' to quit and resolve the issue yourself."[/I]

If I click "Yes," Adept Updater crashes and I get the KDE Crash Handler. Under "short description," it says:
*The application Adept Updater (adept_updater) crashed and caused signal 6 (SIGABRT).*
Under the "Backtrace" tab, it says:
[I]This backtrace appears to be of no use.
This is probably because your packages are built in a way which prevents creation of proper backtraces, or the stack frame was seriously corrupted in the crash.

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".[/I]

When I run "sudo apt-get install -f" it takes me immediately to a package configuration window for *libpam0g* with the warning about how it has to restart certain services.

When I run "sudo apt-get update" it downloads updates from the internet sources, then stops with this error:
[I]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/I]

When I run "sudo apt-get upgrade" it immediately ends with the same error.

I just ran "sudo killall dpkg" and it apparently killed it. I went back and ran "sudo apt-get upgrade" and it still stops immediately -- *E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.*

And, well, I already mentioned what my computer does when I run that command from konsole.

---

### Post by diatribe on 2007-09-12
it seems like you have two instances of adept running, or you are running apt-get at the same time adept is open.  type 

ps x|grep adept

and kill any processes that show, then try running apt-get again

---

### Post by snevensmores on 2007-09-12
I did that and it only listed adept_notifier and the grep command. I killed adept_notifier. I just ran "sudo apt-get update" and it still says:

[I]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
[/I]

It seems to me that I need to figure out how to run that command so it actually WORKS (as opposed to it shutting down kdm and then just sitting there).

---

### Post by diatribe on 2007-09-12
sudo dpkg --configure -a

---

### Post by snevensmores on 2007-09-12
When I run that, I have the problem that I mentioned in my first post. It will kill kdm, and then it just sits there and does nothing. I'll try it one last time just to see if it'll do anything different....

---

### Post by diatribe on 2007-09-12
you can try using ctrl+alt+f1 to switch to tty1, login and run the command.  this way if X dies you will still be able to see any output

---

### Post by snevensmores on 2007-09-12
This is really weird... 
I ran "sudo dpkg --configure -a" and it went into the configuration program that I mentioned before. It then warned me about the services that it would restart. After I said "OK," it said "*kdm stopping...*"

The screen went blank and apparently "hung" again. I restarted the computer and ran the command again from konsole and it didn't launch anything... just showed me another prompt. I started up Adept Updater and now things are working fine and I'm currently applying updates.

I have no idea how we "fixed" the situation, but at least it's working. Thanks for the help!

---

### Post by diatribe on 2007-09-12
congrats :D

---

