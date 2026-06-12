---
title: "I need help to setup a server and I'm a newbie!!"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Wariwba on 2008-02-11
Hi.

To start with I guess I should tell you that I'm a newbie!!! I have never tried to use any kinds of linux before. I have installed Ubuntu 7.10 server edition and I want to install Plone 3 on it and setup a intranet. (go to [http://plone.org]("http://plone.org") to get more info about Plone) Here's my problem.

My first problem is that I have to connect to the internet through a proxy-server. The proxy is proxy.something.somethingels.com and it's using port: 8080 - How do I configure Ubuntu the right way? I typed [http://proxy.something.somethingels.com/8080](http://proxy.something.somethingels.com/8080)  under the install -but I don't think it works...

I'm trying to follow this guide to setup Plone 3: 
[http://www.semioticpixels.com/blog/2007/infrastructure/install-plone-3-on-ubuntu-710/]("http://www.semioticpixels.com/blog/2007/infrastructure/install-plone-3-on-ubuntu-710/") 

...when I get to step 2 - I get the message "Connection refused". That's why I think that there's something wrong with the way I connect to the internet.

I hope you can help me - regards
Wariwba.

---

### Post by hyper_ch on 2008-02-11
(1) if you want to setup a full server for hosting/email/... then I'd follow this guide here:
[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)
I'd even suggest to use debian instead of ubuntu... but that's my preference.

> **Wariwba said:**
> I want to install Plone 3 on it and setup a intranet.
Shall the server only run in the intranet or also be reachable through the internet?

> **Wariwba said:**
> My first problem is that I have to connect to the internet through a proxy-server. The proxy is proxy.something.somethingels.com and it's using port: 8080 - How do I configure Ubuntu the right way? I typed [http://proxy.something.somethingels.com/8080](http://proxy.something.somethingels.com/8080)  under the install -but I don't think it works...
Who is tryinjg to connect through the proxy server? You or the server you want to setup?
Don't use a slash ("/") for the port but a column (":") --> [http://proxy.something.somethings.com:8080](http://proxy.something.somethings.com:8080)


> **Wariwba said:**
> 
...when I get to step 2 - I get the message "Connection refused". That's why I think that there's something wrong with the way I connect to the internet.

If the network isn't setup proprely the server cannot access the internet and download it. If you don't want to the server to get outside access, you could of course download it to your computer and then transfer it to the server with a usb pendrive, cd... or if you are in the local network you can ssh into the server and use scp for transfer.

---

### Post by Wariwba on 2008-02-11
Hi and thanks for the response.


> Shall the server only run in the intranet or also be reachable through the internet?
The server should only run the intranet (Plone 3). It will be connected to another local Windows 2003 server that has internet access. No, at this point the intranet shouldn't be reachable through the internet.

> Who is tryinjg to connect through the proxy server? You or the server you want to setup?
Don't use a slash ("/") for the port but a column (":") --> [http://proxy.something.somethings.com:8080](http://proxy.something.somethings.com:8080)
The server I'm trying to setup should access the internet through another proxy-server. How do I change the proxy from "/" to ":"

Thanks.

---

