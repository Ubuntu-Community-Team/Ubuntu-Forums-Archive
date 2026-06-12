---
title: "new to servers"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by zeusdo on 2006-06-27
I posted this thread in the server section but I didn't get any response so I figured I'd try here.

First of all, I'm a total newbie when it comes to servers. I'm hoping someone can point me in the right direction. I run a small company and currently we have 4 computers all running WinXP. We use Quickbooks Online edition for our accounting and we want to buy the premiere desktop version of Quickbooks but of coarse we will loose the ability to access it from anywhere. Here is what I'm thinking.

If we use one of our computers as a server, then we can still all have access. At the same time, this will also help us with file sharing. So basically, we will all have the desktop version of Quickbooks on our PCs but the server will be hosting the application. Does this make sense?

If someone can point me in the right direction, weather it be a web site or a book to get, that would be great. Thanks.

---

### Post by mips on 2006-06-27
Quickbooks support a multiuser environment but you have to buy the 5-User version of premiere which is US$1400.

To setup such an environment you can use either a dedicated server or a desktop pc as a server for the data file.

Read the links below for more detailed info:
[http://www.quickbooks.com/support/networking/](http://www.quickbooks.com/support/networking/)
[http://quickbooks.intuit.com/product/accounting_software/premier_edition_financial_planning_tools.jhtml](http://quickbooks.intuit.com/product/accounting_software/premier_edition_financial_planning_tools.jhtml)

---

### Post by zeusdo on 2006-06-27
I understand the the deal with Quickbooks but what I'm trying to figure out is how to setup a simple file server.

---

### Post by halfvolle melk on 2006-06-27
You could try this
```
sudo apt-get install apache2
sudo apt-get install pure-ftpd
sudo adduser <someusername>
sudo vi /etc/passwd
```
and change
```
<someusername>:x:1000:1000:<somusername>,,,:/home/<someusername>:/bin/bash
```
to
```
<someusername>:x:1000:1000:<somusername>,,,:/home/<someusername>/./:/bin/bash
```
In /home/<somusername> you can than make public_html. All that goes there in on the web at x.x.x.x/~<somusername>

That gives you an ftp server and a webserver. Worked for me

Hope this helps.

---

### Post by zeusdo on 2006-06-27
Thank you for your response but I have no idea what that means. Did I mention that I have never worked with a server before. And once I do get it setup, do I install Quickbooks on the server or just host the data file there? And if so, how?
I'm such a total newb. Is there a set-by-step tutorial somewhere?

---

### Post by halfvolle melk on 2006-06-27
I only figured this out myself yesterday so the above is about all I know on servers.

Lets assume you've got an Ubuntu machine running, the one that needs to be the server. Click Applications -> Accessories -> Terminal. In this terminal just type the above commands. Maybe instead of vi you're more comfortable with Gedit, so you could use that. ie:
```
sudo gedit /etc/passwd
```
Adding /./ to the line as suggested above will prevent <someusername> from viewing the entire system/harddrive. Instead it can only access its own /home directory.

Furthermore I'll assume the IP of the server is 10.1.1.5 (or whatever). If you type the IP in your browser on another computer at that network, it will show the content of /var/www/cantremember which is some default page. In the home dir of each user that the server has, you can make the directory "public_html" the contents of which can be accessed from another machine through 10.1.1.5/~username.

As for the FTP part, apparently it just works!
edit: for instance "lftp username@10.1.1.5" or with your favourite client.

And I don't know the first thing about Quickbooks but for US$1400 I'd expect some service ;)

---

### Post by mips on 2006-06-27
halfvolle melk,

I don't think your suggestions are suitable for the OPs needs, he wants to install a product that only runs on a MS OS.


zeusdo,

Did you even look at the links I posted ???
The ones below could not be any clearer (even got screenshots), it tells you all the step you need to do, how to share folders etc. The 3rd link tells you the physical system requirements.

[http://www.quickbooks.com/support/networking/downloads/QuickBooks%202006%20Network%20Installation%20Guide.pdf](http://www.quickbooks.com/support/networking/downloads/QuickBooks%202006%20Network%20Installation%20Guide.pdf)
[http://www.quickbooks.com/support/networking/downloads/White%20Paper%20QB2006%20Network%20Configuration.pdf](http://www.quickbooks.com/support/networking/downloads/White%20Paper%20QB2006%20Network%20Configuration.pdf)
[http://www.quickbooks.com/support/faqs/qb2006/319478.html](http://www.quickbooks.com/support/faqs/qb2006/319478.html)

I suggest you contact QuickBooks tech support or alternatively pay someone to do the installation for you. Just read the guides above as it tells you everything you will need to know.

---

### Post by halfvolle melk on 2006-06-27
Oops, sorry. I think I got carried away when I read "how to setup a simple file server." :)

---

### Post by zeusdo on 2006-06-27
mips

Yes I have looked at those links in the past and I guess I was getting ahead of myself. It says that it should be on a Windows system so a Linux server is not my answer for a Quickbooks network. I'm just going to order the Quikbooks and try it out but I still want to play around with a server just for file storage and sharing.

---

### Post by FuturePast on 2006-06-27
As you have said, a Linux-based server is not appropriate for your Quickbooks setup.
If you do want to explore using an Ubuntu Linux server, you can download and burn a CD from [http://www.ubuntu.com/download]("http://www.ubuntu.com/download")
Just put the CD in the drive before booting and play around!

---

### Post by zeusdo on 2006-06-27
I will, thanks for your input.

---

