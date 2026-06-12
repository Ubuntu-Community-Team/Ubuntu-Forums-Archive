---
title: "installation question"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Caermundh on 2007-06-02
I have downloaded the ubuntu 7.04 desktop version of ubuntu and i am trying to install it on a Dell Inspiron 4100. I managed to burn the CD and boot the laptop just fine, and the install program *seems* to be running fine...except that its running really really REALLY slow. For example, it spent about two hours reading from the CD from the time i clicked the "INSTALL" icon to the time it came up to the language selection screen. The mouse is frozen completly, but i can hit enter to get through the screens. After selecting the language, its been reading from the CD for another hour or so so far and im still not to the next step.

I'd like to know if this is normal? or is something fubared with my CD? I read somewhere about burning the CD at a slower speed to avoid a corrupted CD, and i think i burnt it at normal speed. Would that create a problem like this?

---

### Post by dbbolton on 2007-06-02
> **Caermundh said:**
> I have downloaded the ubuntu 7.04 desktop version of ubuntu and i am trying to install it on a Dell Inspiron 4100. I managed to burn the CD and boot the laptop just fine, and the install program *seems* to be running fine...except that its running really really REALLY slow. For example, it spent about two hours reading from the CD from the time i clicked the "INSTALL" icon to the time it came up to the language selection screen. The mouse is frozen completly, but i can hit enter to get through the screens. After selecting the language, its been reading from the CD for another hour or so so far and im still not to the next step.

I'd like to know if this is normal? or is something fubared with my CD? I read somewhere about burning the CD at a slower speed to avoid a corrupted CD, and i think i burnt it at normal speed. Would that create a problem like this?
i think your cd is probably damaged. make sure you check the md5 sum of the iso before burning it. also, don't use a CD-RW as they are notorious for messing up- use a good quality CD-R, and burn the iso at 1x.

---

### Post by taurus on 2007-06-02
Yes, try to burn it at a slow speed like 4x instead of the default value.  And if you want to install Feisty on your machine, perhaps you should consider using the alternate CD.  With alternate CD, you don't have to boot into live first before you can install it.  You install it from the first menu.

---

### Post by Caermundh on 2007-06-02
Wow, i think thats about the fastest response ive ever gotten to a message post ever! heh. Thank you. I'll go back and actually read the instructions for checking the MD5 sum this time. (This is what I get for not following instructions huh? heh.)

---

### Post by Qchan on 2007-06-02
[b][color=darkred]
Hmm...

Does it take awhile for your PC to boot into Ubuntu? If it does, then it may not be the CD but the HDD instead. You should run a HDD stress test and make sure that is not the issue.

You can download such a tool here:
[http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)

Just burn the ISO to a CD and boot from it.
[/b][/color]

---

### Post by Hendrixski on 2007-06-02
> **Caermundh said:**
> Wow, i think thats about the fastest response ive ever gotten to a message post ever! heh. Thank you.

:-) that's because we actually like the operating system we're using, and what it stands for.  Enough so that we stick around and answer questions that at one point somebody has answered for us.

Welcome to the community.  We hope you find all your questions answered quickly, (though we recommend asking google or the "search" feature on the forums before posting).  

Once you get int installed If you need live help then check out IRC!  You can click on Applications-->Add/Remove and select XChat (it's an IRC client) then pick a screen-name and go to the channel called #ubuntu... and it's kind of like ubuntuforums, but live.  Ask a question and someone will answer it whom you can have a dialog with, and pose followup questions.

Also, check out the LoCo team for your area.  You can talk to people in person about what you want your technology to do for you and they'll know how.  Because you shouldn't have to adjust your lifestyle to your technology, it should adjust to you.  And that's why we all use Ubuntu....

so again.. welcome to the community, and we hope to see you around.

---

### Post by rusty4r on 2007-06-02
> **Caermundh said:**
> Wow, i think thats about the fastest response ive ever gotten to a message post ever! heh. Thank you. I'll go back and actually read the instructions for checking the MD5 sum this time. (This is what I get for not following instructions huh? heh.)

Have you seen the psychocats page about burning the iso and the checksum?
[http://www.psychocats.net/ubuntu/index.php]("http://www.psychocats.net/ubuntu/index.php")

---

### Post by Caermundh on 2007-06-02
Ok, thank you all for all the replies. First, I checked out the psychocats page, very helpful stuff there. I may need to read it more thouroghly and attack this project again armed with better information. i also checked the MD5 sum, that's good to go. I re-burned the .ISO image to a CD-R at 1x, that also seems to have helped. However, it still runs pretty slow. After reading Qchans reply, I took another look at the hardware on the laptop and realised two things 1) its taking along time just to boot from the CD at all, 2) the laptop only has like 256MB ram and a PIII 1GB processor.

Now that i re-think this, that hardware may not be sufficient for ubuntu 7.04 desktop? Should I maybe go with Xubuntu, or maybe with the alternate CD?

---

### Post by rusty4r on 2007-06-02
I would try the alternate cd first but i think i remember somebody else who couldnt get it done with that much ram and they ended up using Xubuntu

---

### Post by abn91c on 2007-06-02
go to [www.download.com](www.download.com) and serch for a progam called Active ISO Burner, it is a smll no frills ISO burner, I have used i to burn all my downloaded distros and it is fast and works great

---

### Post by Caermundh on 2007-06-02
ok, thanks again all. Its late here (almost 10PM) so i think im going to hit the sack and try this again tommorrow when im fresh. Ill start with the alternate CD image, then try xubuntu if that doesnt work.

---

### Post by Caermundh on 2007-06-03
ok, downloaded and burned the alternate CD and that seems to have done the trick. The install process is using the ASCII based interface instead of the graphical interface. Needless to say its running alot faster. Now all that remains is to see how fast the operating system actually runs. I also need to know where I can get sound video and wireless drivers. the video card is an ATI mobility Radeon, the sound is Cirrus Logic CS4205, and the wireless is a the Netgear MA111 USB wireless adapter.

---

### Post by Caermundh on 2007-06-03
bump

---

### Post by dbbolton on 2007-06-03
> **Caermundh said:**
> ok, downloaded and burned the alternate CD and that seems to have done the trick. The install process is using the ASCII based interface instead of the graphical interface. Needless to say its running alot faster. Now all that remains is to see how fast the operating system actually runs. I also need to know where I can get sound video and wireless drivers. the video card is an ATI mobility Radeon, the sound is Cirrus Logic CS4205, and the wireless is a the Netgear MA111 USB wireless adapter.
why do you need to find drivers?

---

### Post by psyopper on 2007-06-03
> **Caermundh said:**
> ok, downloaded and burned the alternate CD and that seems to have done the trick. The install process is using the ASCII based interface instead of the graphical interface. Needless to say its running alot faster. Now all that remains is to see how fast the operating system actually runs. I also need to know where I can get sound video and wireless drivers. the video card is an ATI mobility Radeon, the sound is Cirrus Logic CS4205, and the wireless is a the Netgear MA111 USB wireless adapter.

For your videocard look here: [http://www2.ati.com/drivers/linux/linux_8.37.6-inst.html]("http://www2.ati.com/drivers/linux/linux_8.37.6-inst.html")

I believe your Cirrus Logic audio will work out of the box.

Your wireless adapter may give you some headaches. Use the search Luke. Try searching this forum with the search box in the upper right corner and enter MA111 USB Wireless, or just USB Wireless. If that doesn't get you anywhere try Googling for "Netgear MA111 USB linux" without the quotes of course!

Good luck!

---

