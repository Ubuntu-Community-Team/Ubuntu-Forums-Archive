---
title: "[SOLVED] Getting a little fed up here,"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-12-01
Take a look at this and then tell me why

[IMG]http://img.photobucket.com/albums/v519/Romin_1/Screenshot-lostfoundProperties.png[/IMG]


I'm not the owner or have authority. Who is the owner, Sanity Clause? I am the _only_ person in the world that has ever laid eyes or hands on this PC. This is not the only instance of something like this happening. Bad enough I have to enter a password everytime I try to do something.

Now that the rant is over does anyone have a solution to this? Please?

Jon

---

### Post by overdrank on 2007-12-01
Hi and maybe this link will help
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mellowd on 2007-12-01
What do you need to do with the lost+found folder?

---

### Post by Dr Small on 2007-12-01
You must login as root in order to change the permissions of Lost+Found.
Complimenting overdrank's post ;)

---

### Post by lespaul_rentals on 2007-12-01
Not sure what file you are fed up over, but if you run the following command you will see a difference:

```
sudo chown -R [your_user_name] [/path/name_of_file]
```

---

### Post by victorbrca on 2007-12-01
Hey Jon,


 Hang in there. This is one of the strongest part or Linux, permissions. You are the only one using the PC, but you are not the only user....

  Here's another link to help you understand...

[http://www.freesoftwaremagazine.com/articles/users_in_ubuntu](http://www.freesoftwaremagazine.com/articles/users_in_ubuntu)


Vic.

---

### Post by PmDematagoda on 2007-12-01
You are asked the password and not given access to system files for a good reason, security and to stop your OS from being messed up. In some cases it can even protect you from yourself since you can destroy the whole OS by deleting a few critical system files if you are not careful.

If you require full control over your OS, then you can boot the Recovery Mode of Ubuntu where you will be given full powers, keep in mind that this is not very safe as the reason I gave before applies and it would also simplify the installation of root kits into your system(If a root kit gets into your system, then you may have a very hard time and will have to reinstall the OS) which can occur when you install applications or do patches from untrusted sources.

---

### Post by Romin-1 on 2007-12-01
Thanks to all of you for the replies and links. I checked them out and did learn a couple things.

No particular file has me fedup, just being denied access to anything ticks me off as it is my PC.

And lastly, if you must know why I was in that particular file, just snooping, plain and simple.

Time for Old Grouchy here to hit the sack.

Thanks again guys,

Jon

---

### Post by Capricori on 2007-12-01
> **Romin-1 said:**
> just being denied access to anything ticks me off as it is my PC.

You're not exactly being denied access, since you know the password. I think of it as my computer's way of stopping me doing stupid things, by getting me to snap back into 'sensible' for a second.
Between myself and my laptop, one of us has to be responsible - the 'root user' thing means it doesn't have to be me :)

Regards, 
Capricori

---

### Post by mellowd on 2007-12-01
Some things you just shouldn't touch, that's why it's protected.

I could say, why can't I delete vmlinuz? The Pc belongs to me. Thing is, if I do my installation is screwed

---

### Post by eolson on 2007-12-01
And more imprtanantly,  it helps keep anybody else from messing with it.   Viruses and all ya know.

---

