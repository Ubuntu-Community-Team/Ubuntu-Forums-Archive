---
title: "Ubuntu was crashed and gnome has reset!Lost all files!"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by siretfel on 2008-01-10
Hi all,

it's been quite a few days using Ubuntu and all was well. Last night was the night that i finished all the settings i wanted regarding gnome appearance, and program installation.

Two files were in the trash that i couldn't erase because i didn't have permition to erase. It was two folders with themes for gnome. Anyway i found this thread [http://ubuntuforums.org/showthread.php?t=648119](http://ubuntuforums.org/showthread.php?t=648119) and used the code in it. When i used the code in terminal nothing happened but seemed the terminal was stuck. 

I closed the terminal and tried to open firefox. Nothing happened. It couldn't open. I tried  to open ANY program at all, vlc,amarok ANYTHING nothing. 

After that I log-out and logged in after a while. 

EVERYTHING WAS RESET TO DEFAULT UBUNTU.BUT ALSO I lost all files.All folders, All settings, EVERYTHING.Like reinstalling ubuntu from scratch.I did a restart an nothing happened. 

Is this possible?
I don't believe with a simple logout and login i lost my files and settings. Any idea how to restore them?

---

### Post by gazj on 2008-01-10
It sounds like you somehow deleted your entire home folder, your entire settings for everything user specific are stored in your home folder as hidden files.

the remove command when used with the -f switch can be very destructive used in the wrong place (certainly when used with sudo), and there really is hardly any need to use it.  sudo rm -r $HOME/.trash/* would have been sufficent.

The reason the terminal seemed to hang is because it was deleting so much and taking a long time.  If you want to see what a rm is doing add the -v (verbose) switch and it will give you detailed output.

Lesson learned.  Be careful with the command line until you get to know it.  Theres loads of guides to get you started on the net.

Unfortunately you can't restore your files now they are banished forever.  On the other hand you will learn from your mistake and more to come but it will be worth it trust me. :)

Good luck with future setups

---

### Post by Sef on 2008-01-10
> Unfortunately you can't restore your files now they are banished forever.

Not correct.  You can possibly recover some or all of them.  Don't use the hard disk on that computer, if possible.  Use a Live CD.  Check out [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12").

From TRK:

> -recovery and undeletion of files with utilities and procedures

---

### Post by geirha on 2008-01-10
Yep, unix commands can be very picky about the syntax, one space in the wrong place on an rm command, and away goes your homedir. It's a better idea to run ```
gksudo nautilus
``` and do it graphically, makes it harder to delete the wrong files.

---

### Post by gazj on 2008-01-10
> **Sef said:**
> Not correct.  You can possibly recover some or all of them.  Don't use the hard disk on that comuter, if possible.  Use a Live CD.  Check out [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12").

From TRK:

I have never managed to recover files from an ext3 filesystem yet.  ext2 I have.  I will remember this next time I'm careless enough to lose something.  Thanks

---

### Post by siretfel on 2008-01-10
First of all thank you all for your answers!!
It seems I did delete the home folder.
But you know...the best thing about all this is that i FELT the power of linux!! Man i deleted everything and the operating system is up and running like NOTHING HAPPENED! 
I have restored all the features I wanted and now I'm gonna keep everything in my external HD.
Anyways i didn't mind losing my data. Besides I liked the fact that I experimented with Ubuntu.
I love it and i think i'm gonna stay

A friend said:
> **gazj said:**
> On the other hand you will learn from your mistake and more to come but it will be worth it trust me. :)

Good luck with future setups

I couldn't agree more man.I'm here to stay and learn! Besides I only lost my graphical staff. Everything i important i still have it.

Thank's again guys.

You really made me feel a lot better! Keep :guitar: :D:D:D

---

