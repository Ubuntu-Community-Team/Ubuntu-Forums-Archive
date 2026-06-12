---
title: "Permissions on Graphic File"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Mad_Max_1412 on 2007-12-01
Guys,

I'm slowly trying to move from Windows XP to Ubuntu, so at the moment some tasks I am still currently undertaking in Windows.

One of these is moving photos from my flash card onto a Windows directory.

The other day, I decided to copy one of these photos over to my Ubuntu box via a mapped drive in Windows Explorer.

I then switched over to Ubuntu and opened the photo in Gimp and adjusted some levels as explained in a magazine tutorial about tweaking photos.

When I went to save the file, it brings up a dialogue box saying:

> Saving '/home/max/Ubuntu_pcss/2007-11-11 004.JPG' failed:  Permission Denied

If I navigate to that location and right-click on the file and choose permissions, it says the owner is "Nobody" and access is greyed out.  The "group" is "nobody" and also has access greyed out.  "Others" has nothing next to it and access is greyed out.  At the bottom of this is a line saying "You are not the owner, so you can't change the permissions".

Is there something I can change in a conf file, eg the smb file, which will allow me to have permissions on files which I move to my Ubuntu box via the mapped drive in Windows Explorer?

I can save my changes by saving as a new name, but this would be a bit tedious as I then would have to delete the original.

Thanks guys.

---

### Post by vikram on 2007-12-01
> **Mad_Max_1412 said:**
> Guys,

I'm slowly trying to move from Windows XP to Ubuntu, so at the moment some tasks I am still currently undertaking in Windows.

One of these is moving photos from my flash card onto a Windows directory.

The other day, I decided to copy one of these photos over to my Ubuntu box via a mapped drive in Windows Explorer.

I then switched over to Ubuntu and opened the photo in Gimp and adjusted some levels as explained in a magazine tutorial about tweaking photos.

When I went to save the file, it brings up a dialogue box saying:



If I navigate to that location and right-click on the file and choose permissions, it says the owner is "Nobody" and access is greyed out.  The "group" is "nobody" and also has access greyed out.  "Others" has nothing next to it and access is greyed out.  At the bottom of this is a line saying "You are not the owner, so you can't change the permissions".

Is there something I can change in a conf file, eg the smb file, which will allow me to have permissions on files which I move to my Ubuntu box via the mapped drive in Windows Explorer?

I can save my changes by saving as a new name, but this would be a bit tedious as I then would have to delete the original.

Thanks guys.

I haven't tried this before since I prefer to use ftp, far more stable and trouble free IMO. Here's what I found in /etc/samba/smb..conf

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

try giving rw permissions so that you can access the file even though nobody is the owner. this may work if you are ok with everyone having rw access to your images. otherwise use the "chown" command to change the owner of the file as root.

---

