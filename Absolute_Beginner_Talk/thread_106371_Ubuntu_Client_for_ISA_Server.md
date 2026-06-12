---
title: "Ubuntu Client for ISA Server"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by Trinimuse on 2005-12-20
I'm new to Ubuntu using the 64-bit version.  I have an ISA Server running on my Internet server and all the client PC's are Windows XP Pro 32 bit.  I tried running Windows XP 64 pro but the ISA client installer is 16 bit and wont work and there's no 64 bit ISA client.  So I installed Ubuntu on a 64 bit PC to see if that could work.  I can see my entire network including the DHCP and DNS, but cant access the Internet.  I've tried searching but results are sketchy.  Can this be done and if so can someone point me in the right direction?  If it wont work, what will or might?  If this is an absolutely nooobie question, please go easy on me.  :confused:  :(  :???:

---

### Post by cwaldbieser on 2005-12-20
[QUOTE=Trinimuse]I'm new to Ubuntu using the 64-bit version.  I have an ISA Server running on my Internet server and all the client PC's are Windows XP Pro 32 bit.  I tried running Windows XP 64 pro but the ISA client installer is 16 bit and wont work and there's no 64 bit ISA client.  So I installed Ubuntu on a 64 bit PC to see if that could work.  I can see my entire network including the DHCP and DNS, but cant access the Internet.  I've tried searching but results are sketchy.  Can this be done and if so can someone point me in the right direction?  If it wont work, what will or might?  If this is an absolutely nooobie question, please go easy on me.  :confused:  :(  :???:[/QUOTE]
Are you making your PCs authenticate with ISA to access the Internet?  If so, are you using basic authentication or NTLM authentication or something else?

---

### Post by Trinimuse on 2005-12-20
Basic authentication.  thank you for replying.  If there is a webpage or url that you can send me to, it'll be greatly appreciated.

---

### Post by cwaldbieser on 2005-12-20
[QUOTE=Trinimuse]Basic authentication.  thank you for replying.  If there is a webpage or url that you can send me to, it'll be greatly appreciated.[/QUOTE]
Well, with basic authentication I think it should be pretty easy if I am reading your setup correctly.

Am I correct that you have your ISA server set up as an HTTP proxy server?  If you are using Firefox on Ubuntu, you need to Edit -> Preferences -> General -> Connection Settings to set up the proxy.  for the URL to the proxy, you should use something like:

[http://user:password@proxy-server-addr:port](http://user:password@proxy-server-addr:port)

That should work fine for basic authentication, I would think.

For Konqueror, Settings -> Configure Konqueror -> Proxy.  You can manually configure the proxy here, and the form gives you a place to enter the authorization info.

For command line tools like wget, apt-get, curl, etc., most of them respect the HTTP_PROXY and FTP_PROXY enviroment variables, which are set up like the URL fo Firefox, above.  You can set them in you ~/.bashrc file.

For synaptic, I think there is also a proxy section under the tools menu.

---

### Post by Trinimuse on 2005-12-21
thank you, thank you.  I did something else though.  I completely removed my ISA server.  Now my network runs with a linux box with IPCOP as my router.  Its faster, and I dont have to worry about 32bit, 64-bit or cross platform issues.  Thank you again!

:p

---

