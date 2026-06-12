---
title: "XMMS skins install"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Jareth on 2006-10-05
How does one install skins for XMMS?

Ta

---

### Post by bodhi.zazen on 2006-10-05
Put them in ~/.xmms/skins

---

### Post by Splittor on 2006-10-05
Yah there's nothing to install, just copy the files to ~/.xmms/Skins, and they should appear in the Skin Browser in XMMS.

---

### Post by sean blah blah blah on 2006-11-19
you guys have the right idea...but i have been trying for two days...im still new to linux...so please...how do you copy..? my comp is so angry with me and wont let me do anything that any one has recomended:confused:

---

### Post by taurus on 2006-11-19
You mean you can't even move stuff around in your own $HOME directories???

---

### Post by sean blah blah blah on 2006-11-19
i can do the home directories thing but well i read that if i type gksudo nautilus it lets me drag in drop it the areas thet i cannot normaly drag and drop...but as far as using the terminal to do the things that matter...like copy and move...it hates me...:-k

---

### Post by CupofDice on 2006-11-19
Just download/move the skin to your desktop, open up nautilus, go to view/show hidden files, go to .xmms/Skins, and move the skin in there by drag/drop. 

To use the terminal, the command is "cp" for copy. Lets say the file is on your desktop.

Open your terminal
```

cd Desktop (this will move you to your Desktop)
cp skin ~/.xmms/Skins
or you can move it
mv skin ~/.xmms/Skins

```

There is no need for sudo, unless your permissions are messed up.

---

### Post by sean blah blah blah on 2006-11-19
they probaly are messed up...well for now i got rid of xmms and went to audio something...im trying beryl or..well ill get back to this in a sec](*,)

---

### Post by taurus on 2006-11-19
> **sean blah blah blah said:**
> they probaly are messed up...well for now i got rid of xmms and went to audio something...im trying beryl or..well ill get back to this in a sec](*,)
What's the output of this command from a terminal then?

```
ls -la ~
```

---

### Post by sean blah blah blah on 2006-11-20
i just wiped it all out lome program was lagging the whole thing up....???
when i put the ls command i got this..
sean@sean-desktop:~$ ls -la ~
total 88
drwxr-xr-x 13 sean sean 4096 2006-11-20 16:03 .
drwxr-xr-x  3 root root 4096 2006-11-20 15:41 ..
-rw-r--r--  1 sean sean  220 2006-11-20 15:41 .bash_logout
-rw-r--r--  1 sean sean  414 2006-11-20 15:41 .bash_profile
-rw-r--r--  1 sean sean 2227 2006-11-20 15:41 .bashrc
drwxr-xr-x  2 sean sean 4096 2006-11-20 15:45 Desktop
-rw-------  1 sean sean   26 2006-11-20 15:45 .dmrc
-rw-------  1 sean sean   16 2006-11-20 15:45 .esd_auth
lrwxrwxrwx  1 sean sean   26 2006-11-20 15:41 Examples -> /usr/share/example-content
drwx------  4 sean sean 4096 2006-11-20 16:03 .gconf
drwx------  2 sean sean 4096 2006-11-20 16:03 .gconfd
-rw-r-----  1 sean sean    0 2006-11-20 15:46 .gksu.lock
drwx------  7 sean sean 4096 2006-11-20 16:01 .gnome2
drwx------  2 sean sean 4096 2006-11-20 15:45 .gnome2_private
drwxr-xr-x  2 sean sean 4096 2006-11-20 15:46 .gstreamer-0.10
-rw-r--r--  1 sean sean   86 2006-11-20 15:46 .gtkrc-1.2-gnome2
-rw-------  1 sean sean  171 2006-11-20 16:03 .ICEauthority
drwx------  3 sean sean 4096 2006-11-20 15:45 .metacity
drwx------  3 sean sean 4096 2006-11-20 16:03 .mozilla
drwxr-xr-x  3 sean sean 4096 2006-11-20 15:45 .nautilus
-rw-r--r--  1 sean sean    0 2006-11-20 15:46 .sudo_as_admin_successful
drwx------  2 sean sean 4096 2006-11-20 15:45 .Trash
drwx------  2 sean sean 4096 2006-11-20 15:45 .update-notifier
-rw-------  1 sean sean  123 2006-11-20 16:03 .Xauthority
-rw-r--r--  1 sean sean  759 2006-11-20 16:03 .xsession-errors
sean@sean-desktop:~$

---

### Post by r@ndom@n on 2007-07-02
> **Splittor said:**
> Yah there's nothing to install, just copy the files to ~/.xmms/Skins, and they should appear in the Skin Browser in XMMS.

i just installed linux today. total noob question - where do i find "~/.xmms/Skins"?

---

