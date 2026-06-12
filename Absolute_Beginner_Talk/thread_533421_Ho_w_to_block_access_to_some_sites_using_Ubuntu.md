---
title: "Ho w to block access to some sites using Ubuntu?"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by tico on 2007-08-23
Does anybody know how could I prevent Ubuntu users to access some specific sites?

Thanks

---

### Post by moffa on 2007-08-23
Not sure of the best way but I would add them to my hosts file under 127.0.0.1.

The hosts file is located in /etc/hosts but if they have root access to the computer, they could always remove it.

---

### Post by LowSky on 2007-08-23
You mean for internet sites in firefox?

Try this 

[https://addons.mozilla.org/en-US/firefox/addon/3145]("https://addons.mozilla.org/en-US/firefox/addon/3145")

---

### Post by Hobo Joe on 2007-08-23
There is an addon for Firefox that does this. 

I can't remember the name off the top of my head but it's something like 'blockit'.

---

### Post by asmoore82 on 2007-08-23
> **moffa said:**
> Not sure of the best way but I would add them to my hosts file under 127.0.0.1.

The hosts file is located in /etc/hosts but if they have root access to the computer, they could always remove it.

I second that.

---

### Post by tico on 2007-08-24
> Not sure of the best way but I would add them to my hosts file under 127.0.0.1.

The hosts file is located in /etc/hosts but if they have root access to the computer, they could always remove it.

It works fine.

Thanks.

---

### Post by tico on 2007-09-28
Continuing this topic:

If I want to block orkut, I add [www.orkut.com](www.orkut.com) to my hosts file under 127.0.0.1 (/etc/hosts) and it apparently works. I know that you can access orkut using another mirror addresses that point to [www.orkut.com](www.orkut.com) ([http://images.orkut.com](http://images.orkut.com) etc.). Is there a way to block access to v.g orkut without needing do find out every new phantom/mirror address that pops up every day?

Thanks.

---

### Post by Malibu Illusion on 2007-09-28
If you're looking to block specific sites you could always set up a box with Squid Proxy/Squidguard and route internet access through this box.

You may wish to research this.

---

### Post by HermanAB on 2007-09-28
You can get a very good blocking hosts file here:
[http://everythingisnt.com/hosts.html](http://everythingisnt.com/hosts.html)

The very same thing works on Windoze and Linux.

Cheers,

Herman

---

### Post by crjackson on 2007-10-24
> **HermanAB said:**
> You can get a very good blocking hosts file here:
[http://everythingisnt.com/hosts.html](http://everythingisnt.com/hosts.html)

The very same thing works on Windoze and Linux.

Cheers,

Herman

Awesome..  Thanks for the link...

---

### Post by Mishal on 2008-02-23
I was wondering if there is a way to block all proxy sites too.

What's the point of blocking a site if it can be accessed using a proxy website anyway?

Anyone has ideas?

Can I do something like:
127.0.0.1 [www.proxy****.com](www.proxy****.com)
to block all sites which contain the word 'proxy'? If not, how do I do it?

---

