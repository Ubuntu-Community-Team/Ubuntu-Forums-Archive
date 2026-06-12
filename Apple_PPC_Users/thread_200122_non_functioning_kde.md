---
title: "non functioning kde"
date: 2006-06-19
forum: Apple PPC Users
---

### Post by vallis on 2006-06-19
Hi everyone,
I have been running (k)ubuntu on my sony laptop for quite a while now and have been enjoying it very much.
Recently i was given an old iMac g3 with OS X installed.  I decided that removing OS X and installing kubuntu would be a good idea.  Everything seemed to work ok up until the point of logging into kde.  The system comes up fine and the kde login screen appears, the mouse works as it should but everything else is very slow.  clicking the menu button has no effect and clicking on the username field has no effect for a few minutes. When the username field eventually appears it takes a long time for any typed text to appear.  I can drop to a terminal view easily enough and can see that the cpu is at 99% idle, so it's not the cpu being over worked.
I have seen other posts about problems with hardware acceleration and dri issues. I'm not sure if this is what i am experiencing or if this is a different problem.  At the moment i have still been unable to log in to kde.

the system specs are as follows:
iMac gray
600Mhz g3 cpu
256MB system memory
ati 128rage2 graphics
running kubuntu 6.06

any advice would be very much appreciated

---

### Post by N8K99 on 2006-06-19
Are you able to sign into a getty? I know what you want to use is the pretty and sexy KDE GUI, but first we need to determine if you are able to actually use Linux. 

So, if you press Ctrl+Atl and F1 you should get a black screen with a command prompt inviting you to sign in. If you can actually login with your user name and password, try entering the command [B]startx 

[/B]If you are lucky then you will be taken through the start up process for kde and end up on the desktop. 

If you are not lucky, then it is more than likely just a minor problem with your configuration file for the X windows package. This can be solved by rebooting from your install CD in rescue mode.

---

### Post by Ptero-4 on 2006-06-20
vallis. You need to disable dri in the /etc/xorg.conf file.

---

### Post by vallis on 2006-06-20
Cheers for the advice.
i have been able to log in using a getty terminal (thats how i found out the system was mostly idle).  i hadnt thought of trying startx, unfortunatly it doesnt work as X is already running.  i can pkill X and kde then use startx, but this only gets me back to the semi-frozen login screen.  i have disabled dri (i think) by commenting out 'Load "dri"' in the modules section of xorg.conf and also commenting out the whole DRI section.  kde still fails to load :(
i decided to install xfce4 to see if it worked and so far it seems to be working quite well.  I'd still rather be using kde, so i dont really know where to go from here.  does xfce4 working mean that my kde install is broken? should i reinstall?  i guess this also means that the X server is working as it should.

again, any advice would be much appreciated.

---

