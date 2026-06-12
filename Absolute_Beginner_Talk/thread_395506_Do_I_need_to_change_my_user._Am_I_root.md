---
title: "Do I need to change my user. Am I root?"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Chilli Bob on 2007-03-28
OK, long story short. I bought a $50 pc on eBay and installed Dapper to see what's what. That was a few weeks back and I'm hooked. The problem is I didn't read much background on Linux before starting, so forgive me if I have this all completely wrong.

As I understand it, the name you put in at installation (in my case "rob") is given root privaleges, without actually being root. (as oposed to most other Linux). Now, I have copied all my files from my old M$ pc, and burned all my CD's to OGGs ( iRiver rocks by the way). Now I read that running day to day stuff as "root" isn't a great idea. What should I do? I see two options.

1. Create a new user, called, say, "admin" or "root", grant that user admin privileges, then remove the admin privs from "rob". or.....

2. Create a new user, say, "chilli", with normal priviliges and copy all my "rob" folders into this new home folder.

I tried option one, but couldn't log in as the new name because Ubuntu said that the new home folder didn't exist, even though I could clearly see it when logged in as "rob".

I tried option 2, but couldn't move the folders due to permision problems.

Can anyone suggest what to do, or have I got it all wrong and can run as "rob" with no danger to the system.

Option three is to just burn my files to disk and do a new install of Feisty in a few weeks time.

Thanks in advance. Please be kind to noooobs!

---

### Post by Zzl1xndd on 2007-03-28
I wont say im an expert on this subject but as I understand it there is a second hiden account that is root and the main account only gets root when using Sudo commands.

---

### Post by Arby on 2007-03-28
You don't need to worry about the security of your everyday 'rob' user. I think you have misunderstood slightly. You haven't got it completely wrong, just missed a few finer points.

When you create the initial user account the password you give it can be used to assume root privileges when required. But that user does not run as root all the time.  Your account named 'rob' will run as a standard user account most of the time. You only assume root privileges temporarily when you need them. To do this you would prefix your command with 'sudo' which stands for 'super user do', like so ```
sudo some_command
``` In this case 'some_command' is executed with root privileges. Prior to typing sudo you are working as regular user rob, once that command has completed you go back to being regular user rob. It's only that one command that runs as root.

In short, you don't need to worry about creating extra accounts you can use the regular account 'rob' quite safely.


I hope that clarifies things a bit. You may also find this useful [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).

Arby

---

### Post by Catsworth on 2007-03-28
That's it exactly (I think).

*root *is an account on the system that (in the normal course of things) you will have no access to.

Your account (*rob*) can temporarily act with the same level of priviledge as root by using the *sudo* (or *gksudo* for graphical applications) command in the terminal when issuing commands, or by entering your password when asked to in any graphical interface that requires root priviledges to run (Synaptic for example).

---

### Post by Chilli Bob on 2007-03-28
WOOHOO! Thanks everybody! For a moment there I thought I would have to read the manual! :biggrin:

---

### Post by Catsworth on 2007-03-28
> **Chilli Bob said:**
> WOOHOO! Thanks everybody! For a moment there I thought I would have to read the manual! :biggrin:

Oh yeah, and don't forget to RTFM!!!  :lolflag:

---

