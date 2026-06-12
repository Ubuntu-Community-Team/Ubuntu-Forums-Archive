---
title: "Bind 9 Master files not found"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by quicksilver1234 on 2007-07-09
Hi All,
I"m trying to install Bind 9.
I keep getting errors like 
```
zone mydomain.com/IN loading master file named.mydomain.com: file not found 
```

I've got /etc/bind/named.conf.options with
```
directory "/var/cache/bind" 
```

I've got my zone files in /var/cache/bind/
So why does it keep saying file not found? What do i need to do, to trouble shoot this?
If my path is bad, how do I find where it's looking?
The files have permissions of Owner:root Group: bind (read only) Could it be a permissions thing?
-Silver

---

### Post by quicksilver1234 on 2007-07-09
I made the zone file permissions of 777 - read, write, execute, Owner - Root, Group - Bind,  and it still couldn't find the file.

---

### Post by shrift on 2007-07-09
what are you doing when you get those errors? Can you post some of the commandline code that's leading up to the errors?

---

### Post by quicksilver1234 on 2007-07-10
Hi,
I hope this helps.

Error log
```
Jul  9 20:14:16 bluejumpingfrog named[3844]: starting BIND 9.3.2 -u bind -t /var/lib/named
Jul  9 20:14:16 bluejumpingfrog named[3844]: found 1 CPU, using 1 worker thread
Jul  9 20:14:16 bluejumpingfrog named[3844]: loading configuration from '/etc/bind/named.conf'
Jul  9 20:14:16 bluejumpingfrog named[3844]: /etc/bind/named.conf.options:42: option 'fetch-glue' is obsolete
Jul  9 20:14:16 bluejumpingfrog named[3844]: listening on IPv4 interface lo, 127.0.0.1#53
Jul  9 20:14:16 bluejumpingfrog named[3844]: listening on IPv4 interface eth0, 12.34.56.83#53
Jul  9 20:14:16 bluejumpingfrog named[3844]: listening on IPv4 interface eth0:1, 12.34.56.84#53
Jul  9 20:14:16 bluejumpingfrog named[3844]: listening on IPv4 interface eth0:2, 12.34.56.85#53
Jul  9 20:14:16 bluejumpingfrog named[3844]: both "recursion no;" and "allow-recursion" active
Jul  9 20:14:16 bluejumpingfrog named[3844]: command channel listening on 127.0.0.1#953
Jul  9 20:14:16 bluejumpingfrog named[3844]: command channel listening on ::1#953
Jul  9 20:14:16 bluejumpingfrog named[3844]: zone 0.in-addr.arpa/IN: loaded serial 1
Jul  9 20:14:16 bluejumpingfrog named[3844]: zone 127.in-addr.arpa/IN: loaded serial 1
Jul  9 20:14:16 bluejumpingfrog named[3844]: zone 0.0.127.in-addr.arpa/IN: loading master file named.local: file not found
Jul  9 20:14:16 bluejumpingfrog named[3844]: zone 255.in-addr.arpa/IN: loaded serial 1
Jul  9 20:14:16 bluejumpingfrog named[3844]: zone bluejumpingfrog.com/IN: loading master file named.bluejumpingfrog.com: file not found
Jul  9 20:14:16 bluejumpingfrog named[3844]: zone localhost/IN: loaded serial 1
Jul  9 20:14:16 bluejumpingfrog named[3844]: running
```

/etc/bind/named.conf
```
include "/etc/bind/named.conf.options";
zone "." {
	type hint;
	file "/etc/bind/db.root";
};
zone "localhost" {
	type master;
	file "/etc/bind/db.local";
};
zone "127.in-addr.arpa" {
	type master;
	file "/etc/bind/db.127";
};
zone "0.in-addr.arpa" {
	type master;
	file "/etc/bind/db.0";
};
zone "255.in-addr.arpa" {
	type master;
	file "/etc/bind/db.255";
};
include "/etc/bind/named.conf.local";
```

/etc/bind/named.conf.options
```
options {
	directory "/var/cache/bind";
	auth-nxdomain no;    # conform to RFC1035
	allow-recursion { localnets; };
        recursion no;
        fetch-glue no;
};
```

/etc/bind/named.conf.local
```

zone "bluejumpingfrog.com"{
        type master;
        file "named.johnpatten.com";
        notify yes;
};
zone "0.0.127.in-addr.arpa"{
        type master;
        file "named.local";
        allow-update { none; };
};
```

/var/cache/bind/named.bluejumpingfrog.com
```
$TTL 604800;
bluejumpingfrog.com.    IN      SOA  ns1.bluejumpingfrog.com.  webmaster.bluejumpingfrog.com. (
   2000021600 ; 
   86400 ;
   7200 ; 
   1209600 ; 
   604800 ) ; 
       IN A          12.34.56.83  
       IN NS         ns1.bluejumpingfrog.com.
       IN NS         ns2.bluejumpingfrog.com.
       IN MX    5    mail               ; 
ns1    IN A          12.34.56.84    ; 
ns2    IN A          12.34.56.85    ;
mail   IN A          12.34.56.83    ;
       IN MX    5    12.34.56.83    ;
www    IN CNAME      node1            ; 
```

---

### Post by quicksilver1234 on 2007-07-10
bump. anyone got any thoughts?
Does the zone files HAVE to end in .db? I assumed it was just plain text.  does db mean anything?

The examples use  
file "example.com.db";

[http://www.bind9.net/manual/bind/9.3.2/Bv9ARM.ch03.html#id2547350](http://www.bind9.net/manual/bind/9.3.2/Bv9ARM.ch03.html#id2547350)

---

