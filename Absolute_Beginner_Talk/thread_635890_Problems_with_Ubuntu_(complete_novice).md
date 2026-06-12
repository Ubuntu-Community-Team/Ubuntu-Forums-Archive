---
title: "Problems with Ubuntu (complete novice)"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by staidasquo on 2007-12-09
Having been reading about Ubuntu for a while I installed it from a CD from the Linux Format mag. I have used windows in all flavours for years and part of my job is to train people in using windows based software - ie I have a reasonable knowledge of windows beyond just "using" it. I have to say I'm disappointed in Ubuntu at the moment - it doesn't make sense, and isn't intuitive as windows is. I appreciate this probably a case of getting used to it and I really want to press on and dump XP!

1. I downloaded loads of updates after install which seemed a sensible thing to do - however something called XFCE seems to have taken over the desktop and the top and bottom toolbars have disappeared?
I can't even see how to get on the internet now as the icons have gone? How do I get the desktop back to the original Ubuntu boot up screen?

2. I also downloaded Ubuntu Studio (as I use that pc for music recording and editing) but now all I have is an ISO image which won't simply "install"? What do I need to do to install it?

Can anyone help 'cos I really don't want to get too hacked off and go back to XP? I'm prepared to put in the effort and stick with it - and maybe sorting out the above problems will give me some basic tips?

Ta.

---

### Post by rune0077 on 2007-12-09
1. As far as I know XFCE *is* a desktop in itself. Try uninstalling it with Synaptic . Then make sure you have gnome-desktop installed (if not, install it), reboot, and you should be back to the standard desktop.

---

### Post by Ub1476 on 2007-12-09
For some reason you have managed to install the XFCE desktop environment. The default for Ubuntu is Gnome (I know, funny names). You should be able to choose from the different environments in the login screen under "session". I recommend you to remove it though atm.

```
sudo apt-get remove xubuntu-desktop
sudo apt-get autoremove
sudo apt-get install ubuntu-desktop --reinstall
sudo apt-get clean
```

Those commands should probably clean up for you. You can everything through Synaptic (GUI) if you would prefer that too though. 

And, Ubuntu Studio is an OS as Ubuntu, so you would need to install it like Ubuntu. Burn the .iso, boot from it and install.

---

### Post by rkd on 2007-12-09
From a quick look at their web site, Ubuntu Studio is another Linux distribution, based on Ubuntu.  So what you would have to do is burn a DVD from the .iso that you downloaded, boot from it, and install the Ubuntu Studio OS from it.  Of course, that probably would wipe out your current Ubuntu (or something else) on your hard disk unless there is a way to tell it to squeeze itself into the remaining free space on your computer.  Maybe that's okay with you if you haven't spent much time setting up your newly-installed Ubuntu -- you'll have to decide that.

Maybe you can run Ubuntu Studio as a Live CD, without affecting your hard disk, until you decide whether you really want to use it, though I didn't notice anything mentioning that.  After all, it is based on Ubuntu, so it might run as a Live CD, too.

I really don't know anything about Ubuntu Studio -- I'm just making some assumptions after spending just a minute looking at their web site.  Perhaps if you spent a little time exploring the information on their web site, you could find directions for integrating Ubuntu Studio with an existing Ubuntu system rather than replacing it, though I didn't notice any such directions in my hasty glance at the site.

---

### Post by staidasquo on 2007-12-09
Thanks for these replies - especially Ub1476 - I didn't even notice the options button as it's not lit. I have regained my desktop!
I didn't realise Ubuntu Studio was an OS in it's own right, just thought it was an application. I'll check out the website and see if I can install it in it's own partition.

Thanks again - I will keep going..........

---

### Post by overdrank on 2007-12-09
> **staidasquo said:**
> Thanks for these replies - especially Ub1476 - I didn't even notice the options button as it's not lit. I have regained my desktop!
I didn't realise Ubuntu Studio was an OS in it's own right, just thought it was an application. I'll check out the website and see if I can install it in it's own partition.

Thanks again - I will keep going..........

Hi and ubuntu studio is in the repo's on gutsy. So if you would like to use studio then all you have to do is go to system, administration, synaptic and search for ubuntu studio. Good luck! :KS

---

### Post by staidasquo on 2007-12-09
Sorry? "Ubuntu Studio is in the repos in gutsy"?  It's like I've entered Narnia........seriously, what does that mean?

---

### Post by overdrank on 2007-12-09
> **staidasquo said:**
> Sorry? "Ubuntu Studio is in the repos in gutsy"?  It's like I've entered Narnia........seriously, what does that mean?

It means if you would like to use the applications that are used in Ubuntu studio then you can use them in Gutsy 7.10. Just install them through synaptic manager. 
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by staidasquo on 2007-12-09
Ok, onwards and upwards. Thanks for helping - I think I've a lot to learn yet!

---

### Post by Ub1476 on 2007-12-09
> **staidasquo said:**
> Sorry? "Ubuntu Studio is in the repos in gutsy"?  It's like I've entered Narnia........seriously, what does that mean?

Gutsy Gibbon is the codename for Ubuntu 7.10 (which means it was released 2007 October). The next Ubuntu release will be called Hardy Heron/Ubuntu 8.04 which will be released 2008 April.

Repos/repository means where data is stored. "The repos" in Ubuntu is what packages you find in Synaptic or add/remove or through the command "apt-get". 
If you open System>Administration>Synaptic packagemanager, you will see there are about 20.000 different packages available. Quite much, isn't it?

In Synaptic (or a more user friendly "add/remove") you can search for almost everything you would ever want to install or need. To install the Ubuntu Studio packages (themes and apps), just search for it in Synaptic. To install things like VLC media player, Deluge bittorrent client, K3b burning program, just search for it and Ubuntu will automatically install. 

It's very simple when you get used to the Linux way;)

---

### Post by staidasquo on 2007-12-09
Thanks Ub1476 - bits are starting to make sense now. I will keep trying, honest! With these few tips and replies other things are falling into place.

---

### Post by CideRed on 2007-12-09
> **staidasquo said:**
> Sorry? "Ubuntu Studio is in the repos in gutsy"? ** It's like I've entered Narnia**........seriously, what does that mean?

Gave me the biggest laugh of the last month, cheers for that.

I too am a novice linux user and have struggled on for the past four weeks getting to grips with the subtleties of linux and Ubuntu in particular. I've read so much my head spins but step by step (albeit very small steps) the fog is clearing, well not so much clearing as getting less dense. Which is more than I can say for myself. Must be an age thing.

I hope you resolve your problem soon.

---

