---
title: "telling me i don't have permision?"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-02-17
ok so i'm trying to edit something that i need to. and it's telling me i don't have permission? how do i override it or something?:)

---

### Post by sb12 on 2008-02-17
> **RadiationHazard said:**
> ok so i'm trying to edit something that i need to. and it's telling me i don't have permission? how do i override it or something?:)

sudo command_goes_here

---

### Post by jaytek13 on 2008-02-17
You have to open up the file you are trying to edit with sudo. For instance, if you were using gedit to edit the file, you would open a terminal and then type ```
sudo gedit /path/to/file
``` then you would be able to save it.

---

### Post by julian67 on 2008-02-17
> **RadiationHazard said:**
> ok so i'm trying to edit something that i need to. and it's telling me i don't have permission? how do i override it or something?:)

If you're using gedit (or similar) to make the edit launch the application with root privileges like so: Alt+F2

```
gksudo gedit /path to the file to be edited
```

or if you're in a terminal using vim or nano or similar:

```
sudo vim /path to the file
```

If you're using graphical apps (i.e. not terminal) then it's better to launch them as root with gksudo instead of sudo.

---

### Post by RadiationHazard on 2008-02-17
all i'm trying to do is put some files into a folder...

---

### Post by jaytek13 on 2008-02-17
> **RadiationHazard said:**
> all i'm trying to do is put some files into a folder...


Same concept. You have to use sudo. The terminal would be:

```
sudo cp file_to_copy /location/to/copy/to
```

Alternatively you can open up an application with sudo and copy/paste or something

```
sudo nautilus
```

---

### Post by RadiationHazard on 2008-02-17
i've always used sudo nautilus
but when i do that now it just doesn't do anything...=\\\\\

---

### Post by julian67 on 2008-02-17
> **RadiationHazard said:**
> all i'm trying to do is put some files into a folder...

5 minutes ago you said you were trying to edit a file but ran into permission problem so you got answers appropriate to editing a file as root. 

Perhaps you need to describe your difficulty a little more, and accurately. 

Are the files and folder owned by your user account? Are they in your home directory or somewhere else like another user's home or on an external drive? If on an external drive is it ntfs or linux filesystem?

edit: to launch nautilus as root don't use sudo, use gksudo

---

### Post by RadiationHazard on 2008-02-17
there in my directory /usr/share/ and so on
i usually use
```
sudo nautilus
```
to work with files and stuff that i don't have "permission" too
but now when i try nothing happens...
all i'm trying to do is replace some old files with some updated ones.

---

### Post by julian67 on 2008-02-17
> **RadiationHazard said:**
> there in my directory /usr/share/ and so on
i usually use
```
sudo nautilus
```
to work with files and stuff that i don't have "permission" too
but now when i try nothing happens...
all i'm trying to do is replace some old files with some updated ones.

try launching nautilus with Alt+F2 then ```
gksudo nautilus
```

---

### Post by RadiationHazard on 2008-02-17
nothing? :(

---

### Post by julian67 on 2008-02-17
> **RadiationHazard said:**
> nothing? :(

open a terminal, write ```
gksudo nautilus
``` hit return, enter your password edit: and hit return again! and actually copy and paste the result into your next reply.  It's difficult to help without some real feedback from you.

---

