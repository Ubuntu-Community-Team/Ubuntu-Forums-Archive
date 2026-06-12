---
title: "Changed wrong permissions"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by benzies on 2006-11-20
It appears that when i thought it would be smart to chmod 777 -R /*
it turns out it causes more trouble than its worth

When i login i get an error message telling me to change permissions to 664 $home and somthing about a dprmc file ...

If somone could help putting this all back to normal that would be great.

---

### Post by bodhi.zazen on 2006-11-20
I have seen this before and I think it is easier to re-install.

For your .dprmc file"

.drmc file permissions:

	sudo chmod 644 .dmrc

	sudo chown username .dmrc

	sudo chmod 755 /home/username

	sudo chown username /home/username



	OR

	sudo chown  username userfolder 

	sudo chmod 755 /home/userfolder

	sudo rm -rf /home/userfolder/.dmrc



	[http://www.ubuntuforums.org/showthread.php?t=168015](http://www.ubuntuforums.org/showthread.php?t=168015)

---

### Post by benzies on 2006-11-20
ahh thankyou very much.  But one must ask, what if i chown -R benzies /*

---

### Post by benzies on 2006-11-20
haha chown-R doesnt work anyway

---

### Post by benzies on 2006-11-23
ok, so your advice was great thanks. But now im faced with more problems and that is ive lost colours in my terminal, and programs are reporting with errors that the wrong permissions are allowed, and wont install.

How can i revert EVERYTHING ?? :(

---

### Post by bodhi.zazen on 2006-11-23
> **benzies said:**
> ok, so your advice was great thanks. But now im faced with more problems and that is ive lost colours in my terminal, and programs are reporting with errors that the wrong permissions are allowed, and wont install.

How can i revert EVERYTHING ?? :(

The problem is we would need to know the default permissions of each and every file and directory !

Try this script:> 
#! /bin/bash

for X in /*
	do

	if [ "$X" != /home ]
	then
		chmod="$chmod $X"
	fi
done

for X in $chmod
	do
	if [ "$X" != /root ]
	then
	sudo chmod 755 $X $X/*
	else
	sudo chmod 750 $X $X/* 
	fi
done

Save this script in /home/user_name as chmod1

Then:```
chmod a+x chmod1
sudo ./chmod1
```

I do not know if this will help or not.

You could always re-install !

---

### Post by benzies on 2006-11-23
Okay did what you said. Terminal now opens with the error "cannot execute child process" and this too sudo: /etc/sudoers is mode 0755, should be 0440

now i cant change any permissions using chmod.
 

BTW i have re-installed i have seperate partitions...

---

### Post by benzies on 2006-11-23
im really not looking forward to another re-install. But it looks like i may have to now.  BUt, when i re-install there will still be permission errors on my home drive... 

So now im just going to guess i will make a new user, copy the contents of the old user and hopefully the permissions should all be set fine again...

---

### Post by bodhi.zazen on 2006-11-24
> **benzies said:**
> im really not looking forward to another re-install. But it looks like i may have to now.  BUt, when i re-install there will still be permission errors on my home drive... 

So now im just going to guess i will make a new user, copy the contents of the old user and hopefully the permissions should all be set fine again...

I am afraid reinstalling is easiest.

You can always set the permissions either by booting to the live CD or to the rescue mode.

FYI: This is how we all learn Linux. I have broken my share of installs and I know the feeling :lol:

There is no need to change the permissions to 777 as you should be able to access everything as root....

---

