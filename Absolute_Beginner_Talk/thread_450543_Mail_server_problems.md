---
title: "Mail server problems"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by tipalm73 on 2007-05-21
I'll get more descriptive of problem as I go.

Im trying to configure a mail server via a howto on web. I am on comcast.

My first question is:

Is there anywhere i use the hds1.spfldbk1.cmcast.net? I use my dyndns name mostly mywebsit.mine.nu... but I havent had much success.

Any advice tips? I just reloaded EVERYTHING so as I reconfigure I'll be more specific.

Thanks in advanced.
\\O/

---

### Post by Cypher on 2007-05-21
I'm sorry, you're going to have a be a little descriptive about what your problem/question is?

I see a mention of a "howto on web" with no link. I see your 'hostname' from Comcast and DynDNS mentioned.

What exactly are you trying to accomplish?

---

### Post by ruy_lopez on 2007-05-21
I don't know what server you are running (postfix?, sendmail?) but some ISP's (AOL) block port 25 to third-party email servers. Also other mail servers won't accept your email unless there is a DNS PTR entry reverse mapping your IP to your hostname. Dynamic DNS usually only sets up the A record, so that might be a reason. Have you set up the Dynamic DNS service to have an MX entry? What are your mail logs saying?

---

### Post by tipalm73 on 2007-05-21
I am going to be running postfix.

Here is link to the setup I am using: [http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)

I am starting over because the first setup would work internally, but not externally

I am being vague cause I started over. At this point my question is do I need to use the the isp address anywhere in the config? By isp address I mean the hdsn1.spfldbk1.comcast.net.

Im installing the programs from work so tomorrow I can provide a better idea. I am just curious about that comcast address.

Thanks in advanced, sorry I am a noob =]

---

### Post by ruy_lopez on 2007-05-21
You need to setup the dynamic dns service so that it has a valid MX entry. As for your ISP's hostname, you shouldn't need that. What you can do, is include your ISP's email address, so that mail sent from your server will have your ISP's email address.

In other words, if your normal email address is "tipalm73@comcast.net" or something like that, include this in your "/etc/postfix/main.cf" file:

```
smtp_generic_maps = hash:/etc/postfix/generic
```

And in the file "/etc/postfix/generic" include:

```
[your local username]@[your local hostname]            [your ISP username]@[your ISP hostname]
i.e.
tipalm73@ubuntu_box              tipalm@comcast.com
```

Important! Once you've done this, you have to run this:

```
sudo postmap /etc/postfix/generic
sudo postfix reload
```

You should then be able to send mail masquerading as your ISP email address straight from your local machine.

If you want to receive mail, you must have a valid MX entry setup with the dyndns.

---

### Post by tipalm73 on 2007-05-21
Thanks for advice I'll try it.

On dyndns I do have it set to myserver.mine.nu. I'll keep you posted.

Thanks again.

---

### Post by ruy_lopez on 2007-05-21
I just ran DIG myserver.mine.nu

```
myserver.mine.nu      14400      IN      A     127.0.0.1
myserver.mine.nu                        IN     MX
```

That'll be why you can only send mail locally. 127.0.0.1 is the loopback address. I've never used dyndns myself (I use no-ip). But isn't there some sort of software you run which tells dyndns which dynamic ip you've been assigned. Before configuring your mail server, you should concentrate on getting dyndns to work properly.

Since I'm unfamiliar with the dyndns setup I'm afraid I'll have to defer help until you've got that configured.

This command will tell you the ip that is assigned to myserver.mine.nu

```
dig myserver.mine.nu
```

---

### Post by tipalm73 on 2007-05-21
its actually tipalm.mine.nu, I was being sneaky =]

so I used dig and this is what I got:

```
 
; <<>> DiG 9.3.4 <<>> tipalm.mine.nu
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 25087
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;tipalm.mine.nu.                        IN      A

;; ANSWER SECTION:
tipalm.mine.nu.         60      IN      A       24.147.178.158

;; Query time: 29 msec
;; SERVER: 68.87.71.226#53(68.87.71.226)
;; WHEN: Mon May 21 20:54:51 2007
;; MSG SIZE  rcvd: 48

```

---

### Post by ruy_lopez on 2007-05-22
You look to be all set up, in terms of DNS. I see a valid MX record.

As for the configuration of postfix, first try and see if you can receive mail. Usually its easier to receive mail, than send mail. There are lots of things that can go wrong with sending mail (unfortunately, sometimes they are other people's fault).

Also check out the postfix documentation for info on specific configuration terms:

[http://www.postfix.org/documentation.html](http://www.postfix.org/documentation.html)

Let us know if you run into any problems.

---

### Post by tipalm73 on 2007-05-22
Thanks for all the advice. I will update this if I get it to work =]

One question though, how can you see the valid MX entry? When I dig tipalm I see nothing for MX.

Thx again.

---

### Post by ruy_lopez on 2007-05-22
For MX type this:

```
dig MX tipalm.mine.nu
```

best of luck.

---

