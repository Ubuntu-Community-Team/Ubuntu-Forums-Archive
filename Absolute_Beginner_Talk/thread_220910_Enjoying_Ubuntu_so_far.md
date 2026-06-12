---
title: "Enjoying Ubuntu so far"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by Phen0m24 on 2006-07-22
Hi everyone - total Ubuntu/Linux noob here.  I wanted to install something different on my laptop to give me some Linux exposure.  (have ABSOLUTELY none)  Right off the bat, I had to search the forum because my HP laptop wouldn't boot from the DVD.  (downloaded the 6.06 LiveDVD iso)

Tried changing the boot sequence but that didn't work.  Kept booting into XP.

So in case any other HP laptop users out there are yanking out their hair either trying to run the LiveDVD or install -

Disable Quickboot.

Enable Multiboot.

Set the boot order to optical drive and then hard drive.

Once the order is set, disable Multiboot.

Reboot and the DVD will fire up.  (at least it did for me!)

Did the GPartEd deal - set the drives up.  Am now running on a fresh install and liking the looks of this OS!  I feel like I accomplished something!  8) 

I have to say though, when you're used to things like .exe files and automatically installing Firefox plugins, the command prompt sudo deal is a little intimidating.

But I'm giving it my best shot.

Glenn

---

### Post by Ziox on 2006-07-22
glad you like ubuntu, and about you installing .exe files. Unlese you want to install windows-only programs, then i would say that installing thing in ubuntu is better, safer, and faster than on windows(unless of course your programs aren't in the repos, which is rare). Now if you need basic help and how to install most stuff, then visit the last link in my signature.  It is a great guide.

---

### Post by Phen0m24 on 2006-07-22
Hey Ziox -

Thanks for the reply.  I bookmarked the site!  As far as the Windows/Linux deal, I'm sure I'll get used to it.  And I'm assuming I'll be better off for doing so.

Glenn

---

### Post by viciouslime on 2006-07-22
I don't quite get what you mean about automatic installation of firefox plugins? It works just the same under ubuntu as under windows for me...

---

### Post by Phen0m24 on 2006-07-22
> **viciouslime said:**
> I don't quite get what you mean about automatic installation of firefox plugins? It works just the same under ubuntu as under windows for me...

Well, you know when you get the little indicator that shows you have a missing plugin?  I double click on Flash and each time I try to install it it says installation failed.  So I'm here trying to figure out how to do it from the terminal.  Ack.  I'll get it.

---

### Post by ThrobbingBrain66 on 2006-07-22
```
sudo aptitude install flashplugin-nonfree
```
should do the trick

---

### Post by Phen0m24 on 2006-07-22
> **ThrobbingBrain66 said:**
> ```
sudo aptitude install flashplugin-nonfree
```
should do the trick

Couldn't find any package whose name or description matched "flashplugin-nonfree"

The download is sitting right there on the desktop.  ](*,)

---

### Post by Ziox on 2006-07-22
did you enable the extra repos.? check my signature for the link for the how to.

---

### Post by jimmygoon on 2006-07-22
> **Phen0m24 said:**
> Couldn't find any package whose name or description matched "flashplugin-nonfree"

The download is sitting right there on the desktop.  ](*,)

If you downloaded it to your desktop then you should either double click it ... or use the terminal and do the following

"cd Desktop"
"sudo dpkg -i packageName.deb"

or just enable the extra repositories, its in somone's sig, and then do that command ("sudo apt-get install flashplugin-nonfree")

---

