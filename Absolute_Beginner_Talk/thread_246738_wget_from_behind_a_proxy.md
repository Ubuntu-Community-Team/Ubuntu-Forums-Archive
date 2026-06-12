---
title: "wget from behind a proxy"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by bplus on 2006-08-29
Hi,
I ve been reading the wget manual and it says I can specify a proxy at the command line. Which is fine for most things.
However I'd like to set it up permanently to use a proxy is there any way to do this?

thanks in advance!

---

### Post by djf on 2006-08-29
Wget will check for the following variables in the environment:

http_proxy - This variable should contain the URL of the proxy for HTTP connections. 
ftp_proxy - This variable should contain the URL of the proxy for HTTP connections. 

If they are set, wget will automatically use the specified proxies . It is quite common that HTTP_PROXY and FTP_PROXY are set to the same URL. I assume you use the bash shell (default in ubuntu). You can specify the HTTP proxy environment variable in your ~/.bashrc by adding a line like:

```
export http_proxy=www.your.proxy:port
``` (IP:Port is also possible)

You can list all set environment variables by typing "printenv" in your terminal, or you can see a single variable by typing "printenv variablename" (eg. printenv PATH). If it worked printenv http_proxy should return [www.your.proxy:port](www.your.proxy:port)

P.S. The variable names are case sensitive and they used to be all caps. Which means that some tools will ignore http_proxy and check for HTTP_PROXY instead.

---

### Post by bplus on 2006-08-30
hey thanks for that, I did that thing you suggested with setting the proxy



but I get this error now:
> 
Error in proxy URL [ftp://*****/*****@wwwcahce****.***.uk:8080:](ftp://*****/*****@wwwcahce****.***.uk:8080:) Must be H TTP.

I didnt try to set a ftp so I dont know why its bringing this up when I setup http proxy.

Any ideas?

---

### Post by djf on 2006-08-30
Well, [ftp://*****/*****@wwwcahce****.***.uk:8080](ftp://*****/*****@wwwcahce****.***.uk:8080) is not a Webserver, but a FTP server (as indicated by the ftp:// ) so wget refuses to use it for downloading off webservers.

Try using an HTTP server ```
http://someproxy:port
```. 


P.S. I noticed a little mistake in my above post: 

ftp_proxy - This variable should contain the URL of the proxy for FTP connections.

---

