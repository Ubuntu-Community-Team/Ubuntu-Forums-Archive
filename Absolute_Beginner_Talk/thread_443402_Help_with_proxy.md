---
title: "Help with proxy"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by nho3 on 2007-05-14
I am an Information Systems Specialist aka IT Analyst. I am new to Linux but not to computers. I want to use Linux here at work on a Virtual Machine. I have VM Server 1.0.3 installed and Ubuntu is running on it. I am currently using Firefox in Ubuntu to write this post. At my work place we have a Microsoft based Proxy server running. It uses AD accounts to authenticate. Firefox is able to authenticate with the proxy and access websites using the credentials I put in the Firefox properties interfaces. I have tried to set the proxy settings in apt.conf so that APT and the Synaptic program can access the internet.

The following is my current apt.conf. 

```
http::proxy "http://domain\@jfontenot:password@10.10.16.5:8080/";
ftp::proxy "http://domain\@jfontenot:password@10.10.16.5:8080/";
```

At this point the Network Proxy GUI is set to "Direct Connection to the internet" I read somewhere on the forums that it is best to not use that setting. Somebody said it was best to set the proxy in the configuration files. I tried both ways and neither works. I've also tried using Acquire::http::proxy etc but that doesnt work either.

Right now when I do **sudo apt-get update** I get error "111 connection refused." I have tried changing the format of the proxy command in the apt.conf but this format is the only one that works. If I leave out the **domain\@** part it will gives me a proxy authentication error.

Oh and I am using the latest version of Ubuntu.

---

### Post by Cypher on 2007-05-14
Perhaps [this link]("http://www.getautomatix.com/wiki/index.php?title=Proxy_configuration") might help?

---

### Post by nho3 on 2007-05-14
> **Cypher said:**
> Perhaps [this link]("http://www.getautomatix.com/wiki/index.php?title=Proxy_configuration") might help?

I tried everything on that site and I still get error 111. 

I installed Ubuntu on my home computer and everything worked fine. It seems to be a problem with the proxy here at work :( Please help.

---

### Post by Cypher on 2007-05-14
Within firefox, are you simply using the syntax of 
```

username:password@proxy-server:proxy-port

```
and have it work?

---

### Post by nho3 on 2007-05-14
> **Cypher said:**
> Within firefox, are you simply using the syntax of 
```

username:password@proxy-server:proxy-port

```
and have it work?
In Firefox I just put in the ip and port in their properties dialog box. When I opened Firefox it asked for login name and password. Once I put that in it worked.

---

### Post by nho3 on 2007-05-16
I still can't get the Synatptic software to use the proxy or apt-get update.

---

### Post by nho3 on 2007-05-25
Can somebody please help me? I still can't get the proxy to work.

---

