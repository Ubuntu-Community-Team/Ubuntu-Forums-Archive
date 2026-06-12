---
title: "Installing CGI-Proxy"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by camRW on 2006-06-19
Right now I'm trying to install CGI proxy, but I can't get it working.  I put the CGI script on my server and I changed the permissions to 755 for the script, but when I view it on my server, it just shows a text file.  I think it might be my perl.  When I run 'sudo apt-get install perl' it says that I have the latest version.  In the script I have the #! set to #!/usr/bin/perl (Which was default), but I can't find my perl directory in /usr/bin.  Any ideas on where perl is?

UPDATE: I did have the right perl directory, and it works from command line, but it won't work in my browser!

---

### Post by breaking on 2008-03-08
Try with the new version
[http://rapidshare.com/files/97988487/cgiproxy.2.1beta16.zip.html](http://rapidshare.com/files/97988487/cgiproxy.2.1beta16.zip.html)

---

### Post by lespaul_rentals on 2008-03-10
I know this thread is very old, but I thought I'd reply anyway.

To fix this problem, you need to edit your sitesenabled file and add "ExecCGI" (without quotes) to the path to your website's directory.

---

