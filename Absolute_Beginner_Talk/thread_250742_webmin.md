---
title: "webmin"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by Ueler on 2006-09-04
Hello,
I have installed webmin however when I get the login screen and I try and login as root and my root password I can't get in. Any suggestions?

---

### Post by jorn on 2006-09-04
By default there is no root account. Use this step to create one:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_set.2Fchange.2Fenable_root_user_password](http://easylinux.info/wiki/Ubuntu_dapper#How_to_set.2Fchange.2Fenable_root_user_password)

---

### Post by RichJacot on 2006-09-04
Hello,

I don't recall exactly what I did but:

Does your /etc/webmin/miniserv.users  file look like this?

root:x:0

---

### Post by RichJacot on 2006-09-04
Hello,

I don't recall exactly what I did but:

Does your /etc/webmin/miniserv.users  file look like this?

root:x:0

Thats really " root : x : 0 "  without the spaces.

---

### Post by ryedunn on 2006-09-04
Im having exactly the same problem and that is what it looks like if I change it to something like
ryedunn : x : 0
it will let me in but no modules are loaded  See #20 in the FAQ
[http://www.webmin.com/faq.html](http://www.webmin.com/faq.html)
Unfortunately this really doesnt help us.

I have verified createing a root account found in the previous post does work.

---

### Post by Ueler on 2006-09-04
ThanksJorn!
I am able to login now.

---

### Post by SlowYaRoll on 2006-09-19
There's a new version of webmin out that allows you to login with users that have sudo root privs.  This means you no longer have to tinker with the activing the root account.

But if you're not using the latest version of webmin, this will work:

Here's another way to install webmin, which is very simple. This should apply to all Ubuntu versions, but then again, I'm still very new to Linux.

Download the webmin DEB file from Webmin's website.
([http://www.webmin.com](http://www.webmin.com))
([http://www.webmin.com/download.html](http://www.webmin.com/download.html))

Go to the directory where you've downloaded the DEB file.
(i.e. cd /home/usernamehere/Desktop/)

Run the dpkg --install command on the DEB file you've downloaded.
(i.e. sudo dpkg --install webmin_1.290.deb)

----This will take a few moments to install----

At this point, webmin is installed and running. You may access Webmin via your web browser.
([http://localhost:10000)](http://localhost:10000)).

You'll be prompted for a username and password. By default, Webmin copies your system's root password as the Webmin root password. Since the Ubuntu installation never prompts you to set a root password, you are unable to enter the root password.

To fix this problem, run the following command:
sudo /usr/libexec/webmin/changepass.pl /etc/webmin root enterpasswordhere

You should now be able to log into Webmin with the username root and whatever you've set as the password.

---

