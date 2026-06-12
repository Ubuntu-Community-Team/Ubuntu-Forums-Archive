---
title: "view php in firefox browser"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by dynoweb on 2007-07-04
How do you view php documents in firefox browser?

---

### Post by Malibu Illusion on 2007-07-04
The Firefox browser should open PHP documents by default, without you adjusting anything.  PHP outputs are, essentially, HTML.  The scripts execute server-side.

This very forum is using PHP; if you can see this in the browser in question then it's opening PHP documents correctly.

---

### Post by coolen on 2007-07-04
As in...the actual PHP file? You don't.
PHP files are processed by the HTTP server, and the results sent to the browser. You don't see the PHP text, just the resulting HTML.

---

### Post by dynoweb on 2007-07-04
> **coolen said:**
> As in...the actual PHP file? You don't.
PHP files are processed by the HTTP server, and the results sent to the browser. You don't see the PHP text, just the resulting HTML.

so how do i do that so i can see th result?

---

### Post by avik on 2007-07-04
> so how do i do that so i can see th result?

You can't.

 Unless I suppose you ask the webmaster for the files... The point is the web browser never sees the PHP because it isn't sent the PHP.

---

### Post by dynoweb on 2007-07-04
> **avik said:**
> You can't.

 Unless I suppose you ask the webmaster for the files... The point is the web browser never sees the PHP because it isn't sent the PHP.

i am the webmaster i just want to know how to view the results of my php in the browser.

---

### Post by Taliskerd on 2007-07-04
You need a web server that is set up to process php documents.
(If I remember correctly that's described in the php install documents)

---

### Post by Mickeysofine1972 on 2007-07-04
Hey

If your running this code on localhost through apache then your mime types are screwed up because you might not have all the right modules for apache installed.

If you check for php in synaptic and install andthing to do with php and apche you should see it start to work

Mike

---

### Post by hyper_ch on 2007-07-04
In order to run your local .php script files you need to install a webserver (e.g. apache2) and php4/5...

If you chose apache you then need, after the install of php4/5 to enable it by issuing:

```

sudo a2enmod php4

```
or
```

sudo a2enmod php5

```

---

### Post by abinavkris on 2008-03-17
just rename test.php to something like test.htm or test.html :KS

---

