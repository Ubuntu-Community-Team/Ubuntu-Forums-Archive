---
title: "Help!"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by RobotoWorks on 2007-11-09
I just downloaded the Vista'ish side bar off of GNOME-LOOKS, when I went to install it(It was in a zipped file) it gave me this message "Invalid archive. Archive must contain a directory with the screenlet's name." What is wrong?

---

### Post by matthewcraig on 2007-11-09
Have you checked with the GNOME-LOOKS website support forums?

---

### Post by RobotoWorks on 2007-11-09
I didnt know there was one.

---

### Post by Maestro23 on 2007-11-09
> **RobotoWorks said:**
> I didnt know there was one.

Where there any special instructions in the author's comments about installing his screenlet?

---

### Post by Paul820 on 2007-11-09
Extract the file you downloaded and put it in the .screenlets folder inside your home directory. The .screenlets folder is hidden so you will have to pres Ctrl+h to find it. Then restart screenlets.

---

### Post by RobotoWorks on 2007-11-09
Even with "CTRL+H" I cant find the file

---

### Post by SunnyRabbiera on 2007-11-09
this might be a zip within a zip
just unzip the file you downloaded and see what is in there.

---

### Post by RobotoWorks on 2007-11-09
Inside is just a regular folder. When installing the screenlets app though terminla ran into a few 404 errors if that helps

---

### Post by bulldog on 2007-11-09
Create a folder named .screenlets in your /home folder.
Unzip the file into this folder.

---

### Post by Maestro23 on 2007-11-09
> **RobotoWorks said:**
> Inside is just a regular folder. When installing the screenlets app though terminla ran into a few 404 errors if that helps

You were showed in your other thread how to go in and check your sources thru the GUI.  I even posted a screenshot for you.

As for the screenlet you downloaded, I ask again: Were there any special instructions posted by the author on installing the screenlet?  Do you have a link to what you downloaded?

---

### Post by Paul820 on 2007-11-09
Do you have screenlets installed and running? If you do there is a **folder**, not file, inside your home folder called **.screenlets**. It's hidden, it should be there if you have screenlets installed and running. The zipped file that you downloaded, extract it and there is a folder inside, put that folder inside the **.screenlets** folder. When you restart screenlets that folder will be read and the sidebar will appear as a screenlet to put on your desktop.

---

### Post by Pumalite on 2007-11-09
You could try this:

[http://www.screenlets.org/index.php/FAQ#Installation](http://www.screenlets.org/index.php/FAQ#Installation)

---

### Post by Maestro23 on 2007-11-09
> **Pumalite said:**
> You could try this:

[http://www.screenlets.org/index.php/FAQ#Installation](http://www.screenlets.org/index.php/FAQ#Installation)

I have provide that link for him twice already in 2 of his other threads.

---

### Post by Pumalite on 2007-11-09
Good. This is a reminder then.

---

### Post by RobotoWorks on 2007-11-09
I have it installed and running using that tutorial, only when I installed through terminal it gave me a bunch of 404 errors even thoughs its running

---

### Post by Pumalite on 2007-11-09
Funny: 404 means bad connection or not having acquired the key for the repo properly, or the repos down momentarily..

---

### Post by Maestro23 on 2007-11-09
> **RobotoWorks said:**
> I have it installed and running using that tutorial, only when I installed through terminal it gave me a bunch of 404 errors even thoughs its running

If it installed correctly, you should have a menu item for it.

---

### Post by RobotoWorks on 2007-11-09
I installed it using Phil's broken down tutorial and heres what terminal gave me:

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release.gpg [189B]
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy/screenlets Translation-en_US
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy/screenlets Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
404 Not Found
Fetched 1B in 6s (0B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) 404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Pumalite on 2007-11-09
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy/screenlets Translation-en_US

It seems your connection was refused even though your key was obtained.

---

### Post by RobotoWorks on 2007-11-09
So what do I do, reinstall?

---

### Post by Pumalite on 2007-11-09
Try and try again until they accept your connection. You have to see that repo 'hit'

---

### Post by RobotoWorks on 2007-11-09
I tried it 5 times, but the same thing happened

---

### Post by RobotoWorks on 2007-11-09
Peoples?

---

### Post by RobotoWorks on 2007-11-09
Bump....

---

### Post by Pumalite on 2007-11-09
Recheck all your steps. Or change your server. Or both.

---

### Post by RobotoWorks on 2007-11-09
How do I change servers? And I did check the steps yet its not working

---

### Post by Paul820 on 2007-11-09
What does your sources.list file look like? Copy and paste it here as you seem to be having trouble updating those sources. Maybe there is something in there that can clear things up.

---

### Post by Pumalite on 2007-11-09
System>Administration>Software Sources (Change 'Download From' to Main or other convenient to you.)

---

### Post by Maestro23 on 2007-11-09
> **RobotoWorks said:**
> How do I change servers? And I did check the steps yet its not working

Do not bump your posts every 15 minutes.


System>>Admin>>Software Sources

Download From

*Your sources look hosed as well.  Post your sources.list

> cat /etc/apt/sources.list

---

### Post by RobotoWorks on 2007-11-09
What exactly do I do now? And what to you mean my sources are hosed?

---

### Post by llamakc on 2007-11-09
Cut/paste the contents of the file:

/etc/apt/sources.list

We need to see it.

---

### Post by RobotoWorks on 2007-11-09
Almost done I just need to know, do I copy to sources.list or sources.list.d?

---

### Post by llamakc on 2007-11-09
Follow my directions. /etc/apt/sources.list

---

### Post by RobotoWorks on 2007-11-09
But sources.list is a text file when sources.list.d is an actual folder

---

### Post by Maestro23 on 2007-11-09
> **RobotoWorks said:**
> But sources.list is a text file when sources.list.d is an actual folder

Please post the:
> sources.list

---

### Post by llamakc on 2007-11-09
> **RobotoWorks said:**
> But sources.list is a text file when sources.list.d is an actual folder

What part of my request to cut/paste the contents (what is written IN the file) of /etc/apt/sources.list is confusing you? If I had wanted you to list the contents of a directory I would have asked you to list the contents of the DIRECTORY, not the file.

For example, here is mine:

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
#
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

# VirtualBox
deb http://www.virtualbox.org/debian gutsy non-free

# gutsy awn
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator

```

Now that is MINE tailored for my system. We want to see what's in your /etc/apt/sources.list file. This file DEFINES where the package management system goes to fetch updates and packages from.

---

### Post by RobotoWorks on 2007-11-09
Well here ya go, dont blame me if this is not right

[[IMG]http://img340.imageshack.us/img340/5333/screenshot1nt9.png[/IMG]](http://imageshack.us)

---

### Post by Paul820 on 2007-11-09
:shock:

---

### Post by RobotoWorks on 2007-11-09
Sorry my fault, turns out I was born without a brain!

Here is what your looking for:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

---

### Post by Paul820 on 2007-11-09
There you go, there's your problem, for some reason all your sources are commented out. Every line that begins with a # then followed by deb, take the # off the beginning of the line. For example this line
> # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
Change it so it reads like this
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
Do this for the rest of the lines that begin with > # deb. Don't take it off any other line but those.

---

### Post by Maestro23 on 2007-11-09
> **Paul820 said:**
> There you go, there's your problem, for some reason all your sources are commented out. Every line that begins with a # then followed by deb, take the # off the beginning of the line. For example this line

Change it so it reads like this

Do this for the rest of the lines that begin with . Don't take it off any other line but those.

To edit this file, type in terminal:

gksudo gedit /etc/apt/sources.list

Make the changes that Paul820 told you to and SAVE the file.  Then run the following commands.

> sudo apt-get update

sudo apt-get upgrade

---

### Post by RobotoWorks on 2007-11-09
Thanx, it finally worked. Im sorry for being so dumb

---

### Post by RobotoWorks on 2007-11-09
One ore thing, when I load the screenlets app, I get this message "Unable to connect or launch daemon. Some values may be displayed incorrectly"

---

### Post by Maestro23 on 2007-11-09
> **RobotoWorks said:**
> Thanx, it finally worked. Im sorry for being so dumb

Only problem I see is that you are tyring run with Ubuntu/Linux before you crawl or walk with it.  You want all this pretty eye-candy that is NOT critical to the stable operation of your system.

You say you are new to the computer world so to speak, and I'm wondering why you picked Ubuntu/Linux over and Windows based system to start your journey into the computer world.

You need to take some time to** read and digest** the documentation that people link you to when they are helping you with a problem.

These forums are by far the best I have seen for any distro of Linux when it comes to helping and being patient with people new to linux.  But there comes a point where you have got to start picking up on stuff and not **posting/bumping** the same questions over and over when you have already been help with said problem. (Giving the commands and linked to the proper documentation)

***Check your Private Messages.**  I have given you some links to doing stuff in Ubuntu (Installing Software, Repository Management, Multimedia codecs, etc...)

---

### Post by RobotoWorks on 2007-11-09
Got it, I assure you in time I'll learn. I am not new new to the computer thus Ive been on Windows for a few years.

I have recently gotten internet access on my computer and thus meaning Im new to the web.

I chose Ubuntu/Linux because Ive herd many people say very good things about it and frankly I was getting tired of Windows.

I agree when you say these forums are the best as I see many getting helped al the time.

When you say "Read the documentation" I do but sometimes its written in suc away that I do not understand it and thus is why I must re ask questions.

I will try to become better and not have to ask as many questions, Sorry for any inconvienence.

---

### Post by Maestro23 on 2007-11-09
> **RobotoWorks said:**
> Got it, I assure you in time I'll learn. I am not new new to the computer thus Ive been on Windows for a few years.

I have recently gotten internet access on my computer and thus meaning Im new to the web.

I chose Ubuntu/Linux because Ive herd many people say very good things about it and frankly I was getting tired of Windows.

I agree when you say these forums are the best as I see many getting helped al the time.

When you say "Read the documentation" I do but sometimes its written in suc away that I do not understand it and thus is why I must re ask questions.

I will try to become better and not have to ask as many questions, Sorry for any inconvienence.

No prob man.  Questions are good... Repeated questions that have been answered before are not.:)

Just take your time, you will start to get the hang of Ubuntu.  Check those links I sent you in your PM.  Will explain how to do the good stuff... not just the eye-candy.:)

---

### Post by RobotoWorks on 2007-11-09
Eye Candy is great! But what are the essentials?

---

### Post by Paul820 on 2007-11-09
> When you say "Read the documentation" I do but sometimes its written in suc away that I do not understand it and thus is why I must re ask questions.

I know what you mean, most of the instructions do expect you to have a little bit of knowledge navigating folders, editing files and a grasp on a few of the commands. Don't let it get to you, believe me, once you get the basics down and you start to feel comfortable navigating folders etc you will start to enjoy it more. It can be very difficult at first because it's completely different to what you are used to ( windows ). I will put a few links here and when you get the time please go through them and try and learn as much as you can. People on these forums are always willing to help but you have to help yourself sometimes. :)

[http://www.linuxcommand.org/]("http://www.linuxcommand.org/")
Free books, grab some of these: [http://www.tldp.org/guides.html]("http://www.tldp.org/guides.html")
Free online linux courses: [http://www.linux.org/lessons/]("http://www.linux.org/lessons/")
More free books: [http://www.linux-books.us/linux_general.php]("http://www.linux-books.us/linux_general.php")

That should do you for now, and we all hope to see you back on here helping out others :)

---

### Post by Maestro23 on 2007-11-09
> **Paul820 said:**
> I know what you mean, most of the instructions do expect you to have a little bit of knowledge navigating folders, editing files and a grasp on a few of the commands. Don't let it get to you, believe me, once you get the basics down and you start to feel comfortable navigating folders etc you will start to enjoy it more. It can be very difficult at first because it's completely different to what you are used to ( windows ). I will put a few links here and when you get the time please go through them and try and learn as much as you can. People on these forums are always willing to help but you have to help yourself sometimes. :)

[http://www.linuxcommand.org/]("http://www.linuxcommand.org/")
Free books, grab some of these: [http://www.tldp.org/guides.html]("http://www.tldp.org/guides.html")
Free online linux courses: [http://www.linux.org/lessons/]("http://www.linux.org/lessons/")
More free books: [http://www.linux-books.us/linux_general.php]("http://www.linux-books.us/linux_general.php")

That should do you for now, and we all hope to see you back on here helping out others :)

Between those book recommendation and the** slew** of links I gave him... Brain overload. Does not compute.. Does not compute...:lolflag:

Bombard the newbie with info. :smile:

---

### Post by RobotoWorks on 2007-11-09
Thanx guys, but please dont delete this thread since I have it bookmarked for future reference

---

### Post by Paul820 on 2007-11-09
> **Maestro23 said:**
> Between those book recommendation and the** slew** of links I gave him... Brain overload. Does not compute.. Does not compute...:lolflag:

Bombard the newbie with info. :smile:
There is tonnes of info there, brain overload for anyone :lolflag:
@RobotoWorks, threads don't get deleted. The information stays for others that search for the same problems.

---

### Post by Maestro23 on 2007-11-09
> **RobotoWorks said:**
> Thanx guys, but please dont delete this thread since I have it bookmarked for future reference

Threads don't get deleted.

Tell you something that I do when it comes to my system.  I keep what I call a **changelog**.  Everytime I install something, change something, etc... I document it in a Open Office or AbiWord document.  Include the commands used, any threads that were referenced , website links, etc...

Makes things easier when it comes to trouble shooting when things go wrong.

---

