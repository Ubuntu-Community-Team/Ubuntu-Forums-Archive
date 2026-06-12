---
title: "how do you make and mount an iso on ubuntu?"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by L_o_N_e_R on 2006-08-10
title says all ^^^^

---

### Post by L_o_N_e_R on 2006-08-10
bump i know some1 here knows ;p

---

### Post by Jagot on 2006-08-10
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning](http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning)
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_create_Image_.28ISO.29_files_from_CD.2FDVD](http://easylinux.info/wiki/Ubuntu_dapper#How_to_create_Image_.28ISO.29_files_from_CD.2FDVD)

---

### Post by L_o_N_e_R on 2006-08-10
error

file.iso: no such file or directory

---

### Post by L_o_N_e_R on 2006-08-10
i think i found the problem

i need to put the iso in the /media/iso folder


how do i do that?

---

### Post by Jagot on 2006-08-10
I'm assuming this is with regards to mounting the .iso?

You do not need to put it in the /media/iso directory - that is where it mounts to.  When it says file.iso, you have to put in the actual name of the .iso file you are trying to mount.  For example, if you wanted to mount the Ubuntu iso, the file name would be ubuntu-6.06-desktop-i386.iso

---

### Post by L_o_N_e_R on 2006-08-10
still doesnt work....(the iso is in my desktop)


heres what i put



sudo mount Starcraft-Broodwar.iso /media/iso/ -t iso9660 -o loop

---

### Post by Jagot on 2006-08-10
Can you copy and paste exactly the output you get when you try to mount it?

---

### Post by L_o_N_e_R on 2006-08-10
Starcraft-Broodwar.iso: No such file or directory


-_- where do i hate to put it? anywhere?

---

### Post by Jagot on 2006-08-10
You are aware that you have to point to the directory that the .iso is in?  The error that it is giving suggests that it cannot find the file.

```
sudo mount Starcraft-Broodwar.iso /media/iso/ -t iso9660 -o loop
```

The code above that you put will only work if the .iso is in your /home directory.  If it is on your desktop for example, then it would be:

```
sudo mount /home/YOUR_USER_NAME/Desktop/Starcraft-Broodwar.iso /media/iso/ -t iso9660 -o loop
```

---

### Post by L_o_N_e_R on 2006-08-10
w00t it worked :) thnx

sry but is there a way to mount it as a image file??

---

### Post by NMStang218 on 2006-08-10
^^^^^exactly

If you are unsure where you are at in the prompt, then type "dir" to see what files are present in your current directory. 

I am a complete newbie to linux (hopefully that will change) and this thread helped me mount an iso file:D

---

### Post by Jagot on 2006-08-10
> **L_o_N_e_R said:**
> sry but is there a way to mount it as a image file??

I don't quite understand.  It already is an image file.  You have mounted it so you can see the contents.

---

### Post by L_o_N_e_R on 2006-08-10
> **Jagot said:**
> I don't quite understand.  It already is an image file.  You have mounted it so you can see the contents.

 i wanted it so i dont have to use the cd anymore 
i run cedaga and SC is slow(i read somewhere that using an iso will make it faster)


sry if im confusing :(

---

### Post by Jagot on 2006-08-10
OK, I'm afraid I have no idea about that one - somebody else will have to answer that for you.

---

### Post by L_o_N_e_R on 2006-08-10
-_-

---

### Post by DC@DR on 2006-09-03
Try this nice howto, it creates a script for you to mount .iso file, very handy: [http://www.ubuntuforums.org/showthread.php?t=87369&highlight=mount+.iso+file](http://www.ubuntuforums.org/showthread.php?t=87369&highlight=mount+.iso+file)

---

