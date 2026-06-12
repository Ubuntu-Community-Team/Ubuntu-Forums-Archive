---
title: "user permissions"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-24
how can i give my user account administrative permission for doing anything?  thanks.

---

### Post by PeterJS on 2008-01-24
> **Matt26 said:**
> how can i give my user account administrative permission for doing anything?  thanks.

If you don't already have admin privilages you can't give them to yourself, it'd be rather poor security otherwise, eh?

But you probably already have admin rights, open up a terminal and run:
```

groups

```
This will tell you what groups your account is in, if you're in the admin group you have admin rights.

---

### Post by Rhubarb on 2008-01-24
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

By default ubuntu does not have a root account.
If you want to do anything that requires root, ubuntu will prompt you to enter your password in.
For all other cases, in the terminal, type in **sudo <command>**.

---

### Post by spiderbatdad on 2008-01-24
assuming you are the admin of the computer, you can set user privileges graphically: System>>Administration>>Users and Groups. Click on the user name, choose properties, then User Privileges. Under the advanced tab, there is an option for assigning the user to groups, too. Root is one of them. IDK if that would work...it certainly wouldn't be smart, unless your goal is to break your system asap. You can also create a root account for your user like:```
su root
``` I believe.     There is no reason for that, though,  because you can make your user root, like:```
sudo su
``` Or just use sudo as needed.

---

### Post by Matt26 on 2008-01-24
is there a way to override these prompts so i can allow for any changes to be done without intervention?

---

### Post by mr_ed on 2008-01-24
Yes, of course, but you remove all your "shoot your foot" protection.

Run "sudo visudo" and changing
%admin ALL=(ALL) ALL
to
%admin ALL=(ALL) NOPASSWD: ALL

should do the trick.

---

### Post by Matt26 on 2008-01-24
thanks for the info- i am having an issue with creating folders and editing the name of a new ext3 partition that i have recently created.. every time i do one of these tasks i get the error message that i cannot do this access is denied- should i not be able performs these functions without being a root user?

---

### Post by PeterJS on 2008-01-24
If it's outside your home directory, or something system wide you need to be root to do. Linux has a real permission system, users can't just do what ever they want, administrative users can, but they have to explicitly request elevated privileges through sudo.

---

### Post by Matt26 on 2008-01-24
i have changed the main group for my user account under advanced to both root and admin and still cannot make the changes.. shouldn't this work?

also, what is the default main group a user account is assigned- i can't remember what is was originally before i changed it.

---

### Post by PeterJS on 2008-01-24
You can only have one main group so it's either admin or root, but not both. The default group name is the same as your user name.

And  no amount of messing with groups will ever make an account root or not root. The defining characteristic of the root account is being UID 0.

---

### Post by Matt26 on 2008-01-24
sorry, more specifically- i have changed the user account main group to admin and tried making these changes which yielded an error message saying i could not do this, and then changed the main group to root and tried again but got the same result- i am assuming that if you change the main group to one of these it will allow that user account to have administrative privileges?

---

### Post by PeterJS on 2008-01-24
No, just being in the admin group gives you administrative privilages. Administrative privilages lets you use sudo to temporarily grant root privilages.

But to actually BE ROOT, has nothing to do with what group a user is in and everything to do with the account's UID. UID 0 is root. Any account that is not UID 0 is not root and never will be root, and there's only one account per UID, so the only account that is root is root.

---

### Post by Matt26 on 2008-01-24
ok thanks- so i guess my next question is, what is the easiest way for me to perform these tasks (create folders on new partitions and rename partitions) without having to issue sudo commands at a terminal window or create a new user account with the proper privileges?

---

### Post by PeterJS on 2008-01-24
> **Matt26 said:**
> ok thanks- so i guess my next question is, what is the easiest way for me to perform these tasks (create folders on new partitions and rename partitions) without having to issue sudo commands at a terminal window
You can run:
```

sudo bash

```
To launch a shell with root privilages, and anything done from that shell will have root permissions. For a graphical file browser you can run:
```

gksudo nautilus

```
> 
or create a new user account with the proper privileges?
I guess I wasn't clear on this, the only account that has those privileges is the account that has a user ID of 0, you can't create an account that has a userID of 0 because one already exists and it's the root account. I guess you could rename the root account, change it's home directory and login in to that. But at the end of the day that amounts to logging in as root which is a really bad idea.

Have you read:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
and
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Matt26 on 2008-01-25
what is the difference between these 2 commands in terms of what each does?  i am still learning the basics of linux commands so i don't completely understand how these both work.  thanks.

---

### Post by PeterJS on 2008-01-25
> **Matt26 said:**
> what is the difference between these 2 commands in terms of what each does?  i am still learning the basics of linux commands so i don't completely understand how these both work.  thanks.

Sudo presents it's password prompt on standard output, ie terminal text, and expects a response standard input, keyboard input in the terminal. Since any time bash is going to be running you can safely guarantee there will be a terminal for it to run on, it's reasonable to ask for a password on the terminal.

Gksudo on the other hand pops up a graphical window to ask for the password, and expects a response in that window, cutting out the requirement to have a terminal open to receive input from, making it suitable for using with the run dialog, or a menu entry.

You can also run graphical apps with sudo, you just have to open a terminal first and leave it open the whole time the program is running. There's no technical reason you can't do this, it's just it clutters things up with un-needed windows, and there's a perfectly good tool available to avoid the clutter so why not use it.

---

### Post by Matt26 on 2008-01-25
thanks for all the information- i still don't fully understand the operations and limitations of Ubuntu when it comes to simple tasks like renaming a volume label or creating a folder that is not within your user directory- so why is there an option when you right-click on a volume label to rename it if you can't even use it?  isn't there a way to perform these tasks from the GUI without using terminal commands?

---

### Post by PeterJS on 2008-01-25
> **Matt26 said:**
> thanks for all the information- i still don't fully understand the operations and limitations of Ubuntu when it comes to simple tasks like renaming a volume label or creating a folder that is not within your user directory
Think about it this way, if a malicious user or program was loose on your system would you want them doing those things? If there was a second user on the machine would you want them making those sort of changes when you're not paying attention, something as simple as changing a partition label will change where it automounts, which could break symlinks or scripts. Many of the security features aren't obvious in a single user environment, but Unix, and Linux by extension isn't a single user operating system, it's a multi-user system, designed as such, and it's merely coincidental that there's only one user in this case.
> 
- so why is there an option when you right-click on a volume label to rename it if you can't even use it?  isn't there a way to perform these tasks from the GUI without using terminal commands?
I assume the option is there because Nautilus can be run with elevated privileges, where it would be applicable. And absolutely you can run nautilus (or any other program, that's how the menu entry for synaptic works) with elevated privileges with out resorting to the command line. Press Atl+F2 to get to the run dialog and use:
```

gksudo nautilus

```
If you find yourself doing that often enough you could put a launcher on the top panel or a menu entry that would run nautilus as root.

---

### Post by Matt26 on 2008-01-25
what is nautilus- is this the desktop GUI?  maybe i am confusing this with GNOME...

---

### Post by PeterJS on 2008-01-25
Gnome is the whole suite, the panels, desktop, menus, and a bunch of the configuration tools. Nautilus is just the file browser, pretty much everything in the places menu launches nautilus in one form or another.

---

### Post by STW on 2008-01-29
Hi. I am actually having the same problem as what Matt26 is having.
I installed a new 500gb hard disk, and use Partition Editor (GParted) to partition it into 2 partitions.

There's no option in Partition Editor which allow me to mount the newly created partitions  (unlike what I've read in other posts), so I ended up using Nautilus to mount them.

After I mounted the 2 new partitions, I got "disk" and "disk-1" as their name.
Now I want to change the name of this newly mounted partition to something that I want (e.g. Data Disc, etc...). I right-click on the empty space in Nautilus, chose <Properties> and under the Name column, I tried to change it from "disk" to a new name say "Data Disc", and I got this error message:

"The item could not be renamed"
"You do not have permissions necessary to rename "disk".
 

Apparently the owner of these 2 newly mounted partitions are ROOT, and thus I couldn't rename them. But since I am the one who mounted the partitions, shouldn't I be the owner, rather than ROOT?

I tried using the command "gksudo Nautilus", and it opened up the Nautilus window and logged me in as ROOT, but under that Nautilus windows, I couldn't find the 2 newly mounted partitions -- "disk" and "disk-1", so I still can't rename them.

Please advise what else can I do?
Thanks.

---

### Post by Matt26 on 2008-01-29
i have run into all the same symptoms you are describing (minus GParted not giving you the option to mount) and have been trying to find answers for days now on these same issues.

what i found to work for changing the name of a volume is to use the command e2label (changes the label of an existing ext2/ext3 filesystem) as such:

- open Terminal window and type **sudo e2label /dev/sdb1 MyFiles**
- when prompted enter your user account password

this is only an example and your usage of the command will most likely differ- the **/dev/sdb1** portion of the command refers to the name of the hard drive as it is found under GParted, then the **MyFiles** portion if the new label to give it- i had to unmount then remount my volume for this to update, and ran into an error the last time i did this and the volume wouldn't unmount properly, but rebooting seemed to do the trick.

unless i am mistaken, you also cannot have spaces in your label- i tried this and got an error message, so i don't know if you can have spaces or not- can anyone confirm this?

---

