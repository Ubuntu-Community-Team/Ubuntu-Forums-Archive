---
title: "how can I see the source code of an application?"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by h-town on 2008-03-25
In the same way I can see the code of a website.. Do I need a special program or can I do this through a GUI from Ubuntu?

---

### Post by Oldsoldier2003 on 2008-03-25
> **h-town said:**
> In the same way I can see the code of a website.. Do I need a special program or can I do this through a GUI from Ubuntu?

in Firefox its View> Page Source (or CTRL + U) but this will only give you the parsed source. If you want to see the actual source of a dynamically generated web page you are SOL if the web server is properly configured.

---

### Post by h-town on 2008-03-25
What I mean is how can i see the code of an application like Gimp.

---

### Post by pseudo-random on 2008-03-25
When you have a program you have its compiled form. The source code is totally different. Fortunately with open source you can go and download the gimp source code and are free to edit it.
If you want to peek into a closed source program then thats reverse-engineering and you'll need a debugger/hex editor to do that.

---

### Post by Oldsoldier2003 on 2008-03-25
> **h-town said:**
> What I mean is how can i see the code of an application like Gimp.

if an application is truly GPL you can download the source code from the applications main website. GIMP's source can be downloaded at [http://www.gimp.org/downloads/](http://www.gimp.org/downloads/)

---

### Post by h-town on 2008-03-25
That's cool. I was reading about those $100 laptops that run on linux and you can see the code of any program with the touch of a button or right click or something. I was curious if ubuntu had a similiar feature.. thanks.

---

### Post by pedro_orange on 2008-03-25
If the package you require the source for is in the Repos.

Then just do a:

```
sudo apt-get source <packagename>
```

Without the <>'s ofc.

---

