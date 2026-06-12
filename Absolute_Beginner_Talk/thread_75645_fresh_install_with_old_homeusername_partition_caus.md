---
title: "fresh install with old /home/username partition causes trouble"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by towsonu2003 on 2005-10-14
I tried to install 5.04 to hard disk which already had a home partition. I did everything correctly (I guess) up until logging in to gnome. Once I logged in, gnome gave weird errors (don't remember now). The errors were about write permissions so I checked them. 

I noticed that although ubuntu set /home/username (my old home partition remounted after fresh install) as my home directory, the owner:group looked weird; they were numbers instead of my actual username and group (something like 1500:2450 instead of owner:group).

I had to 
sudo chown -r username:username /home/username/
so that write permissions are fixed. (For some reason ubuntu did not like username:users scheme.)

Here is the question: what do you do so that ubuntu sets up your old home with correct persissions? was chown -r a correct behavior or did I cause security leaks by doing that? 

PS. I searched google but I guess I could not come up with correct keywords... english=my second language...

---

### Post by fourchannel on 2005-10-14
the reason why it did that was because each user in linux is assigned a number. So on your harddrive, each file is associated with a user number. in most cases, the system will replace the number with the user name, but in your case it did not. reason is your old /home/username was from a different system, and the user number on that system didn't match anything on your comp, so it just used the number.


> was chown -r a correct behavior or did I cause security leaks by doing that? 
yes, it was the right thing to do, no it wont cause security leaks. once you overwrite the user numbers to new ones, ubuntu won't give the error when you start up again.

it is a good practice to make sure that everything in the folder has the right permissions also, to set this execute

```
sudo chmod -R 644 /home/username
``` 
and what that does is make sure that other people can't delete files or erase anything. 

if you want to make it so that nobody but you can see what's in your folder use:

```
sudo chmod -R 600 /home/username
```

---

### Post by towsonu2003 on 2005-10-14
thanks. 
interestingly, both
sudo chmod -R 600
and
sudo chmod -R 644
took away my permissions to enter into my own home directory. So I fixed this with
sudo chmod -R u+x /home/usernames 
I'm pretty sure this not a good thing to do though :)

I guess this is about executing directories? 644 and 600 took away the execute permissions of the folders. Not sure though. Confused.

---

### Post by towsonu2003 on 2005-10-14
hmm
just read about u+X...
So I fixed the executable permissions of everything with:
sudo chmod -R 600 /home/username
sudo chmod -R u+X /home/username
Now I will log off of gnome and log in to see if its conf files are okay.
Still confused, but less..

---

### Post by towsonu2003 on 2005-10-14
everything is fine -thanks
it's interesting that 600 and 644 works for your but not for me.

---

