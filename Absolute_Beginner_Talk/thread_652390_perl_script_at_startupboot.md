---
title: "perl script at startup/boot?"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by autobot on 2007-12-28
Okay, I am using HoTTProxy, a perl script to create a proxy server for cellphones.  It works great, but I would like it to run at startup, in case of a power outage or something.

First, it took me 3 days to get HoTTProxy working, as I am a newb with linux.  There was something in the instructions about the script having to reside in the home directory, where it resides with a folder and some configuration files.  Thus, I can't put it into the init.d directory.  I made a small script, just for the heck of it, to change the MAC  address at boot following the instructions at [https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto).

I got that script to work, so I tried making a script that simply launches the perl script at boot and nothing happens. 


Now, I also tried adding the script to the startup session, with slightly better results.  I rebooted after adding the perl script and I saw it flash up in a terminal window briefly before closing and disappearing. 

This is my first experience in Linux and my shell scripting is not all that great.  So, the test script I made didn't work at first because it had sudo in it, but I edited the sudoers file and added the user and it worked.  I hear that isn't the most secure way to do things, but I am not sure why it won't work for the other script that launches the perl, HoTTProxy?

---

### Post by blueridgedog on 2007-12-29
You can call the script via an entry in the file /etc/rc.local. 

Call it with an absolute path such as /usr/local/bin/myscript

Be certain to place it prior to the exit 0 line

If the script fails due to being unable to locate it's config files, you can add them to the path or you can try using a cd to the correct location prior to running the script or editing the script to put in absolute paths to the items it is trying to call.

---

