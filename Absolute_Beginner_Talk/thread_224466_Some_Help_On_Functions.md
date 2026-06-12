---
title: "Some Help On Functions"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by WPAStrangla on 2006-07-28
I need someone to help me explain some functions.  I been trying to install some drivers but really didn't understand how to make them work. :?

[http://www.nvidia.com/object/linux_nforce_1.0-0310.html]("http://www.nvidia.com/object/linux_nforce_1.0-0310.html")

Example:
[B]STEP 2: Begin Installation 
From within a shell with root privileges, type "sh NFORCE-Linux-x86-1.0-0310-pkg1.run" to initiate the installation.[/B]

If someone could help me and guide me through the process I would greatly appreciate it. Please, if you can, add some screenshots.

Thanks

---

### Post by aysiu on 2006-07-28
Step #1: Delete that .run file you downloaded.

Screenshots:

Step #2: [http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)

Step #3:
[http://monkeyblog.org/ubuntu/installing/#three_steps](http://monkeyblog.org/ubuntu/installing/#three_steps)

You're going to search for *nvidia-glx* and *nvidia-kernel-common*.

---

### Post by WPAStrangla on 2006-07-28
I am using version 5.04 of Ubuntu, will that effect the process?

---

### Post by nalmeth on 2006-07-28
For many reasons, it would be better if you could use the most recent version ubuntu.

Since 5.04, there was Breezy (5.10) and now Dapper (6.06)

Here are instructions for installing Nvidia's driver for Ubuntu:
Applications -> Accessories -> Terminal
```
sudo apt-get install nvidia-glx linux-restricted-modules-$(uname -r)
sudo nvidia-glx-config enable
```

---

### Post by WPAStrangla on 2006-07-28
Thanks, I am downloading 6.06 now and hopefully will have it installed by tomorrow. I will probably be back later asking more questions :(

---

