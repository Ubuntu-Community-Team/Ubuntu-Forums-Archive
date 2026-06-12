---
title: "How do I remove password protection for hard disk access"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by aachen on 2008-03-18
I have 4 partitions in my hard disk and whenever I want to access a partition, ubuntu prompts me to enter administrator username and password. Its really uncomfortable to enter it each time I switch on my pc. 
Can anyone tell me how to remove this protection so I can access the partitions just by clicking on it.

Thanks

---

### Post by hyper_ch on 2008-03-18
chown the mounted folder to your user.

---

### Post by aachen on 2008-03-18
Chown the mount folder to user folder ? Can you explain what does it mean ?

---

### Post by taurus on 2008-03-18
What filesystem are those partitions and how do you mount them?  Do you mount them through /etc/fstab?

Open a terminal and post the outputs of these commands.

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by hyper_ch on 2008-03-18
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by aachen on 2008-03-18
I am not using Linux right now. So I cant post the output of these commands right now. but I will do it later and also see the help links posted by hyper_ch  and then post again.

---

### Post by hyper_ch on 2008-03-18
basically you mount those drives somehwere in your file system... so once they are mounted, you change ownership to your user....that's all that is required (or you could modify the mount commands to mount it as your user)

---

