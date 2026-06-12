---
title: "Request for help with a failed DNS bind9 config on ubuntu on linode server"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by simonshields on 2008-04-09
Hi All

I'm using ubuntu on a linode server. I've tried to setup a DNS server. I followed the instructions in 
[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)

/etc/init.d/bind9 restart fails
/etc/init.d/bind9 restart
 * Stopping domain name service... bind                                                           rndc: connect failed: 127.0.0.1#953: connection refused
                                                                                           [fail]
 * Starting domain name service... bind                                                    [fail]

The domain is shieldsenterprises.com.au. When you do a dig shieldsenterprises.com.au it says

root@none:/etc/bind # dig shieldsenterprises.com.au

; <<>> DiG 9.4.1-P1 <<>> shieldsenterprises.com.au
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 14682
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;shieldsenterprises.com.au.     IN      A

;; ANSWER SECTION:
shieldsenterprises.com.au. 86400 IN     A       203.17.36.111

;; AUTHORITY SECTION:
shieldsenterprises.com.au. 43200 IN     NS      ns1.enetica.com.au.
shieldsenterprises.com.au. 43200 IN     NS      ns2.enetica.com.au.

;; ADDITIONAL SECTION:
ns1.enetica.com.au.     76646   IN      A       203.17.36.33
ns2.enetica.com.au.     77992   IN      A       203.17.36.4

;; Query time: 254 msec
;; SERVER: 64.5.53.6#53(64.5.53.6)
;; WHEN: Wed Apr  9 00:24:00 2008
;; MSG SIZE  rcvd: 135

The /etc/bind/named.conf.local says
root@none:/etc/bind # more named.conf.local
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
zone "shieldsenterprises.com.au" {
type master;
file "/etc/bind/zones/shieldsenterprises.com.au.db";
};
# linode ipaddress 67.18.208.78
zone "208.18.67.in-addr.arpa" {
file "/etc/bind/zones/rev.208.18.67.in-addr.arpa";
};

my named.conf.options says

root@none:/etc/bind # more named.conf.options
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you might need to uncomment the query-source
        // directive below.  Previous versions of BIND always asked
        // questions using port 53, but BIND 8.1 and later use an unprivileged
        // port by default.

        // query-source address * port 53;

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        forwarders {
                203.17.36.33;
                203.17.36.4;
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

my zones/rev.208.18.67.in-addr.arpa says
root@none:/etc/bind/zones # more rev.208.18.67.in-addr.arpa
//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS server.
// in my case, it.s 1, as my IP address is 192.168.0.1.

@ IN SOA ns1.shieldsenterprises.com.au. admin.shieldsenterprises.com.au. (
2007031001;
28800;
604800;
604800;
86400
)

IN NS ns1.shieldsenterprises.com.au.
78 IN PTR shieldsenterprises.com.au

my zones/shieldsenterprises.com.au.db says
root@none:/etc/bind/zones # more shieldsenterprises.com.au.db
// replace example.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server

shieldsenterprises.com.au. IN SOA ns1.shieldsenterprises.com.au. admin.shieldsenterprises.com.au. (
2007031001
28800
3600
604800
38400
)

// Replace the following line as necessary:
// ns1 = DNS Server name
// mail = mail server name
// example.com = domain name
shieldsenterprises.com.au. IN NS ns1.shieldsenterprises.com.au.
shieldsenterprises.com.au. IN MX 10 mail.shieldsenterprises.com.au.

// Replace the IP address with the right IP addresses.
www IN A 67.18.208.78
mta IN A 67.18.208.78
ns1 IN A 67.18.208.78


Maybe I haven't understood the process correctly,

Any help sincerely appreciated.

Simon

---

### Post by RealPSL on 2008-04-13
Well let us start that first error. Are you running the ```
/etc/init.d/bind9 restart
``` as the root user or with ```
sudo /etc/init.d/bind9 restart
``` as in looking at the error it seems to be having trouble binding to 953 which is the rndc port.

---

