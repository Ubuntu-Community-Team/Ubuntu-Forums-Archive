---
title: "Accessing a windows shared folder"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by aznboi on 2005-11-21
I have skimmed the forum a little trying to look for this but i dont really understand how to do it:
I have a shared folder on my XP comp and am trying to get some files from it through my Ubuntu laptop. I have done the following:
```
apt-get install samba
```
but thats all ive done lol.... what shuold i do next? thnx

---

### Post by kennethb on 2005-11-21
What version of Ubuntu did you install? Samba should install automatically so you can use Natulis to browser to your Windows box.

---

### Post by aznboi on 2005-11-21
I  have 5.10

---

### Post by aznboi on 2005-11-21
when i go to System>Network Servers it shows my windows box but when i try to browse it it gives me the follwing error:
```
The Folder Cotents Could Not Be Displayed.
```

---

### Post by racecat on 2005-11-21
I think you also need smbfs. There is a little setup to do and how you do it depends on how you want to share files. You should be able to find it in the wiki. If you're using Hoary (5.04) it is in the "Unofficial Ubuntu Users Guide".

Good luck,
Bill

---

### Post by racecat on 2005-11-21
Oh, yeah. You have to reboot after installing smbfs (at least I did in 5.04) to make it work. It didn't prompt me to do it, it just didn't work until I did.

Bill

---

### Post by aznboi on 2005-11-21
thnx i will try that

---

### Post by aznboi on 2005-11-21
ok just finished downloading it, now a reboot and seeing how it fairs. thnx

---

### Post by Ruso on 2005-11-21
Try to write this command in xterm.

"mount -t smbfs //IP_of_Windows_machine/windos_shared_name /mnt"

so it looks like this for example "mount -t smbfs //192.168.1.5/my_docs /mnt"
Post here, what errors it gaved to you, if any. 
If no errors then just go to /mnt dir.

---

### Post by racecat on 2005-11-21
Oops, sorry. Reread your post. What I suggested is for sharing files on the Ubuntu box and accessing from a Windows PC. I haven't had any luck getting 5.10 to do what you want, although I have had luck with it in 5.04. I frankly find accessing from the Windows box less cumbersome and faster.:rolleyes: 

Have fun,
Bill

---

### Post by aznboi on 2005-11-21
lol i rebooted for no reason! thnx for the help anyway tho. anyone else kno how?

---

### Post by Ruso on 2005-11-21
aznboi

have u tried what I've said??

---

### Post by casper_2095 on 2005-11-22
you want "smbclient"
$ man smbclient
$ smbclient //somecomputer/someshare

---

### Post by aznboi on 2005-11-22
[QUOTE=Ruso]aznboi

have u tried what I've said??[/QUOTE]
o wow sry man i didnt see ure post! lol sry ill try it when i get home.

---

