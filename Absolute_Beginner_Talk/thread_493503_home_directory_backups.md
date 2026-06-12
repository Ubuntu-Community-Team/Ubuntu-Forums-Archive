---
title: "home directory backups"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by actioncomics on 2007-07-05
I have played with linux enough, so now i am going to format the hard drive and start clean.  I am going to format my 40GB hard drive as follows:
20GB Windows (used for games only)
19GB Linux (root directory)
512 swap file
512 boot or temp directory (not sure on this one)

My second drive will be a 160GB drive used by both linux and windows as a /home directory.

now for my questions
1.  should i create a boot directory if I have the extra space?  if not should i make it a "temp files" directory instead and is 512MB enough for a temp directory?

2.  can i store all of my program settings in linux under /home?  are some stored somewhere else?

3.  maybe this is to simple of an idea but can i just burn my /home onto dvd and then restore it later by simply copying everything back over.  or do i need to worry about permissions?

Mostly what i am looking to do is keep most of my settings in place so that if i have format again or my drive crashes i can easily restore things.  in windows i use portable software (except for games) that way i can keep my programs and settings all in the same place and easily restore them if necessary.  I would like to accomplish the same with linux (if possible).  sorry this was so long winded, I would like to do this right the first time.  thanks for any advice.

---

### Post by kevinlyfellow on 2007-07-06
> **actioncomics said:**
> I have played with linux enough, so now i am going to format the hard drive and start clean.  I am going to format my 40GB hard drive as follows:
20GB Windows (used for games only)
19GB Linux (root directory)
512 swap file
512 boot or temp directory (not sure on this one)

My second drive will be a 160GB drive used by both linux and windows as a /home directory.

now for my questions
1.  should i create a boot directory if I have the extra space?  if not should i make it a "temp files" directory instead and is 512MB enough for a temp directory?


I haven't really seen much need for a boot partition.  These are mainly useful if you have multiple linux distros installed.  I'm not sure on the advantages of having that as a temp directory.

> 
2.  can i store all of my program settings in linux under /home?  are some stored somewhere else?


User preferences are stored in /home/username.  Most system wide configurations are in /etc

> 
3.  maybe this is to simple of an idea but can i just burn my /home onto dvd and then restore it later by simply copying everything back over.  or do i need to worry about permissions?

Mostly what i am looking to do is keep most of my settings in place so that if i have format again or my drive crashes i can easily restore things.  in windows i use portable software (except for games) that way i can keep my programs and settings all in the same place and easily restore them if necessary.  I would like to accomplish the same with linux (if possible).  sorry this was so long winded, I would like to do this right the first time.  thanks for any advice.

I'm not sure, but there are only a few files that you need special permissions for in your home directory.  Everything else can be easily changed on the commandline (all in one sweep too)
```
chown -R username:groupname homedirectory
chmod -R 700 homedirectory
```
I can't remember the files that need special permission off the top of my head.  But there are backup utilities in linux, perhaps someone can suggest a good one?

There is a program called [mondo rescue]("http://www.mondorescue.org/").  What it does is makes an installation disk with your current setup, so that it will completely reinstall everything, including your partition setup.  It sounds like something you might be interested in.

---

### Post by ramjet_1953 on 2007-07-06
How much RAM does your system have?

Generally, it is good practice to set your swapfile partition to twice the size of your RAM.

Regards,
Roger :cool:

---

### Post by Rui Pais on 2007-07-06
> **actioncomics said:**
> 
1.  should i create a boot directory if I have the extra space?  if not should i make it a "temp files" directory instead and is 512MB enough for a temp directory?
 No need for separate partitions. Make thing simple is always the best choice. 
 > 
3.  maybe this is to simple of an idea but can i just burn my /home onto dvd and then restore it later by simply copying everything back over.  or do i need to worry about permissions?
 yes you need to take care with permissions. use:
```
cp -a 
``` 
-a is for archiving. 
It will preserve your ownerships and permissions.

---

