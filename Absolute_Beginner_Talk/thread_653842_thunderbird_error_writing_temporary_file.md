---
title: "thunderbird: error writing temporary file"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Jense on 2007-12-30
Hi,

I recently have problems with thunderbird. Saving messages as drafts or just trying to attach files frequently generates the error "Unable to save your message as draft. Error writing temporary file."
A reboot usually fixes the problem, but it keep reappearing after a while. I get the feeling this is down to some permission problem, since I had simular errors using crossover office, where a reboot would fix the problem, but they also reappear after a while.

I don't know weather this might be related to a kernel I just compiled. Some things didn't work so well afterwards, so I am still using the generic kernel from the repositories. However I might have messed things up during the configuring of the new kernel - I just don't know if this can effect older kernels I am using.

system:
386, 7.10

So, any help or ideas would be much appreciated - Thx

---

### Post by markharding557 on 2007-12-30
might be worth checking the permissions of the tmp directory,on my pc this is owned by root but allows write access to all users.
many programs use the tmp directory for temporary files

---

### Post by Jense on 2008-01-02
yeah, did that, or tried but I must have gotten something wrong. I am not so sure how to use the chmod command correctly. Now I actually get a permission error, though I thought I had given the user read and write access to the temp directory.
I tried the following two commands, posted somewhere in this forum:

sudo chmod 4750 /tmp/
sudo chmod ug+rw /tmp/

Now when I try to access a video stream (for example) where I got previously the errormsg. "not enough space" I now get a permission error.
I also tried creating a simbolic link to another partition. but :( 

So some help to undo what I have done and maybe fix this problem would be nice.

Oh i forgot - I think the whole problem originates from my system partition being full. So this is why I got the idea to create the temp on another partition

---

