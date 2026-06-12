---
title: "eMac 700Mhz G4 Resolution Problems, Weird. Please help."
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by lgonzo99 on 2005-12-26
Ok. I know that there are previous threads that have been previously posted about this issue. From the threads that I was able to find, I tried everything but nothing seemed to work for me. Here is was my problem:

I first tried out the Ubuntu Live CD on my Apple eMac 700Mhz computer. The CD worked great, which did not have any problems finding the correct resolution for my monitor. So, I decided to try out installation version of Ubuntu. Interestingly enough, in the installation version of Ubuntu, everything worked fine, except the video resolution. I am a windows user for over 10 years, and am just now trying to get into using Linux as my primary OS. With the little experience that I have had with Linux, I thought it was weird that the Live CD would recognize the correct resolution settings for my eMac, but the actual installation CD would not.

Remember, I am a Newbie at using Linux, so I was very luckyto find this thread ([http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution](http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution)) which got me on the right track. I did what the person suggested in that thread, but it didn't work for me. But I kept thinking to myself, Why does the Live CD work and the Installation not work. So, here's what I did, I backed up my /etc/X11/xorg.conf file while I was using the installed version of Ubuntu (with SU privilages), then I shut down my system and booted my computer using the Ubuntu Live CD. For some reason, while using the Live CD, I couldn't seem to find the installation directories of the installed version of Ubuntu, I could only see the virtual partion the Live CD had created, so I had to back up /etc/X11/xorg.conf from the Live CD to my windows computer in my home network. (for other newbies like myself, you go to "Places" on the top panel of the desktop and then select "Connect to server....) and type in the appropriate information to connect to the windows machine) 

After I backed up my xorg.conf from the Live CD session, I rebooted my computer and booted into my installed version of Ubuntu. Then, I connected to my Windows computer where I had saved the Live CD xorg.conf file, and copied it to the /etc/X11/ directory but I called it xorglive.conf. Then I opened up a terminal with SU privilates by typing (sudo -su), then I closed the GUI session by typing (sudo /etc/init.d/gdm stop) and then I replaced the existing copy of xorg.conf with the xorglive.conf hoping it would work by typing (sudo cp /etc/X11/xorglive.conf /etc/X11/xorg.conf). And then I restarted the GUI session again by typing (sudo /etc/init.d/gdm start) and it worked!

While you experienced users out there are probably rolling your eyes at this thread, in my linux-newbie mind, this is a big accomplishment. And my question to you experienced uers is, Why would the installed version of Ubuntu not recognize a higher resolution than 640x480? And the Live CD version of Ubuntu easily recognize a resolution of 1024x768 without a problem if they are supposed to be the same? Now I know this is probably not the best method of correcting the resolution problem I had, but it certainly worked, but by doin so, did I hut my system in any way?

Thank you in advanced for any comments and replies to my questions.

Thanks again.

Luis.

---

