---
title: "Resolution"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by sim085 on 2006-07-14
Hi, I have just installed Ubuntu, and something that I have noticed is that it only allows me to arrive up to a resolution of 800x600.  However in my Windows XP I am allowed to a resolution of up to 1024x768.

Now before making this post I have searched a little in this forum, and found out that I need to modify the file \etc\X11\xorg.conf.

I have tried to open this using the normal text editor and update it.  However I was not allowed to save the changes, since it seems I do not have enough permissions! Is there a way how I can increase my permissions even when using the gui?

Since I did not have enough permisions I decided to do it all using the Terminal.  Therefore I have entered the syntax 'sudo nano \etc\X11\xorg.conf'.  I then modified the screen element with my wanted resolution of 1024x768.  However this did not work :(

I am sure I am doing something wrong!

Is there someone willing to explain to me what I need to change, how, and why I need to change it?  I added the 'why' because I would like to be learning while doing this change.

regards,
sim085

---

### Post by T700 on 2006-07-14
Try this:

```
gksudo gedit
```

When the editor opens, navigate to the file, *make a backup copy, *and then make your changes to the original.  Save the file.  Close all your applications.  Restart your computer.

Paul

---

### Post by bigken on 2006-07-14
try running sudo dpkg-reconfigure xsever-xorg in the terminal and use the space bar to select your resolutions ;)

it will ask for your password 1st

---

### Post by Katryx on 2006-07-14
If you use gnome, try:
```
sudo gedit /etc/X11/xorg.conf
```
Once you've done the edit, log out and press CTRL+ALT+BACKSPACE to restart xserver.

---

### Post by sim085 on 2006-07-14
Ups ...

Okej I think I have done something teribly wrong now!
I tried following the instructions set on this website:

[http://doc.gwos.org/index.php/ChangeResolution#Adding_custom_modeline](http://doc.gwos.org/index.php/ChangeResolution#Adding_custom_modeline)

basically the first step says to put the line it gives in the monitor section, and that is what I did:

```

Section "Monitor" 
   .. lines that where already there.
   Modeline 1024x768_75.00" 81.80 1024 1080 1192 1360 
   768 769 772 802 -HSync +Vsync
EndSection

```

And then I added the extra subsection display for the 1024x768 resolution. 

However when I restarted it told me that my xorg.conf has something wrong.  I have a blue screen and grey screen and ok options.

Should I format and start again.  PS: I did keep a backup of my previous xorg.conf.

regards,
sim085

---

### Post by sim085 on 2006-07-14
Just some extra details ...

The exception it gave me is in the Monitor section, Modeline identifier expected!

regards,
sim085

---

### Post by bigken on 2006-07-14
no dont reformat boot into safe mode from the grub menu and run the dpkg-reconfigure xserver-xorg this will fix  it ;)

---

### Post by sim085 on 2006-07-14
ok, no reformat :D

I am in the terminal like menu (the one that comes if you do not have a gui) could some one please tell me the command to delete the current xorg.conf file.

if I delete the current file I would then run the following command:

sudo cp /etc/X11/xorg.conf_bck /etc/X11/xorg.conf

and thus I would have my original settings back right?

regards,
sim085

---

### Post by avtolle on 2006-07-14
in terminal, type sudo rm <name of file>. The copy command you posted will restore, as I understand it.

---

### Post by sim085 on 2006-07-14
Yes, however for some reason, when I am typeing the following command I get the error message that no such file or folder exsists

sudo cp \etc\X11\xorg.confbck \etc\X11\xorg.conf

However I am sure I had created it before!

regards,
sim085

ps: How I can go in the X11 folder and list all the elements in it?  I know that to list all elements you need to use the 'ls' command.  However I can not understand how I can go to the etc folder! it only let me arrives till the home folder :(

---

### Post by avtolle on 2006-07-14
From your last post, looks like you're using backslash, not slash, retype and let us know.

Re: PS, cd /etc/X11 (I think; I'm relatively new also).:confused:

---

### Post by sim085 on 2006-07-14
yes you where right .. everything working now .. and yes I entered in the etc\X11 folder as well :D

what is the restart command (that is the command to restart the computer) I am only asking so I do not stay pressing the restart button all the time :)

regards,
sim085

---

### Post by bruce89 on 2006-07-14
> **sim085 said:**
> yes you where right .. everything working now .. and yes I entered in the etc\X11 folder as well :D

what is the restart command (that is the command to restart the computer) I am only asking so I do not stay pressing the restart button all the time :)

regards,
sim085

If you mean to restart X, it's Control+Alternate+Backspace
If you mean to restart from the command line, it's *reboot*.

---

### Post by sim085 on 2006-07-14
Thanks :) I now have my GUI back :D

Now back to try setting up the 1024x768 resolution! hopefully I will be more lucky this time! :)

regards,
sim085

---

### Post by sim085 on 2006-07-14
Okej it worked finally, however all I did copy is the following section:

```

Section "Screen" 
      ...
      DefaultDepth 16 
      SubSection "Display": 
           Depth 16 
           Modes "1280x1024" "1024x768" 
      EndSubSection 
 EndSection

```
So my question is; Where does the following part go? and why is it needed?

```

# 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz 
Modeline 1024x768_75.00" 81.80 1024 1080 1192 1360 768 769 772 802 -HSync +Vsync

```

Regards,
sim085

---

### Post by sim085 on 2006-07-14
Okej I am finally done :D

Well it took a little longer then in Windows :) however I am happy with the end result :D

Thanks to all for all the given help :)

regards,
sim085

---

### Post by cjm5229 on 2006-07-14
Echo, > dpkg-reconfigure xserver-xorg Try this while you still have an xserver to fix.:) 
 
OK, Never mind, I was interupted in the middle of my reply, didn't see you got it solved.

---

### Post by sim085 on 2006-07-15
Thanks anyway :)

Regards,
sim085

---

