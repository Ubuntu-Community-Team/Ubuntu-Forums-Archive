---
title: "How can i install Greasemonkey on my profile in firefox ?"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by tiptip on 2007-02-17
Hello,
I wanted to install Greasemonkey from :
[http://greasemonkey.mozdev.org/](http://greasemonkey.mozdev.org/)

But the only way i can install it was by running :
```
sudo firefox
```
(it doesnt let me install it as a normal user).
But when i run firefox with "sudo firefox" it doesnt enter to my profile  :/

How can i install Greasemonkey and use it on my user account ?

p.s.
At synaptic there isn't the newest version of Greasemonkey.

---

### Post by sumguy231 on 2007-02-17
Greasemonkey is just a normal extension, so it should install to your profile directory in ~/.mozilla. What happened when you tried to install Greasemonkey? Have you tried installing it from addons.mozilla.org?

---

### Post by tiptip on 2007-02-17
Yes, i tried but i get the same result :

[[IMG]http://img256.imageshack.us/img256/7200/screenshot1lz4.png[/IMG]](http://imageshack.us)
[http://img256.imageshack.us/img256/7200/screenshot1lz4.png](http://img256.imageshack.us/img256/7200/screenshot1lz4.png)

In the "FirefoxError Console" i see : "InstallLocation has no properties" and clicking brings me to this line of code :
```
var installLocation = this.getInstallLocation(item.id);
```

---

