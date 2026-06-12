---
title: "[SOLVED] User &amp;quot;administer the system&amp;quot; status... from command line"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by steve_4802 on 2007-12-01
Hi All,
The Ubuntu road has been bumpy but I feel I'm getting the feel for things. Was making good progress before deleting all the files in my home directory. Long story.

Anyway. Not concerned about the files in there anyway, so just want to recreate an account that is as good as the first account (I only had one). 

I have created a new user with :sudo useradd -m XXXX
I also created a password for the account.

I am now back in and thought it was all ok but am finding I don't have many priviliges. How can I make this account as good as the original? I assume I can use the terminal to grant special privileges and administrative rights? If so how, as I can't do it within the GNOME as I can't even get the user and groups part of the administration of the system dropdown - it's just not there.

Finally, with the correct permissions will this account be as good as the first account. I read somewhere that the first account will always be different and have more rights etc.

Thanks in advance team.

---

### Post by red_Marvin on 2007-12-01
You might be intereseted in the usermod command, especially with the -a and -G flag
I as an admin am member in the groups *adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev*. Check which groups you are member of with the *groups username* command. Note that you need to be superuser to add yourself as a superuser, so if you lost your original account (?) you'll need to boot into recovery mode before running the usermod command.

---

### Post by steve_4802 on 2007-12-02
That's the sort of thing I was after - thanks

---

