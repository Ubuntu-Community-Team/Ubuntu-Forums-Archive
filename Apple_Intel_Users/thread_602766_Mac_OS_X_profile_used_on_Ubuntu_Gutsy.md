---
title: "Mac OS X profile used on Ubuntu Gutsy?"
date: 2007-11-04
forum: Apple Intel Users
---

### Post by freakyfelt on 2007-11-04
I have my MacBook Pro triple booted between OS X, Ubuntu Gutsy, and Vista and was wondering if there is any way that I could set it up so that my user profile is accessible from all 3 (maybe even to the extent of having the user directories of all 3 OS'es to remap to the same profile). Any ideas? Each OS has its own partition, but I could make a new partition and dedicate it to my profile if I needed to.

---

### Post by LeopoldBloom on 2007-11-07
I'm not sure if it works with Vista since I am triple-booting with Leopard, XP and Ubuntu but I remember during the install it asked me if I wanted to bring over a user account from the XP partition. As for OSX, I don't have anything for you, but am interested.

---

### Post by dward526 on 2007-11-07
As far as Ubuntu is concerned, it does not import user info from Vista

---

### Post by cyberdork33 on 2007-11-07
There is a thread on here about sharing a home partition between OSX and Ubutnu. This is not recommended though as there are several hidden configuration files in your home directory that may have undesired effects on either OS.

Doing this also requires that you edit some system level user properties (userid and groupid) to make the users appear the same to both OSX and Linux. This is not a trivial change.

---

### Post by freakyfelt on 2007-12-09
Well, after doing a little bit of research, I made a sort of profile sharing.It's very grotesque and not secure by any means as my method doesn't support user permissions. But that could be taken care of (theoretically) with a different file system if someone knows of a better one. Also note that I'm using FAT32 and it doesn't support files over 4 GB. An alternative would be to use NTFS and use MacFUSE, though I have not tried this method (yet). Anyways, here's what I did in a pretty format.

**Partition the drives, setting Linux, Windows, and User partitions as MS-DOS, Mac as HFS+**
The order I recommend is EFI, OS X, User, Windows, and Ubuntu as Ubuntu/Linux recognizes EFI. Vista will treat is as empty space as it only supports BIOS.

The following is taken from [http://www.macosxhints.com/article.php?story=2007041217125440:](http://www.macosxhints.com/article.php?story=2007041217125440:)
**Set up user accounts in OS X**
Copy user directories to new drive
```
sudo ditto -rsrcFork -V /Users /Volumes/User/
```
Go to System Preferences -> Accounts -> Right click on each account and choose Advanced Options.
Change Home Directory to /Volumes/User/<username> and click OK
Restart
```
sudo mv /Users/<username> /Users/<username>.org
sudo ln -s /Volumes/User/<username> /Users
sudo rm -dr /Users/<username>.org

```
NOTE: If you later add a new user, you will need to do the following in OS X:
Create the user
```
sudo ditto -rsrcFork -V /Users/<username> /Volumes/User/<username>

```Adjust home directory in Accounts
```
sudo ln -s /Volumes/User/<username> /Users
sudo rm -dr /Users/<username>
```
**Install Windows XP and Upgrade to Windows Vista normally and set up user accounts**
The reason you need to upgrade is that Vista does not like OS X's ability to boot from EFI and will notify you of an error about GUID. By installing XP first and then upgrading, you avoid that error. Roundabout yes.

Several people are probably wondering why I went with Vista. To be honest, I hate Vista. BUT, Vista comes with two things that I do like. First, it finally uses the standard home folder set up that Linux and OS X use (Documents, Music, etc). Second, Windows Vista (finally) brings the love and joy of symlinks that have graced our presence in other operating systems for years now. I'm going to take advantage of this by just symlinking all of the user folders across to Vista. While this may not be the best method, it helps keep Windows to itself and just shares the needed stuff. So the command for symlinking in Vista:

Open a command prompt in elevated privileges by right clicking Command Prompt and selecting the appropriate option.
```
cd C:/Users/<username>
rd Documents	#Removes the directory Documents to make room for the symlink
mklink /d Documents D:/<username>/Documents	#Makes a directory symlink named Documents

```
Repeat the last two options for each folder you wish to symlink

**Install Linux (In my case Ubuntu)**
When it comes time to partition, choose manual. For the user partition, tell it to mount to a certain place (by default /media/<user partition name>). We will link to it in a moment using symlinks. Set up your user accounts with the same names if you wish for simplicity as I don't know how to set up one common user and password database.

**Set Linux to use your User directories**
The best way I found to set up the directories was to use symbolic links. It's tedious, but a shell script could probably be made to do the same task if you need to batch process it. So anyways:

```
sudo rm -rf /home/<username>/Documents #Deletes current Documents directory in home directory
sudo ln -s /media/User/<username>/Documents /home/<username> #Makes a symlink from home directory to user's Documents directory

```Repeat that for all of the folders you want symlinked. The desktop folder will not be able to symlink because of instability issues with Gnome. Unless someone knows something I don't (very likely).
 I recommend symlinking your Library folder just in case you want to share some settings with, say, Firefox and Thunderbird. Which brings me to...

**OPTIONAL Firefox and Thunderbird Sharing**
[http://www.downloadsquad.com/2007/05/23/sharing-your-thunderbird-and-firefox-data-between-ubuntu-and-win/](http://www.downloadsquad.com/2007/05/23/sharing-your-thunderbird-and-firefox-data-between-ubuntu-and-win/)
User profiles in Mac OS X are stored in ~/Library/Application Support/Firefox and Thunderbird respectively. I would recommend using the OS X profiles as they are already on your user partition.

In Windows go to Start -> Run... and type in &#8220;firefox.exe -profilemanager&#8221; and press OK.
In the box that pops up, choose Create a New Profile and press Next.
Click &#8220;Choose Folder&#8221; and navigate to your Library in your symlinked Library folder. Then go to Application Support -> Firefox -> Profiles, select the profile and press Open. Click Finish and Start Firefox.

In Linux, press Alt + F2 and type in &#8220;firefox -profilemanager&#8221; and press Run.
In the box that pops up, choose Create a New Profile and click Next.
Click &#8220;Choose Folder&#8221; and navigate to your Library in your symlinked home directory. Then go to Application Support -> Firefox -> Profiles and select the appropriate profile and click Open. Click Finish and Start Firefox. Voila! Your Firefox profile is now available no matter which OS you are in.

NOTE: Make sure that all 3 OS use the same versions as incompatibilities may show up. For example I forgot that I was running Firefox 3 Beta on Mac OS X and Firefox 2.0.11. Not pretty at all as FF3 uses a database for history and bookmarks (which I love btw). Also, themes might look awkward as some aren't designed for all three OS'es. But to each their own.

And that's it. If anyone has a better method please let me know. Yes, this means that each user has to set up a password in each OS, but at least their home folders will be synced across the board.

---

