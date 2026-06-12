---
title: "Desperate: ATI driver issue"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by scholzilla on 2007-12-18
In a woefully common flash of stupidity, I took a cavalier approach to enabling the ATI accelerated graphics driver without doing any preliminary research. Now, when I start-up, the linux kernel loads and then I get a dark grey screen of death that never goes away. So, how do I disable this f***ing driver without having access to term or anything other than my bios and settings menus? Everything was going so well until I did this...please don't tell me I have to reinstall.

---

### Post by Presto123 on 2007-12-18
I think there is a quicker way, but of course, you will probably have to do it from terminal. Someone should come soon to post the command, so you don't have to try to figure that one out.

Also, I would do a search for it in these forums, someone has probably already found a solution. Beats waiting for someone to post. :)

---

### Post by scholzilla on 2007-12-18
Thanks. I did do my due diligence on searching the posts, but haven't found this problem. Anyone else?

---

### Post by Presto123 on 2007-12-18
Question: Did you install the drivers? I never have run the ATI cards as I am an avid Nvidia user. Looks like it paid off on here as there are many problems with the ATI cards.

---

### Post by Presto123 on 2007-12-18
Look through this thread: [http://ubuntuforums.org/showthread.php?t=641939&highlight=disable+ati&page=2](http://ubuntuforums.org/showthread.php?t=641939&highlight=disable+ati&page=2)

---

### Post by jfinkels on 2007-12-18
When in dire need, reconfigure X using the following command at one of the virtual terminals (Ctrl+Alt+F1):```
sudo dpkg-reconfigure -phigh xserver-xorg
``` This command tells dpkg to try and figure out what configuration is best and only ask you for high priority questions ("-phigh").

If that works, can you post the output of the following command?```
cat /etc/X11/xorg.conf
```

---

### Post by Presto123 on 2007-12-18
Good thing you posted that bit about what it does, I was looking at that and never have had to run it to my knowledge. I was a bit afraid to post that and have him worse off.

---

### Post by lswest on 2007-12-18
what you can also do is go into a recovery console (basically just a terminal, if you can't get to one through a normal boot) and do ```
 sudo vim /etc/X11/xorg.conf
``` and find the line that says which driver you are using and change it.  Not sure what the normal driver is for ATI, but you can use vesa to get a gfx interface, and play with the rest later on.  to use vim: I to insert, esc to exit insert mode, when out of insert mode just type ":w" to write changes, and ":q" to quit or  ":q!" to quit without saving.

---

### Post by sdowney717 on 2007-12-18
sudo dpkg-reconfigure xserver-xorg
this will reconfigure using the open source ATI driver.


you can also install ENVY from your terminal window when booted into safe mode

sudo  apptitude install envy

then run envy using text install from the terminal

But if it is a 9200 then ATI driver is not supported.

---

### Post by neotasic1 on 2007-12-18
> **sdowney717 said:**
> sudo dpkg-reconfigure xserver-xorg
this will reconfigure using the open source ATI driver.


you can also install ENVY from your terminal window when booted into safe mode

sudo  apptitude install envy

then run envy using text install from the terminal

But if it is a 9200 then ATI driver is not supported.

Can't speak for the ATI 9200 but I have the 9200SE and it has worked out of the box with both Feisty and Gutsy (I ran Beryl in Feisty with no problems and am currently running Compiz Fusion in Gutsy with zero issues). No extra drivers required.  (64 bit Gutsy and Feisty install if that makes any difference).

Unless you mean Envy doesn't support it?

---

### Post by sdowney717 on 2007-12-18
9200 will work with open source ubuntu drivers.
ATI does not support 9200 with the current driver.

I did notice ENVY has an older version for legacy cards. So I would guess the version of ENVY for older cards  is using older supported binary drivers.

I have tried the open source and I wish it was better as it is so slow with 3d games.

---

### Post by stchman on 2007-12-18
> **sdowney717 said:**
> sudo dpkg-reconfigure xserver-xorg
this will reconfigure using the open source ATI driver.


you can also install ENVY from your terminal window when booted into safe mode

sudo  apptitude install envy

then run envy using text install from the terminal

But if it is a 9200 then ATI driver is not supported.

Envy is not in the repos so that command will not work.  It looks as though your video driver is borked up so you will need to start Ubuntu in recovery mode.

To install the latest envy do the following, you need internet access.

```

cd ~
wget http://www.stchman.com/tools/envy_0.9.9-0ubuntu2_all.deb
sudo dpkg -i ~/envy_0.9.9-0ubuntu2_all.deb

```


Then run envy -t.  Select the Uninstall ATI driver option.

---

### Post by stchman on 2007-12-18
> **sdowney717 said:**
> sudo dpkg-reconfigure xserver-xorg
this will reconfigure using the open source ATI driver.


you can also install ENVY from your terminal window when booted into safe mode

sudo  apptitude install envy

then run envy using text install from the terminal

But if it is a 9200 then ATI driver is not supported.

Envy is not in the repos so that command will not work.  It looks as though your video driver is borked up so you will need to start Ubuntu in recovery mode.

To install the latest envy do the following, you need internet access.

```

cd ~
wget http://www.stchman.com/tools/envy_0.9.9-0ubuntu2_all.deb
sudo dpkg -i ~/envy_0.9.9-0ubuntu2_all.deb

```


Then run envy -t.  Select the Uninstall ATI driver option.

According to ati.amd.com the Radeon 9200 is supported in Linux using the 8.28.8 driver.

---

### Post by scholzilla on 2007-12-18
Thanks to all who took the time to reply. I learned a lot from what you wrote and learned how little I know. 

The following seemed to work for me, as unsophisticated as it is:

1. booted up with the install CD
2. logged in
3. restarted and removed the install CD
4. for reasons I don't comprehend, this permitted me to log in normally (ie, my graphics came back). I should note that rebooted without first booting up with the install CD doesn't work at all. Again, I don't get it.
5. went to System --> Administration --> Restricted Drivers Manager and disabled the ATI accelerated graphics driver. I shan't be using this again.
6. rebooted and all has worked fine over several reboots now.

Can't explain it, but it worked not once, but twice.

---

