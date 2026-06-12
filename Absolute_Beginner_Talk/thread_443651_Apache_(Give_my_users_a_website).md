---
title: "Apache (Give my users a website)"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-05-14
How do I configure apache so that.

/home/x/www will be a webpage at
[http://localhost/x/](http://localhost/x/) or [http://x.localhost/](http://x.localhost/)

So for any user x that wants to have a webpage. All they have to do is create a ~/www/ directory, and then they can create there website.

Thanks

---

### Post by Cypher on 2007-05-14
Follow my post [here]("http://ubuntuforums.org/showpost.php?p=2638509&postcount=5"). You basically enable the UserDir option, that way each user creates a "public_html" directory and then it's accessible at "http://localhost/~username"

---

### Post by Skrynesaver on 2007-05-14
You need to enable the userdir module and edit it as by default the users' public html directory is ~/public_html/ this can be accessed from a web browser at http:127.0.0.1/~username/.
You can of course symlink to this directory from within the server root

---

### Post by guysmiley25 on 2007-05-14
Awesome guys, thanks heaps. I new it wasn't something too bad but its been along time since I played around with apache.

another way to enable the userdir module is:
```
sudo a2enmod userdir
```

And I'll guest that it is the same to enable any other module.

Just a few more questions, does it have to point to "~/public_html"

And does it have to be "http://hostname/~username"

It would be nicer if there did not have to be the "~" in there. And if the "public_html" could have a different name. However for now this is fine.

Thanks again.

---

### Post by esoterica on 2007-05-14
It sounds like your wanting something that does what cPanel will do for your Apache server...

[http://www.cpanel.net/index.html](http://www.cpanel.net/index.html)

I have no idea what the free alternative to cPanel is though, sorry, I'm sure there is something like it out there and available for free where you don't have to pay the high licensing cost associated with cPanel. I'm only familiar with cPanel unfortunately since I lease a dedicated Linux server and cPanel was included with my hosting for no additional (direct) charge.

This allows each of your users to very easily have their own separate domains on your single server so no need for the ~ in the URL's. If there is another working free alternative to accomplishing the same thing I'd certainly be interested in hearing about it.

This also unfortunately allows each of your users the ability to run insecure scripts and who knows what else on their account though. I'd make sure that at a minimum if your going to allow them this type of access you at least make sure you have mod_security installed on the server with a good mod_security rule set in place.

---

### Post by esoterica on 2007-05-15
Here's another detailed set of instructions for doing this with Tomcat that I just ran across while looking for something else entirely. I don't like Tomcat so I can't help you beyond this. The information may lead you to some other alternatives as well though like .war files that are mentioned.

[http://www.ex-parrot.com/~pete/tomcat-vhost.html](http://www.ex-parrot.com/~pete/tomcat-vhost.html)

He even has a free script there for automating this.

---

### Post by Skrynesaver on 2007-05-15
The userdir.conf file in /etc/apavhe2/mods_enabled allows you to set the default name of this directory.  You can symlink from the server root to that directory as part of a custom user creation command.

---

