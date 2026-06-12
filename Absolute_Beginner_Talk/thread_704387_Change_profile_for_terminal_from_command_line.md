---
title: "Change profile for terminal from command line"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by peterlauri on 2008-02-22
Hi,

I have two profiles in my Terminal 2.18.2 emulator. Is there any way to change active profile via the command line? The reason for this is that when I connect to a specific server I want it to change colors etc so I can differentiate between the two different machines.

The two machines are really identical, but one is live and one is development, and I cannot afford to make mistakes :)

Best regards,
Peter Lauri

---

### Post by rapiscan on 2008-02-22
Looking at the man page for gnome-terminal, looks like you have the following option:

--window-with-profile=PROFILENAME
Open a new window containing a tab with the given profile.  More than one of these options can be provided.

So you could create a new application launcher with something like this as the command:

gnome-terminal --window-with-profile=MyProfileName

---

