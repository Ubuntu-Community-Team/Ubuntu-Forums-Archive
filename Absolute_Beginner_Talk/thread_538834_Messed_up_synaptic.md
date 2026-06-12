---
title: "Messed up synaptic"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by vertex78 on 2007-08-30
I was screwing with synaptic and enabled some download source and now I keep getting this error then synaptic closes

E: Dynamic MMap ran out of room
E: Error occurred while processing xexec (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

How can I fix this???

---

### Post by dstew on 2007-08-30
The usual cause is that a package is exceeding the default memory cache limit. You can set this limit by editing the /etc/apt/apt.conf file. If there is a line like this, you can increase the value:```
APT::Cache-Limit "16777216";
```
If the line doesn't exist, then you can add it.

---

### Post by vertex78 on 2007-08-30
I looked and that file is not there.

---

### Post by st33med on 2007-08-30
I can confirm that there is no apt.conf file as well, even though I don't have the problem.

---

### Post by dstew on 2007-08-31
You can just create the file. Most of the apt configuration is stored in other files, but it will read /etc/apt/apt.conf and add the variables there to its configuration. You can check the entire apt configuration by using the **apt-config dump** command.

---

### Post by jesnev on 2007-09-02
ok, 
I have the problem.
Done what is recommended. 
APT::Cashe-Limit 1666777216;
Problem still remains.

This kind of bug is not what I expected. I have been running Ubuntu for quite a long time and never experienced anything like this. I am a little upset now! I hate to re-install!

Has anyone a cure?
JesNev

Changed to 16777216; processer is burning hot;  apt-cache seems running wild.

---

### Post by 1hutchy on 2007-09-05
If its not to late,  then try this, & if it doesnt work I'll be amazed as it worked for me-
  sudo rm -vf /var/lib/apt/lists/*

---

