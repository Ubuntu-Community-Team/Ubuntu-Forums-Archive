---
title: "gnome-desktop-environment messed up my KDE"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-07-24
Hi,

I had KDE up and running just fine so I decided to try Gnome as well. For this I used Adept where I chose the ***gnome-desktop-environment*** package. All seemed to go well until I restarted. 

Although I had chosen KDE as my default GUI it actually started in Gnome. Thing is that I had Gnome installed previously and it used to look a lot better. This Gnome that I got on my computer look horrible. I guess I could go through the options and try to fix it but that means more work. Anyway, besides the looks it doesn't even work. The logout/restart button does nothing no matter how many times I press it. Instead I have to go into text mode and reboot from the command line. Also, all Gnome menus are showing KDE applications !... :confused: 

As if this wasn't enough, my KDE is also messed up now. This still seems to work OK but now I've got all these Gnome applications in my KDE menus and they've got no icons! :confused: Good thing is that my KDE applications are still there...

Anyone got any ideas on how to install both Gnome and KDE on the same machine without messing up any of them?

---

### Post by pbaehr on 2006-07-24
For a little while I had both KDE and Gnome installed. This was on Breezy, and Gnome was there first. I installed KDE through apt-get (not recommended since it is a pain in the *** to remove). They both worked fine and independently and then, when I ultimately removed KDE, everything went back to the way things were.

So, I can't help you repair what happened, but I can vouch that they can exist side-by-side. The only difference in my situation was that I was installing KDE after Gnome and I used apt-get instead of adept.

---

### Post by ovimunt on 2006-07-24
*bump*

---

### Post by mjpoetic on 2006-07-25
You may want to try finding the file ~/.gtkrc-2.0

If it exists...it was created when you used Kcontrol (or maybe something else) to specify the GTK theme and font used.  What you want to do is either delete it or rename it to something like ".gtkrc-2.0-bak" without the quotes of course.

Hope this helps. :)

p.s.
Now when you log into to Gnome the next time...everything should be fine.  If not, you could try to log into the "root" account and rename your home directory to something like "/home/usr_old" where "usr" is your username.  Then when you log back into your account, the directory will get recreated.  You can then copy your settings back over from the "/home/usr_old" directory.  This is one of those last resort options but it isn't that cumbersome a task.  In Windows you'd usually have to reinstall your system to fix some things.

---

