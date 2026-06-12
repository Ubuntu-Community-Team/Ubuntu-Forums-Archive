---
title: "still can't access system administration apps"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by navy_doc on 2006-07-24
](*,) I still can't access system administration apps. I'm posting in the absolute beginner section, because as far as Linux (and Unix) is concerned I AM, so please don't throw techno babble at me. 

After years of Windows, I can point and click, anything else, assume I have no idea what you are talking about, and you'll be pretty much on the money.

I'm looking for a reason to like Linux, but so far I haven't found one. Four years ago I tried it, with the same result - frustration and headaches....:confused:

---

### Post by Metacarpal on 2006-07-24
Hi!  Welcome to Ubuntu.  We'll do our best to help make the transition as painless as possible.  Just like when you first started using Windows, there is a learning curve, but with a bit of help you'll have it figured out in no time.

What applications are you trying to access?  Are they programs already in your menu, or do you need to add them?  If you have the programs, what happens when you try to run them?

Give as much detail as possible, so we can help you better.  :)

---

### Post by Thund3rstruck on 2006-07-24
There is a lot of hype surrounding linux, but it needs to be noted that its not for everyone. Its all we use (me and my family) but it took a lot of time and effort to climb that learning curb to get to the point we're at now.

---

### Post by Uncle Spellbinder on 2006-07-24
After trying a few distros over the past year or so (Fedora Core 3 and 4, Open Suse and now Ubuntu Dapper Drake 6.06 LTS) I can safely say that I've found my Linux home. I still use Windows occasionally, mainly for apps not available on Linux (Acid Music Studio in particular). Other than that, I've not logged on to Windows for nearly a month. I really don't miss it. :cool:

---

### Post by navy_doc on 2006-07-24
OK, I can't instal any programs or even updates. spinning circle appears "starting adminstative application" appears on the bottom bar for a few seconds and then both dissapear - nothing happens. I should be prompted for the adminstrator password I believe? I only set up one user, so by default that should be the administrator, but I don't appear to have any administrator privelages.

Under system>administration  I cannot open: Disks, Networking, Services, Shared Folders, Software Properties, Synaptic Package Manager, Time & Date, Update Manager, Users & Groups.

result, I prety much have a dumb terminal...:(

---

### Post by arkangel on 2006-07-24
what happens when you type this  in the  terminal ?

# sudo -H -s 

in theory  the first  account you have created (when installing )  belongs by default to the administrative group

---

### Post by navy_doc on 2006-07-24
rob@:~$ sudo -H -s
sudo: unable to lookup  via gethostbyname()
rob@:~$

---

### Post by arkangel on 2006-07-24
Ok  could  you please   check your file /etc/hosts

#gedit /etc/hosts 

at least you should  have  lines like 

127.0.0.1 localhost "mydomainname"
127.0.1.1 "mydomainname" 

if not  reboot , and enter  in recovery mode, now  you are  root and edit  /etc/hosts file  accordingly

be carefully  by typing as root

---

### Post by navy_doc on 2006-07-24
127.0.0.1 localhost -HOME-
127.0.1.1 Acer

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by navy_doc on 2006-07-24
127.0.0.1 localhost -HOME-
127.0.1.1 Acer

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I gues I need to edit so the first two lines have the same host name...

---

### Post by navy_doc on 2006-07-24
rebooting in recovery mode took me to the command line, and I have NO idea what to type. 

I tried: 
#gedit /etc/hosts 
gedit /etc/hosts 
edit /etc/hosts 

none of which did anything....

---

### Post by SilverBear on 2006-07-24
This sounds like a problem I encountered with Ubuntu. By default you don't have the traditional Unix/Linux "root" account, so you can't log in as root to a grapic interface to do administrative chores. 

There is a way to create "root" and then get Ubuntu to let you log in as root, but some of the admin features still don't work under a GUI.

Mepis 6 just came out a couple days ago. Mepis now is based on Ubuntu repositories, so the availability of programs --including "Automatix"-- is the same as Dapper.  Except Mepis is more traditional Linux in the sense that you create a "root" account during the install and then a "user" account. Afterwards, at login, you can log into the KDE desktop for administrative things and into your user account for everyday activities.[Mepis's default GUI is KDE --same as Kubuntu uses, whereas Ubuntu uses "Gnome" Desktop]

Ubuntu doesn't let you do that by default because, I guess, it is very easy to screw things up really quickly if you have root power and you start pointing and clicking without knowing what you're doing. 

Ubuntu takes one feature of Linux, the "sudo" command, and makes it the default way of handling administrative tasks.

"Sudo" means that the "su" --the "super-user" AKA "root"-- is allowed to "do" one command.

For example, let's say you want to edit your fstab file, so that you can control the permissions for read & write on some data partitions you share with windows. Since the file you want to edit -- /etc/fstab -- is "owned by root, you who have logged in as navy_doc are NOT allowed to edit it!

So you open the terminal window [AKA a "console"] and you get a prompt that looks something like this:

navy_doc@1[~] $
[I'm using Mepis right now so it might be slightly different]

The important point to note is the final character. A prompt ending in a $ means you are logged in as a regular user. When you are logged in as root, the final character in your prompt is #

Enter the sudo command. In regular Linux if you want to do the chore I outlined above without logging out of your desktop and logging back in as "root" you could type [in the blank space after the $ prompt]:

sudo gedit /etc/fstab

The system would then prompt you to enter the root password and it would open up the GEdit text editing program with the file /etc/fstab loaded IN SUPER-USER mode so you could edit and save it, as if you were logged in as root.

The only difference in Ubuntu is that since there is by default no super-user, all you need to do is put in your own USER password and you get to temporarily run as if you were root!

You will notice that this works only one command at a time, and through the CLI [command line interface, or terminal].

However, in Ubuntu you should be able to do some GUI admin tasks --like adding & updating programs. After you click on "Add & Update Programs" in you main menu, the GUI should open up and let you look at what you may install. If you click the check-box to install a new program, you will be prompted with a popup window saying "Administrative Rights are required" and prompting you for a password.  

It's Ubuntu's GUI aspect to sudo. You enter your own user password, and the install of your chosen program should commence.

If this does not seem to resemble what is going on for you, say so. I have left some details out of my explanation so that you get the most important points without too much surrounding fog. If sudo is not working for you, or if you aren't being prompted for a password in the menu-driven admin tasks, perhaps there is some other problem besides your unfamiliarity with Ubuntu.

all the best,
SilverBear

---

### Post by navy_doc on 2006-07-24
rob@:~$ sudo gedit /etc/fstab
sudo: unable to lookup  via gethostbyname()
rob@:~$


I'm not getting any password prompts with 'Add/Remove' or when attempting to open any administration application...

---

### Post by SilverBear on 2006-07-24
Hi, navy_doc.

I spent so much time writing out my previous post, the discussion moved right past me!

Let me read what you've said, think on it a bit, and log into my wife's Ubuntu machine so we're on the same page. 

With a root prompt, though, you really should have gotten an open editing window when you typed: 
gedit /etc/hosts

---

### Post by arkangel on 2006-07-24
in the console  try  with vi


# vi /etc/hosts


to  edit  the text  press  "i"  ,  to go out  of insert mode press "esc", to  save  ctl+w+q, to exit vi without saving the changes use ctl+q+!

vi is  editor a little tricky to handle , sorry

---

### Post by Metacarpal on 2006-07-24
> **navy_doc said:**
> rebooting in recovery mode took me to the command line, and I have NO idea what to type. 

I tried: 
#gedit /etc/hosts 
gedit /etc/hosts 
edit /etc/hosts 

none of which did anything....

Follow the instructions posted by a member named Mustard [in this thread.]("http://www.ubuntuforums.org/showthread.php?t=91455&page=2")

That oughtta fix you right up.

---

### Post by navy_doc on 2006-07-24
I used VI, was able to make the change, but when I rebooted, the change was not there. I pressed ctl+w+q more than once, but it seems that for some reason it did not save...

---

### Post by arkangel on 2006-07-24
i was thinking  something else, because I do automatically  sorry 

 when  you  have edited the  file   press "esc" then  press ":"

at the botton of the terminal  will appear  ":"  so then type  wq and enter 

please see the picture and good luck :)

---

### Post by SilverBear on 2006-07-24
I've got to go for a couple hours.
If the other guys can't get you straightened out, try:
[http://www.mepis.org/node/1462](http://www.mepis.org/node/1462)

Sorry to have to say so, but it sounds like you have a bad installation and are going to need to re-install Linux from the beginning. Maybe Metacarpal is right and you can fix it. I hope so.


But if you need to re-install, you can try Ubuntu again, or try Mepis first and see if it works out better for you before you try tackling this kind of problem.  No distro is without some problems. But I've found fewer quirks in Mepis than in any other distro. 

The KDE desktop might be easier than Gnome for someone used to MS Windows. I liked Gnome at first, when I ran Ubuntu "Warty Warthog" and "Breezy Badger,"but I seem to prefer KDE now.

SUSE 10.1 is another distro I've had very few problems with, but I think it's a whole DVD you need to download to install it. Mepis is just 1 CD, and it's one of the best LiveCD Linux distros, too. 

all the best,
SilverBear

---

### Post by navy_doc on 2006-07-24
I'm thinkin bad instal is more likely now. I tried 'Mustard's' solution, using nano at the command line, and it did indeed change the host file as desired. it now reads:

127.0.0.1 localhost.localdomain localhost acer

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

However I still cannot access any adinistration applications..](*,)

---

### Post by alan yeates on 2006-07-24
Had exactly the same problem, turned it was from downloading mss core fonts, Ubuntu will not allow 2 things requiring root to work at the same time if one is a downloader is still working, which in my case was an unresolved download. Do use add/remove programs if possible rather than terminal or say easy ubuntu, but having said that I can't tell you how to get out of a bad download, since as you are finding you can't use most tools. I just reinstalled in frustration!

---

### Post by SilverBear on 2006-07-24
My son & I fixed the plumbing soorer than I thought we would, so I'm back.

Navy-doc:
Don't get the idea that I'm bashing Ubuntu, because I've been a fan since Warty. But so far, Dapper Drake [6.06] is a lame duck as far as I'm concerned.  I have my family using it, but they don't have a dual-boot machine and they don't do admin chores on it. And I keep it simple when I fix things up for them.

My own personal experience with Dapper? I eagerly installed it the day the final release came out --after having been involved with alpha testing and submitting bug reports. But even with the Final Release I started having more problems than I ever did with Breezy or Warty. Attempting to put it on my laptop with an XP install hosed the entire MBR so I couldn't boot anything.[all partitions prepared, and SUSE 10.1 already running in a dual boot, with Dapper going to be #3.]

I rescued my XP and resolved to use Dapper only on my desktop machine. I was nicely installed and running fine for a while, until an update from Ubuntu mysteriously hosed my installation!

At that point I decided that Dapper was too buggy for me to waste time with. I have 4 other working Linux distros installed on my desktop that are not causing me headaches, and life is too short. . .

Anyway, I'd hate for you to get soured to Linux by your first experience. Try Mepis before you give up on it. Maybe Dapper will get fixed up in the near future, but for me, it's too high-maintenance. 

all the best,
SilverBear

---

### Post by navy_doc on 2006-07-24
> **alan yeates said:**
> Had exactly the same problem, turned it was from downloading mss core fonts, Ubuntu will not allow 2 things requiring root to work at the same time if one is a downloader is still working, which in my case was an unresolved download. Do use add/remove programs if possible rather than terminal or say easy ubuntu, but having said that I can't tell you how to get out of a bad download, since as you are finding you can't use most tools. I just reinstalled in frustration!

After reinstall did it work OK? What about after installing updates?

---

### Post by alan yeates on 2006-07-24
> **navy_doc said:**
> After reinstall did it work OK? What about after installing updates?
actually reinstalled several times, wrongly assumed updates were giving me problems, but it was an unresolved repository connection all the time! there seems no obvious way to close a connection once opened under sudo, even closing down the system does'nt work, a few seconds later the broken download starts again and again..... all fine now, my command line skills are also much developed!:D

---

### Post by navy_doc on 2006-07-24
> **SilverBear said:**
> My son & I fixed the plumbing soorer than I thought we would, so I'm back.

Navy-doc:
Don't get the idea that I'm bashing Ubuntu, because I've been a fan since Warty. But so far, Dapper Drake [6.06] is a lame duck as far as I'm concerned.  I have my family using it, but they don't have a dual-boot machine and they don't do admin chores on it. And I keep it simple when I fix things up for them.

My own personal experience with Dapper? I eagerly installed it the day the final release came out --after having been involved with alpha testing and submitting bug reports. But even with the Final Release I started having more problems than I ever did with Breezy or Warty. Attempting to put it on my laptop with an XP install hosed the entire MBR so I couldn't boot anything.[all partitions prepared, and SUSE 10.1 already running in a dual boot, with Dapper going to be #3.]

I rescued my XP and resolved to use Dapper only on my desktop machine. I was nicely installed and running fine for a while, until an update from Ubuntu mysteriously hosed my installation!

At that point I decided that Dapper was too buggy for me to waste time with. I have 4 other working Linux distros installed on my desktop that are not causing me headaches, and life is too short. . .

Anyway, I'd hate for you to get soured to Linux by your first experience. Try Mepis before you give up on it. Maybe Dapper will get fixed up in the near future, but for me, it's too high-maintenance. 

all the best,
SilverBear


If noone comes up with a solution in the next couple of days, I'll try a wipe and reinstall. 

I see a lot of potential in Ubuntu, so I want to give it a fair shake, but forehead vs masonary has its limits...;)   My BIOS gives me the option to boot to just about anything, and I put Ubuntu on a seperate HD, so I get the benefit of the decent spec of my desktop, but without putting my XP setup at risk. I learned my lesson from my last Linux experiment (Dual Boot on a partitioned HD) which went South, taking Windoze with it! 

Thanks for all the advise guys.

---

### Post by alan yeates on 2006-07-24
Don't wipe, just reinstall, we have an intelligent system here, not Windoze!

---

### Post by Ragazzo on 2006-07-24
What does command "hostname" print?

---

### Post by navy_doc on 2006-07-24
rob@:~$ sudo hostname
sudo: unable to lookup  via gethostbyname()
rob@:~$

---

### Post by osmith on 2006-07-25
these  guys  had the same problem and the thread is a little  one 

[http://www.ubuntuforums.org/showthread.php?t=188337](http://www.ubuntuforums.org/showthread.php?t=188337)

---

### Post by navy_doc on 2006-07-25
Problem solved!! I had change /etc/hosts OK, but had missed the note about changing /etc/hostnames also. Now that's done the problem has gone away. Many Thanks ::-D

---

### Post by Metacarpal on 2006-07-25
Glad you were able to get it sorted out, Doc! :)

---

