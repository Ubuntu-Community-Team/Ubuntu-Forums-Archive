---
title: "Obscure Message, At Least To Me"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Imperial on 2007-07-11
Ubuntu v7.04 installed Desktop fine, and I didn't get any error messages when I installed Apache2 using the Synaptic Package Manager.

The problem I'm having is when I start Apache2, I told that it started, but I get this message:> Apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for server name.I've search my book and can find no information about this.

Any help would be appreciated.

Thank you.

---

### Post by dreadlord_chris on 2007-07-11
> **Imperial said:**
> Ubuntu v7.04 installed Desktop fine, and I didn't get any error messages when I installed Apache2 using the Synaptic Package Manager.

The problem I'm having is when I start Apache2, I told that it started, but I get this message:I've search my book and can find no information about this.

Any help would be appreciated.

Thank you.

edit the httpd.conf file

Under section 2: main server configuration.

unhash # ServerName ....:80

and change the name after the ServerName to your FQDN name.

( hou can type hostname at the command line to see you server name)

---

### Post by Imperial on 2007-07-11
Thank you for the reply.

My /etc/apache2/httpd.conf is empty!

Is there another httpd.conf that I am not finding?

---

### Post by Imperial on 2007-07-11
After repeatedly doing fresh installs (about 7 times) and every time ending up with a httpd.conf that is empty, I must conclude that the Synaptic Package Manager must have a bug.

I finally did a lamp install using xampp-linux-1.6.2. This seemed to work alright with only minor problems.

Does anybody know if my assumption about there being a bug in the Synaptic Package Manager when installing Apache2 in the Ubuntu Desktop v7.04?

---

### Post by avik on 2007-07-11
Apache 2 doesn't use httpd.conf by default, but I believe you can still look around near that file for other .conf files.  One of them will have the desired settings.

---

### Post by Imperial on 2007-07-11
That's interesting.> The first thing that httpd does when it is invoked is to locate and read the configuration file httpd.conf. The location of this file is set at compile-time, but it is possible to specify its location at run time using the -f command-line option as in

/usr/local/apache2/bin/apachectl -f /usr/local/apache2/conf/httpd.conf

If all goes well during startup, the server will detach from the terminal and the command prompt will return almost immediately. This indicates that the server is up and running. You can then use your browser to connect to the server and view the test page in the DocumentRoot directory and the local copy of the documentation linked from that page.
This is from [http://httpd.apache.org/docs/2.2/invoking.html]("http://httpd.apache.org/docs/2.2/invoking.html")

Please note that that is for v2.2

---

### Post by dreadlord_chris on 2007-07-13
> **Imperial said:**
> After repeatedly doing fresh installs (about 7 times) and every time ending up with a httpd.conf that is empty, I must conclude that the Synaptic Package Manager must have a bug.

  I finally did a lamp install using xampp-linux-1.6.2. This seemed to work alright with only minor problems.

  Does anybody know if my assumption about there being a bug in the Synaptic Package Manager when installing Apache2 in the Ubuntu Desktop v7.04?

 heh... sorry about that, spaced the Apache*2* part - the config file is (ironically enough) /etc/apache2/apache2.conf

 and no, that empty httpd.conf that keeps getting installed is not a bug - it's a *feature* :guitar:*it's there for backward compatibility...
 .wysiwyg { background-attachment: scroll; background-repeat: repeat; background-position: 0% 0%; background-color: #ffffff; background-image: none; color: #666666; font-family: "Arial [monotype]", "Arial [monotype]", "Helvetica [Adobe]", "Arial [monotype]"; font-style: normal; font-variant: normal; font-weight: 400; font-size: 10pt; line-height: normal } p { margin: 0px; }

---

