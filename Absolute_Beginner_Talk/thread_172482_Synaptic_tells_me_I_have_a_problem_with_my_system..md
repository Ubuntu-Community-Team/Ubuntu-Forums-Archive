---
title: "Synaptic tells me I have a problem with my system. How do I fix it?"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by Belathor on 2006-05-08
Synaptic keeps telling me this is wrong with my system. However, being a newbie I have no idea what it means. Any help would be appreciated!

```
W: Duplicate sources.list entry cdrom://Ubuntu 6.06 _Dapper Drake_ - Beta i386 (20060420) dapper/main Packages (/var/lib/apt/lists/Ubuntu%206.06%20%5fDapper%20Drake%5f%20-%20Beta%20i386%20(20060420)_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 6.06 _Dapper Drake_ - Beta i386 (20060420) dapper/restricted Packages (/var/lib/apt/lists/Ubuntu%206.06%20%5fDapper%20Drake%5f%20-%20Beta%20i386%20(20060420)_dists_dapper_restricted_binary-i386_Packages)
```

---

### Post by louis_nichols on 2006-05-08
You'll have to delete 2 lines in sources.list

1. Start by making a backup of the file, in case anything goes wrong:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

2. Open the file for editing as root:

```
sudo gedit /etc/apt/sources.list
```

3. Find the duplicate entries and delete one line of each. They will be lines containing the keyword cdrom.

4. Run ```
sudo apt-get update
``` to check everything is fine:

NOTE; As an advice, packages that are on cdrom become useless after installing the OS, as it is better to just fetch them online. So my suggestion is that, after deleting the duplicate lines, to comment out the other lines reffering to the cdrom repo, by placing a # sign in front of each line.

---

### Post by Belathor on 2006-05-08
sweet! Thanks so much!

---

