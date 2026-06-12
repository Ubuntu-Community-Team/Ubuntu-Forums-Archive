---
title: "VMware and Apache Webserver"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by cmuehlebach on 2007-07-19
hi there,

as salutation, i'm gonna play a song for all ubuntu forum users :guitar:
i may have to say that my english isn't very good, because it isn't my native language

i've installed VMWare on my Ubuntu 6.06. 
i used this tutorial to install vmware: [http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

..it runs great!

now, my chef "told" me to add an apache webserver to the same system. he doesn't give me more information, and thats why i'm here :)

i don't understand what the sense of "VMWare cooperating with apache" is?
can i run vmware on httpd?


is there a tutorial about that? 

i'm really happy and thankful for any help!

---

### Post by ihristov on 2007-07-19
I am not sure what the question is.

Are you asking how to install apache within the host or withing a particular virtual machine that happens to be running Ubuntu?

If you are asking on how to install the web interface to VMWare, this is a different story.

What version of Ubuntu are we talking about here? 6.06?

---

### Post by cmuehlebach on 2007-07-20
hi,

i run ubuntu 6.06.

on this ubuntu system i have installed vmware server. my chef wants that i install apache webserver on the same system too. -> thats no problem, i think. but whats next? can i run vmware-server on apache? or can they communicate together?

look at this: [http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)
on this link, in the comments, a guy wrote this:

> The httpd deamon has difficulties to write to /var/run/vmware/ and could not create the httpd directory.

solution from the forums of vmware:

add this at the end of /etc/init.d/rc

 # vmware httpd fix <<start>>

mkdir /var/run/vmware/httpd/
chown www-data /var/run/vmware/httpd
chgrp nogroup /var/run/vmware/httpd
chmod 700 /var/run/vmware/httpd
/etc/init.d/httpd.vmware start

# vmware httpd fix <<end>>

what does this mean? does vmware server already have a webserver? or had this guy installed apache too?



greetings

cmuehlebach

---

### Post by ihristov on 2007-07-20
When you install the VMWare Server you can launch the executable "vmware", this is the "VMware Server Console" which is a normal GUI application. With the "VMware Server Console" you can create new VM, start existing VM, etc.

If you want to manipulate VM from a remote system you can:

1) install the "VMware Server Console" application on the remote machine for the corresponding platform (the Windows version if the remote system is Windows, or the Linux version if it's Linux)

or

2) install on the Linux host the web version of the "VMware Server Console" which would allow you to simply launch a web browser on the remote system, hit a specific URL and "have" a "VMware Server Console" within the browser. In other words it saves you the requirement to have to install the "VMware Server Console" client on the remote system.

In order to install solution 2) you need to install Apache first and then follow the instructions from VMWare on where and how to install the VMWare stuff (I think it's written in Perl).

Having said that I have never installed the web version of "VMware Server Console", because I never needed it.

---

