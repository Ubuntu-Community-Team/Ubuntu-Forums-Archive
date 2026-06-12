---
title: "Perl execution"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by AMiSM on 2007-08-15
Hi, folks!
  I've admired Linux for a very long time, but have only really committed to it just the other day.  I'm greener than Kermit full of castor oil.
  I've been using ActiveState Perl under WinXP for about a year or so.  I need to get up and running with Perl under Ubuntu now, but it's just not cooperating.

  It says something about enabling the Universe component, or "command not found", or that the program isn't installed.

---

### Post by Warren Watts on 2007-08-15
Perl is already installed on a fresh Ubuntu install.
Can you be more specific?  What happens when you type
```
perl -v
```
in terminal?

---

### Post by Hospadar on 2007-08-15
I think perl should be installed by default, but it sounds like it's not for you, so let's try installing it and see what happens.

Open up synaptic, (System->Administration->Synaptic) go to Preferences->Repositories and check the universe and multiverse boxes on the "ubuntu software" tab then close the preferences window and click "reload" in synaptic (this might already be done)

Then on a command line ( you can do it in synaptic too if you want, just search for "perl") do a ```
sudo apt-get install perl
```
If it says it is already installed, then let's reinstall it:```
sudo apt-get --reinstall install perl
```

PS. I'm assuming you are getting this message:
```
The program 'perl' is currently not installed.  You can install it by typing: sudo apt-get install perl
Make sure you have the 'universe' component enabled
bash: perl: command not found

```

---

### Post by AMiSM on 2007-08-15
Ok, the crawler script I'm trying to use is messing up.  I did a test script and it worked when I typed "perl Test.pl".  Thanks for answering!

---

### Post by Nervouswreck on 2007-08-15
You can also write perl shell scripts in any terminal text editor. I use pico

```

#!/usr/bin/perl
print "Hello world!!\n";

After exiting

chmod +x *filename*

```

This has an added advantage because you can integrate shell commands

---

