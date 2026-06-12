---
title: "is there a way to be the superuser in the GUI?"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by jonsayer on 2007-07-12
The title says it all. I want superuser privileges in the gui. I am having trouble uninstalling Vmware, so i am just going around deleting every vmware file. All of them are in protected folders. I can delete them just file in terminal with "sudo rm filename" but it is very tedious. if I could do this in the GUI, it would be faster.

Is this possible? if not, can we plz get this in Gutsy

---

### Post by Al3xK3aton on 2007-07-12
use the root user account; it's much more powerful.

---

### Post by Nythain on 2007-07-12
gksudo nautils

---

### Post by wpshooter on 2007-07-12
Yes, it is possible.  But I would warn you that is NOT adviseable to use this long-term, i.e. I would go back and reverse it as soon as I was thru using it temporiarly.

There are instructions for doing so on the forums if you will do a search.  I used to have a printed out copy but I have lost them.

Good luck.

---

### Post by sisco311 on 2007-07-12
```
 gksu nautilus
```

---

### Post by SirGrant on 2007-07-12
you know you don't have to delete all the files individually you can delete the whole folder.  Just cd .. to the directory above it and sudo rm -r /path/to/folder/  and it will delete the whole folder.

---

### Post by kavon89 on 2007-07-12
(deleted)

---

### Post by Al3xK3aton on 2007-07-12
If you want to, you can replace the password with a shorter one, like "ubuntu" or "money" or "passw0rd" or "letmein".

---

### Post by dannyboy79 on 2007-07-12
> **Al3xK3aton said:**
> If you want to, you can replace the password with a shorter one, like "ubuntu" or "money" or "passw0rd" or "letmein".

out of all 4 of those, I don't think 1 is "strong". Maybe the password but I can almost gurantee that brute force programs will most likely check for zero's instead of o within the word "password" I strongly suggest against changing ANY password to any of these. Whether it be the user's password or the root password. Just my 2 cents.

---

### Post by Calash on 2007-07-12
> **sisco311 said:**
> ```
 gksu nautilus
```

Use this method...it requires 0 alterations of the security setup and it will let you do what you are looking for.

I had the same VMWare issues you are...having installed it from the vmware site.  It is in the repos now, so once you get things working install it from there and you will be good.

---

### Post by Nekiruhs on 2007-07-12
> **Al3xK3aton said:**
> use the root user account; it's much more powerful.
This is NOT a good idea. There is a security reason why sudo is implemented.

---

### Post by phr0ze on 2007-07-12
> **dannyboy79 said:**
> out of all 4 of those, I don't think 1 is "strong". Maybe the password but I can almost gurantee that brute force programs will most likely check for zero's instead of o within the word "password" I strongly suggest against changing ANY password to any of these. Whether it be the user's password or the root password. Just my 2 cents.

Yeah, all the brute force progs replace letters with numbers and symbols now. And anything under 8 characters will be forced quickly. Dont use any words in your passwords anymore.

This isn't fool proof but will provide more security than most users have...
Pick a 4 or 5 letter word
Pick a 4 digit number
Mix the letters and numbers
Make sure at least one capital and one lowercase letter
Put a symbol in there

Example:
Word - Money
Number - 2600

M2o6n0e0y$

It looks confusing but it is easy to remember and much harder to brute force. You can put your own variation to this scheme, spell your word backwards, group letters and numbers in pairs instead of singles, etc. But its a start.

Ohh and if you use windows, make sure your system passwords are at least 15 characters because of a vulnerability in Windows password storage. - If you worry about that sort of thing.

---

### Post by Al3xK3aton on 2007-07-12
The problem with that is that those passwords are much more difficult to remember. This is why I suggested simple passwords.

---

### Post by phr0ze on 2007-07-12
> **Al3xK3aton said:**
> The problem with that is that those passwords are much more difficult to remember. This is why I suggested simple passwords.

It looks complicated but its not. You just remember one word (maybe your mom's name) and a 4 digit number (maybe your birthdate). If you cant remember either of those then you have a problem. Those are  a last resort, but everyone has some 4 digit numbers and 4 letter words they'll never forget.

---

### Post by dannyboy79 on 2007-07-12
we're aren't telling you that you can't, just that there are security implications if someone was to ever gain access to your computer or your network. they'd be able to brute force your machine within less than 1 minute, I can gurantee that too!!! 

Do as you like, it's your computer. What I do, is just pick a phrase that I like, then I throw in dashs, underscores, change letters to uppercase, and then throw in symbols and numbers. I checked it once, it gave me an approximate time of 44 years. HA, no 1 will crack it since it'll be changed by then

---

### Post by Gen2ly on 2007-07-12
> **dannyboy79 said:**
> we're aren't telling you that you can't, just that there are security implications if someone was to ever gain access to your computer or your network. they'd be able to brute force your machine within less than 1 minute, I can gurantee that too!!! 

Do as you like, it's your computer. What I do, is just pick a phrase that I like, then I throw in dashs, underscores, change letters to uppercase, and then throw in symbols and numbers. I checked it once, it gave me an approximate time of 44 years. HA, no 1 will crack it since it'll be changed by then

lol, have you ever not remembered what your password was though?

---

