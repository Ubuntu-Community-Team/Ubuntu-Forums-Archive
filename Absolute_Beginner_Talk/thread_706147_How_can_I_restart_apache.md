---
title: "How can I restart apache"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Usta_AsH on 2008-02-24
hello, how can I restart apache server?

---

### Post by adw on 2008-02-24
In console, type the following
```
sudo /etc/init.d/apache2 restart
```
also, stopping apache easily done with
```
sudo /etc/init.d/apache2 stop
```

---

### Post by angrboda on 2008-02-24
Depe&#324;ding on how you mean to restart - something like this:

```

sudo /etc/init.d/apache2 restart
```

or

```
apachectl -k restart
```

You will need the permissions to do that - so a sudo or su might be needed.

For more detailed instructions see:

[http://httpd.apache.org/docs/2.0/en/stopping.html]("http://httpd.apache.org/docs/2.0/en/stopping.html")

---

### Post by tehnad on 2008-03-13
> **angrboda said:**
> Depe&#324;ding on how you mean to restart - something like this:

```

sudo /etc/init.d/apache2 restart
```

or

```
apachectl -k restart
```

You will need the permissions to do that - so a sudo or su might be needed.

For more detailed instructions see:

[http://httpd.apache.org/docs/2.0/en/stopping.html]("http://httpd.apache.org/docs/2.0/en/stopping.html")

Your post is somewhat conflicting. If the user has Apache 1.3.* installed then they can use ```
apachectl -k restart
```. If they have Apache 2.* installed then the command is: ```
apache2ctl -k restart
```.

---

