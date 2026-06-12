---
title: "Cannot connect to Internet"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by kvay101 on 2007-01-01
New to Linux, installed Ubuntu 5.1.0 from CD.  Everything seems to work, except I cannot conncet to the internet.  I have a router that assigns IP via DHCP and that worked.  My linux machine can see my other Windows boxes, but when I put in an Internet address (Google.com  for instance) into Firefox I get "the document contains no data"  This happens with name or IP address.  I  can ping ebsite IPs from terminal command line and get responses.  I've run out of ideas.

---

### Post by ctsdownloads on 2007-01-01
Personally, I would start off fresh with Ubuntu 6.06 Dapper Drake. Then assuming you are simply using a typical ethernet card (NIC), you should be automatically detected unless you have run out of IP addies on the network. Don't laugh, it happens to those who reduce their available number from the default number to something much less than that. ;)

---

### Post by jonathan.lees on 2007-01-01
Chcek to see if your DNS is working ok, open a terminal and type:

```

dig google.com

```

And compare it against mine:

> 
; <<>> DiG 9.3.2 <<>> google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 37903
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.                    IN      A

;; ANSWER SECTION:
google.com.             167     IN      A       64.233.187.99
google.com.             167     IN      A       64.233.167.99
google.com.             167     IN      A       72.14.207.99

;; Query time: 456 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Mon Jan  1 16:36:25 2007
;; MSG SIZE  rcvd: 76


You could also try using wget. Try something like:

```

wget http://slashdot.org

```

It should return a file called index.html, which it
is the main page of slashdot, but without all the images.

You could also try:

```

wget -p http://slashdot.org

```

which will fetch the front page and its requisities, i.e., all the images
needed to display the page.

---

### Post by kvay101 on 2007-01-01
The dig google.com returned results the same as yours.   after running wget [http://slashdot.org](http://slashdot.org), it resolves and connectst to 66.35.250.150, then has "HTTP request sent, awaiting response... 200 OK
Length: Unspecified [text/html]

[<=>                                                  ] 0       --.--K/s


the <=>  goes from left to right in the brackets indefinitely

---

### Post by mgmiller on 2007-01-01
I have to agree with ctsdownloads.  Do a clean install of Dapper 6.06.  Good chance it will "just work".  I remember I used to have network issues on Ubuntu 5.x that took some fiddling to get going.  As of 6.06, I had clear sailing.

---

### Post by jonathan.lees on 2007-01-01
Did wget not download the index.html?

---

### Post by jonathan.lees on 2007-01-01
Here's what I get when I issue a wget [http://slashdot.org](http://slashdot.org)

> 
wget [http://slashdot.org](http://slashdot.org)
--18:05:01--  [http://slashdot.org/](http://slashdot.org/)
           => `index.html'
Resolving slashdot.org... 66.35.250.150
Connecting to slashdot.org|66.35.250.150|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [      <=>                            ] 67,769        38.93K/s             

18:05:05 (38.84 KB/s) - `index.html' saved [67769]


---

### Post by jonathan.lees on 2007-01-01
Maybe mgmiller etc are right, you might wanna upgrade. Your DNS seems to be ok, you could also look at /etc/resolv.conf and confirm that is correct.

---

### Post by kvay101 on 2007-01-01
I really have nothing to lose, since I have nothing on this machine, I'll upgrade.   
Thanks for help.

---

### Post by kvay101 on 2007-01-20
Well had errors downloading and creating cd off another machine, so sent for cd of 6.06.1.  Loaded it and installed.  I get the exact same results as I did with earlier version.  Now what?

---

