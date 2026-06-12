---
title: "Failed Synaptic Installs. Now boots to command line only."
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by pmueller on 2006-07-09
Hello,

My struggles with Ubuntu have been going on for some time. Despite Windows XP and Dos experience, I feel like a newbie, because things go wrong and often.

Recently, I was trying to install more codecs, mplayer, gxine, and vmware player to a rather spare installation of Dapper Drake with all of the updates and very little else than the basic install.

I started to run into difficulty with the installation ov vmplayer using snyaptic. I was receiving errors after it started to go through the install routine and showed that it did not complete installation. I opted to reinstall vmplayer and synaptic finally showed it as installed.

I tried to install the proprietary codecs through the terminal. I did not get complete satisfaction with gxine, so I decided to install mplayer.  Mplayer would play my mp3's finally, but I received a blinking error and the music was disrupted with slight pauses. When I tried to uninstall Mplayer I was getting errors about the vmplayer! I decided to uninstall vmplayer through synaptic.

There were no improvements in the playing of my mp3's. I rebooted  and now I can not get into the Gnome GUI at all. I can only get a command prompt.

What do I do now?

Do I reinstall Dapper for my third time and download all of those repositories and updates again using my 56k modem, about 3 0r 4 hours worth?

Do I save all of my updates somehow and rebuild my system?

Did I make a mistake by installing more than one program at a time through Synaptic?

Is Synaptic really fool proof? In other words is there something wrong about my Ubuntu copy?

How can I backup a working system, so that I do not have to reinstall and download updates over and over again?

By the way, I had an additional problem with the modem dial program. It was never able to save my login, phone number, and password. I had to enter it every time, even though I selected my created Nashua, New Hampshire connection.

Any thoughts, comments, and partial answers are appreciated?

Paul M in New Hampshire

P.S. I am still impressed with Linux and Ubuntu even though I am having these problems. Windows gave me a few headaches also with endless security updates, firewall updates, and antivirus updates. I believe the Ubuntu system will be much more secure.

---

### Post by crystal on 2006-07-09
> Do I save all of my updates somehow and rebuild my system?
I have never tried this myself, but you can download the .deb files for packages using *aptitude download*. Presumably you can save them to a CD, then install them later.

---

### Post by woedend on 2006-07-09
all of the files you have updated should be save in the /var/cache/apt/archives
folder I believe(maybe one more under that).  If you can copy these to a CD or another partition, when you reinstall, if you put those files back in the same directory you got them from, when you run the updates it will download nothing and install from the hard drive.
as far as the problem...thats a tough on to pin down...you can TRY
sudo apt-get install ubuntu-desktop and see if or what it wants to install.
HTH

---

### Post by teet on 2006-07-09
Since you don't have any data to save or anything, I would just wipe it clean and start over anew.

Then I would use Automatix, EasyUbuntu, or BUMPS to install the media codecs/players you need.

[http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)

-teet

---

### Post by pmueller on 2006-07-09
Hi,

Thanks for all of your responses in a very short time. I will combine the approaches that you suggest, but I will take some time off to get some exercise and enjoy this great day.

Additional repository questions:

It took me about 2 hours to enable and download all of the regular repositories over the 56k modem. I do not want to lose this in a fresh new install. Wouldn't it be possible to use a live CD and move this information to another partition or hard disk drive?  Where is the repository information found? 

Cheers and Kudos,
Paul M

---

### Post by pmueller on 2006-07-09
Hello,

I tried the "sudo apt-get install ubuntu-desktop" at the command line and it started to unpack(?) a few of my missing files and dependencies. It could only go so far though and said that I needed to get some of the packages over the net.  I put my install cd in to see what would happen and I rebooted to a command prompt ubuntu login and password. I still did not have a graphical Gnome GUI.

Next I tried a variation, "sudo aptitude install ubuntu-desktop". This command seemed to unpack more files and said that I would see the x desktop (?) after I rebooted. Sorry, I did not write all of these things down.

I rebooted and got back into the Gnome desktop. Things are still a little weird. I lost all of my deskto icons. When I go to places and click on my cd drive , my home directory, or my hard disk drive I get this message: Could not open location 'file:///media/hda2'

Details: There is no default action associated with this location.

My dialup window still does not save my password, telephone number, login, or modem detect information.[-o< 

However, things are much better.

I am reluctant to install Automatix until I resolve these other issues.

Paul M
[http://ubuntuforums.org/images/smilies/eusa_pray.gif](http://ubuntuforums.org/images/smilies/eusa_pray.gif)

---

### Post by pmueller on 2006-07-10
Hello, 

After I made that last post,I went on line and typed into terminal: sudo aptitude install Ubuntu-desktop. This command action found more missing dependencies. Later, the terminal window said that I would see changes after I rebooted,

At the reboot I got my desktop icons back. Back up at the task bar selecting 'Places' and 'Hda2' would give me a file browser window, not the error previously reported.

I am using Automatix right now and getting a "gzip"error. Perhaps, I will ask about this in a separate thread.

It is real nice to see that Ubuntu has a way to heal itself, when things go wrong. Has anyone written a sticky on restoring a system gone haywire?

Thanks for all of your help,

Paul M in New Hampshire

---

