---
title: "Is desktop suuposed to be permissions 777?"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-20
the question lies in the title...:)

---

### Post by ComplexNumber on 2006-05-20
[quote=erik1397]the question lies in the title...:)[/quote]no, but it can be if you have no internet access and you're the only user. . that makes everything readable, writable, and executable. when i want to make something that was previously owned by root to be writable etc, i always do a 'chmod -R 777 <file name>' on it.
if its multiuser system, you don't want other individuals stealing your mp3's and changing the date of your wedding anniversary reminder in evolution so that the wife clouts you, etc.

---

### Post by Mustard on 2006-05-20
I think I prefer 700 myself.  I've got multiple users on this system though, so I don't like other people peeking through my stuff.

---

### Post by user1397 on 2006-05-20
[quote=ComplexNumber]no, but it can be if you have no internet access and you're the only user. . that makes everything readable, writable, and executable. when i want to make something that was previously owned by root to be writable etc, i always do a 'chmod -R 777 <file name>' on it.
if its multiuser system, you don't want other individuals stealing your mp3's and changing the date of your wedding anniversary reminder in evolution so that the wife clouts you, etc.[/quote]
wow thanks for that warning! i do have an internet connection and im the only user, but my desktop permissions was at 777?! i changed it to 755. 
Do you think i got hacked??!! :)

---

### Post by ComplexNumber on 2006-05-20
**erik1397**
what i want you to do is to set the directory  /home/<username> to 700 by using sudo chmod 700  /home/<username>. 700 just makes it so that only the owner (ie you) can read, write, and execute your home directory. other users can't see inside your home directory. thats the only directory that matters. it doesn't matter what the permissions are inside your home directory (except for those of sensitive data etc) are because other users can't access your home directory, so the permissions inside are largely irrelevant.
and no, i don't think you've been hacked :).

---

### Post by jrobinson5 on 2006-05-20
What do all these numbers mean? Like 777 and 775 and 700.

---

### Post by professor_chaos on 2006-05-20
[QUOTE=jrobinson5]What do all these numbers mean? Like 777 and 775 and 700.[/QUOTE]

this might be helpful
[http://www.elated.com/tutorials/management/unix/permissions/](http://www.elated.com/tutorials/management/unix/permissions/)
Number 	  	Read (R) 	Write (W) 	Execute (X)
0 	  	No 	No 	No
1 	  	No 	No 	Yes
2 	  	No 	Yes 	No
3 	  	No 	Yes 	Yes
4 	  	Yes 	No 	No
5 	  	Yes 	No 	Yes
6 	  	Yes 	Yes 	No
7 	  	Yes 	Yes 	Yes

---

### Post by user1397 on 2006-05-20
[quote=ComplexNumber]**erik1397**
what i want you to do is to set the directory  /home/<username> to 700 by using sudo chmod 700  /home/<username>. 700 just makes it so that only the owner (ie you) can read, write, and execute your home directory. other users can't see inside your home directory. thats the only directory that matters. it doesn't matter what the permissions are inside your home directory (except for those of sensitive data etc) are because other users can't access your home directory, so the permissions inside are largely irrelevant.
and no, i don't think you've been hacked :).[/quote]
thanks for the info, i changed my /home permissions

---

### Post by jrobinson5 on 2006-06-06
Thanks, Eric. That was just what I needed to know.

---

