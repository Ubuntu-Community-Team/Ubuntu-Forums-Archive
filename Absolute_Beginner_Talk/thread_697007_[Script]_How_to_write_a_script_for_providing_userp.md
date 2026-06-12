---
title: "[Script] How to write a script for providing user/pass to a wireless network"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by just4priya on 2008-02-14
Hi,

"How To: Manual Network Configuration without the need for Network Manager"
I tried the steps from the post and was able to receive an IP.
The network is an unencrypted n/w. Though it requires a username and passwd to be submiited from the web .
How do i automate such steps ..as in after login i directly get connected and there is no need for providing auth details on web page.

Cheers,
just4priya

---

### Post by talsemgeest on 2008-02-15
Could it be done using a shell script?

---

### Post by just4priya on 2008-02-18
i want to pass a username and passwd for a webpage that asks for authentication.

---

### Post by hyper_ch on 2008-02-18
you could write a php script making use of the snoopy library (sourceforge) that will auto-submit the login information. E.g. as a startpage in your browser you'd call then this php script - but it would mean to run apache/php on your computer.

---

### Post by just4priya on 2008-02-19
Could we do it it using nomal shell command wget?

---

### Post by talsemgeest on 2008-02-19
I don't think so...

---

### Post by just4priya on 2008-03-12
The webpage i want to pass this information is .cgi
I want to pass username and password i.e. submit data to .cgi form..

Deperately looking for answers

---

### Post by just4priya on 2008-03-13
Hi All, 

How do i post data to .cgi form ?
I wanted to pass values for username and password which is available in the form.

Any help/suggestions appreciated..

Thanks,
Priya

---

### Post by bodhi.zazen on 2008-03-13
If you want a shell script take a look at expect :

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

	[http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

You could then write a script or enter those commands in /etc/rc.local

---

