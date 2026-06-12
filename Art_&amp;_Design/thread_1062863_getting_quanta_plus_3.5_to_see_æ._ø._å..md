---
title: "getting quanta plus 3.5 to see æ. ø. å."
date: 2009-02-07
forum: Art &amp; Design
---

### Post by Drenriza on 2009-02-07
When i make a page in quanta plus 3.5, it does not know how to see letters æ. ø. å. So when i save the page into index.html it displays it like Ã¦Ã¸Ã¥.

I've been in :settings->configure quanta plus->environment: and set default character encoding to utf8. so whats going wrong?.

Thanks for any help in advance.

---

### Post by alex.rayu on 2009-02-09
You should set both IDE to UTF8 and the page charset to UTF8 in the <meta> tag. I use Geany and Aptana studio.

---

### Post by Drenriza on 2009-02-10
do you know where i find these ide & meta places?

because i've looked everywhere and can't really find it.

---

### Post by alex.rayu on 2009-02-10
I am attaching a sample empty html file with the required meta tag included in the head section. 

As for Quanta IDE, I don't use it so somebody else should comment.

---

### Post by AJB2K3 on 2009-02-10
> **Drenriza said:**
> do you know where i find these ide & meta places?

because i've looked everywhere and can't really find it.

have you tryed 
[www.wc3.org]("http://www.wc3.org") or [http://www.w3schools.com]("http://www.w3schools.com")
this is from my site and its the first line to be written before any html.
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
      "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
```
[COLOR="Red"]<head> tag is just to show its position in the page code.[/COLOR]

---

### Post by Drenriza on 2009-02-12
> **AJB2K3 said:**
> have you tryed 
[www.wc3.org]("http://www.wc3.org") or [http://www.w3schools.com]("http://www.w3schools.com")
this is from my site and its the first line to be written before any html.
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
      "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
```
[COLOR="Red"]<head> tag is just to show its position in the page code.[/COLOR]


Thanks, this helped me alot and now i can see
æ. ø .å in the text

---

### Post by AJB2K3 on 2009-02-12
> **Drenriza said:**
> Thanks, this helped me alot and now i can see
æ. ø .å in the text

I'm glad I was able to help you with your issue.

---

