---
title: "[SOLVED] Ubuntu Studio installed. Big oops. I wish it was as easy as Ctrl+Z"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by shuukazedojo on 2008-03-06
Hello all. A couple of days ago I was looking for some software to edit a video to make a tutorial. After getting no response with Kino, I moved to Ubuntu Studio. Installed via Synaptic along with everything attached to it. It called for a system restart, so I did so. When I reboot I'm told that my resolution is too low and need to change it. I bumped it up one, (out of pure ignorance since I don't understand what I was supposed to do). That seemed to screw things up so I went in to Screen and Graphics and played around with that until I really messed things up. I found a thread on here talking about how to "reset" it using this procedure:

[CENTER][I]"At login - simultaneously press Ctrl+Alt+F1 
Type in user name and password
When brought to the prompt, type: sudo dpkg-reconfigure -phigh xserver-xorg
Then when it's finished running that: sudo reboot
Will reboot in Safe Graphics Mode"[/I][/CENTER]

Then I was able to go back in to the same area and figure out the resolution. After this command, all of my theme, icon, and compiz settings are gone. This isn't a big deal. I can redo all of that. 

I uninstalled Ubuntu Studio via Synaptic with a success message afterwards. THEN, I go into the Applications menu, and guess what's there: all the programs from Ubuntu Studio. I tried to find them under Add/Remove, but they're not showing up there either. 

I'm also getting some error messages which I can get images of if anyone feels it would be helpful.

Quite a predicament.

Ideally, I would be able to do a System Restore and turn back time a couple of days, but I've read that isn't a feature of Ubuntu. PLEASE CORRECT ME IF I'M WRONG!

Any ideas on how to get things back to the way they were a couple of days ago???????????????????

Sorry for the long post and thank you in advance for any help you can provide!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by athaki on 2008-03-06
I'd say bite the bullet, back up all your personal data, and reinstall ubuntu.  I know it sounds harsh but a fresh install is the best that can be offered until some system restore feature is standardized.

---

### Post by shuukazedojo on 2008-03-07
Thank you. I'll keep that in mind as a last ditch effort, but I would really hate to have to redo all the drivers, network settings, etc. just because one or two files are out of whack. 

Does anyone know more about this GNOME Settings Daemon? I keep getting these error messages (see attached). I could probably fix the Ubuntu Studio remains issues if I could somehow restore whatever deals with this Settings Daemon. Any ideas?

---

### Post by oldos2er on 2008-03-07
Have you tried uninstalling Ubuntu Studio?

---

### Post by shuukazedojo on 2008-03-07
Initially, I went to synaptic and searched for "Ubuntu Studio" and marked it for complete removal. It gave me a successful completion message, but the programs that were installed with it were still on. This morning I thought, "why don't I just do the same thing with each of those programs?" So I did. I searched each program individually and marked all related files for complete removal. 

Still having trouble. I think the error messages may shed some light. I attached them to my last post. Thank you for your help!!! Please let me know if you have any other ideas.

---

### Post by Fixman on 2008-03-07
If Ubuntu Studio applications don't work, then the link may yet be there. To fix that, right click the menu->edit menus, and remove all Ubuntu Studio icons.

---

### Post by wolfen69 on 2008-03-07
just because the apps show up in the menu doesnt mean they are still installed. (this happened to me) just go to system>preferences>main menu and remove them from the menus.

---

### Post by shuukazedojo on 2008-03-07
Thank you for your help. I am so sorry for the unclear communication. After I uninstalled each program via synaptic, they were removed successfully from the menu. 

The trouble I'm still having is regarding the theme, etc. Before this fiasco I had Compiz running some cool stuff. When I go back in to try and reset the settings, it gives me an error message (see the second error message in the pic I posted as an attachment above). 

I feel that the GNOME Settings Daemon has something to do with all of this since it's mentioned in both error messages. I just don't really know what it is or how to go about fixing it. Any ideas on this? Has anyone checked out the error messages? Has anyone encountered them before? How were they fixed?

Thank you!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by RedRat on 2008-03-07
Don't feel bad, I had a similar problem in trying to install Ubuntu Studio!! It messed my system up also, I could not start the xserver. Basically , had to go in and re-install ubuntu. All works well now.  Glad to see that I am not the only one to have problems.

---

### Post by shuukazedojo on 2008-03-07
I've been doing some more research. I think it may be a bug in Gutsy...

[http://ubuntuforums.org/showthread.php?t=579167&highlight=GNOME+Settings+Daemon](http://ubuntuforums.org/showthread.php?t=579167&highlight=GNOME+Settings+Daemon)

I'll try it after dinner and post whether or not it did the trick.

---

### Post by shuukazedojo on 2008-03-08
Well, went to try the fix in that thread. Couldn't find the directory. I kept searching for more answers and it seems this is a pretty common issue. It isn't always Ubuntu Studio sparking the change. Sometimes it's completely random. 

I did get it fixed, however. Reinstalled any items related to GNOME in Synaptic. Then installed the Restricted Driver from NVIDIA. I went back into the System>Preferences>Appearance>Visual Effects tab and was able to set it to Custom!!! Everything snapped back to the way it was before the Ubuntu Studio install. 

I hope this helps someone out there. I also hope this issue is fixed before the official release of Hardy Heron (users of Hardy in its alpha stage are reporting this issue too). 

Thank you everyone for your help. One thing that is always nice to know is that there are people in the community there to help if an issue arises. That's better than any tech support line you could sell!!!!!!!!!!

:guitar:

---

### Post by Drunky on 2008-03-10
If anyone is trying to upgrade from Ubuntu to Ubuntu Studio please use this [Ubuntu Help Wiki.]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy")

It will save you trouble and time.

---

