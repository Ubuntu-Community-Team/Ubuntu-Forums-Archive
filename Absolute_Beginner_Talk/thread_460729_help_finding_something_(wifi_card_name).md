---
title: "help finding something (wifi card name)"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by silentjudas on 2007-05-31
ok this
hp pavilion dv6225

what card does it use

i cant find it ANYWHERE! 

i need a company and name or whatnot to do this

[http://www.linux.com/article.pl?sid=06/09/05/2055232](http://www.linux.com/article.pl?sid=06/09/05/2055232)


please please please help!

---

### Post by 5-HT on 2007-06-01
Is it not listed in the product specs/manual that came with the notebook or on HPs site (there are multiple versions of the dv6225 so you'll have to check for your exact model)?

You can also try 'lspci'

---

### Post by Inxsible on 2007-06-01
yup
```
lspci
```
is  a much better way of finding out what hardware you have on your machine rather than trolling thru multiple websites and assuming you would have the same :)

---

### Post by khardbored on 2007-06-01
There are three different versions of that notebook.
HP Pavilion dv6225eu Notebook PC
HP Pavilion dv6225tx Notebook PC
HP Pavilion dv6225us Notebook PC

Which one is yours?
::edit::

Even the HP website doesn't list the model/manufacturer of the cars in any of the three models. Pretty lame. They all have generic "WLAN" for their model. I also tried checking out driver downloads for the cards on their website and that didn't yield any details as to what the mystery card is. How very lame of them.

---

