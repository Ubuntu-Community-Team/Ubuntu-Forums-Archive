---
title: "CLI command to search for a file?"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Scorpuk on 2006-09-30
Need to find a file on my computer, but can only use cli as I am using putty to connect to it while at work.

Basically I have installed webmin, but need to run the command:

```
sudo /usr/libexec/webmin/changepass.pl /etc/webmin root enterpasswordhere
```


When I go into the usr folder there is no libexec folder. :???: 

I am guessing that when I used dpkg to install it, it got installed elsewhere as I can still goto the login screen on my browser.



So need to locate the file changepass.pl


Tnx.

---

### Post by klytu on 2006-09-30
> **Scorpuk said:**
> Need to find a file on my computer, but can only use cli as I am using putty to connect to it while at work.

Basically I have installed webmin, but need to run the command:

```
sudo /usr/libexec/webmin/changepass.pl /etc/webmin root enterpasswordhere
```


When I go into the usr folder there is no libexec folder. :???: 

I am guessing that when I used dpkg to install it, it got installed elsewhere as I can still goto the login screen on my browser.



So need to locate the file changepass.pl


Tnx.

Try:

```
sudo updatedb
```

Wait for that to finish, then do:

```
locate changepass.pl
```

Hope this helps you.

---

### Post by Scorpuk on 2006-09-30
> 
```
sudo updatedbWait for that to finish, then do:
```



```
locate changepass.plHope this helps you.
```

The above worked a charm.


The file was installed in usr/share/webmin :D 


Tnx.

---

