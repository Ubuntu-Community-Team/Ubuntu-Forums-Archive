---
title: "Samba frustrations"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Hitchhiker42 on 2007-08-28
Okay, I'm sure this is all very simple, but as a newbie, I'm not finding it so, and I think I got in over my head and made some mistakes, and now I can't figure out how to fix them, and I'm about ready to tear my hair out.

I was trying to make it so that the Win computers on our home network could see my computer. I could already see them, and access their files, but when they tried to access mine, they were prompted for a username and password, so I attempted make a user account under samba using the following command:
```
 sudo smbpasswd -a windows
```

It prompted me for my Ubuntu password and a samba password, but then said
```
Failed to modify password entry for user windows
```
and then I couldn't see or access the windows computers, never mind them being able to see me.

ETA: Okay, turns out they can see me, but there is still a prompt for username/password.

I restarted samba, and when that didn't work, I reinstalled samba and smbfs, but still no luck.

I would like to be able to:
1) See and access the windows computers from my linux computer
2) See and access my linux computer from the windows computers

Any help y'all can give would be great, as this has been really frustrating.

---

### Post by hyper_ch on 2007-08-28
You first need to add a system user called windows and then you can the smbpasswd...

You can only add users to the samba list that are actually on the system itself :)

---

### Post by Hitchhiker42 on 2007-08-28
See, I knew it was simple! Does the user "windows" need to be admin, desktop, or unprivileged? Are there any other setting I need to change? Does user "windows" need a home folder?

Also, I can see the rest of the network now. How? Who knows.

---

### Post by hyper_ch on 2007-08-28
can be unprivileged and doesn't require a home folder...

---

