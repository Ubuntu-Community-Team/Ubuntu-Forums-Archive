---
title: "System Restore - does Ubuntu have an equivalent to Windows?"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-05-26
One feature I liked in Windows XP is its System Restore.  For those not familiar with System Restore, it is a feature that allowed one to take a snap shot of the system state.  I found it useful to "Create a Restore Point" when I had setup XP the way I wanted it.  A System Restore equivalent with Ubuntu would be useful as I have found myself screwing up a configuration and wishing I could roll back to the way it was.

So, is there an equivalent System Restore feature in Ubuntu?

Thanks

Carl

---

### Post by meng on 2007-05-26
I don't believe Ubuntu has this feature yet, although I had heard it was being seriously considered, perhaps even worked on. I haven't paid that much attention to developments since Dapper though.

---

### Post by starcraft.man on 2007-05-26
Uh, No. I never found that feature too useful in XP, it certainly wasn't full proof and often it did not fix the problem that I had encountered, if it was malicious enough.

Ubuntu doesn't really need that function. Everything that is done in Ubuntu, can usually be undone just as easily. Not to mention Ubuntu just doesn't crash that often, and certainly won't get infected by a trojan or virus that will force you to restore (not always getting rid of them I might add in xp).

If you want to image your disk, that will provide the best full proof back up. Go [here,]("http://linuxappfinder.com/backupandrecovery/driveimaging") and read up on one of them. I can't recommend any particular one, I still use a paid imaging product I had gotten prior to getting linux >.>.

---

### Post by carloslosgrande on 2007-05-26
I believe there are a number of Partition imaging apps, but I happened across this howto in the forums some time ago and it works really well for me, because its really simple just like me, its courtesy of ubuntugeek I believe.

Ubuntu Tricks - how to generate a list of installed packages and use it to reinstall packages

This tutorial will work for any Debian based system, but is written specifically for Ubuntu.
I’ve recently had the occasion to make a complete list of software installed on one of my Ubuntu boxes, and then reinstall it from scratch. Here’s a quick and easy way to generate a list of installed .deb packages, and then use that list to quickly reinstall them.
digg_url = 'http://digg.com/linux_unix/Ubuntu_tricks_how_to_create_a_list_software_and_use_it_to_restore_your_pc';
First, let’s make the list. You’ll be doing all of this in a Terminal Session:
**> dpkg --get-selections | grep -v deinstall > ubuntu-files**
NOTE: Wordpress interprets two dashes (- -) as one dash (–). When you’re putting this into your CLI, make sure it’s dropping two dashes ‘- -’ without the space between them.
Now you’ve got a list of all of your installed debs in a fairly small file. In my case, I simply moved this file to a thumb-drive. You could also store it on a seperate partition or on a disk somewhere. Heck, it’s not that big, email it to your gmail account.
So now you’ve got this list and all is well, until you’re Ubuntu install either dies or has to be reinstalled for some reason. Go ahead and do the base install.
Once you’ve got Ubuntu back up and running, copy your ubuntu-files back into your home directory and do the following:
[B]> sudo apt-get update
sudo apt-get dist-upgrade
sudo dpkg --set-selections < ubuntu-files[/B]

NOTE: Wordpress interprets two dashes (- -) as one dash (–). When you’re putting this into your CLI, make sure it’s dropping two dashes ‘- -’ without the space between them.
Now you’ve told your system what it needs to install, so let’s install it all.
**> sudo dselect**
This will open up a dselect session. Type** ‘I‘** and allow dselect to install of the the packages listed in your ubuntu-files document. When it’s finished, type **‘Q‘** and hit the ENTER key to exit dselect.
Now you’re a lot closer to where you were before.

---

### Post by NT4.0 on 2007-05-26
I have been keeping my system backed up with partimage.

I made a separate partition for partition image backups. To back up/restore, I boot with Ubuntu CD, mount this partition, install partimage (I keep the deb package on it too) and run it to backup/restore the system partition.

When I used Windows XP, I used System Restore a few times, but it proved to be unreliable. IMHO, this is absolutely unneeded in Ubuntu (although partimage might be good on the CD).

---

### Post by Kobalt on 2007-05-26
I think [Simple Backup Suite]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite") is dealing with this quite well, since it's GUI and very flexible.

---

### Post by indytim on 2007-05-26
Like NT4, I'm also using Partimage for system backups.  My approach is to do the updates only on Saturday morning.  I then take an image of each of my operating system partitions (Kubuntu 6.10, Kubuntu 7.04, Xubuntu 7.04) along with the associated /home partitions.  I do a double redudancy save ( to my second hd and also to an external hd).  I purge out at 3 weeks.

It's a bit drastic, but it gives me full recovery if something goes "south".  

Just one of many approaches :)

IndyTim

---

### Post by starcraft.man on 2007-05-26
> **Kobalt said:**
> I think [Simple Backup Suite]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite") is dealing with this quite well, since it's GUI and very flexible.

Ooooh, I like. Never seen that before. Off to install it, after lunch at least.

---

### Post by cwmoser on 2007-05-27
That was a very good tip showing how to create a file of installed packages.  I've gone and done that and put it on a backup.

Now, that will allow one to install packages with  the *default* config files -- is there a utility that will collect all the config files as they are currently modified?

Thanks

Carl

---

