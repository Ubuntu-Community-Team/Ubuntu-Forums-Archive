---
title: "using open ssh"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by DarchAengel on 2007-08-29
I am on a mac and I have my gf on linux.  I wanted to know if there was a way for me to use ssh so as to directly connect to her so I can send her files.  If someone could walk me through this that would be great.

---

### Post by finer recliner on 2007-08-29
[https://help.ubuntu.com/community/SSHHowto?highlight=%28ssh%29](https://help.ubuntu.com/community/SSHHowto?highlight=%28ssh%29)

---

### Post by DarchAengel on 2007-08-29
Okay my question is this...In order to use ssh do the computers in question need to be connected to the same network?  My problem is that I am here in NYC and my gf, who I am trying to connect to lives upstate.  If ssh is the answer I would really appreciate some help understand the process outlined on help.ubuntu.com.  If it is not the answer I would I attempt to directly connect to her for the purpose of file transfers.  She is running Ubuntu and I am on a Mac.

---

### Post by bvmou on 2007-08-29
There are a couple easy free ways to do this.  If she is on Ubuntu have her install the package 'openssh-server' with the command "sudo apt-get install openssh-server".

When you want to send her a file the syntax is "scp [with '-r' option if you want to recursively copy and recreate folders] /local/file.format [email]username@hercomputer.herd[/email]omain:remote-folder/"

If you want to ssh into her computer and manipulate files the command is "ssh username@hercomputer"

If you would like her to add a user for you the syntax is "sudo useradd -m 'your-username'"

If you want to get bunches of files and transfer lots of things use "sftp user@herdomain"


The trickier part can be getting to her computer since she is likely behind a router and you need to find her on the web.  There are a couple parts to this.  You may want to take advantage of a free service called dynamic dns, available at dyndns.com.  You choose a domain name like girlfriendupstate, and then you can locate her at girlfriendupstate.dyndns.org.  She will install a package on her computer (if she is not behind a nat router) called ddclient ("sudo apt-get install ddclient), or most modern routers have the capability of updating dyndns automatically.  You can do this through the web interface to the router, usually by pointing your browser to 192.168.1.1 or """.0.1 and finding the menu item.  A list of default router information is available here: [http://www.phenoelit-us.org/dpl/ll dpl.html]("http://www.phenoelit-us.org/dpl/dpl.html")

There is one more thing, also to be configured through that router interface.  SSH by default looks for port 22.  You need to enable port forwarding on the router, have it send requests to port 22 to her computer.  That is usually available as an option in the router.  Again, this is not necessary if she is not behind a router, in which case something like ddclient will be enough.

Feel free to pm if you would like clarification, or leave further questions here.

---

