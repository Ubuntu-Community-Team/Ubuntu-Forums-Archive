---
title: "By mistake i deleted all the groups :(, how to restore it."
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by savanc on 2007-02-16
HI everyone,

I am relatively very new to Linux and Ubuntu. 
Actually, my boss give me to look at my collegue's work who was using Ubuntu. So u can imagine i am totally new.

I feel great seeing Ubuntu working.  But then i did mistake and now i am not able to do any  of administrative work.

My problem:

I didn't know any thing about Groups and security related to Ubuntu and how it works. So when i show many groups i though my college might have autorised various groups so they can acess his files. 

So without thinking anything :( i am so stupid. I went to system-administration-users and groups- groups  
i selected all listed groups and deleted. :( I think i might have left only my user login current one. So that is working.
But now i am not able to do any of administrative activities. Cuase i think i have also deleted group-admin and all :( without understanding.

System is working but no acess :(. How can i restore. Is there any way to come out of this.
In this pc when i boot up i have some different kernals and kernals with (recovery)  also. Root password works in on of kernals(recovery) but its not working with the one from where i deleted all groups.

Hope i able to discuss problem correctly. 
If any confusion you can ask me. 

Please help me . Thanks lot in advance.

Regards,
savan

---

### Post by PetePete on 2007-02-17
ok, you should be able to solve this...

theres prob a better way of doing things, but seeing as no ones replied to you yet, i'll give you my dodgy advice :D

boot up with the Live CD, then open up terminal, mount your linux partition (look for advice on these boards for that as i can't remember exact commands, but should be something like, mount /dev/hda1 /someWrittableDirectoryYouHaveAccessTo )
f

then run the command 
cp /etc/group /whereEverYouMountedIt/etc/

then open the file which you just copied and add in the missing groups such as the new users groups.

restart the PC and pray lol##


edit;
just realised that may not work due to shaddowing , but its worth a try... remember to add yourself to the required groups, or use the terminal to do that from the recovery console.

---

### Post by savanc on 2007-02-18
Hey pete,

Thanks lot, I will give it a try and lets see wat happens. 
will post u back.

thnax again

---

