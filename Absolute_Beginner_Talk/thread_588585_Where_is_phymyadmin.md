---
title: "Where is phymyadmin?"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by maudmoonshine on 2007-10-23
On searching here this appears to be a common problem?
 
I'm using 7.10 and have LAMP installed and working perfectly.
 
I installed (well, it looks like I did and it, 7.10, says it is installed when I do another apt-get install myphpadmin) it; and, all cockie like, entered [http://192.168.0.50/phpmyadmin](http://192.168.0.50/phpmyadmin) into my browser and nothing happens.
 
Using the documented _[COLOR=#810081]http://localhost/**phpmyadmin**[/COLOR]_ does not work either. Not that I expected it to as the machine I'm running the browser on is on my network, so its localhost will know zilch about the server's localhost.
 
So where is phpmyadmin on my server?

---

### Post by escobar_ on 2007-10-23
This might be a stupid question, but did you remember to run

```
sudo /opt/lampp/lampp start
```

[http://localhost/phpmyadmin]("http://localhost/phpmyadmin") should work.

---

### Post by maudmoonshine on 2007-10-23
>  
This might be a stupid question

 
No such thing where I'm concerned.
 
>  
sudo /opt/lampp/lampp start

 
I've never heard of doing that, or needing to do it. All the LAMP componants start at boot.
 
I ran it just to see and all I get is:
 
sudo: /opt/lampp/lampp: command not found

---

### Post by Crooksey on 2007-10-23
> **maudmoonshine said:**
> No such thing where I'm concerned.

sudo: /opt/lampp/lampp: command not found

```

sudo /opt/lampp/lampp start
```

Thres no : and you need either "start", "stop" or "restart" at the end.

---

### Post by maudmoonshine on 2007-10-23
You misread me, I think.
 
I entered:
 
sudo /opt/lampp/lampp start
 
and I got (get):
 
sudo: /opt/lampp/lampp: command not found
 
as the response.
 
And, after just looking, /opt is completely empty (other than . and .. of course).

---

### Post by maudmoonshine on 2007-10-23
Gave up; uninstalled phpmyadmin; installed it again.
 
Guess what ... it now works!
 
You tell me...

---

### Post by escobar_ on 2007-10-23
Good to hear you got it working. :)

It seems I mixed up xampp and lampp. I installed [xampp]("http://www.apachefriends.org/en/xampp-linux.html") and have to start it the way I described.

---

