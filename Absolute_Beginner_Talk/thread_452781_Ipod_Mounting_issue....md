---
title: "Ipod Mounting issue..."
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by SmashingTool on 2007-05-23
This morning, i plugged my Ipod in for the first time and had no issues at all. 2 hours later, I tried again and suddenly i'm getting an error saying "You are not privileged to mount the volume 'CLOUDY'." (Cloudy being the name of my windows formatted Ipod). I have searched all over google and these forums, and tried solutions related to my problem, but i never found another instance of this happening. While plugged in, the ipod shows the usual "Do not disconnect" screen

None of the music programs can see it, and when i try using the script

sudo mount /dev/sdb2 /media/iPod

I get a message saying

mount: mount point /media/iPod does not exist

And as far as i can tell, i cant create said mount point. What do i do?

---

### Post by cymen on 2007-05-23
From memory, I had a similar problem in that the ipod mounted once and then never was recognised again. My not very elegant way of solving it was to install gtkpod (which, to be fair, I was going to do anyway) and let it automatically handle the mounting of my ipod. Things have been fine ever since.

In your case, it sounds like you're trying to mount it to a directory that doesn't exist. So, make it and then mount! 

```
sudo mkdir /media/ipod
sudo mount /dev/sdb2 /media/ipod
```

---

