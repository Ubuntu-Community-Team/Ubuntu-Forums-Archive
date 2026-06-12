---
title: "phpmyadmin"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by EtrOFsouls on 2006-03-19
I'm working on setting up Apache - php - mysql. 

I got everything installed, and tested Apache and php by using [http://localhost/testphp.php](http://localhost/testphp.php) and got the info screen that I was supposed to get, so I'm happy up to this point.

However, I also tried using phpmyadmin, with [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)  and come to a login screen. So I'm thinking that all is good, but when I try to login using my normal login, I get an access denied msg. I've also tried as root, but get the same result.

So..I'm wondering...do I need to setup a specific user in order to access phpmyadmin, or is there maybe just something wrong with my setup?

Any help or advice is greatly appreciated.

Thanks in advance

---

### Post by dermotti on 2006-03-19
Have you set the root password for mysql yet? If not you can try just logging in as root, and dont put a password in the password field. Otherwise you will need to set a root password.

---

### Post by EtrOFsouls on 2006-03-19
Yeah, just after posting this, I stumbled upon the config file and noticed that 'root' was the default login with no password. Talk about feeling stupid  lol

Now all I have to figure out, is what to do with all this stuff. All I really want, is to create a nice intranet site for my company. Something other than the plain old html site we have now. I know absolutely nothing about apache, mysql, and php. I guess I really have my work cut out for me.

Thanks for the quick reply :)

---

