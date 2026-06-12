---
title: "Setting up BIND9"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by AutootuA on 2007-09-09
I'm  trying to setup bind9 on 6.06. I want to make sure that I have it configured correctly. The server will be used for email. The machine name is "mail" on my domain "nunyad.biz". Should nunyad.biz and mail.nunyad.biz both have a MX record???

**/etc/bind/named.conf.local**
```
//
// Do any local configuration here

        zone "nunyad.biz" {
                type master;
                file "db.nunyad.biz";
                allow-update { none; };
        };

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

```

**/var/cache/bind/db.nunyad.biz**
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     mail.nunyad.biz. admin.mail.nunyad.biz(
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      mail.nunyad.biz.
        IN      MX      10 mail.nunyad.biz.
        IN      A       192.168.254.160
mail    IN      A       192.168.254.160
www     IN      A       192.168.254.160

```

When ever I do a "nslookup" on mail.nunyad.biz and nunyad.biz I get:
```
Server:         192.168.254.160
Address:        192.168.254.160#53

Name:   mail.nunyad.biz
Address: 192.168.254.160


Server:         192.168.254.160
Address:        192.168.254.160#53

Name:   nunyad.biz
Address: 192.168.254.160


```

But when i run "host -t mx *domain*":
```
host -t mx nunyad.biz
nunyad.biz mail is handled by 10 mail.nunyad.biz.

host -t mx mail.nunyad.biz
mail.nunyad.biz has no MX record

```

**dig mx nunyad.biz**
```
; <<>> DiG 9.3.2 <<>> mx nunyad.biz
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 62767
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;nunyad.biz.                    IN      MX

;; ANSWER SECTION:
nunyad.biz.             604800  IN      MX      10 mail.nunyad.biz.

;; AUTHORITY SECTION:
nunyad.biz.             604800  IN      NS      mail.nunyad.biz.

;; ADDITIONAL SECTION:
mail.nunyad.biz.        604800  IN      A       192.168.254.160

;; Query time: 2 msec
;; SERVER: 192.168.254.160#53(192.168.254.160)
;; WHEN: Sun Sep  9 13:51:06 2007
;; MSG SIZE  rcvd: 79

```

dig mx mail.nunyad.biz
```
; <<>> DiG 9.3.2 <<>> mx mail.nunyad.biz
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 50962
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;mail.nunyad.biz.               IN      MX

;; AUTHORITY SECTION:
nunyad.biz.             604800  IN      SOA     mail.nunyad.biz. admin.mail.nunyad.biz.nunyad.biz. 2 604800 86400 2419200 604800

;; Query time: 2 msec
;; SERVER: 192.168.254.160#53(192.168.254.160)
;; WHEN: Sun Sep  9 13:52:34 2007
;; MSG SIZE  rcvd: 91

```

---

### Post by livinginx on 2007-09-09
I don't know a whole lot about configuring these programs individually as I am more the type to get a prebuilt package, but one of the problems that I see is you have all of your I.P. addresses set as a local private network.

That meaning that anybody outside of your router wouldn't be able to utilize your services.

Find out what you external I.P. address is, then you will use that I.P. for the MX records and the like.

---

### Post by HermanAB on 2007-09-09
The 192.168. range is not publicly routable.  Also, BIND is very finicky regarding syntax.  I would use:

mail.nunyad.biz.   IN A   1.2.3.4 

Also, remember to do the reverse PTR entry.  Many/most mail servers look for that and will refuse mail coming from a server with no reverse lookup.

Cheers,

H.

---

### Post by AutootuA on 2007-09-09
This server is behind a Firewall/NAT Device. I can access it with out a problem. I'm using Zimbra on this server and I need everything set perfectly for it to work correctly.

---

