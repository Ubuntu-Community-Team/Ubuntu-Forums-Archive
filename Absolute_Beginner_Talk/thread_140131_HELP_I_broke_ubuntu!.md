---
title: "HELP I broke ubuntu!"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by shishio on 2006-03-05
Hi,

I was trying to install glib2.8.3 but it kept complaining about my previous glib installation (2.4.x) so I had the greatest idea: I went into the /lib directory and deleted the libglib.so.0 files. 

Then I found I couldn't use gedit anymore... and new terminal windows wouldn't launch.... so I decided to restart the computer because when in doubt the best thing to do is turn things on and off.... 

So now ubuntu throws me into a terminal window (looks like dos) without going into the nice graphic user interface. 

I believe what I need to do is somehow create those libglib.so.0 files again and throw throw them into /lib directory, and edit my ld.conf.so that it points to wherever they are. I'm not sure how to do this. I think I have to use the libtool utility included with glib but I don't know the proper syntax. Am I on the right track?

Also does anyone know where the startup scripts are stored? The ones that are run before I get a command prompt?

Thanks...

---

### Post by aggiechemist on 2006-03-05
Libraries are really not my thing, so I can't help much there.

But start up scripts will be in the /etc/init.d directory. You may want to try tools like rcconf to choose what startup scripts get run.

supo apt-get install rcconf

Also, can you get the terminal to become a GUI? You could try commands like xserver or gdm. I don't do this much, but maybe you can still get back to your system.

Hope that helps!

---

### Post by christhemonkey on 2006-03-05
Ok, i think you need to reinstall your glib stuff, try something along the lines of:
```
sudo apt-cache install glib2.4.x
```
Something like that!
and your startup things are all in ```
/etc/init.d/
```
Allthough that isnt really startup stuff thats the last runlevel thing.

---

### Post by shishio on 2006-03-05
Thanks for the replies.... I tried the 'apt-cache' method doesn't recognize the 'install' command. I tried

sudo apt-get install glib2.4.12

but it can't find the package name. I guess I have to determine the exact package name. Does anyone know what it is?

---

### Post by christhemonkey on 2006-03-05
[http://packages.ubuntu.com/breezy/libs/libglib2.0-0](http://packages.ubuntu.com/breezy/libs/libglib2.0-0)
I think that is what youa re looking for!
You can just save it from there and then do a
```
sudo dpkg -i /where/that/file/is/bla.deb 
```

---

### Post by shishio on 2006-03-05
So I reinstalled libc6 and libglib2.0-data but it didn't reinstall the files that I initially deleted from the lib directory that caused this mess in the first place. So ubuntu still throws me into the dos terminal command prompt? Any other ideas?

How do you edit the boot order to boot from a cd before the hard drive?

---

### Post by jamesstansell on 2006-03-05
> How do you edit the boot order to boot from a cd before the hard drive?You normally would change your BIOS settings for that.  When the computer first starts, before it runs the boot sequence, it usually prints a message about the function key to use to view and change the BIOS setting.

---

### Post by shishio on 2006-03-05
I have an ubuntu 5.04 install cd. I was thinking I could mount it from the terminal and just reinstall everything. I'm not sure what I should run from the cd-rom, I don't see any of those green colored file names which you can run...

---

### Post by christhemonkey on 2006-03-05
You need to boot from it (i think!) just browsing the cd wont help.
Before you do boot from the CD and do a complete reinstall.
what happens when you do a
```
sudo /etc/init.d/gdm start 
```?

---

### Post by shishio on 2006-03-05
Hey guys thanks for all your help. I did two things to fix my problem, I'm not sure which one actually fixed it (I didn't try them independently).

I found some (old?) libglib.so files in my /usr/local/lib directory and copied them over to my /lib directory.

It dawned on me then, that when I do 

sudo ./configure 
sudo make install

for the glib-2.10.0 package, I must be installing the library files in my /usr/local/lib directory instead of my /lib directory.  So I logged in as root (sudo su) and re-ran the ./configure and make install as well hoping it installs junk in the /lib directory instead of the /usr/local/lib directory.

Is anythingthat I've said even remotely correct? 

Then I rebooted, and now I'm back in ubuntu writing this post! Yeah!1 I'm a linux haxor

---

### Post by jamesstansell on 2006-03-05
/etc/init.d/gdm should have some enlightening messages about which shared libraries aren't being found.  Essentially the ones that shishio knows he removed, but having the exact name would be helpful.

I believe there is an apt tool for which packages are no longer installed properly, but I don't remember the name right now.

---

### Post by jamesstansell on 2006-03-05
shishio, you're very brave to be messing with your libc like that.  You can learn a lot that way!

I hope you have a backup copy of anything you care about.

-james.

---

