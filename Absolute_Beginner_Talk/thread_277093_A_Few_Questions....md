---
title: "A Few Questions..."
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by cmmike1 on 2006-10-14
Recently I put Ubuntu 6.06 onto a secondary hard drive on my computer. I really like it and I have been using it more than windows xp for the past few days. I want to use it more often but I have a few questions that need to be answered.

1.) I've downloaded all the codecs that I know of to play movies and music. There is no problem with that. The problem come when I try to watch movies in Firefox/Swiftfox. I get a black box that says Kaffine starter plugin in when i want it to just play in the browser. Is there anyway to fix this and if so can you please help me out.

2.) I have a lot of music and movies on my windows xp partition that i would like to be able to watch. What i did was i partitioned the Ubuntu drive because i wasn't using all of it and i wanted to have 10 gigs for sharing between XP and Ubuntu. I set it up to be fat32 because i thought ubuntu could read and write to it but every time i go to acces the drive it gives me this error


error: device /dev/hda5 is not removable

error: could not execute pmount

I'm pretty new to ubuntu so if you have any answers to my questions please assume i know nothing about it and provide as much info as you can. I really appreciate any help i can get from this great community.

---

### Post by adwait on 2006-10-14
For your first problem, I am not sure whether your movies are playing or not. If they are playing but in a different window, you can't really do much about it. But if they aren't playing at all, then install the mplayer plugin for firefox.

For your second problem, the drives shoudl ideally be automatically mounted and hence if you try to mount them again it will give an error. Try the command 
```
df
```

to see if they are mounted. If the drive you want isnt mounted, you need to mount it using
```
sudo mount /dev/<whatever> /<mnt location>
```

---

### Post by cmmike1 on 2006-10-14
i'm not really understanding the mounting part. I understand that i need to type sudo mount /dev/hda5 but what do you mean by mount location?

---

### Post by jimrz on 2006-10-14
check out [[COLOR="Sienna"]**_this_**[/COLOR]]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")guide on mounting FAT partitions

---

### Post by cmmike1 on 2006-10-14
thank you so much. that worked exactly how i wanted it to work.

---

### Post by cmmike1 on 2006-10-15
i have a few more questions about videos in firefox. i have remvoed kaffeine from my pc because i hated it but i still have the plugin. i thouhgt i remvoed it when i used synaptic but i guess i missed something. can someone tell me how to change it so i can play all my media in mplayer? if this is anyhelp here is my about:plugins.




if you have good settings for video playback please tell me how you have gotten them stpe by step if possible. i thank everyone who read this post.

---

### Post by cmmike1 on 2006-10-15
Anyone. I know you're not supposed to bump after a few hours but i really need to know because i want to make watching movies enjoyable.

---

