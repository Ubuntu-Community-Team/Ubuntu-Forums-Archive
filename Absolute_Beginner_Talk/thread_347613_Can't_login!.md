---
title: "Can't login!"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by John14335 on 2007-01-27
Long story short I selected and tried to 'open with gdebi' about 53 different debian packages downloaded from the ubuntu repository at once. I realised the mistake I made and instead of sitting and closing all those windows that were going to appear I clicked the button on the side and tried to logout. That didn't happen and it seemed that the packages were still loading. So I hit the restart button on my cpu.
Once I restarted Ubuntu booted up fine but now when I try to login to my account it just tries to login and throws be back at the login screen! I'm using Edgy eft, Please help.

---

### Post by sardion on 2007-01-27
When you get to the login screen, press ctrl-atl-F3

This will drop you to text-only mode (sorry).

Type your username and password at the prompts in text mode.

Then you will have a command line.

Type:

sudo dpkg -configure -a

And then:

sudo aptitude upgrade


If these give no errors, you are good to go, if there are errors post them here.

After you do that, type

sudo shutdown -r now

that will reboot.

---

### Post by John14335 on 2007-01-27
Although that sudo dpkg -configure -a did give an error of 
dpkg: unknown option -o
I continued with the upgrade line and it logs in fine, thanks a lot sardion!

Another question though, is it safe to toss a bunch of debian packages from some other folder to /var/cache/apt/archives ?

---

### Post by cpate4 on 2007-02-13
try --configure instead of -configure.
 
that will get you past the -o problem you are seeing.

---

