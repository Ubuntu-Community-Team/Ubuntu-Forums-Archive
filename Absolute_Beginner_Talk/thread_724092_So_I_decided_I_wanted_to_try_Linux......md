---
title: "So I decided I wanted to try Linux....."
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Eldamar on 2008-03-14
First let me ask for patience I really don't know what I'm doing but I'd like to learn so that brings me here.  I recently built a new desktop for myself. Hardware: 19" widescreen 1440x900, Abit ip35 pro, intel e8400, 2gig ddr2 800, evga 8800gts 512, barracuda 320gig sataII, OCZ 700wat psu, and a dvd burner.  I think most of my troubles are hardware compatibility related but here's what's happened.  I got a second old 20 gig ide harddrive that I hooked up on the master spot on the ide cable and set the jumper to cylinder select allowing my bios to control priority. I burnt the gutsy destkop amd64 cd and tried installing that way but I couldn't get past the first install option screen at first then I disabled splash and made it to a screen telling me my graphics were running in low and gave me some options for setting my display.  I tried several of those options and after that the only thing I would get is a blinking cursor in the corner of my screen even after 30 minutes of waiting.  Then I tried  the alternate gutsy install cd which was a bit more successful other than when I got to the Select Software portion it failed at 85% I retried that step with the same results and moved on to the install grub boot loader step which also failed, tried the lilo boot loader step and that failed.  Then I finished the remaining steps.  I was thinking I could just install ubuntu on the second harddrive and use bios to set boot priority for whichever os I wanted to use.   But when I tried to boot with the small hard disc as priority it failed.  So I switched the bios ad was surprised to see a menu appear asking me to select the os.  The menu timed out and started to load ubuntu by default.  I got all these exception codes continually for like ten minutes and every here in there it would say that something was initializing and eventually I got to where it said to log in.  I tried several things and couldn't get logged in.. Hmm in writing this I just realized another name to try on login I'm still a little how the computer name account name and all that works yet.  So that's kind of where I'm stuck at for the moment.  I know I have a lot to learn, but I thought I would write down my frustrations and perhaps someone can give me some tips..  Regards

---

### Post by steve-shinn on 2008-03-14
Have you tried running the pc from the live cd .... ie. allowing the pc to boot from the CD.

If everything runs OK using the live cd, it's almost certainly NOT a hardware issue.

---

### Post by Eldamar on 2008-03-14
Yes that is what I tried first but couldn't get past where it said I was running low graphics and gave me display setting options and I tried several things include vesa drivers lowest settings and also setting it where it should be set either way it resulted in an unending blinking cursor in the corner of my screen and that's it..

---

### Post by Joeb454 on 2008-03-14
Try booting the Live CD from Safe Graphics mode :) And see if that helps

---

### Post by Eldamar on 2008-03-14
I think I did that I tried it with splash removed and also did the code nosomethin nosomethin vga=771?  and the second option in the installation menu.

---

### Post by jonabyte on 2008-03-14
I hate to say this, but you may also want to consider a different distro, I have had problems with ubuntu in the past and went with suse. 
I had recent problems with suse and then was able to get ubuntu up (at home).

---

### Post by The Titan on 2008-03-14
or you could try the alternate CD, that will install it.  The only reason i say this is because i could only get to like 85% on the live cd and it would crash.  But the alternate CD worked just fine for me.

---

### Post by smurphy_it on 2008-03-14
#1 Recommendation... Use paragraphs, makes reading alot easier!

As for everything which you typed.  You are sitting at a login prompt but unable to login.  During the setup process it should of given you an opportunity to create a user account and password.  You might want to re-run the setup, or boot into recovery mode (reboot, and hit escape when prompted by grub) then once logged in type cat /etc/passwd that should tell you all of the user accounts on the computer.  The one you created would have a UID of 1000.  Once you know the name of the user account you can change the password.

Here is an example with a username of John for my example.

passwd john
now type in a new password you want to use

After all that is done, type shutdown -r now (that will reboot your computer).

Once rebooted you should hopefully be able to login.  If so, jump in a terminal and type dmesg > dmesg.log

That will output the contents of your login process (and any errors) to a dmesg.log file in your home directory.  Post another message and attach the dmesg.log file so we can see what errors you are hitting.

---

### Post by aeiah on 2008-03-14
apparently there are some issues with this motherboard.

[http://ubuntuforums.org/showpost.php?p=3372889&postcount=47](http://ubuntuforums.org/showpost.php?p=3372889&postcount=47)

the easiest thing to do would probably be to unplug that small ide hard drive and see if the livecd works. you can think about partitioning the 300gb hdd if this ends up being the case. dont rush into it though it you've got vista on your pc, as i dont think its quite as simple to dual boot as it is if you have windows xp

and could you use paragraphs please? i dont mean to be a grammar nazi, but it makes things a lot easier to read

---

### Post by Eldamar on 2008-03-14
Well where there is a will there is a way right ;)  I may also end up trying the i386 version but I think I'm actually getting close to success.  The second half of my first post is with the alternate install which is where I hit 85% and it failed.  I couldn't ever really get into the live cd at all.  But that was late last night and I've slept on it since then so when I get off work I'll tackle it again and see what I can come up with. I half heartedly tried the rescue mode install last night but I quit when I got to the screen asking me where I wanted my main root system :
/dev/sda1
/dev/sdb1
/dev/sdb3
/dev/sdb5
I think were the options.  I think sda1 would be my sata hard drive right?  the sdb1 would be where I want to put the main root system sdb3 or 5 would be the swap partition?  Let me know where I should put  it and I might try that again

---

### Post by smurphy_it on 2008-03-14
SDA = 1st Hard Drive (sata)
SDB = 2nd Hard Drive (sata)

do a fdisk -l /dev/sdb and post the output so we can see what partitions there are and more importantly what they are.

PS.  Do a CD Check on the Ubuntu CD next time you boot from it to ensure there is nothing wrong with it!

---

### Post by Eldamar on 2008-03-14
Sorry for my poor forum skills (wow I need lots of work) I will use paragraphs now.

Thanks for the replies on both the chipset and logging-in that gives me two areas to try new things.  I'll let you know how it goes and if I can get logged in I will post that error log for you.

Regards

---

### Post by Eldamar on 2008-03-14
Ok I'm back on task

I've retried booting with what I had installed it just hung after going through tons and tons of exception codes. 

 Next I tried disconnecting the ide drive and just seeing if the live cd would boot with just sata enabled and set to ahci, since I have both cd drive and hd sata. Same result, my monitor just goes to sleep and my computer seemingly does nothing even when left for an hour to figure itself out.  so I just hit ctl+alt+del and restart.  

*sigh* Confused

I think I might have multiple problems here but nvidia graphics seems to me to be a likely culprit since I can't see any of the graphical install methods

---

### Post by Joeb454 on 2008-03-14
Did you ever try booting in safe mode?

Sorry if you did, I only read the last few posts after my last post :)

---

### Post by Eldamar on 2008-03-14
Jeob454 yeppers I did, 

I'm currently trying the desktop i386 live cd and I actually saw the bar going back and forth after choosing the regular install.  however after the bar got done going back and forth now I'm seeing the screen full of "[numberhere] buffer i/o error on device fd0, logical block 0" which is something I've been seeing alot no matter what I try.  Is that something that is normal or is it a problem I need to resolve?

---

### Post by Joeb454 on 2008-03-14
It can't read one of your drive's, though I don't have any idea what fd0 could be :(

---

### Post by Skidpad on 2008-03-14
> **Joeb454 said:**
> It can't read one of your drive's, though I don't have any idea what fd0 could be :(
Floppy Drive.  (I can't help more than that though  :(  )

---

### Post by Eldamar on 2008-03-15
Yeah it's the floppy drive.. so I was able to solve that issue

However I still cannot see anything after the initial selection screen on the live cd.  

I put in the desktopi386.iso cd and it actually goes through the progress bar page then I got a low graphics thing telling me to set up my graphics settings and I haven't been able to get past that screen I set it up with what should be my settings nvidia geforce 8 driver 1440x900 widescreen@60hz but after that it dumped me out to shell command line.

I rebooted and tried it again and then it booted me out to shell right after the progress bar thingy both in regular and graphics safe mode.

so I'm still stuck.  If I can get back to the graphics set up I will try the vesa drivers maybe...

---

### Post by Eldamar on 2008-03-15
I think this is the same problem I am having:

[http://ubuntuforums.org/showthread.php?t=459459]("http://ubuntuforums.org/showthread.php?t=459459")

---

