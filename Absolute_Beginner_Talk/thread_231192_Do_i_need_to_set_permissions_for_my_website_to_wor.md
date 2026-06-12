---
title: "Do i need to set permissions for my website to work?"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by Hawkowl on 2006-08-07
My site isn't working..
Could it be because i have not got the permissions right?
The folder /var/www has root as owner and root as user

and number view 755  
is that normal?

thx

---

### Post by mority on 2006-08-07
To get help you should describe as exactly as possible what you want to do, what you did so far to achieve that, and what is going wrong. Do not make assumptions about what's going wrong, or at least, don't let those assumptions be the only information you give the reader of you post and potential helper (maybe you want to read this excellent document: [How To Ask Questions The Smart Way]("http://catb.org/~esr/faqs/smart-questions.html")).

So you want to set up a webserver. What package did you install? Maybe apache or apache2? Please point your browser to [http://localhost](http://localhost) and tell us what you see.

---

### Post by Christmas on 2006-08-07
Not sure if this is what you are looking for, however I'm using Apache as my web server and for every file that I have to write using PHP I had to put the permissions to read/write for owner, group & others. So just "chmod a+rw filename" where filename could be located in your /var/www or something else. For example I put all my files where the page hits and page visitors numbers are kept in /var/tmp/kh.

LE: Also, I found out this by reading the Apache's FAQ, it contains every information you could think of there. Some links:

[http://www.apache.org/](http://www.apache.org/)
[http://httpd.apache.org/docs/2.0/](http://httpd.apache.org/docs/2.0/) (I think these are the right ones)

And also if you're intersted in HTML, PHP or whatever language of this kind:

[http://www.echoecho.com/school.htm](http://www.echoecho.com/school.htm)
[http://techtuts.com/](http://techtuts.com/)

---

### Post by Hawkowl on 2006-08-07
I recently installed ubuntu on a brand new box.
I have the gnome interface on.
I installed apache2.
I also tried installing a number of virtual hosts.

The relevant .conf files are pasted in their entirety a few posts below in the post "virtual hosts problem"

would appreciate any help :-k

---

### Post by Christmas on 2006-08-07
It should be so simple setting up your server. I mean all you have to do is copy/paste the html or php or whatever files into your /var/www then just go to [http://your_ip_here/your_page.html](http://your_ip_here/your_page.html). Or [http://127.0.0.1/your_page.html](http://127.0.0.1/your_page.html) or [http://localhost/your_page.html](http://localhost/your_page.html). To copy them use either Nautilus as root (gksudo nautilus) or open the Terminal and "sudo cp your_file /var/www". You can also just simply delete the apache's default files from there.

---

