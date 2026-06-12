---
title: "ubuntu 8.04 issues in my macbook"
date: 2008-04-29
forum: Apple Hardware Users
---

### Post by hananias on 2008-04-29
I'm new in ubuntu but not scared to try things out, and get in the terminal...so I managed to triple boot my macbook.  90gigs for Leopard, 40g for Windows Vista, 15g for Ubuntu.  Vista runs great out of the box!  Is true what they say, a Mac is the best windows computer.  I wish I could say the same for Ubuntu...here are some issues I'm having.
[LIST=1]
[*]isight not recognized in skype or ekiga (what ever that other program is)
[*]runs super HOT!!!  almost burns my hand on the bottom.  so i don't like to stay in ubuntu too long...scared.
[*]video streaming in the internet is terrible.  in os x and windows, i can watch anything, anywhere...in Ubuntu I can only watch videos from Youtube. (not msn, cnet.com, or nba.com) i'm also have issues trying to install video plug ins (too complicated for me, like I said..."I'm new in Ubuntu")
[/LIST]
I guess that's all I can remember for now.  My main concern is with the HOT temps, and the video streaming!!  what the deal is??:confused:  Can some one help??

---

### Post by benanzo on 2008-04-29
To fix your iSight follow [this]("http://ubuntuforums.org/showthread.php?t=764616") guide.

Video from those sites you mentioned are streaming in proprietary video formats which Ubuntu can't support out of the box for legal reasons.  However, it's perfecting easy to install support for them by going to **Applications -> Add/Remove**.  Then under the **Show** menu change to **All available applications**.  With the **All** category selected in the menu on the left search for **restricted**.  This will return two results, go ahead and install **Ubuntu restricted extras**.  You should be able to watch your videos now.

Or, you can do the exact same thing as above by opening a terminal (Applications -> Accessories -> Terminal) and typing:
```

sudo apt-get install ubuntu-restricted-extras

```
Then enter your password.

Good Luck!

---

### Post by hananias on 2008-04-29
Thanks for the quick reply and advice...I`ll try that as soon as I get back from work.  I`ll report back with the result!  Thanks, at least for now I have hope there is a fix.

---

### Post by hananias on 2008-04-30
Well, I've followed everything by the text, still nothing works right.  Neither the isight nor video streaming didn't work.  With out those two...life in Ubuntu is very hard.  I need my skype working right, and I like to keep up with tech and NBA watching the videos.  I don't know what I'm doing wrong.  I guess I need more experience with Ubuntu.  I just basically copy and paste, I don't know much of what is going on.

---

### Post by sands on 2008-04-30
Try this..
It worked for me.. 
I copied AppleUSBVideoSupport file from mac installation into / directory.. and gave /AppleUSBVideoSupport in the driver path dialog box.
[http://ubuntuforums.org/showthread.php?t=766866](http://ubuntuforums.org/showthread.php?t=766866)


For the heat issue.. Follow this..
*open terminal
*type *su*
*enter root pass
*enter *modprobe applesmc*
*enter [I]echo 3000 > /sys/devices/platform/applesmc.768/fan1_min

[/I]enter the fan speed of your wish instead of 3000

if you cd into [I]/sys/devices/platform/applesmc.768/
[/I]There you can see lot of other files.. you can view the values by using *more filename* and change the values by using echo value > filename

Hope that helps.. Most of this info is in the previous posts and also in the ubuntu documentation..
Check this [http://help.ubuntu.com/community/MacBook](http://help.ubuntu.com/community/MacBook)

---

### Post by hananias on 2008-05-01
Well, I tried everything posted here and still no luck.  I can't find or access that directory were the driver for isight is at.  I guess it doesn't exist in my files, or for some reason I can't access them.
The videostreaming now I can see the pages load up, but never play...even if I choose to open by player externally they won't play.
The fan speed, I can't find applesmc.768.  I've tried going through the terminal, and even directly through files I can access it.  I guess I am ignorant and missing something.  I'll keep trying this steps, but if some one had similar problems please let me know what you did exactly.  Thanks all who posted here!

---

### Post by sands on 2008-05-01
[I]unless you load applesmc you cant find those files..

[/I]*sudo modprobe applesmc*

---

### Post by hananias on 2008-05-01
sign of progress.  Thanks to all your help.  i was able to fix the fan issue, is running a little cooler.  

the isight, i found the isight firmware.  But I can't copy it to my /lib/firmware folder

I had installed the isight firmware tools from the synaptic, but i don't know what's next... anybody??

---

### Post by cyberdork33 on 2008-05-01
> **hananias said:**
> I had installed the isight firmware tools from the synaptic, but i don't know what's next... anybody??
You have to get a copy of that file onto your Ubuntu partition so you can extract the firmware.

---

### Post by hananias on 2008-05-01
> **cyberdork33 said:**
> You have to get a copy of that file onto your Ubuntu partition so you can extract the firmware.

Well, I copied it in my desktop, but still I tried to copy from there into the firmware folder and I get message "don't have permission" 
so i don't know how to get the permission to copy and paste the firmware.  so even though, the file copied to the desktop that. does that mean it isn't in my ubuntu partition? :confused:

---

### Post by benanzo on 2008-05-01
You need to have administrator privileges in order to create/delete/modify files in system folders like /lib/firmware.  You can do this easily by hitting Alt+F2 then typing "gksudo nautilus" then entering your password.  Now browse to your desktop (/home/username/Desktop) and copy the AppleUSBVideoSupport file, then browse to "/lib/firmware" and paste it.

Or you can do it in a terminal (Applications -> Accessories -> Terminal) by typing:
```

sudo mv $HOME/Desktop/AppleUSBVideoSupport /lib/firmware

```

Then enter your password.

---

### Post by cyberdork33 on 2008-05-01
> **hananias said:**
> Well, I copied it in my desktop, but still I tried to copy from there into the firmware folder and I get message "don't have permission" 
so i don't know how to get the permission to copy and paste the firmware.  so even though, the file copied to the desktop that. does that mean it isn't in my ubuntu partition? :confused:
_[http://ubuntuforums.org/showthread.php?t=764616](http://ubuntuforums.org/showthread.php?t=764616)_[]("http://bersace03.free.fr/ift/")

---

### Post by hananias on 2008-05-02
Wow!  Thanks I can't believed it worked!  I'm going have to change this thread from issues in my macbook to issues fixed in my macbook:)
One thing I've noticed now, is that  my mic is not working.
I looked at the steps in the wiki for macbook, but to no success.  Anyone have ideas?  here are some shots of my sound set up...

---

### Post by cyberdork33 on 2008-05-02
enable the capture channels and make sure that they are turned up as well. Inputs are assigned to a capture channel.

---

### Post by hananias on 2008-05-02
> **cyberdork33 said:**
> enable the capture channels and make sure that they are turned up as well. Inputs are assigned to a capture channel.

Many thanks to so many people out there for helping me so much in this thread.  I can't believe how fast and generous all have been here.  I'm happy to say that all major issues are stable for now...well see if  I don't screw something up later. :popcorn:
For now this is what I've got!  Ubuntu rules :guitar:

---

