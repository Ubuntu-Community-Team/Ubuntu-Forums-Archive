---
title: "Questions"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by CheeseQueen452 on 2006-11-21
I'm considering switching to Ubuntu(I'm currently using Xandros but having problems), & I have some questions:

Is version 6.10 still a test version, or is it a final release? I'm downloading it as I type, but I won't install it if advised not to. I already have a CD for 6.0.6, so I can install that if needed.

I've read a little bit about Frostwire. How well does it work compared to Limewire? Is it more stable? When looking at the screenshots, I noticed it looks almost identical to Limewire, which appeals to me since I won't have to learn how to use it. It's available in the repository, correct? Or do I have to download the .deb?

Will I have to set up a user account, then log in as root to have full permissions for copying, deleting, & editing files? Can I auto-login as root?

I don't have time to try Ubuntu today, as I'm preparing to leave home tomorrow for the holiday weekend, but I may install it next week when I return.

---

### Post by gareththegeek on 2006-11-21
> Is version 6.10 still a test version, or is it a final release?

It's final release...> JUST ANNOUNCED: Ubuntu 6.10, code named Edgy Eft, has been released with many exciting new features. Visit the download page for CD images. from [www.ubuntu.com](www.ubuntu.com)

> Will I have to set up a user account, then log in as root to have full permissions for copying, deleting, & editing files? Can I auto-login as root?

In Ubuntu there isn't a root account. Usually you switch to superuser privileges using the sudo command, for example

$sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
Password: xxxx

You then won't need to enter your password again for a while (I think it's 15 minutes)

You can create a root account if you prefer and log in that way like most other linux distros. There is an auto log in feature but I wouldn't recommend autologging into the root account everytime for security reasons.

HTH G!

---

### Post by Amit Yaron on 2006-11-21
> **gareththegeek said:**
> 
In Ubuntu there isn't a root account. Usually you switch to superuser privileges using the sudo command, for example



Depends on how you have installed your Linux: if it was an "expert" installation you would have a root account and password.

---

### Post by steevk on 2006-11-21
I'm not sure how familliar you are with the Mac OS, but Ubuntu works like that.

When you try to do something that needs root privledges, it pops up a box asking for your account password, and then does it.

---

### Post by Henry Rayker on 2006-11-21
Edgy is, admittably, less stable than Dapper. Ubuntu releases 3 versions, then a LTS version. Each cycle, the first will probably be the least stable, the second being more stable and the third being even more stable. The LTS to cap off the cycle will be the most stable and will have support and updates for 3 years (for desktops), while the others have support and updates for 18 months (again, for desktops.

In my experience, Edgy is less stable in the Wifi arena (and I have heard that it is less stable with ATI video cards, I believe). If you use either of those features, I might stick to Dapper.

My suggestion, however, is to set up 2 5GB partitions; one for Edgy and one for Dapper. You can play around with the two, get to know them a little bit. Edgy has more "cutting edge" features, and that may be a selling point for you. This suggestion works best if you can keep your Xandros install around as well. That way you have a "safe point" to keep your files in, if Ubuntu decides to go crazy.

All that being said, welcome to the community. The choice is yours; if you don't have the time to test the two, then just pick one and go with it. If you have the time to invest, though, it may prove to be a good idea.

---

### Post by CheeseQueen452 on 2006-11-21
Thanks for the responses. Sounds like version 6.06 is the way to go for now, so I'll try that. Now, about user accounts..... As I understand it, I have to set up a user account & use the sudo command for superuser priviledges? Can't I simply log in as the superuser(administrator, if you will) just as I would a user account? I'm a little confused about this, & I could never quite understand the sudo commands. If I wanted to copy a file from one folder to another, & a message pops up saying I don't have the priviledges, what next? Will I be asked for the admin password, & the file is then copied? Do I log in as the admin, in order to copy the file?

During the installation, will it ask me to set up a user account, or will it automatically set up a superuser(root/admin) account? I would like to avoid having to use passwords & commands as much as possible.

---

### Post by Paul133 on 2006-11-21
Ubuntu will set up a root account, but you won't be root. While it is possible to log in as root, most people just use "sudo". As for how sudo works, you simply prefix your command with sudo. So, if I want to do something that requires permissions in the GUI, a box will pop up asking me to enter my password. If I want to do something I don't have permission for in the CLI, I must prefix the command with sudo. For example, ```
 sudo halt 
``` to shutdown.

---

