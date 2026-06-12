---
title: "Start up error"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Done_Fishin on 2007-05-06
I have obviously done something wrong when I changed some permissions and I now get this warning in a box just after signing in 

[img]http://picsorban.com/upload/dscn3923 cropped.thumb.jpg[/img]

click [**_here_**]("http://picsorban.com/upload/dscn3923 cropped.jpg") for larger image 


anyone tell me how to reset this or what I might have done wrong?

Thanx

---

### Post by Happy_Man on 2007-05-06
You've gone and changed your /home permissions, and that's the computer's way of saying that they're messed up, go fix them. Your /home partition should be owned by you and only you... nobody else.

---

### Post by Done_Fishin on 2007-05-06
> **Happy_Man said:**
> You've gone and changed your /home permissions, and that's the computer's way of saying that they're messed up, go fix them. Your /home partition should be owned by you and only you... nobody else.

Thanks for that input but does that mean I just click on properties for the Home folder , select the permissions tab, then apply NONE to the settings there? I am somewhat confused about what I changed to require these changes

---

### Post by Happy_Man on 2007-05-06
You want to change those permissions to yourself, and the group to yourself.

---

### Post by Done_Fishin on 2007-05-06
I have recently ( trying to figure out where I have gone wrong changed the permission but haven't re-booted yet.

On the permissions tab I have 
Owner -- me 
Folder Access : Create & delete files
File access: ---

Group: -- me 
Folder Access : Create & delete files
File access: ---

Others
Folder Access : None 
File access: ---
execute is highlighted (allowing executing file as program

Would this be correct?

---

### Post by Done_Fishin on 2007-05-08
I figured out what was happening. I was putting a clone of the same disk on the same IDE cable as  a slave drive.
It semed to be looking at the grub, l;ooking at the first drive boot partition realising that it had the same info on the second drive boot partition (because there was another grub installed?) and then using the second disk as the boot medium
I am just guessing of course. It doesn't make sense. I found out after I copied a folder from a CD to a folder on the drive. Only when  I came to find it when booting the driver on it's own it was gone. I had also given the desktop A different background and this also disappeared when booting

---

