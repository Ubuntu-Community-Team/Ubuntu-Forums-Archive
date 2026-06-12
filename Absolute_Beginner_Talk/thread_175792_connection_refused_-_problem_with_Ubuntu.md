---
title: "connection refused - problem with Ubuntu"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by without_nick on 2006-05-13
I've just installed Ubuntu and it seems like I have a silly problem with it. When I try to use firefox, and input any website I receive: "The connection was refused when attempting to contact google.com (or any other website)" I have no idea why is it happening. I can ping without any problems, update and download with wget but cannot access any website. I can't download another browser because I get connection refusal everytime I would try. I checked router logs, and it seems like the connection wasn't really refused, so I assume the connection was refused from other severs and not from router. I really need help with this. Thanks

---

### Post by linuxusr50 on 2006-05-13
Are you running a firewall?  This sounds like a firewall issue or possibly a DNS issue.  You indicate you can ping ok.  Have you tried putting the dot address of the page you want to go to in the browser.  For example instead of putting in [www.google.com](www.google.com) put in googles dot address of [http://72.14.203.99](http://72.14.203.99).  If you are able to get to Google this way you will want to check your DNS settings in /etc/resov.conf

Luck

---

### Post by without_nick on 2006-05-14
Nope, I'm not running any firewall on router however I may be running iptables. That way or any other way of going on anywebsites doesn't work also. Maybe if you know, can you tell me how to somehow turn off iptables?

---

### Post by without_nick on 2006-05-14
seems to work very well. I experimented with resolv.conf a little bit, and I changed the dns servers to the ones provided by my ISP (verizon). Thanks,

---

### Post by linuxusr50 on 2006-05-14
Not sure how to disable but if you do the following as root it should display the chains that built in Iptables.  Unless you have done any iptables configuration, I doubt if that is the problem.

```
iptables -L
```

Your problem sounds like something wierd with the browser or possibly your connection to your provider.  Try the following from a terminal and see if you get a response.  You will need to try the Yahoo site as google does not respond to the telnet request.  If you get the HTML code for Yahoo's site as a response you may want to try a different browser to see if it is only Firefox giving trouble or a bigger issue.

```
telnet yahoo.com 80
```

> Once you get the following response type hello and hit the Enter Key twice.
Trying 66.94.234.13...
Connected to yahoo.com.
Escape character is '^]'.



hello
<ENTER>
<ENTER>

> HTML code from Yahoo's site is returned.
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html><head>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
<meta name="robots" content="noindex,follow">
<title>Yahoo! - Incorrect URL</title>
<meta http-equiv="refresh" content="60; url=http://www.yahoo.com/">
</head>

---

### Post by linuxusr50 on 2006-05-14
Great! Looks like you solved it.  I was in the process of working up a response to your previous post when you got it working, hence the late post.

---

