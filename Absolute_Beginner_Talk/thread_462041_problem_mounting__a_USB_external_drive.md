---
title: "problem mounting  a USB external drive"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by clumpy on 2007-06-02
I have an IDE 3.5 external USB case that I use for quickly transfering data from one machine to the next without having to drag the whole machine with me. It works with every drive I have ever put in it, except one, it simply won't boot.  If I put the drive back in the machine it works fine. I played around with the jumpers but to no avail. I am at a loss, Anyone have any ideas?  I really need to get the data onto another drive soon so this is a pressing problem. All help is welcome


Also trying to write to my USB drive, the system tells me it is read only, How can I change the access permission so I can write on it? 

thanks


clumpy

---

### Post by Inxsible on 2007-06-02
What do you mean it won't boot ? the drive ??

for you permissions problem:
```
sudo chown -R <your-username>:<your-group> <device-name>
```

So assuming your username is clumpy and your group is also clumpy and the device is /dev/sda1
```
sudo chown -R clumpy:clumpy /dev/sda1
```

---

### Post by Inxsible on 2007-06-02
if it is an external drive, you should use pmount to mount it.
```
sudo pmount <device-name> <mount-point>
```

Post the output of so that I can give you an exact pmount command
```
sudo fdisk -l
```

-l is lowercase L. Make sure your external drive is connected when you run the above command

---

