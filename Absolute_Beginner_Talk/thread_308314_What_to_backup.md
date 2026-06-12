---
title: "What to backup?"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by thelocust on 2006-11-27
**[SIZE="2"]Ok so after a few installs and switching from ubuntu to kubuntu I have everything the way I want it for the most part. I want to instal Beryl but that was the reason for the last install so this time im going to backup my system before proceeding. I think the utility I want to use is Keep, but if anybody knows of a simple app to backup thats better than keep I'm open to sugestions. Now what to back up? So far I got my home directory, xorg file, repositories, and thats it. Also added to list above (but i dont know were the files are at) are my kde settings and my programs (is there any file that adept looks at to see what it should have installed that I can copy so if I have to reinstall I can paste and it will download everything? I doubt it I will probably have to make a script). If there is anything else I should backup please let me know. Also I'm not realy interested in making an image of my hdd I am fairly new to linux and I would like to learn from this. Thanks for any inputs.8)[/SIZE]**

---

### Post by David_T on 2006-11-27
You can backup just /home and /etc and be in pretty good shape.
For a list of installed packages, you can just type dpkg -l.  That lists all packages in /var/lib/dpkg/status.  The installed ones start with ``ii''.  Ones you've uninstalled start with ``rc''.

---

### Post by qpieus on 2006-11-27
Your KDE settings are in your home directory (in ~/.kde). I've seen several recommendations to backup /etc. There's a lot of config files in there, like fstab, sources.list, samba files, etcetera. All kinds of stuff that would be handy to have available if you need it. My /etc is only 10 MB, so it's not a big deal to back it up. As far as backing up programs, a lot of your programs installed config files in your home directory (usually in hidden subdirectories), so as long as you back up everything in your home, those are covered. Check this thread for a cool way to get a list of all your installed packages and how to use that list to re-install:
[http://ubuntuforums.org/showthread.php?t=261366]("http://ubuntuforums.org/showthread.php?t=261366")
Another link: [http://ubuntuforums.org/showthread.php?t=306727]("http://ubuntuforums.org/showthread.php?t=306727")

---

### Post by JNowka on 2006-11-27
I personally use Kdar to do my backups.  This program allows you to backup everything on your system into a compressed file, password it if you like, and slice the files up into appropriate sized peices for the media you will be saving it to (CD, DVD, etc).  So far I have been both satisfied and impressed with Kdar.  I just stored my 20 gig main drive to 2 2gig, and 1 372mb files.  If you have installed a bunch of programs you don't want to have to redownload, and install, this also means that those get saved to.

---

