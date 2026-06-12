---
title: "can't connect to apt-get through an isa server"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by jefh262 on 2007-09-08
I got firefox to work through its setting but i can't get apt-get to work:
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.16-2ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.16-2ubuntu0.1_i386.deb)
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
 I am at college on a wireless network and the proxy is proxy1 a the port is 8080 the domain is computing, my username is bob and my password is cheese (not really). Can anyone help please.

---

### Post by mikeyphi on 2007-09-08
Have you setup the Proxy settings under 'System/Preferences/Network Proxy?

---

### Post by shearn89 on 2007-09-08
Have a look [here]("http://ubuntuforums.org/showthread.php?t=96802#post533842"), it might solve your problem (sounds similar anyway).

---

### Post by jorno on 2007-09-10
I don't know if anyone still has this problem, but I found my solution in another post.

The steps mentioned here earlier are good and all, BUT if those of  you who's got this problem is in a Windows environment with a Microsoft ISA Proxy that need authentication, this is the solution that worked for me:

You need to install NTLMAPS.

[http://packages.ubuntu.com/feisty/web/ntlmaps](http://packages.ubuntu.com/feisty/web/ntlmaps)
* Go there, and download, either from within Firefox (if you manage to get Proxy working with Firefox - I did, but not apt-get or Synaptics or anything else).
* Download the package for ntlmaps (this is for Ubuntu Feisty)
* Start a terminal, find your downloaded package, and type:
*sudo dpkg -i ntlmaps_0.9.9.0.1-6_all.deb*
This should guide you trough the installation of the package...

BUT, my problems didn't stop there!
After, I had to edit /etc/ntlmaps/server.cfg manually.
( *sudo vim /etc /ntlmaps/server.cfg* )
Then I saw that the config-file was formatted with DOS (not UNIX), so I had to tell vim to convert it to UNIX-format. Do this in vim:
*:set fileformat=unix*
*:wq*
This should convert the file, and save it.
I also had to change some of the options:
Under the [CLIENT_HEADER] section, I had to comment out the first Accept and User-Agent part (Windows 98), and then uncomment the next part (Windows 2000 emulation).
Then I filled in "NT_HOSTNAME" (remembered what PC number this workstation had in Windows), and "NT_DOMAIN").

After those changes, restart ntlmaps:
*/etc/init.d/ntlmaps restart*

And point all your proxy-settings to: [http://127.0.0.1:5865](http://127.0.0.1:5865)

Make a file: */etc/apt/apt.conf*
Acquire::http::Proxy "http://127.0.0.1:5865";

And then try "*apt-get update*".

You could also insert this into:
System -> Preferences -> Network Proxy

And in Synaptics:
System -> Administration -> Synaptics -> Settings -> Preferences -> Network:
Manual proxy configuration:

127.0.0.1 port 5865 (no authentication)


This should do the trick! It did for me.. Please ask if there is something not clear yet, or if I should correct any of this. (Sorry, English is not my native tongue).

---

