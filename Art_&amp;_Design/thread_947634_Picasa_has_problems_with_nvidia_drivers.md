---
title: "Picasa has problems with nvidia drivers"
date: 2008-10-14
forum: Art &amp; Design
---

### Post by ipetter on 2008-10-14
Ok... I've searched and found similar problems, but no solution. Here's the problem:

I've installed the nvidia drivers using Envy NG, as the stock Ubuntu ones stopped working for me after the latest kernel update. Since installing the drivers using Envy NG I have a strange problem with Picasa. Everytime I start it it says
```
/dev/nvidia0 or /dev/nvidiactl are not accessable. Picasa will crash if these files are not accessable. 
To fix this, as root, please run: chmod 666 /dev/nvidia0 /dev/nvidiactl
```

So I fire up the terminal and execute the commands, and everything works fine until I reeboot or log out. It appears that the nvidia drivers are automatically resetting the permissions on logout!

But what about groups... Yes, I've tried that too. And the correct useres are added to the group "video". But the problem is that the group permissions for the two nvidia files are automatically reset to "44" on every logout. And "44" is not a valid group name. So I'm screwed!

The problem is the same on both Picasa 2.7 and 3 beta, so no luck there either. And I've allready tried reinstalling the nvidia drivers, to no avail.

Help please :confused: If not a permanent fix, can somebody please make me a script that'll set the permissions back to 666 on every login, for every user?

---

### Post by ipetter on 2008-10-17
Bump.... Anyone?

---

### Post by hod139 on 2008-10-26
I had the same problem, and to fix it I did this:

1)  System->Administration->Users and Groups
2) Clicked Unlock.  
3) Clicked on Properties, selected the user privileges tab, and added myself to the "Capture video from TV or Webcams, and use 3d acceleration" group.

Hope that works for you.

---

