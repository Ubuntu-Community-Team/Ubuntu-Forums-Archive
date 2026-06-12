---
title: "hoary hedgehog help!!!"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by redbuller on 2006-05-18
Firstly, hi to everyone in the community, secondly help!!! Having sent away for a copy of ubuntu ages ago i finally got round to trying it but after 8 or more hours and several installs i`ve decided i need help lol....As far as i know everything installs fine then ubuntu starts but all i get is a totally black screen. I then looked around the forum for people with similar problems and found a few who had a black screen with the white curser in the top corner which i dont have. I`ve tried all the advice given in the other posts but still can`t get past this problem. I can start a console session if i press ctrl /alt/f1-f6 and pressing ctrl/alt/backspace opens a login screen for 2 seconds then it goes black again. As i`ve said i tried various things from other posts including code: startx.....sudo this and that.... dpkg this and that,but to be honest i have no clue what these things are for...What i did notice when ubuntu was starting was one thing failed....ror:temporary failure at name resolution...when i tried startx i noticed it said something about it being already started at 0 or something along those lines. oh and i`ve also tried the live cd and its exactly the same results with that. Tested the live disc on my desktop and it works fine. Im trying to get it working on a dell inspiron 1300 1.50 celeron m 760mb ram. Any help would be very much appreciated.

---

### Post by NoUse on 2006-05-18
Hoary hedgehog is an older version of Ubuntu.  Do you have a fast internet connection? If so, you might try upgrading to Breezy via this link:
[https://wiki.ubuntu.com/BreezyUpgrade](https://wiki.ubuntu.com/BreezyUpgrade)

What kind of video card do you have?

---

### Post by WakkiTabakki on 2006-05-18
Edit: NoUse, you beat me to it!

Hmmm... First of all, you should really get a newer version of Ubuntu. There's been loads of improvements in the later versions. The latest (Dapper) is just weeks away from release, and (after using different test versions since early February) it's really wicked! I of course can't promise anything, but I'm fairly sure it'll work a LOT better...

But, well, lets try to figure out whats stopping Hoary from runnng X... 
If you press ctrl-alt-F1, do you get a login screen at all? (it'll be in text mode)
If yes, login in and type:
```
cd /var/log
```

Notice that in this folder there are a lot of log-files, one is called Xorg.0.log. 
This log-file contains details of the start-up of X (the graphical user interface). 
Post that file here, and we'll try to figure out whats wrong...

In case you're not too familiar with the command interface, here's a few handy commands
```

ls    - List contents of current folder
ls | more     - Lists contents of current folder, one page at a time
cat <file> | more   - Prints the contents of a (text) file to the screen one page at a time

```

The Xorg.0.log contains LOADS of information, but look especially for lines beginning with (EE), those are errors...

Also, the file /etc/X11/xorg.conf should be interesting to look at. It contains the current UI configuration (such as video card, monitor, resolution, refreshrate, drivers for mouse and keyboard etc...)


Edit again: If you're dual-booting this comp with windows you can download a driver that lets you access the Ubuntu partition from windows, so you don't have to muck about with the command line stuff. 
Check it out on [http://www.fs-driver.org/]("http://www.fs-driver.org/")

Good luck
/N

---

### Post by redbuller on 2006-05-18
ok thanks to you both for the replies. First thing is yes i know it`s an older version but to be honest i dont want to download the the newest release and still have the same or similar problems im having now and still be none the wiser. Its a laptop so the graphics are integrated but i know where your going i noticed some of these problems are graphics card related but trying a new card isnt an option. I`ve downloaded the ext2 file system but i will have to install ubuntu again before i can try anything. Tomorrow i will have another go at this and hopefully with some success. i will keep you guys posted.   thanks

---

### Post by IYY on 2006-05-19
Many problems have been fixed in Breezy, and many more were fixed in Dapper, especially when it comes to laptops. I'd suggest to get the Dapper beta. It is stable, and you'd have a much better chance of a smooth installation.

---

### Post by dmizer on 2006-05-19
breezy has been around for a while.  it's a very mature version.

a quick search indicates that your main problems will probably be quite typical, but not video related.  some sound issues and wireless internet might be difficult.

but people have been working with breezy for a while.  and many people with your computer have been working with breezy for a while.  so even if you do have problems, you are likely to get answers.

if you're dead set on using hoary, we'll see what we can do.  lol ... just try not to be offended if people often suggest upgrading ;)

as of now though, probably your quickest and easiest way to fix your problems is to upgrade.

edit:
just happened to think that your problem might be fixed by adding noapic to your kernel.

start a console session. and type:
```
sudo nano /boot/grub/menu.lst
```
scroll through with your arrow keys and look for the line that goes something like this (your numbers will be different than mine):
> /boot/vmlinuz-2.6.12-10-386 root=/dev/hda1
be careful ... this should not be under the section for (recovery mode).
also, there may be more than one line that looks like this ... choose the one that does not have a # in front of it.

once you've found the correct line, just add
> noapic
to the end of it.

save by hitting ctrl + x then confirm you want to save by typing the letter y, and on the next choice, just hit enter.  that should put you back to your prompt.

then reboot by typing sudo shutdown -r now.

see if that fixes it.  if you have trouble finding the correct line in your menu.lst file, post the contents of the file to the thread here, and we can point out the correct line.

---

### Post by Sef on 2006-05-19
Another reason to switch is that Hoary has only about 5 months of support left on it (November 2006.)   Breezy has 11 months left (April 2007.)  Dapper will have about 3 years of support left (April 2009) once it has gone stable (1 June 2006.)

---

### Post by redbuller on 2006-05-19
Ok you guys, after some thought i`ve decided dapper is the way to go. I`ve downloaded it and will attempt to install when i finish this post. Don`t worry though i will have a few new problems for everyone later tonight lol...I`d like to thank everyone for their input though, it`s good to find a forum with enthusiastic member`s.  THANK YOU ALL.

---

### Post by Sef on 2006-05-20
You're welcome.  Please post any questions that you have about Dapper.

---

