---
title: "Wierd Screen Problem"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by drakebarimore on 2007-06-07
I was ready to get a refund on Linux yesterday, but I calmed down after I FINALLY was able to get ubuntu to play viideo and then sound.  Then I even got it to all play on my wide-screen tv by changing the resolution in System / Preferences / Screen Resolution.  

But guess what?  Today I couldn't even get my PC to boot right.  It kept cutting out.  

I had already had it hooked up to my TV, but the tv went back to doing what it said before I changed the resolution "Not Supported."  I tried hooking the regular PC monitor back up to the pc and a funny thing happened.  With both the TV and monitor hooked up, it would boot and after I signed in the TV would display.  

Does anybody know how I can make the TV display reliably whenever I boot up?

---

### Post by Hendrixski on 2007-06-07
a refund?  Are you using an enterprise version of Linux?  Ubuntu is not only free (as in freedom) but it's also free of charge.

I don't know what your situation was with sound and video but usually all of that can be automatically installed from Ubuntu's repositories. 

As for the signal cutting out, did you edit your xorg.conf file at all?  That usually doesn't end well.  Try restoring it to a backup you made (because you never edit any system files without making a backup) and restarting the xserver (because you never need to reboot in Linux, except for kernel updates, otherwise your computer can just stay on indefinitely).  You can restart X by hitting ctrl+alt+backspace.

Hope that helps... if not... at least it bumps your question back to the top of the list where someone else can give more insight.

---

### Post by drakebarimore on 2007-06-07
thanks but I didn't edit anything called xorg.  I simply went to System / Preferences / Screen resolution and set it to the next one down.  That made the TV pick up the signal and I could see everything ok, but upon reboot, my system became unstable.  

Fist of all, it would not display on the TV when booting.  I ended up hooking the pc monitor back up and that worked, but I don't want to use this monitor.  This pc is used in our livingroom and is meant to be hooked up to our big-screen tv.

So, I need to figure out how to set Ubuntu up so that it will reliably boot and run when only connected to my TV.

If anyone else has any more ideas, please let me know.

: )>  


PS.  I know Ubuntu is free... I was speaking figuratively meaning I was ready to give up.  It just seems like I can't make things run right and if I can get things to run right then not for long.

Pressing On!

---

### Post by w4ett on 2007-06-07
Here is a thread which I think will help you set the default resolution for your Video card/monitor setup.

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by drakebarimore on 2007-06-07
Yeah but thats entering codes, and I've never done that.  Besides, I installed Automatix2 and now Ithat is the only option under System Tools off the Applications menu.  After I installed that, I can't find a command line anymore.

---

### Post by w4ett on 2007-06-07
You can find the terminal under Applications>Accessories>Terminal
Click on it and drag it to your desktop for easy access
 Double click it to enter the terminal  and input your selected commands....it can be as easy as copy and paste in most circumstances

---

### Post by drakebarimore on 2007-06-07
Ok, cool.  I found it.

Terminal says this:  "andy@andy-desktop:~$ "  when I open it.  Do I simply past the commands at the end of the dollar sign ($) ?

---

### Post by w4ett on 2007-06-07
exactly......

---

### Post by drakebarimore on 2007-06-07
One more question before I go try this.   The instructions start off saying for me to give a command to back it up.  Will it be easy to restore if I screw it up?  And, knowing me, if I'm not able to restore it, can I simply reinstall all over again?  I'm obviously new and I don't really have much saved on my OS yet.

---

### Post by w4ett on 2007-06-07
The instructions in that tutorial seem pretty good....even down to the method to back-up.  If you prefer, a clean install if you screw-up can SOMETIMES be easier than repairing, but xorg.conf isn't that hard to fix, especially when it really isn't working right to begin with.  8)

---

### Post by drakebarimore on 2007-06-07
immedietly after entering the first command, it asks for my password but won't let me enter it.  I use numbers for my password but regardless of which key I strike, the cursor disappears for a second and then starts blinking again.

---

### Post by w4ett on 2007-06-07
> **drakebarimore said:**
> immedietly after entering the first command, it asks for my password but won't let me enter it.  I use numbers for my password but regardless of which key I strike, the cursor disappears for a second and then starts blinking again.

Type your password as you originally set it.....the terminal keeps your password secret (invisible) then press <enter>

---

### Post by drakebarimore on 2007-06-07
That brings me to a window titled " Configuring xserver-xorg"

which has this in it: 

For the X Window System graphical user interface to operate correctly,    &#9474;  
 &#9474; it is necessary to select a video card driver for the X server.           &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Drivers are typically named for the video card or chipset manufacturer,   &#9474;  
 &#9474; or for a specific model or family of chipsets.                            &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; X server driver:                                                          &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                              sisusb           &#8593;                           &#9474;  
 &#9474;                              tdfx             &#9618;                           &#9474;  
 &#9474;                              tga              &#9618;                           &#9474;  
 &#9474;                              trident          &#9646;                           &#9474;  
 &#9474;                              tseng            &#9618;                           &#9474;  
 &#9474;                              vesa             &#8595;                           &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                          

I think it wants me to select one of those, but I don't know which.

Does anybody know what I should choose?

---

### Post by w4ett on 2007-06-07
We need to know the video card you have installed in your computer and the size of on-board memory then you can select the proper driver  (ATI) for ATI Radeon Cards, NV for Nvidia, Via for S3 series...etc.

---

### Post by drakebarimore on 2007-06-07
This one is a ATI Radeon X300SE 256mb @ 400MHZ  325MHz VPU  ?Whatever that means.

---

### Post by w4ett on 2007-06-07
select ATI from your list of choices...this will install the open source drivers....we'll worry about the proprietary drivers later.....

---

### Post by drakebarimore on 2007-06-07
Well, I was just about to reply that ATI wasn't one of the options when my screen went out.  Now, I can't get my system to boot.  I guess I'll star a new post asking for advice on getting my system to boot.  I don'tknow what happened, I did not make any changes with the xorg thing.

Oh well, if anybody wants to help me figure out how to get my system booting again, look for my new post.

Thanks all for trying to help.

---

### Post by drakebarimore on 2007-06-08
Ok,  got the pc working again.  Thats just wierd why the pc screen died like that.  Anyway, back to trying to get my Ubuntu to display on my wide-screen.

At last attempt, I had entered into "Configuring xserver-xorg" and was trying to decide amongst the following:


&#9474; sisusb &#8593; &#9474;
&#9474; tdfx &#9618; &#9474;
&#9474; tga &#9618; &#9474;
&#9474; trident &#9646; &#9474;
&#9474; tseng &#9618; &#9474;
&#9474; vesa &#8595; &#9474;

W4ett advised me to select the ATI selection, but "ATI" is not among the offerings.

Another thing that is puzzling me is, after making these changes, will my regular pc monitor still work?  Or will only the wide-screen work?  I of course can only have the monitor hooked up to the computer while I am making these configuration changes because it is the only one that presently works.  So, I guess I'll have to make these changes and then reboot with my TV hooked up to see if the changes take effect.

If anybody has any further recommendations, please feel free to help.  I appreciate everything.

Thanks.

---

### Post by w4ett on 2007-06-08
use the up and down cursor keys to scroll through the available options <spacebar> selects options and <enter> confirms selection

---

