---
title: "/home partition and clean install"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by R_U_Q_R_U on 2007-07-06
I am planning on doing a clean Fiesty install on my new Dell laptop. The plan is to have three partitions: /, /home and /swap. I have read that it is better to do clean installs when each new Ubuntu release comes out rather than an upgrade.

If I have a separate /home partition, will a clean install (of a new release) maintain all my custom settings? Or, is it just to keep my data files safe. Specifically, where can I learn what is maintained and what is overwritten in the / partition as compared to what is saved in /home. For example, is wallpaper stored in /home or / ?

---

### Post by kosmic on 2007-07-06
When Installing a new version of ubuntu choose the same /home partition for your new install but DO NOT CHOOSE Format partition...

In the end you will have a new ubuntu version and all your /home content intact :)

---

### Post by Matakoo on 2007-07-06
> **R_U_Q_R_U said:**
> 
If I have a separate /home partition, will a clean install (of a new release) maintain all my custom settings? Or, is it just to keep my data files safe. Specifically, where can I learn what is maintained and what is overwritten in the / partition as compared to what is saved in /home. For example, is wallpaper stored in /home or / ?

Most if not all of your settings will be saved. Wallpapers, security certificates, color scheme, Firefox bookmarks, e-mails, contact lists, game settings, you name it. On top of my head, I can not think of an exception to that. Well, if you have say a custom soundtheme and the paths to the soundfiles are something like /usr/share/sounds/, those will be lost but otherwise you're safe if you don't accidentally reformat /home during install.

All that being said, I don't think it's necessary to do a clean install. An upgrade is in most cases just as good. Maybe not if you've used pre-releases or the system is in a mess anyway...but if properly maintained, a clean install shouldn't be necessary. The only time it really is necessary is if you switch from 32bit to 64bit. 

But if you now only have a / partition, it probably is easier to do a clean install. For a workstation, I say you've chosen the right partition scheme. /, /home, and swap should be sufficient for that. Maybe adding /usr as well and having it mounted read-only except when installing things, but that might be a bit overkill. I'd do that for a server (as well as a separate /var partition), but I'm not following that suggestion on my own workstation.

---

### Post by R_U_Q_R_U on 2007-07-06
Thanks for all the great information...

> **kosmic said:**
> When Installing a new version of ubuntu choose the same /home partition for your new install but DO NOT CHOOSE Format partition...

In the end you will have a new Ubuntu version and all your /home content intact :)

When doing a clean install, when I get to the partitioning part of the install routine do I accept the defaults if I have a separate /home partition? I am just a little fuzzy about how to do a clean install with the partitioning scheme setup this way.

Thanks:confused:

---

### Post by az on 2007-07-06
> **R_U_Q_R_U said:**
> I am planning on doing a clean Fiesty install on my new Dell laptop. The plan is to have three partitions: /, /home and /swap. I have read that it is better to do clean installs when each new Ubuntu release comes out rather than an upgrade.?

Not true.  It's better to dist-upgrade from one release to another.  However, if you have lots of non-official software (software from sources other than Ubuntu), then it can take some skill to make sure that software keeps working or doesn't interfere with the rest.

> **R_U_Q_R_U said:**
> 
If I have a separate /home partition, will a clean install (of a new release) maintain all my custom settings? Or, is it just to keep my data files safe. Specifically, where can I learn what is maintained and what is overwritten in the / partition as compared to what is saved in /home. For example, is wallpaper stored in /home or / ?

It depends on the applications.  Most desktop apps keep a base config in /etc, but custom settings are saved in /home.  Some apps will only use /etc, but those are either system utilities or older applications.

Your user cannot write to any other directory other than the home drive, so any settings that are saved as your user has to be kept in /home.

Some apps don't do well with running a differnt version of the config files in your home drive.

---

### Post by Matakoo on 2007-07-06
> **R_U_Q_R_U said:**
> When doing a clean install, when I get to the partitioning part of the install routine do I accept the defaults if I have a separate /home partition? I am just a little fuzzy about how to do a clean install with the partitioning scheme setup this way.

I would use the manual partitioning, and take a good thorough look at the partitioning table to see if the values look like they should. Whatever you have in /home is most likely things you do not want to lose, so I at least would be very reluctant to accept the defaults. Call me paranoid...

How large a harddrive do you have? It would be easier to help out with reasonable estimates on how large the different partitions should be.

---

### Post by Matakoo on 2007-07-06
> **az said:**
>   However, if you have lots of non-official software (software from sources other than Ubuntu), then it can take some skill to make sure that software keeps working or doesn't interfere with the rest.

I'm not sure I agree with that. If you've compiled from source, yes. Or used .deb files created with checkinstall. Proper debs, whether downloaded and installed with dpkg -i or using a third party repo, well, they usually work fine after a dist-upgrade. Well, assuming the dependency rules were written correctly that is. I never had a problem with it anyway. YMMV.

Then again, I'm no stranger to compiling from source and fixing things when/if it breaks. Which it rarely does :)

---

### Post by dptxp on 2007-07-06
One should always have a separate data partition, it can be /home. If you ever have to reinstall the OS, your data including downloaded stuff that you normally save to /home OR data partition shall remain undisturbed.

So a minimum of 3 partitions including SWAP is suggested.

---

### Post by R_U_Q_R_U on 2007-07-06
> **Matakoo said:**
> I would use the manual partitioning, and take a good thorough look at the partitioning table to see if the values look like they should. Whatever you have in /home is most likely things you do not want to lose, so I at least would be very reluctant to accept the defaults. Call me paranoid...

How large a harddrive do you have? It would be easier to help out with reasonable estimates on how large the different partitions should be.

Its a 100 GB SATA drive with 2 GB RAM. I plan to do 10 GB for root (/), 2 GB for Swap and the  remainder  for /home.  It was suggested to also  setup  a /usr partition but I am not sure why  I would do so  or what  to store there. Is 10 GB too large for the root?

---

### Post by az on 2007-07-06
> **dptxp said:**
> One should always have a separate data partition, it can be /home. If you ever have to reinstall the OS, your data including downloaded stuff that you normally save to /home OR data partition shall remain undisturbed.

So a minimum of 3 partitions including SWAP is suggested.

No.  The installation process should be as simple and as foolproof as possible.  Anyway, there are much simpler ways to back up your data.  And if your hard drive dies, it will usually affect every partition on it.

> **R_U_Q_R_U said:**
> Its a 100 GB SATA drive with 2 GB RAM. I plan to do 10 GB for root (/), 2 GB for Swap and the  remainder  for /home.  It was suggested to also  setup  a /usr partition but I am not sure why  I would do so  or what  to store there. Is 10 GB too large for the root?

Where did you hear this?  You don't need a seperate /usr partition.

If you're at all concerned about wasting space, or running out of space because of partitioning, then just leave everything on the / partition and you will have avoided that problem.

---

### Post by R_U_Q_R_U on 2007-07-06
> **az said:**
> Where did you hear this?  You don't need a seperate /usr partition.

See message #3 in this thread.

---

### Post by R_U_Q_R_U on 2007-07-06
> **az said:**
> No.  The installation process should be as simple and as foolproof as possible.  Anyway, there are much simpler ways to back up your data.  And if your hard drive dies, it will usually affect every partition on it.

Point taken. That is why I asked this question. Many of the Ubuntu resources I have visited suggested the three partition setup. I am trying to figure out if I should bother, or as you say, keep it simple with just one partition. Other than a physical hard drive failure, I see some merit in separating the data from the OS. But as you mention, it is simple to back up data, either to CD, or another hard drive.

---

### Post by Matakoo on 2007-07-06
> **R_U_Q_R_U said:**
> Its a 100 GB SATA drive with 2 GB RAM. I plan to do 10 GB for root (/), 2 GB for Swap and the  remainder  for /home.  It was suggested to also  setup  a /usr partition but I am not sure why  I would do so  or what  to store there. Is 10 GB too large for the root?

No, mine is even bigger (20 gig in my case). My swap is too btw, although both are bigger than they really need to be. But I had some hd-space to waste...well, rather that I thought it's better to waste some space rather than finding out later that you're running out of room on /. Can be fixed for sure, but it's a bother I'd rather not face if I can avoid it.

10 gig for / is more than sufficient in most cases, and you're not very likely to run out of room with that. I would have about 3 gig free using that size, and that is not likely to change with everything I need already installed. Add a couple of gig if you want to play it safe.

A separate /usr is not necessary, although it has benefits in some cases. For a home/private desktop machine you can safely ignore doing that.

Strictly speaking, it is not necessary having /home on a separate partition either but I would still recommend doing that. If nothing else, because I think /home should always be mounted using the noexec flag which, of course, isn't possible if you just have one huge partition. Even better to have /home on a separate drive if at all possible.

I wouldn't use anything less than three partitions. Swap, /, and /home.

---

### Post by UnixAnt on 2007-07-06
If you come from an old school *nix background, then you will probably have about 10 partitions on your local disk, for a variety of reasons.  I go to client sites to install Linux clusters as part of my job, and as a very rough example, I would generally partition something like this:

(Drive is 36GB, Physical memory 8Gb)

/     1gb
/boot     100mb
/home   10gb
/var     2gb
/usr     10gb
/tmp    1gb

Swap:

Generally, you will want a maximum of 4gb for systems of 4gb - 16gb and above

For systems with 1gb - 2gb memory I would use 2gb swap space

As far as swap is concerned, the less you can get away with the better as far as I am concerned.  Remember, the system will only use swap space when it runs out of physical RAM.  If you assign loads of cheap, low-performance disk (compared to the performance of RAM) you will simply be masking a problem you have with capacity - ie, you don't have enough memory for the box, so buy some more.

The absolute minimum I *personally* would use on a desktop/laptop would be:

/
/boot
/home
/var
swap

I would definitely keep / separate from /home and /var at all costs.

---

### Post by R_U_Q_R_U on 2007-07-06
> **UnixAnt said:**
> If you come from an old school *nix background, then you will probably have about 10 partitions on your local disk, for a variety of reasons. ...

I would definitely keep / separate from /home and /var at all costs.

OK, as this forum section is for noobes, and I am no Linux or Unix guru, can you please explain why I would need /var on a separate partition?

Thanks.

---

### Post by forrestcupp on 2007-07-06
I agree with az.  The simpler the better.  You're better off going with the defaults, which is usually 2 partitions.  One for swap, and one for everything else.  The reason I like this is because you never know how much space you're going to need for /home and for everything else.  If it's all on one partition, you don't have to worry about how much space you'll need.

It's pretty easy to back up your /home folder when you do a clean install, then just reload your original /home data to your new install.  That's what I do.

---

### Post by UnixAnt on 2007-07-06
> **R_U_Q_R_U said:**
> OK, as this forum section is for noobes, and I am no Linux or Unix guru, can you please explain why I would need /var on a separate partition?Thanks.

Certainly!  Out of all the mount points, the one most likely to give you grief without any intervention from the user is /var.

This is because /var holds all the system logs which are constantly being appended, for example /var/log/messages or /var/log/syslog.  Do a tail -f on either of these 2 files, sit back and watch them grow...

Now admittedly, this isn't going to make much difference if you are a casual user of your Linux machine, but if the box is left on all the time then these files will grow out of control relatively quickly.  Yes, of course you can trim them down and write simple cron jobs to clean the logs every month/week/night, but its definitely something to keep in mind.

In Unix/Linux, if the / filesystem hits 100% its usually bad news.  Having /var on a separate partition can lessen the impact of a sudden surge in the log files, which may in time lead to a lack of disk capacity.

If this is too much info for new users - my apologies.  Its definitely something to keep in mind though, and definitely a good practice to get into: isolate your potential problem partitions and keep them separate to / ;)

---

### Post by R_U_Q_R_U on 2007-07-06
> **UnixAnt said:**
> Certainly!  Out of all the mount points, the one most likely to give you grief without any intervention from the user is /var.

This is because /var holds all the system logs which are constantly being appended, for example /var/log/messages or /var/log/syslog.  Do a tail -f on either of these 2 files, sit back and watch them grow...

Now admittedly, this isn't going to make much difference if you are a casual user of your Linux machine, but if the box is left on all the time then these files will grow out of control relatively quickly.  Yes, of course you can trim them down and write simple cron jobs to clean the logs every month/week/night, but its definitely something to keep in mind.

In Unix/Linux, if the / filesystem hits 100% its usually bad news.  Having /var on a separate partition can lessen the impact of a sudden surge in the log files, which may in time lead to a lack of disk capacity.

If this is too much info for new users - my apologies.  Its definitely something to keep in mind though, and definitely a good practice to get into: isolate your potential problem partitions and keep them separate to / ;)

Thanks for the info -- but I don't think that will be an issue for me right now. The machine I am setting up is a new Dell 1521 laptop. I am removing the Vista 80 GB drive and install  a new 100 GB SATA drive. I think this provide plenty of room for general computing use.

---

### Post by Old Pink on 2007-07-06
I've upgraded from 6.06 to 6.10 and then again to 7.04 with absolutely no problem, there's no real need to reformat, just backup and go for the upgrade. :)

---

### Post by R_U_Q_R_U on 2007-07-06
> **Old Pink said:**
> I've upgraded from 6.06 to 6.10 and then again to 7.04 with absolutely no problem, there's no real need to reformat, just backup and go for the upgrade. :)

That seems a popular way to maintain the system. I did read about other suggestions on partitioning here:
[http://www.easy-ubuntu-linux.com/ubuntu-installation-606-7.html](http://www.easy-ubuntu-linux.com/ubuntu-installation-606-7.html)

I am still undecided. As I started this thread I was leaning toward a separate /home partition. But many point out there is no need to do clean installs so...

---

### Post by az on 2007-07-06
> **Matakoo said:**
> 
Strictly speaking, it is not necessary having /home on a separate partition either but I would still recommend doing that. If nothing else, because I think /home should always be mounted using the noexec flag which, of course, isn't possible if you just have one huge partition. 

Why?

So if a user wants to download an run something, they now have to become root?  That's not safe!

> **R_U_Q_R_U said:**
> OK, as this forum section is for noobes, and I am no Linux or Unix guru, can you please explain why I would need /var on a separate partition?


You don't need to on a desktop system.  Your logs are archived regularly and will not take up that much space.  If you are running a server, one way to crash it is to generate a lot of error messages that will end up filling up the drive.  On a webserver, it is trivial to generate more errors per minute than can be archived and so....

I can't think of a useful reason to have a separate /usr partition either...

---

### Post by Matakoo on 2007-07-06
> **az said:**
> Why?
So if a user wants to download an run something, they now have to become root?  That's not safe!

They have to become root to install anyway, since a normal user only have write-access to their own home. Sure, .run files can install things using $HOME as the starting-point but all things considered there are not all that many programs that do not require root-access at some point to install. Especially not if you only take deb-files into consideration.

But why? Consider scripts for instance. They can cause a lot of havoc if not properly checked and debugged. They should not be allowed to run by simply clicking on one, whether on the desktop or in an e-mail attachment. Which could happen in a /home where you're allowed to run programs arbitrarily. Reminds me of what Outlook Express can do...

Malicious websites could take advantage of it too. If nothing can run from /home, it's harder to compromise the system in that way. It requires the user to actively do something to run whatever it is.

As far as I'm concerned, having /home allowing you to execute programs is almost as dumb as being logged in as root constantly. And I can't think of anything that would be suitable to save in your home-directory that need to have the x-flag set.

> **az said:**
> I can't think of a useful reason to have a separate /usr partition either...

Mount it read-only and it's harder for hacker-wannabes to compromise the system binaries (as in replacing a system command with a malicious one). Okay, only a small step toward a more secure system but still.  And for bigger systems, exporting /usr over NFS - and having it RW in such a case would be a really bad idea. That last thing isn't really applicable to a home system though...

And besides, during normal course of events (in other words, simply using the computer) it is not necessary to have /usr writable in the first place. Except when software is installed or upgraded. Otherwise it isn't supposed to change.

Okay, I'll stop now...

---

### Post by UnixAnt on 2007-07-07
> **Matakoo said:**
> As far as I'm concerned, having /home allowing you to execute programs is almost as dumb as being logged in as root constantly. And I can't think of anything that would be suitable to save in your home-directory that need to have the x-flag set.

Erm...shell scripts you have just written and are in the process of testing?

By its very nature, the OS makes it very difficult for unprivileged users to trash the system with gay abandon.  At worst, the most damage you could do is hose your own /home directory.  The fact that you can run a malicious application from your /home dir is irrelevant when you consider that you would be executing the code as an unprivileged user anyway.  This means the code would be restricted to damaging only the directory structure which the user has write access to.

---

### Post by dptxp on 2007-07-07
Everyone has his/her own opinion on partitions. It is for the user to understand the pros and cons. A separate /home or data partition does not complicate the installation in any way. With the huge space we have on HDDs, 1 or 2 GB here and there should not be a matter of concern.

You will feel the heat when you have to reinstall the OS or install another OS without separate data partition.

But again, personal choice.

---

### Post by R_U_Q_R_U on 2007-07-07
> **dptxp said:**
> Everyone has his/her own opinion on partitions. It is for the user to understand the pros and cons. A separate /home or data partition does not complicate the installation in any way. With the huge space we have on HDDs, 1 or 2 GB here and there should not be a matter of concern.

You will feel the heat when you have to reinstall the OS or install another OS without separate data partition.

But again, personal choice.

Some of the discussion in this thread goes way beyond the knowledge base of new users. However, from a general computing best practices viewpoint I still think separating data from the OS makes sense.

So, I am going to go with three partitions: /, /home and /swap and leave it at that.

Thanks for all the options and information!

---

### Post by Matakoo on 2007-07-07
> **UnixAnt said:**
> Erm...shell scripts you have just written and are in the process of testing?

Not really necessary, although convenient. My own preferred method of doing that is:

sudo mkdir /scripts (or wherever you want to store them)
sudo chown user:user /scripts
chmod 700 (or whatever is deemed appropriate for the system/directory in question, world should be no access though)

Edit the script, then

cp ~/testscript.sh /scripts
chmod u+x /scripts/testscript.sh
/scripts/testscript.sh

Admittedly, a few extra steps but worth it IMO. You still need to be careful in debugging the scripts though :)

But to each his own, as long as they are aware of the ramifications of doing things in that way or this way. There's nothing like "one size fits all" after all.

> **UnixAnt said:**
> By its very nature, the OS makes it very difficult for unprivileged users to trash the system with gay abandon.  At worst, the most damage you could do is hose your own /home directory.  The fact that you can run a malicious application from your /home dir is irrelevant when you consider that you would be executing the code as an unprivileged user anyway.  This means the code would be restricted to damaging only the directory structure which the user has write access to.

All true, but that would be a small comfort at best. The most valuable asset on any system with interactive users are, after all, the users data. That's why I don't agree that it's irrelevant that it's only possible for the malicious code to wipe out the user's data. The user in question would in all likelihood consider that a disaster worse than having to reinstall the system. Sure, we all should have backups but in my experience, most people don't.

---

### Post by Matakoo on 2007-07-07
> **R_U_Q_R_U said:**
> Some of the discussion in this thread goes way beyond the knowledge base of new users. 

Yeah, sorry about that. I'll try not to get carried away in the future...

---

### Post by az on 2007-07-07
> **Matakoo said:**
> They have to become root to install anyway, since a normal user only have write-access to their own home. Sure, .run files can install things using $HOME as the starting-point but all things considered there are not all that many programs that do not require root-access at some point to install. Especially not if you only take deb-files into consideration.

I think that there are plenty of example of people installing things to their home drives.  It is a lot more safe to just to it that way, instead of having to become root to run an install script.  Debs are notwithstanding, since they don't touch /home.

> **Matakoo said:**
> 
But why? Consider scripts for instance. They can cause a lot of havoc if not properly checked and debugged. They should not be allowed to run by simply clicking on one, whether on the desktop or in an e-mail attachment. Which could happen in a /home where you're allowed to run programs arbitrarily. Reminds me of what Outlook Express can do...

Malicious websites could take advantage of it too. If nothing can run from /home, it's harder to compromise the system in that way. It requires the user to actively do something to run whatever it is.

As far as I'm concerned, having /home allowing you to execute programs is almost as dumb as being logged in as root constantly. And I can't think of anything that would be suitable to save in your home-directory that need to have the x-flag set.

I think you need a balance.  If you try to prohibit too many things, the user will just log in as root and bypass the restrictions.  I think sudo priviledge escalation is good example of how to balance the use of restricted permissions with user friendliness.

> **Matakoo said:**
> 
Mount it read-only and it's harder for hacker-wannabes to compromise the system binaries (as in replacing a system command with a malicious one). Okay, only a small step toward a more secure system but still.  And for bigger systems, exporting /usr over NFS - and having it RW in such a case would be a really bad idea. That last thing isn't really applicable to a home system though...

And besides, during normal course of events (in other words, simply using the computer) it is not necessary to have /usr writable in the first place. Except when software is installed or upgraded. Otherwise it isn't supposed to change.

Okay, I'll stop now...
Again, if you are on a network, or have dozens of users, sure, make /usr read-only (do you really need to put it on a seperate partitoin for that?)   But for the majority of deaktop users who will be installing software themselves, it's an annoyance and a false sense of security.

> **UnixAnt said:**
> This means the code would be restricted to damaging only the directory structure which the user has write access to.

Vulnerabilities are things that can take over other processes, or trick them into doing things.  You don't have to be root to cause damage.  I just don't think making home noexec or /usr RO will help all that much in most situations - it's only another hoop to jump and is meaningless.


> **dptxp said:**
> Everyone has his/her own opinion on partitions. It is for the user to understand the pros and cons. A separate /home or data partition does not complicate the installation in any way.

Yes it does.  The default way only asks the user to consider one thing:  How much hard drive space to dedicate to Ubuntu.  The manual way is way more involved, and although I'm not saying that nobody should do it, it should not be the default since you don't need to know the "under the hood" issues to run Ubuntu safely and happily.  Not to mention the hassle of going back and readjusting the partition sizes if you make a mistake.

> **dptxp said:**
> 
You will feel the heat when you have to reinstall the OS or install another OS without separate data partition.

You're going to have to backup your data anyway...  What happens if your drive dies?  You should not rely on your data partition as a backup.

> **dptxp said:**
> 
But again, personal choice.

Yes, it is.  And this discussion is about pointing out the pros and cons.  Every one is entitled to decide for themselves.

> **R_U_Q_R_U said:**
> Some of the discussion in this thread goes way beyond the knowledge base of new users.

> **Matakoo said:**
> Yeah, sorry about that. I'll try not to get carried away in the future...

Discussions are beneficial to everyone.  The more info, the better.

---

### Post by R_U_Q_R_U on 2007-07-07
> **az said:**
> 

Yes it does.  The default way only asks the user to consider one thing:  How much hard drive space to dedicate to Ubuntu.  The manual way is way more involved, and although I'm not saying that nobody should do it, it should not be the default since you don't need to know the "under the hood" issues to run Ubuntu safely and happily.  Not to mention the hassle of going back and readjusting the partition sizes if you make a mistake.



OK, so on my 100 GB drive is 10 GB sufficient for /? My plan is:

/ 10 GB
/SWAP 2 GB*
/home ~86 GB

I don't think I will have to resize with this layout.

* Machine has 2 GB RAM.

---

### Post by dptxp on 2007-07-08
> **R_U_Q_R_U said:**
> OK, so on my 100 GB drive is 10 GB sufficient for /? My plan is:

/ 10 GB
/SWAP 2 GB*
/home ~86 GB

I don't think I will have to resize with this layout.

* Machine has 2 GB RAM.

PERFECT.

---

