---
title: "Failed Initializing HAL and Configuration could not be loaded."
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Guruprasad on 2007-07-23
Hi All

I am very new to UBUNTU. I installed Ubuntu Feisty Fawn which worked great for a week.

But one day while checking the Administration-Services I switched off some service. I do not remember which one it was. Later I could not access the services again.It gave message "The configuration could not be loaded. You are not allowed to access teh system configuration." Also after booting a message comes "Failed initializing HAL". My drives with NTFS format are not seen.

If any one knows the way to rectify this. Please let me know.

Regards
Guruprasad

---

### Post by sad_iq on 2007-07-23
Don't really know how to solve your problem but read this thread...it has a list of the most common services and a way to enable/disable them...maybe that can help fix your system: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by jzurawski99 on 2007-07-23
Below is something I posted in another hal issue thread.  It might apply here also.


Re: the infamous Failed to initialize hal error 

--------------------------------------------------------------------------------

I also suffered from this problem. After much searching, it seems that these hal issues might be the result of a recent hal update (just speculating).

Now, with me being a newbie at Ubuntu, take everything I say with a grain of salt. But, these are the steps I followed (gathered from a few other posts) that got me up and running again.

In short, you need to roll back the hal update. Below are the steps I followed to accomplish this.

First, when this error occured I lost all USB, DVD drives and also my network connectivety (wireless and wired).

The line below allowed me to restart dbus and hal (I needed to get my connectivity back for the roll back).

sudo /etc/init.d/dbus restart

Whatever the above line did, it allowed me to manually reconfigure my wired connection (even though it didn't look like it was working, I was able to connect to the internet).

I then followed the instrucitions below to force the hal rollback.

The info below was pasted from a thread titled "Recent HAL update caused frequently failure for "suspend when lid closes"

************************************************** *********************************

Re: Recent HAL update caused frequently failure for "suspend when lid closes" 

--------------------------------------------------------------------------------

I think i found a temp workaround for this: rollback to older versions of those hal packages.

This can be done pretty easily with Synaptic package manager in Ubuntu:

1. Open Synaptic

2. Menu: file -> history, find the history of the day you installed the hal update. For me it is under "5/11":

Code:
Commit Log for Fri May 11 15:08:47 2007

Upgraded the following packages:
hal (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
hal-device-manager (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal-storage1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1

Installed the following packages:
hal-info (20070402-1ubuntu1~feisty1)3. Now, search for each of the first 4 packages in Synaptic, then use "force version" in Package menu to force the latest version for each of them to be 0.5.8.1-4ubuntu12. When doing this for the first package, Synaptic automatically prompts to remove hal-info, which is what we want.

4. Now click on the "Apply" button. These packages will be downgraded to the good version.

5. After that, you'll immediately see the update manager pops up again to tell you there are new hal updates, this is the sign that the downgrading was successful. Of course this time you want to ignore the hal update...

************************************************** *************************************

Again, I have no idea what any of this effects. All I know is that after following the above I regained all hardware functionality. I hope this helps some of you.

JZ

---

