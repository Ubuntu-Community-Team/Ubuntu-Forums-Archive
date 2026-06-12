---
title: "Ubuntu 6.10"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by woody14 on 2007-03-11
I am new to Linux and this forum.  I am having some problems.  When I start from a "live" disk, a screen with Ubuntu logo appears and I choose F4 VGA and set to 800X600 16 and Start or Install Ubuntu.

A screen with Ubuntu logo appears and remains until system boots. But when installed, the logo screen doesn't appear, and I get Cannot Display This Video Mode, Change to 1024X768 60Hz, until system boots, then everything is OK.  I have tried to reconfigure xorg.conf file and even set it to 800X600 and still same problem.  

What file puts the first screen up, is it loaded during installation, and how do I find it?  The xorg.config file seems to control resolution only after boot.  What controls resolution during boot?

When I have Search for Files search for a file in File System, why does it sometimes not find it, even when I can plainly see it?

I have Ubuntu Christian Edition installed.  It seems to be a modified Ubuntu 6.10 which I also have.  Christian Edition doesn't have FreeCell; Ubuntu 6.10 doesn't have GNOME partition Manager.  Is it possible to find and install Freecell from Ubuntu 6.10 or Partition Manager from Christian Edition?  If it is, how do I do it?

I have been trying to get online with Ubuntu.  I have AOL; Peng which I downloaded is supposed to be able to do this.  And just to make things worse the modem is a Winmodem.  Is there a different, or simpler way?  I also downloaded something called Linmodems but I couldn't get some of the needed links to work when I was trying. 

I have The Official Ubuntu Book.  It sometimes seems to be lacking something.  Is there something better, or to I need more than one book?

I also have Ubuntu 6.06 on DVD.  Windows says the DVD is full. Can packages be taken from the 6.06 DVD and used with 6.10 which came to me on CD?  How?

Is posting multiple topics in one post OK, or should I post only one topic per post? Thanks.

Woody

PS I hope this doesn't post twice.

---

### Post by PriceChild on 2007-03-11
*move and bump*

---

### Post by chaplanger on 2007-03-11
> **woody14 said:**
> 

I have The Official Ubuntu Book.  It sometimes seems to be lacking something.  Is there something better, or to I need more than one book?



If you are looking for another book to help with tweaking Ubunutu, I have found *Ubuntu Hacks *to be extremely helpful.

---

### Post by kvonb on 2007-03-12
Whoa, one thing at a time :).

The 800x600 thing:
  This is just a problem when booting into the liveCD right, not on your already installed copy?  I would suggest booting in "safe graphics mode" (I think it's called), that might work.  Once it has booted, logout of X, then you can drop to the "Virtual terminal" by pressing <CTRL><ALT><F1> or <F2> ,F3>,<F4>, they should already be logged in I believe, otherwise login with username "ubuntu", no password.  You can then edit xorg.conf from there with vi or nano: ```
sudo vi /etc/X11/xorg.conf
```, set it to your desired resolution, save and exit the editor.  Now issue the command: ```
sudo /etc/init.d/gdm restart
```.  That will, or rather **should** log you back into X with the new resolution.  Of course being the LiveCD, you would have to do that every time you rebooted.

Internet:
  Winmodems!  Oh joy.  I would suggest going to garage/yard sales, 2nd hand shops, charity shops, friendly local computer shops etc' and looking for an external modem.  Even a 33.6k modem will be fine, (assuming you have serial ports), just to get yourself online.  That way you can skip the major headaches of trying to get a Winmodem working, (for which I would give you a 3% change of success!), and work on the actual AOL connection part.  Once you are actually online you can run either Synaptic (Menu->System->Administration->Synaptic Package Manager), or Add/Remove from the bottom of the Applications main menu to search for and install "freecell" and/or anything else you want.  Then you can also search for guides on getting your WInmodem working.

Packages:
  Some packages can be installed directly from your various CDs/DVDs, but only the simple "standalone" ones, ie they have no other dependencies.  I have had some success by copying **all** the dependant .debs into my /var/cache/apt/archives folder then opening the main .deb and installing it.  **WARNING:**  If you do this on Edgy using Dapper files you could completely mess your system up, the least being that you will need to un-install them all and run an online update, which will take forever and a day using a modem!

Multiple Topics:
  I think that you will have better success when asking single questions, very few people "know everything", and even fewer would take the time to write a long essay as I have just done!  Also it makes it better for anyone else having the individual problems that you are having when they search the forum.

Hope you have luck with that lot, regards, Kev :)

---

### Post by woody14 on 2007-03-12
Just an attempt to reply,  previous try didn't work.  Thanks

woody

---

### Post by woody14 on 2007-03-12
Attempting to repost.

Thanks alot for all the help. 

The graphics problem is when I boot from the installed copy.  With the live CD, I can select 800x600 and have an ubuntu logo screen while it boots.  If I select 1024X768, I get the “Cannot Display…” message box.  I didn’t mention it in my first post, but I also get the “Cannot display…” on shut-down.

I used dpkg-reconfigure xserver –xorg to reconfigure xorg.conf file (I think) to 800X600 72 Hz and my installed copy still had problems.  Does boot-up use this same file?  
Thanks.

---

### Post by kvonb on 2007-03-12
I know it's a pain, but can you write the whole message that appears?

It probably goes past too quickly, so you might have to do it a few times to get the whole line.

I'm wondering if it's a "usplash" problem, you can re-install that through synaptic, from your main menu select System->Admin->Synaptic Package Manager, search for "usplash", then right click on it and select "re-install".

Or if that doesn't seem to do anything, uninstall it, then install it again.

---

### Post by woody14 on 2007-03-13
[CENTER]ATTENTION
CANNOT DISPLAY THIS VIDEO
 MODE,CHANGE COMPUTER DISPLAY
 INPUT TO 1024x768@60HZ[/CENTER]

Those are the exact words, caps and all.  Even the same layout if it will stay when I send it.  I can’t seem to do the usplash instructions as I don’t have internet with ubuntu, yet.  I am not sure if I would get every thing if I tried from Windows.  Thanks.

woody

---

### Post by BKonkle on 2007-04-15
I'm actually having this same problem running Ubuntu 6.10 on a computer with a Radeon 9200 and a flatscreen native 1280x1024 monitor.  I've tried doing a dpkg-reconfigure usplash, and it doesn't seem to have helped.  When booting from the Live CD, the usplash is fine, but when booting from the harddrive install, my flatscreen monitor gives me an "Out of range" message and doesn't display anything until the login screen comes up.

Thanks for any help you can provide!

---

