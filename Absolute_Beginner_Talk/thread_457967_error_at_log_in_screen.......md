---
title: "error at log in screen......"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-05-29
ok ive just logged in to ubuntu (fiesty) and ive typed in my user name, hit enter and then typed in my password and hit enter and then this box comes up saying - user's $ HOME/.dmrc files is being ignored.
This prevents the default session and language from being saved.
File should be owned by user and have 644 permisions
User's $ HOME directory must be owned by user and not writeable by other users.

so my question is what have i done to make this come up, im guesing ive changed permissions on folders i shouldnt have and how do i fix it ? if it is fixable.
cheers in advanced for any help.

---

### Post by Borzo on 2007-05-29
press ctrl+f1, login

type 

ls -l /home 

and see what you get, the ownerships and permissions are here

your home directory should say something like this (techno-mole=your login name)

drwxr-xr-x 51 techno-mole techno-mole 4096 2007-05-29 14:00 techno-mole

press ctrl+f7 to go back o GUI

---

### Post by techno-mole on 2007-05-29
i got the out put you posted, i found the /.dmrc file in the home directory and deleted it, dont get the error anymore, cheers for the help - note to self dont mess about with permissions.
now all i need to do is find out why the latest kernel update killed my networking ?
cheers again.

---

### Post by Borzo on 2007-05-29
update your restricted modules for the new kernel using synaptic and see if networking works

---

### Post by techno-mole on 2007-05-29
cheers ill have ago, im guessing ill need to log into the newer kernel to do it ? ive gone back to -15 from -16.
cheers

---

### Post by Borzo on 2007-05-29
well, if you rely on that networking to get the updates, you need to boot into the previous ( working ) kernel, uninstall the old ones, install the new ones ( they will have the same number as the newest kernel ) and reboot to the new one.

---

### Post by techno-mole on 2007-05-29
i dont need the network to get online (eg for downloading etc etc) that still works, its just the home network thats stuffed, so i cant move files to and from my pc and the others.
ive updated through synaptic, but its not made any difference to the -16 kernel, so i shall do more reading, and maybe try a few things.
cheers

---

### Post by Borzo on 2007-05-29
in synaptic
search for linux-restricted-modules
you need to mark them for removal
you need to mark the ones corresponding to your current kernel for installation
click apply
reboot

---

### Post by techno-mole on 2007-05-29
thats interesting, it would seem that when i went through synaptic the first time i thiught id got all the files, but upon closer inspection i missed one file - linux-restricted-modules-2.6.20- 15-386, now that ive deleted removed that one i can now see the other pc's on the network, i still cant create and delete files but at least im one step closer.
cheers

---

