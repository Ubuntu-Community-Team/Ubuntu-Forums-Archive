---
title: "easyubuntu install"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by gacostac on 2007-10-06
Hi everyone

i tried to install easyubuntu and got this:
"
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package easyubuntu needs to be reinstalled, but I can't find an archive for it.'
"
Now I cant update my computer or use the update manager. I get this rerror every time. 

I have know idea how to solve it, any help is appreciated.

---

### Post by santiagoward2000 on 2007-10-06
Hi gacostac!
Sorry, I don't know how to help you solve your problem, but I just wanted to give you some advise: don't use EasyUbuntu. When I tried it, it messed with my computer. Besides, most of the packages it brings come inside Ubuntu's repositories.
I hope you can fix your problem. Good luck!!

---

### Post by Incense on 2007-10-06
What were you trying to install? Codecs maybe? Check here to install everything you need. 

[http://https://wiki.ubuntu.com/RestrictedFormats]("http://https://wiki.ubuntu.com/RestrictedFormats")

Most everything else is in the repos. I'm actually not entirely sure if Easy Ubuntu is even maintained anymore. The site seems to mention Dapper a lot....

---

### Post by gacostac on 2007-10-06
Thanks guys

Yes, i was trying to install codecs. I will try the other options you mention, How about automatix, is that any good?
Anyway, i still have the problem, I cant run update manager or package manager.... Any ideas on that?

---

### Post by Incense on 2007-10-06
> **gacostac said:**
> Thanks guys

Yes, i was trying to install codecs. I will try the other options you mention, How about automatix, is that any good?
Anyway, i still have the problem, I cant run update manager or package manager.... Any ideas on that?

Automatix is down all the time, and you'll hear a lot of people telling you to stear clear of that program as well. Yeah, it does make things easy, and I have used it in the past with no problems so you can go that route. I just thinkwith recent releases of Ubuntu that you can install codecs and programs so easy that you just don't need a program like Automatix. You learn a bit more about the system when you do it yourself as well. It's up to you.

---

### Post by Incense on 2007-10-06
> **gacostac said:**
> 
Anyway, i still have the problem, I cant run update manager or package manager.... Any ideas on that?

What happens if you run 

```
sudo apt-get update
```

---

### Post by Frak on 2007-10-06
Automatix will be better in the future, but it may be possible that you have broken packages, run
```
sudo apt-get --fix-broken
```

---

### Post by por100pre1 on 2007-10-06
Do this to remove EasyUbuntu:

```
sudo dpkg --remove --force-remove-reinstreq easyubuntu
```

---

### Post by gacostac on 2007-10-07
Thanks a lot guys, this site is a great help for beginner like me. I believe "fix borken" did it :) problem solved.
From now on i will try installing things myself. Can anyone recommend a good place to learn how to do it?

---

### Post by Frak on 2007-10-07
> **gacostac said:**
> Thanks a lot guys, this site is a great help for beginner like me. I believe "fix borken" did it :) problem solved.
From now on i will try installing things myself. Can anyone recommend a good place to learn how to do it?
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

