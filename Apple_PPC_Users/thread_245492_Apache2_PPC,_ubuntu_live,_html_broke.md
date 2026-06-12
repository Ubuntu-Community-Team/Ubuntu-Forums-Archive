---
title: "Apache2 PPC, ubuntu live, html broke?"
date: 2006-08-27
forum: Apple PPC Users
---

### Post by jpowermacg5 on 2006-08-27
I'm running ubuntu 6.06.1 PPC, live CD on a PowerMacG5... and I'm having a problem with apache.

I installed apache2 via "apache2 php5-mysql libapache2-mod-php5 mysql-server" from synaptic package manager.

Well... it works... particially. Only php files actually work on my apache server.... html files appear blank when viewed thru apache via web browser.

Apache2, logs show 200 as the error code on html files.. which means it loaded OK.... but it's totally blank.. when viewing even the apache-default folder.

```
192.168.1.1 - - [27/Aug/2006:22:32:58 -0400] "GET /apache2-default/ HTTP/1.1" 200 1457 "-" "Mozilla/5.0 (X11; U; Linux ppc; en-US; rv:1.8.0.5) Gecko/20060731 Ubuntu/dapper-security Firefox/1.5.0.5"
192.168.1.1 - - [27/Aug/2006:22:33:02 -0400] "GET /apache2-default/ HTTP/1.1" 206 1457 "-" "Mozilla/5.0 (X11; U; Linux ppc; en-US; rv:1.8.0.5) Gecko/20060731 Ubuntu/dapper-security Firefox/1.5.0.5"
192.168.1.1 - - [27/Aug/2006:22:33:03 -0400] "GET /apache2-default/ HTTP/1.1" 206 1457 "-" "Mozilla/5.0 (X11; U; Linux ppc; en-US; rv:1.8.0.5) Gecko/20060731 Ubuntu/dapper-security Firefox/1.5.0.5"

```

Is there anything I need to configure for apache to show html files... I'm running this directly off the ubuntu Dapper Drake PPC cd, as it's the quickest way to load my back website direct from RAM.

If anyone knows what I need to do/install/edit/etc. please let me know. This is the only thing I havn't gotten to work "besides ibm-java-5.0 ppc for firefox as a plugin."

[edit]Also not worthy would be to mention that... .jpg files don't load either... just a link to the image loads in the browser.... something is seriously broke with apache when running live i think.

[edit2]gif files seem to load ok.. will test out different formats and see what works and what doesn't.

---

### Post by jpowermacg5 on 2006-08-31
Anybody ever get Apache working from the liveCD with html, and jpg file support and whatever else might be broke?

---

### Post by FAo10rK on 2007-11-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/95393](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/95393) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The answer of this problem is here :
[https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/95393](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/95393)

You just have to add this line in /etc/apache2/apache2.conf :
EnableSendfile Off

And it works !

Thanks a lot, bapoumba !

---

