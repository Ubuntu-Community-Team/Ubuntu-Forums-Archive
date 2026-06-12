---
title: "not sure if im upgreaded to 6.10"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Tobywuk on 2006-10-27
hello :)

I installed Ubuntu on to my desktop yesterday with the free cd's i received from there website for the version before 6.10 (cant remember name of it) 

once i had it set up and installed, i noticed an update icon flashing, so i clicked it, checked all the updates and let it get to work. There is now no flashing update icon.

Does this mean that im updated to 6.10? or how do i tell what version im currently running?

If im not updated, what is the easiest and quickest way for me to update?

Thankyou :)

---

### Post by Sarisar on 2006-10-27
System -> About Ubuntu should tell you which version.  Or About -> Gnome.

Let us know what is says :)

---

### Post by devilsadvocate1987 on 2006-10-27
You are most probably still using Dapper. If i remember correctly, you will have to replace all occurences od 'dapper' in the sources list with 'edgy'

Type " uname -r " in a terminal. If the kernel name it gives you ends in 'generic' then you are using edgy. Otherwise you are using dapper.

---

### Post by az_human on 2006-10-27
It doesn't sound like you would be.  I believe you'd have to change all of your repositories in your /etc/apt/sources.list file from dapper to edgy and then run a 'sudo apt-get dist-upgrade' before it's going to upgrade your distribution.  If you leave the repositories as dapper then you will continue to receive updates for dapper.  It shouldn't automatically upgrade you to edgy without you modifying that file.

---

### Post by Jay_Dogg on 2006-10-27
Type "lsb_release -a" in a terminal (without "").
That should tell which version you are using.

---

### Post by Tobywuk on 2006-10-27
ah, ok thanks! i cant check it right now as im on my laptop away from home.

Is the easiest way to upgrade to edgy just to download the new ISO, burn it on to disk and install it?

Is there many new features on it that a beginner like me would find different or improved?

thanks :)

---

### Post by bulldog on 2006-10-27
> **Tobywuk said:**
> ah, ok thanks! i cant check it right now as im on my laptop away from home.

Is the easiest way to upgrade to edgy just to download the new ISO, burn it on to disk and install it?

Is there many new features on it that a beginner like me would find different or improved?

thanks :)

A beginner should stick with Dapper :D 

It's better documented and you will get more help if you have a problem.

But don't let me hold you away from Edgy,if you feel comfortable with Ubuntu,just give it a try.

---

