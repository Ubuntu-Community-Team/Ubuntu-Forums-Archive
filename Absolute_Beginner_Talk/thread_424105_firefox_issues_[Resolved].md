---
title: "firefox issues [Resolved]"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by ezman5086 on 2007-04-26
Hey, I'm a total and complete newbie.... though I've really taken a liking to this whole linux thing.  Anyway, I was trying to transfer my settings firefox from my windows partition to linux.  Well, still thinking as a windows user, I copied profile from the directory from the Mozilla/Firefox folder in Application Data.  Then I tried to paste it in it's place in the .Mozilla/Firefox folder in my Home directory.  It all seemed to go well until i tried to restart firefox.  Now, it gives me this message:

"Firefox is already running, but is not responding.  To open a new window, you must first close the existing Firefox process, or restart your system"

I restarted my system, but it does nothing.  There is no firefox process running when I go to the system monitor.  I tried uninstalling it so I could reinstall it using Applications/Add remove programs from the top menubar, but it says that other programs depend on firefox so it won't uninstall.  What should I do, and how can I get all my firefox settings from windows to ubuntu?

If it's any help, I'm running feisty 7.04 on a thinkpad T60

---

### Post by Zuph on 2007-04-26
you can do a "ps -e" in a console to get a list of all running processes.  See if firefox is in there.  If it is, you can kill it by doing a "sudo kill [process number]".  Restart it, and it might make the problem go away.

---

### Post by ezman5086 on 2007-04-26
just did it... but nope.  there's no firefox process...

---

### Post by lluisanunez on 2007-04-26
Was FF open when you copied the Profile folder? If so, there is some file making Ubuntu think that FF is running. It happened to me, then I repeated the operation but closing firefox first

---

### Post by ezman5086 on 2007-04-26
I just tried that twice, restarting in between.  I still get the same message.  is there any way i can just forcefully remove and install firefox.... will it really break everything?

---

### Post by aysiu on 2007-04-26
I don't think this has anything to do with copying the Firefox profile from Windows. This is a known issue even if you're using only one profile that never moved.

Try this:
[http://kb.mozillazine.org/Profile_in_use#Remove_the_profile_lock_file](http://kb.mozillazine.org/Profile_in_use#Remove_the_profile_lock_file)

---

### Post by dpar on 2007-04-26
If aysiu's suggestion doesn't work, try looking at the profile.ini file. It may be still pointing to the old profile name.

---

### Post by ezman5086 on 2007-04-26
thanks everyone, especially aysiu for the links.  I just ended up deleting the whole thing, removing the parent.lock and then copying everything back into the replacement folder.  worked great!

---

