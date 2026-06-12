---
title: "CGI page half-complete, the bare code shows up"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by quatre.sushis on 2007-04-11
Hello everyone,

I just came from Windows planet.
Now I am trying to transfer my data which I created in Windows to Linux Ubuntu enviroment.
Then many many problems occured.

I have a few important cgi files, I want to display it on browser (I use FireFox).
It seems all the configuration (of Apache and MySQL) is perfect now (finally).
But when I open the cgi file, the naked code appears.

I read few articles on this problem, but I could not find any of good solution.
Do you know how to display the content (not code) in this Linux enviroment.
After all, my trensfer from Windows to Linux will be completed.

---

### Post by caffienefree on 2007-04-11
Are the files in /usr/lib/cgi-bin?

---

### Post by seshomaru samma on 2007-04-11
I would try to move your CGI to /usr/lib/cgi-bin
and create a symbolic link with this command:
```
sudo ln -s /usr/lib/cgi-bin /var/www/cgi-bin
```

---

### Post by quatre.sushis on 2007-04-11
First of all, I rewrote these 2 files.
/etc/apache2/apache2.conf
/etc/apache2/sites-available/default

Then I put my homepage files into /home/user/homepage/cgi-bin/

However I did like this
perl file.cgi > temp.html
and tried to click directly to this "temp.html", everything goes fine. (the content comes up, not code)

But I put the adress on browser, the bare code come up.

---

### Post by seshomaru samma on 2007-04-11
mmm...
can you see anything in the logs?
/var/log/apache2

---

### Post by quatre.sushis on 2007-04-12
Thank you very much everyone, I finally could solve the problem.
The problem was not on CGI scripts or Apache conf files themselves, but on other

I already hit this command "chmod 755 *.cgi", but it was not enough.
I also had to do "chmod 666 *.txt" for the text files which my cgi programs read.

My cgi program had such a statement 
open "HTMLOUT,'>tempfile.txt'" || die $!";
I didn't give a browser (=user) permission to write into this tempfile.txt, then || it died every time.

Permission problem is really annoying for the newbie coming from Windows planet.

Thank you a lot.

---

