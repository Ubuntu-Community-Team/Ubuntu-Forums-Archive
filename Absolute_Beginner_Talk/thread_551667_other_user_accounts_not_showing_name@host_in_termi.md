---
title: "other user accounts not showing name@host in terminal"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-09-15
on 2 computers i have an account for me & roommate. if she's logged on and goes to terminal it doesn't show name@host, it either shows a $ by itself or sh-3.1$. she doesn't have admin rights on either computer.

is this a big deal? why does it do that?

---

### Post by jamvegan on 2007-09-15
Apparently, however you created the second account did not give it the default setup.  Your prompt is configured in your ~/.bashrc file, in the section that begins "# set a fancy prompt ...".  If you haven't made any modifications to your .bashrc file that are specific to your account (and if she has not made any changes to hers), you may wish to copy it and your ~/.profile (which calls .bashrc) to your roommate's home directory, and change the ownership to her user.  You can do this by opening a terminal and issuing the following commands:
```
sudo cp .bashrc .profile /home/roommate/
sudo chown roommate: /home/roommate/.bashrc /home/roommate/.profile
```
where you replace "roommate" with your roommate's login name.

However, the prompt itself does not really matter at all.  The fancy one just gives the user a bit more feedback about who's logged in and what directory they are in.

---

