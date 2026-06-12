---
title: "I cannot add Medibuntu's gpg key"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by acadiansteph on 2007-11-05
I have tried several times to add Medibuntu's repositories and the corresponding GPG key. I followed the following instruction on Medibuntu webpage  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)  . I have no problem adding the repositories, but when adding the GPG key, the terminal hangs and no updating gets done (and no GPG key authentication). Does anyone have an idea! Maybe a problem in the script. My OS is Ubuntu 7.04.

---

### Post by hyper_ch on 2007-11-05
How do you try to add it?

---

### Post by acadiansteph on 2007-11-05
Following the instruction for Feisty 7.04.  then adding the GPG key. Adding the  repositories gives me no problems, but when trying to add the GPG key, I get no key or connection and no updating. I copy and paste the scripts to the terminal

---

### Post by hyper_ch on 2007-11-05
And how did you try to do that? Please post according commands.

---

### Post by acadiansteph on 2007-11-05
sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list
in the terminal then 
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update in the terminal

---

### Post by hyper_ch on 2007-11-05
and what error did you get?

---

### Post by acadiansteph on 2007-11-05
No errors, it just hangs and does not add or update. I get a wget-log in my home folder with nothing in it.

---

### Post by hyper_ch on 2007-11-05
The run those two only:

```

sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list

```
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

```

---

### Post by acadiansteph on 2007-11-05
Does not work it hangs for 2-minutes

---

### Post by acadiansteph on 2007-11-05
I get  gpg: can't open `': No such file or directory

---

### Post by philinux on 2007-11-05
Try these one at a time
```

wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by mivo on 2007-11-05
just added the Medibuntu repository and the key on a freshly installed box, and this:

```

sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

... worked flawlessly. I did have a strange problem adding a GPG key for a different repository yesterday, however (for the Screenlets), exactly as described by acadiansteph. What fixed it was rebooting the machine. (This may just have been coincidence.)

---

### Post by derekj212 on 2007-12-30
Thanks, that worked perfectly for me.

---

### Post by tailStrike on 2008-02-17
Was getting errors on medi sources, too, and noticed that one of the tutorials floating around that I blindly followed the other day had me add them directly to /etc/apt/sources.list, but the commands on the Medibuntu wiki page:
 [https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

More apropriately add them to a seperate file in /etc/apt/sources.list.d/.  Just worth mentioning that if following medi's instructions, you should remove any sources you might have previously added to sources.list directly to prevent problems.

---

