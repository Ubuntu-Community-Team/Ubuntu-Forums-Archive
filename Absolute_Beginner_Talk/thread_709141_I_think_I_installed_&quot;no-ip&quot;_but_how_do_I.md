---
title: "I think I installed &quot;no-ip&quot; but how do I know if it's working?"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-02-27
I can't find any documentation on it... thus I don't know if there's a log file that I can check to see how it's working.

Is there a way I can "force" an update to do a test?

I don't want to have to wait for an IP change to see if it's working right.

---

### Post by hyper_ch on 2008-02-27
Installation:

```

sudo apt-get install noip2

```


Configuration:

```

sudo noip2 -C

```

---

### Post by benfindlay on 2008-02-27
If you already have no-ip installed, as opposed to no-ip2, its ```
sudo no-ip -C
``` then follow the prompts!

Hope this helps!

---

### Post by joesmith1234 on 2008-02-27
> **benfindlay said:**
> If you already have no-ip installed, as opposed to no-ip2, its ```
sudo no-ip -C
``` then follow the prompts!

Hope this helps!

Yea, I do this, but after entering my login and password, I get a message that says

Content-Type text/html

...and nothing else.

Then if I try to look at /etc/no-ip.conf there's nothing there...

---

### Post by joesmith1234 on 2008-02-27
> **hyper_ch said:**
> Installation:

```

sudo apt-get install noip2

```


Configuration:

```

sudo noip2 -C

```

Are you sure this package exists?

Ubuntu can't find either the no-ip2 or noip2 package...

---

### Post by benfindlay on 2008-02-27
Have you signed up for an account on the no-ip website and added a host/redirect to it?

---

### Post by Cope57 on 2008-02-27
> **joesmith1234 said:**
> Are you sure this package exists?

Ubuntu can't find either the no-ip2 or noip2 package...

It does, It is what I am using, but then again I am using Debian testing/sid

---

### Post by hyper_ch on 2008-02-27
> **joesmith1234 said:**
> Are you sure this package exists?

Ubuntu can't find either the no-ip2 or noip2 package...

It does:

```

hyper@xubi:~$ apt-cache search noip2
noip2 - client for dynamic DNS service
hyper@xubi:~$

```

Question is, in what repository...

It's in hardy:  [http://packages.ubuntu.com/hardy/noip2](http://packages.ubuntu.com/hardy/noip2)

But I was sure I had it somewhere on Gutsy also...

---

### Post by joesmith1234 on 2008-02-27
> **hyper_ch said:**
> It does:

```

hyper@xubi:~$ apt-cache search noip2
noip2 - client for dynamic DNS service
hyper@xubi:~$

```

Question is, in what repository...

It's in hardy:  [http://packages.ubuntu.com/hardy/noip2](http://packages.ubuntu.com/hardy/noip2)

But I was sure I had it somewhere on Gutsy also...

Is there any way to get it to Gutsy without having to compile?

---

### Post by joesmith1234 on 2008-02-27
> **benfindlay said:**
> Have you signed up for an account on the no-ip website and added a host/redirect to it?

Yea.  All of that works ok, and I can get to the computer from another PC.

Just right now, I'm trying to get the auto updater to work.

---

### Post by benfindlay on 2008-02-27
You have definietly added a host? What happened for me when I first started using it was that I had signed up, but not set up an host address (e.g. USERNAME.no-ip.org) to use, Until I did that, it kept giving me the error that you are getting

Hope this helps!

---

### Post by hyper_ch on 2008-02-27
you could download the hardy .deb file from the ubuntu packages page - but this is not recommended and I don't know if dependencies are met or whether it could break your system.

---

### Post by jeffus_il on 2008-02-27
I set up ip address with no-ip
I installed ip updater software (my router supports DDNS so I set it up there and don't need to run the app)
I have a machine with a ssh server running.
I opened a port on the router to accept incoming ssh and routed it to the ssh server.
I opened a terminal and did ```
ssh myname.hopto.org
``` and logged on to the machine.(it worked)
Of course you can also ping to test the address.

---

### Post by jeffus_il on 2008-02-27
ah! you want the ip address to change, that your service provider controls, call him and ask how you can cancel the lease given on the present address. I am sure that this differs between providers.

---

### Post by Meph1st0 on 2008-02-27
I think there might be an easy way to force your ISP to give you a new IP Address at least temporarily.  If your router supports it, you could change your MAC address (or mask it) and then reboot.  This mightl cause youre ISP to give you a new lease.

---

