---
title: "google anyaltics"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-01-23
I cant remember how to stop google anyaltics from Connecting when viewing a web page..can anyone help?

---

### Post by y-lee on 2008-01-23
I think this works. I found it on a blog a couple days ago and applied it to my system. 

type
```
gksudo gedit /etc/hosts

``` into the terminal.

At the bottom of the file, add this:
```
# BLOCK GOOGLE ANALYTICS
127.0.0.1 www.google-analytics.com
127.0.0.1 ssl.google-analytics.com
127.0.0.1 google-analytics.com
```

Save the file.

---

### Post by rendon on 2008-01-23
[http://www.google.com/support/googleanalytics/?hl=en](http://www.google.com/support/googleanalytics/?hl=en)

maybe...

sounds like a google question...

---

### Post by benny bronx on 2008-01-23
In the alternative, you could download the Firefox extensions Noscript and Customizegoogle.  Noscript blocks it by default and CG has an option, under the privacy tab, to block it.

---

### Post by y-lee on 2008-01-23
I use Customize Google and never paid attention to that option. thanks.

---

