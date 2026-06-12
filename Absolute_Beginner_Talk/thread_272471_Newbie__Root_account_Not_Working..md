---
title: "Newbie : Root account Not Working."
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by 7mm on 2006-10-06
Hi there, I've just Installed UBUNTU 64-Bit successfully. During the Instalation, I've been asked to put my Name, User ID & Password etc. But it never asked about Root password or not even close to it :confused: . Now I'm having a problem Entering Root account to change my settings ](*,) . Please Help Guys.

---

### Post by Ben Sprinkle on 2006-10-06
```

sudo passwd root newpass

```

---

### Post by petri on 2006-10-06
Well in Ubuntu there is no root account what you should use. Of course there is a root account but the idea Ubuntu has is that people should not run as a root all the time.

Every time you need root privilegies you just type **sudo** before the command like in ```
sudo apt-get update
```

Just showing people how to get root pass is not the right way to do things. 

EDIT: Read this [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by 7mm on 2006-10-06
Ok, Le'me try & see. Thank you "Goat Spirit" & "petri".

---

### Post by 7mm on 2006-10-07
Nope Fellows, It's not working.:-| 

I tried - sudo passwd root newpass - command & UBUNTU asked me for password. (Now what?)

I tried - sudo apt-get update - command & again I've been asked for password.](*,) 

Tell me people what's wrong as I'm new to Linux command Line, know nothing about it. So please Help me with details.

I'm try'n to connect to Internet using UBUNTU. But any change related to Administration, asked for root password. I'm helpless without your guidence, Please Help.

---

### Post by Abstract on 2006-10-07
Enter the password of your own user. Sudo works so that if you are in the administer group (which you should be) you enter your OWN password for YOUR account and it'll root you.

For passwd enter the password you want for root.

---

### Post by BitTorrentBuddha on 2006-10-07
Sudo works by using the password on your user account. At the password prompt, simply type your user password (assuming you're in the sudoers group, which you probably are.) If you want a root terminal run: ```
sudo -s -H
```

---

### Post by 7mm on 2006-10-07
Woila! It worked. Now I'm using Internet Connection through UBUNTU. Thanks a lot "Abstract" & "BitTorrentBuddha".

"Goat Spirit" & "petri" your help will always be usefull, Thank you.

Thank you All.

---

