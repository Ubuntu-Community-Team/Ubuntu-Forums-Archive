---
title: "[SOLVED] are you root"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by Johnny3 on 2007-10-01
I get this. When I type it in Terminal. I am using Ubuntu 7.04.
johnny@johnny-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
johnny@johnny-desktop:~$ apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
johnny@johnny-desktop:~$ 

This is the first time I have been asked if I was root. I think I am.
Thanks Johnny3 Gainesville.
Ps I am trying to do Maintenance on this page

[https://help.ubuntu.com/community/AptGetHowto?highlight=%28CategoryDocumentation%29](https://help.ubuntu.com/community/AptGetHowto?highlight=%28CategoryDocumentation%29)

---

### Post by jalanbuntu on 2007-10-01
Use "sudo" if you want to excute a command with root access right.

For example you should type "sudo apt-get update" then type in your password

---

### Post by mcduck on 2007-10-01
No, you are not root. The root account is not enabled by default in Ubuntu (and you don't even need to enable it.). Just use 'sudo' to do things as root user.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

So, for those commands you should use 'sudo apt-get update' and 'sudo apt-get upgrade'. Sudo will then ask for your password to confirm that you are a user with privileges to do such tasks. By default the first user created has these privileges.

---

### Post by Arwen on 2007-10-01
You type "sudo" before all these commands,just like:
> sudo apt-get update and give your root password.
You temporarily become root,it's not safe to login as root all the time but you'll be asked to do so when modifying essential parts of your system.You log in as a normal user.


..and 2 in here are faster typers than me:-P:-P

---

### Post by Cyvros on 2007-10-01
Because of how Ubuntu works, you'll need to do commands like **apt-get** with **su -c**, **sudo** (which I personally prefer) or **gksu** (graphical version of sudo).

So **apt-get update && apt-get upgrade** becomes **sudo apt-get update && sudo apt-get upgrade**.

Hope that helps.

**Edit** Heh. I was beaten by three people in fifteen seconds. :D

---

### Post by PmDematagoda on 2007-10-01
You have to get the root privileges to do something like that. Just put sudo in front of the command you want to give sudo abilities  to, enter your account password(You won't see the password being written) and press enter. Use this with caution as you can break or make your system with this.:)

Whoa, seems like everyone was in a big race to solve this thread, shows you the speed of response of Ubuntu Forums :D

---

### Post by jalanbuntu on 2007-10-01
> **PmDematagoda said:**
> You have to get the root privileges to do something like that. Just put sudo in front of the command you want to give sudo abilities  to, enter your account password(You won't see the password being written) and press enter. Use this with caution as you can break or make your system with this.:)

Whoa, seems like everyone was in a big race to solve this thread, shows you the speed of response of Ubuntu Forums :D

Yep... Ubuntu Forums is faster either then my internet connection or my typing speed..... :guitar:

---

### Post by Johnny3 on 2007-10-01
My mind isn't doing to well. My Honey(my dog) I have had for 14 year was have trouble this morning. She it my companion. Will be lost went the time comes. Of all the thinks I have lost my mind bothers me the most .
Thanks Johnny3
Gainesville, Fl

---

### Post by irish_flu on 2007-10-01
Sorry to hear that your four-legged friend isn't doing well, buddy.

---

